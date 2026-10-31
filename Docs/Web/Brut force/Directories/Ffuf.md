---
share: true
---
```markdown
# Note: Directory and File Discovery with ffuf

## What is ffuf?

- **ffuf** (Fuzz Faster U Fool) is a fast web fuzzer for discovering directories, files, and parameters on web servers.
- Useful for web enumeration and penetration testing.

## How to Use

To search for hidden directories and files:

```bash
ffuf -u http://[IP]/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-large-words.txt
```

- `-u`: Target URL, where `FUZZ` is the placeholder that ffuf will replace with words from the wordlist.
- `-w`: Path to the wordlist (here, `raft-large-words.txt` from SecLists).

## Example

- This command will try each word from the wordlist in place of `FUZZ` (e.g., `http://[IP]/admin`, `http://[IP]/login`, etc.).
- Useful for finding hidden or unlisted directories and files.

## Tips

- You can use different wordlists for different targets or file types.
- Use the `-e` option to specify file extensions (e.g., `-e .php,.html`).
- Review the status codes and response sizes to identify interesting results.

---

**Summary:**  
Use `ffuf -u http://[IP]/FUZZ -w <wordlist>` to quickly enumerate directories and files on a web server.