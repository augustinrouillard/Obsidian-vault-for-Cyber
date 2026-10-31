---
share: true
---
```markdown
# Note: Understanding JWT Tokens

## 1. Structure of a JWT

A JWT (JSON Web Token) is a long string divided into three parts, separated by dots (`.`):

```
header.payload.signature
```

### A. The Header

- Specifies the type of token (JWT) and the signing algorithm used (e.g., HMAC SHA256 or RSA).
- Example:

  ```json
  {
    "alg": "HS256",
    "typ": "JWT"
  }
  ```

### B. The Payload

- Contains the data ("claims"), such as user ID, username, or permissions.
- **Important:** The payload is only Base64-encoded, not encrypted. Anyone can decode and read it.

### C. The Signature

- The most important part for security.
- Created by signing the header and payload with a **secret key** known only to the server.
- If any part of the header or payload is changed, the signature will no longer match, and the token will be rejected.

## Example JWT

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxMjMsInJvbGUiOiJhZG1pbiJ9.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

- **Header:** `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9`
- **Payload:** `eyJ1c2VyX2lkIjoxMjMsInJvbGUiOiJhZG1pbiJ9`
- **Signature:** `SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c`

## Tips

- You can decode the header and payload using any Base64 decoder (or tools like [jwt.io](https://jwt.io/)).
- Never trust sensitive data in the payload—it's visible to anyone with the token.
- The signature ensures the token's integrity and authenticity.

---

**Summary:**  
A JWT consists of a header, a payload (claims), and a signature.  
The payload is readable by anyone, but the signature ensures the token hasn't been tampered with.

```