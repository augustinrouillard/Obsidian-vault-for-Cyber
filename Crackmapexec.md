---
share: true
---
```markdown
# Note: Using crackmapexec for SMB Enumeration

## What is crackmapexec?

- **crackmapexec** is a popular tool for enumerating and attacking SMB (Windows file sharing) services.
- It can be used to check credentials, enumerate shares, and find hidden files.

## Usage Example

If SMBv1 is not available, you can still use crackmapexec to test credentials and look for hidden files:

```bash
crackmapexec smb [IP] -u [login or path_to_loginlist] -p [path_to_passwordlist]
```

- `[IP]`: Target IP address.
- `-u`: Single username or path to a file with a list of usernames.
- `-p`: Path to a file with a list of passwords.

## What Can It Do?

- This tool is mainly used to:
  - Test login credentials against SMB shares.
  - Enumerate accessible shares and files.
  - **Find hidden files** on SMB shares (but not download or interact with them directly).

## Tips

- Use strong and relevant username/password lists for better results.
- If SMBv1 is disabled, crackmapexec will still attempt to enumerate using newer SMB versions.
- Combine with other tools (like `smbclient`) for further interaction if needed.

---

**Summary:**  
Use `crackmapexec smb [IP] -u [login or loginlist] -p [passwordlist]` to enumerate SMB shares and find hidden files, even if SMBv1 is not available.