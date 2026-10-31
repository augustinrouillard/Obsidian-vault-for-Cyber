---
share: true
---

```markdown
# Note: Decrypting GPG Files and Cracking GPG Passwords

## 1. Decrypting a GPG File

To decrypt a file encrypted with GPG:

```bash
gpg --decrypt file
```

- You will be prompted for the passphrase if the file is protected.
- The decrypted content will be displayed in the terminal (or you can redirect it to a file).

## 2. Cracking a GPG File with John the Ripper

If you don't know the passphrase, you can try to crack it using John the Ripper:

1. **Extract the hash from the GPG file:**

   ```bash
   gpg2john file > hash.txt
   ```

2. **Run John the Ripper with a wordlist:**

   ```bash
   john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
   ```

- John will attempt to brute-force the passphrase using the provided wordlist.

## Tips

- Make sure you have the necessary tools installed: `gpg`, `gpg2john`, and `john`.
- Use strong and relevant wordlists for better results.
- If you successfully crack the passphrase, use it with `gpg --decrypt` to access the file.

---

**Summary:**  
- Use `gpg --decrypt file` to decrypt GPG files if you know the passphrase.
- Use `gpg2john` and `john` to attempt to crack the passphrase if you don't know it.