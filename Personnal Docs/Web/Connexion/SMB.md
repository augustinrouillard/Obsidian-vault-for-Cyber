---
share: true
---
```markdown
# Note: Connecting to SMB Shares with smbclient

## How to Connect to an SMB Share

To connect to an SMB share (for example, an anonymous share) using `smbclient`:

```bash
smbclient //IP/Anonymous -N -m SMB2
```

- Replace `IP` with the target server's IP address.
- `//IP/Anonymous` is the path to the SMB share named "Anonymous".
- `-N` tells smbclient **not** to ask for a password (useful for anonymous access).
- `-m SMB2` forces the use of the SMB2 protocol (helpful if SMB1 is disabled on the server).

## Tips

- Once connected, you can use commands like `ls`, `cd`, `get`, and `put` to interact with files and directories on the share.
- If you need to specify a username, use the `-U` option (e.g., `-U username`).
- Use `exit` to leave the smbclient session.

---

**Summary:**  
Use `smbclient //IP/Anonymous -N -m SMB2` to connect to an anonymous SMB share using the SMB2 protocol, without a password prompt.