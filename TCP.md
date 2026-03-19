---
share: true
---
```markdown
# Note: Connecting to HTTP Services with evil-winrm (TCP)

## What is evil-winrm?

- **evil-winrm** is a popular tool for connecting to Windows machines via the WinRM (Windows Remote Management) protocol.
- It is commonly used in penetration testing and CTFs to get a shell on a Windows target.

## How to Connect to a Service

To connect to a WinRM service (over HTTP) on a specific port:

```bash
evil-winrm -i [ip] -u [username] -p [password] -P [port]
```

- `-i`: Target IP address
- `-u`: Username
- `-p`: Password
- `-P`: Port number (default is 5985 for HTTP, 5986 for HTTPS)

## Example

```bash
evil-winrm -i 10.10.10.10 -u administrator -p 'SuperSecret123' -P 5985
```

## Tips

- Make sure the WinRM service is running and accessible on the target machine.
- If you get connection errors, check firewall rules and port numbers.
- evil-winrm can also upload/download files and run PowerShell commands interactively.

---

**Summary:**  
Use `evil-winrm -i [ip] -u [username] -p [password] -P [port]` to connect to a Windows machine over WinRM (HTTP) on a specific TCP port.