---
share: true
---
```markdown
# Note: Directory and Subdomain Enumeration with feroxbuster & gobuster

## 1. Searching for Directories and Files with feroxbuster

- **feroxbuster** is a fast, simple tool for web content discovery (directories and files).

```bash
feroxbuster -u http://10.129.1.15/ -w ~/Téléchargements/directory-list-2.3-medium.txt
```

- `-u`: Target URL.
- `-w`: Path to your wordlist (here, `directory-list-2.3-medium.txt`).
- feroxbuster will brute-force directories and files on the target web server.

## 2. Searching for Subdomains with gobuster

- **gobuster** can be used for virtual host (subdomain) enumeration.

```bash
gobuster vhost -u http://responder.htb -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt --append-domain
```

- `vhost`: Mode for virtual host (subdomain) discovery.
- `-u`: Target domain.
- `-w`: Wordlist for subdomains.
- `--append-domain`: Appends the domain to each word in the wordlist (e.g., `admin.responder.htb`).

## Tips

- Use large and relevant wordlists for better coverage.
- feroxbuster is great for directories/files, gobuster is great for subdomains.
- Review the output for interesting or unexpected results.

---

**Summary:**  
- Use `feroxbuster` to enumerate directories and files on a web server.
- Use `gobuster vhost` to discover subdomains (virtual hosts) on a target domain.