---
share: true
---
```markdown
# Note: SSH Connections and Cracking RSA Private Keys

## 1. Connect to a Server via SSH

To connect using a username and port:

```bash
ssh -p [port] [login]@[ip]
```

- Replace `[port]` with the SSH port (default is 22).
- Replace `[login]` with the username and `[ip]` with the server's IP address.

## 2. Connect with an RSA Private Key

If you have an RSA private key (e.g., `id_rsa`):

```bash
ssh -i /home/augustrain/.ssh/id_rsa [login]@[ip]
```

- `-i` specifies the path to your private key.

## 3. Transfer the RSA Key from the Target (with scp)

To copy a file (e.g., a private key) from the target machine to your local machine:

```bash
scp "username"@"IP_TARGET":"PATH_TO_FILE" .
```

- This will copy the file to your current directory.

## 4. Crack a Password-Protected RSA Private Key

If the private key is password-protected, you can try to crack it with John the Ripper:

1. Convert the key to a hash format:

   ```bash
   ssh2john id_rsa > id_rsa.hash
   ```

2. Run John the Ripper with a wordlist:

   ```bash
   john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa.hash
   ```

- If the password is found, use it to unlock the private key.

## 5. Connect Using the Cracked Key

Once you have the password (if needed), connect with:

```bash
ssh -i id_rsa [login]@[ip]
```

## Tips

- Always set correct permissions on your private key: `chmod 600 id_rsa`
- Use `scp` to transfer files securely between machines.
- Use strong wordlists for better chances when cracking passwords.

---

**Summary:**  
- Use `ssh` to connect to servers, optionally with a private key.
- Use `scp` to transfer files.
- Use `ssh2john` and `john` to crack password-protected SSH keys.