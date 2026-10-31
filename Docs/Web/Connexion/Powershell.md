---
share: true
---
```markdown
# Note: Searching for a File with PowerShell

## How to Search for a Flag File in PowerShell

To recursively search for a file named `flag.txt` on the C: drive:

```powershell
Get-ChildItem -Path C:\ -Recurse -Filter flag.txt -ErrorAction SilentlyContinue
```

- `Get-ChildItem`: Lists files and directories (like `ls` or `dir`).
- `-Path C:\`: Start searching from the root of the C: drive.
- `-Recurse`: Search all subdirectories recursively.
- `-Filter flag.txt`: Look for files named `flag.txt`.
- `-ErrorAction SilentlyContinue`: Suppress error messages (useful for access-denied folders).

## Tips

- You can change `flag.txt` to any filename you are searching for.
- Run PowerShell as Administrator for better access to all directories.
- The command will output the full path(s) to any matching files.

---

**Summary:**  
Use `Get-ChildItem -Path C:\ -Recurse -Filter flag.txt -ErrorAction SilentlyContinue` in PowerShell to search for a file named `flag.txt` anywhere on the C: drive.
