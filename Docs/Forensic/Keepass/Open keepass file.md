---
share: true
---

```markdown
# Note: Cracking KeePass Passwords with John the Ripper

## Accessing a KeePass Database

- To open a KeePass database (`.kdbx`), you usually need a **username** and a **password**.

## Brute-Force Attack with John the Ripper

### 1. Extract the Hash

Use `keepass2john` to extract the hash from your KeePass file:

```bash
keepass2john your_file.kdbx > hash_to_crack.txt
```

### 2. Crack the Password

Use John the Ripper with a wordlist (e.g., `rockyou.txt`) to brute-force the password:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```

## Tips

- Make sure you have both `keepass2john` and `john` installed.
- You can use other wordlists or custom rules for more advanced attacks.
- If you know part of the password or username, use it to optimize your attack.

---

**Summary:**  
Extract the hash from the KeePass database with `keepass2john`, then use John the Ripper to brute-force the password.