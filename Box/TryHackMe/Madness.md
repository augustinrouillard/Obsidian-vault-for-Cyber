---
share: true
---

## 1. Initial Enumeration

I started with an Nmap scan:

```shell
nmap -sC -sV -oN nmap.txt <target-ip>
```

**Results:**
```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
```

- **SSH** (port 22): OpenSSH 7.2p2
- **HTTP** (port 80): Apache 2.4.18

The HTTP server displays the default Apache2 Ubuntu page.

---

## 2. Web Enumeration

- I found an image file that appeared to be a JPG, but its header was corrupted.
- Using `hexedit`, I reconstructed the file and found the string:  
  ```
  th1s_1s_h1dd3n
  ```
- The image was protected by a passphrase.

### Hidden Directory

- Discovered a hidden directory: `/th1s_1s_h1dd3n/`
- In the source code, I found the following comment:
  ```
  <!-- It's between 0-99 but I don't think anyone will look here-->
  ```
- No visible form was present.

---

## 3. Directory Fuzzing & Secret Discovery

- Used Burp Suite to automate requests to the hidden directory, testing all numbers between 0 and 99 as the `secret` parameter:

  ```
  GET /th1s_1s_h1dd3n/?secret=1 HTTP/1.1
  GET /th1s_1s_h1dd3n/?secret=2 HTTP/1.1
  ...
  GET /th1s_1s_h1dd3n/?secret=73 HTTP/1.1  # This was the correct one
  ```

- Visiting:  
  ```
  http://<target-ip>/th1s_1s_h1dd3n/?secret=73
  ```
  revealed the string:  
  ```
  y2RPJ4QaPF!B
  ```

---

## 4. Steganography

- Used `steghide` on the image and found the string:  
  ```
  wbxre
  ```
- Decoding with ROT13 gives:  
  ```
  joker
  ```

---

## 5. Cracking the Image Passphrase

- Used `stegseek` to brute-force the passphrase on the original image with the `rockyou.txt` wordlist:

  ```shell
  sudo stegseek 5iW7kC8.jpg /usr/share/wordlists/rockyou.txt
  ```
- The passphrase found:  
  ```
  *axA&GF8dP
  ```

---

## 6. SSH Access

- SSH credentials:
  - **Username:** joker
  - **Password:** *axA&GF8dP

  ```shell
  ssh joker@<target-ip>
  ```

---

## 7. Privilege Escalation

- Searched for SUID binaries:

  ```shell
  find / -type f -perm -04000 -ls 2>/dev/null
  ```

- Found a suspicious version of `screen` (4.5.0).

- Followed this privilege escalation guide:  
  [https://github.com/YasserREED/screen-v4.5.0-priv-escalate](https://github.com/YasserREED/screen-v4.5.0-priv-escalate)

---

## 8. Flags

- **User flag:**  
  ```
  THM{d5781e53b130efe2f94f9b0354a5e4ea}
  ```

- **Root flag:**  
  ```
  THM{5ecd98aa66a6abb670184d7547c8124a}
  ```

---

**References:**
- [screen-v4.5.0-priv-escalate GitHub](https://github.com/YasserREED/screen-v4.5.0-priv-escalate)

---
