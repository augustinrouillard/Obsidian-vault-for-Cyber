---
share: true
---
```markdown
# Note: PHP Command Injection

## What is PHP Command Injection?

- **Command injection** is a vulnerability that allows an attacker to execute arbitrary system commands on the server through a vulnerable PHP script.
- This usually happens when user input is passed directly to a system function (like `system()`, `exec()`, or `shell_exec()`) without proper sanitization.

## How to Exploit

- The attacker injects commands via a URL parameter (often named `cmd`, `exec`, or similar).

### Example: Listing Files

```text
http://ip/index.php?cmd=ls
```
- This will execute the `ls` command on the server and display the output.

### Example: Reading Sensitive Files

To read the contents of the `/etc/passwd` file (common on Unix/Linux systems):

```text
http://ip/assets/index.php?cmd=cat%20/etc/passwd
```
- `%20` is the URL-encoded space character.

## Tips

- You can try other commands, such as `whoami`, `id`, `uname -a`, or even chain commands with `;` or `&&`.
- Always URL-encode special characters in your payloads.
- If output is filtered, try to redirect it to a file you can access (e.g., `; cat /etc/passwd > /var/www/html/passwd.txt`).

---

**Summary:**  
PHP command injection lets you execute system commands via vulnerable parameters, such as `?cmd=ls` or `?cmd=cat%20/etc/passwd`, to list files or read sensitive data.