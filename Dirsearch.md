---
share: true
---
```markdown
# Note: Using dirsearch for Directory and File Discovery

## What is dirsearch?

- **dirsearch** is a command-line tool for brute-forcing directories and files on web servers.
- Useful for discovering hidden or unlisted resources during web penetration testing.

## How to Use

To scan a specific URL for hidden directories and files:

```bash
dirsearch -u http://<ip-address>/assets/index.php
```

- Replace `<ip-address>` with the target server's IP or domain.
- This command will attempt to find additional files and directories under `/assets/index.php`.

## Example

If you know a file exists at `/assets/index.php`, you can use dirsearch to look for other files or directories in the `/assets/` path.

## Tips

- You can specify custom wordlists with the `-w` option.
- Use the `-e` option to specify file extensions (e.g., php, html, txt).
- Review the output for interesting or sensitive files that may not be directly linked.

---

**Summary:**  
Use `dirsearch -u http://<ip-address>/assets/index.php` to brute-force and discover hidden files or directories on a web server.