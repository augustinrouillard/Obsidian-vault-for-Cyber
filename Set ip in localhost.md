---
share: true
---
```markdown
# Note: Setting a Custom IP for a Domain in /etc/hosts

## Why Edit /etc/hosts?

- Editing `/etc/hosts` allows you to map a domain name (URL) to a specific IP address on your local machine.
- Useful for accessing sites that only exist locally, during CTFs, pentests, or development.

## How to Add a Custom Mapping

To redirect a domain (e.g., `unikka.htb`) to a specific IP (e.g., `10.129.22.9`):

```bash
echo "10.129.22.9 unikka.htb" | sudo tee -a /etc/hosts
```

- This command appends the mapping to the `/etc/hosts` file.
- Now, when you access `unikka.htb` in your browser or with tools, your computer will resolve it to `10.129.22.9`.

## Tips

- You can add multiple domains on the same line, separated by spaces.
- To remove or edit an entry, open `/etc/hosts` with a text editor (e.g., `sudo nano /etc/hosts`).
- Changes take effect immediately—no need to restart your computer.

---

**Summary:**  
Use `echo "IP domain" | sudo tee -a /etc/hosts` to map a domain to a local IP address for testing or CTFs.
