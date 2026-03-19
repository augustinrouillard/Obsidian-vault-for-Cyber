---
share: true
---
```markdown
# Note: Anonymous FTP Connection

## How to Connect to an FTP Server as Anonymous

1. **Connect to the FTP server:**

   ```bash
   ftp 10.80.135.2
   ```

   - Replace `10.80.135.2` with the target server's IP address.

2. **Login as Anonymous:**

   - When prompted for a username, enter:
     ```
     anonymous
     ```
   - For the password, you can usually just press Enter or use any email address.

## Tips

- Anonymous FTP access allows you to connect without a registered account.
- You may have limited permissions (often only download, sometimes upload).
- Always check what files and directories are accessible after login.

---

**Summary:**  
Connect to an FTP server with `ftp <ip>`, then use `anonymous` as the username to attempt an anonymous login.

```