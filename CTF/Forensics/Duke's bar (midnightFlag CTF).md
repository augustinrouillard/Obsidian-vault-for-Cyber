---
share: true
---

```markdown
# CTF Challenge: Log Analysis and Flag Extraction

## Useful Commands

- `grep "Completed"`  
  Search for log entries indicating completed requests.

- `grep -E "212.114.18.5"`  
  Find log entries related to the suspicious IP address.

- `grep "password"`  
  Search for log entries containing the keyword "password".

## Log Analysis

### Example Log Entry

```text
logger=context userId=3 orgId=1 uname=editor1 t=2025-12-02T14:08:58.458872827Z level=info msg="Request Completed" method=GET path=/api/live/ws status=-1 remote_addr=212.114.18.5 time_ms=1 duration=1.224719ms size=0 referer= handler=/api/live/ws status_source=server
```

- **Suspicious IP Address:**  
  `remote_addr=212.114.18.5`

### Another Log Entry

```text
logger=auth t=2025-12-02T10:18:49.052846318Z level=debug msg="Seen token" tokenID=2 userID=2 clientIP=212.114.18.5 userAgent="Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0" authToken=99b15e7bf1c2278202fb364245bd6f80aa193a272c87da8eb98b23cc5259d4ae
```

- **Token and User Information:**  
  - `tokenID=2`
  - `userID=2`
  - `clientIP=212.114.18.5`

### Suspicious Log Line

- **Line 3932 is very suspicious in the log file**

## Database Investigation

- Use `sqlite3 <file.db>` to query the database.

### Example Query

```sql
SELECT id, login FROM user WHERE id=5;
```

**Result:**

```
5|editor2
```

## Flag Extraction

- The flag format is:  
  `MCTF{CVE-2024-9264:/var/lib/grafana/ctf/secret.csv:85.215.144.254:editor2}`

## Summary

To solve this challenge:

1. Analyze log files for suspicious activity, especially related to IP `212.114.18.5`.
2. Use `grep` commands to filter relevant log entries.
3. Investigate the database for user information.
4. Extract the flag, which includes a CVE, file path, IP address, and username.

---

**Flag:**  
`MCTF{CVE-2024-9264:/var/lib/grafana/ctf/secret.csv:85.215.144.254:editor2}`
```