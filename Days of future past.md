---
share: true
---
```markdown
# CTF Challenge: CryptoVault - Secure Message Storage Platform

## Challenge Description

- **URL:** [http://chals1.apoorvctf.xyz:8001](http://chals1.apoorvctf.xyz:8001/)
- **Author:** fl4nk3r
- **Goal:** Retrieve the secure message from the platform's "military grade" security.

## Steps to Solve

### 1. Reconnaissance

- Three main pages: Home, Login, Register.
- Home page source reveals:
  - API base: `/api/v1/`
  - Backup config at `/backup/`
  - Old JS app references config paths.
  - Frontend API integration in `/static/js/app.js`.

### 2. Directory & Endpoint Discovery

- `/backup/` directory: 403 Forbidden.
- Used `ffuf` for directory brute-forcing, no new findings.
- `/static/js/app.js` reveals:
  - API endpoints: `/health`, `/debug`, `/auth/register`, `/auth/login`, `/vault/messages`
  - Debug mode enabled, sensitive endpoints may be accessible.
  - Easter egg: "Check robots.txt for more clues..."

- `robots.txt` shows:
  ```
  Disallow: /backup/
  Disallow: /api/v1/debug
  Disallow: /api/v1/internal/
  ```

### 3. Backup Config Extraction

- Accessed `/backup/config.json.bak`:
  ```json
  {
    "api_key":"d3v3l0p3r_acc355_k3y_2024",
    "app_name":"CryptoVault",
    "database":"sqlite:///cryptovault.db",
    "debug_mode":true,
    "internal_endpoints":["/api/v1/debug","/api/v1/health","/api/v1/vault/messages"],
    "jwt_algorithm":"HS256",
    "notes":"Remember to rotate the API key before production deployment!",
    "version":"1.0.3-internal"
  }
  ```
- The API key is: `d3v3l0p3r_acc355_k3y_2024`

### 4. Debug Endpoint

- `/api/v1/debug` requires the API key in the header (`X-API-Key`).
- Response reveals:
  - JWT algorithm: HS256
  - Secret derivation hint: "Company name (lowercase) concatenated with founding year"
  - Secret key hash (SHA256): `e53e6e2d3018dce302f876eda97d3852f5f1a81192a5f947ed89da9832ea17b8`
  - Company name: `CryptoVault`
  - Founded: `2026`
  - Vault messages endpoint: `/api/v1/vault/messages`
  - Encryption: XOR stream cipher

### 5. JWT Generation

- Secret: `cryptovault2026`
- Role: `admin`
- Algorithm: `HS256`
- Created JWT and used it to access `/api/v1/vault/messages`.

### 6. Message Extraction

- Received 15 encrypted messages, each with a `ciphertext_hex`.
- All messages encrypted with XOR stream cipher.

### 7. XOR Decryption

- Used `xortool` to analyze ciphertexts:
  - Most probable key lengths: 3, 6, 10, 12, 15, etc.
  - Key-length can be 3*n.
  - Ran `xortool xortest.bin -l 6 -c 20` to guess the key.
  - Found possible keys and plaintexts.

### 8. Flag Discovery

- Decrypted message revealed the flag:

**Flag:**  
`apoorvctf{3v3ry_5y573m_h45_4_w34kn355}`

---

## Summary

- Recon the site and endpoints.
- Extracted API key from backup config.
- Used debug endpoint to get JWT secret derivation.
- Generated admin JWT and accessed encrypted messages.
- Used `xortool` to decrypt XOR-encrypted messages.
- Found the flag.

---

**Tips:**
- Always check for backup files and debug endpoints.
- Use hints in comments and robots.txt.
- Automate JWT generation and API requests.
- Use tools like `xortool` for XOR cipher analysis.

```
