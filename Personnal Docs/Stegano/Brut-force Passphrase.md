---
share: true
---

- Used `stegseek` to brute-force the passphrase on the original image with the `rockyou.txt` wordlist:

  ```
  sudo stegseek <file> /usr/share/wordlists/rockyou.txt
  ```