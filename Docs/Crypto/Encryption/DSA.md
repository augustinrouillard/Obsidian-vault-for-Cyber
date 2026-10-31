---
share: true
---
```markdown
# Note: DSA (Digital Signature Algorithm)

## What is DSA?

**DSA** (_Digital Signature Algorithm_) is an asymmetric cryptographic standard used **exclusively for digital signatures**.  
Unlike RSA, DSA is **not designed for encrypting messages**, but only for ensuring two key properties:

### 1. Authenticity

- Proves that the message truly comes from the expected sender (e.g., the spaceship).

### 2. Integrity

- Guarantees that the message has not been altered during transmission.

## How Does DSA Work?

- DSA operates with a **private key** and a **public key**.
- The **private key** is kept secret by the signer.
- The **public key** is derived from the private key and shared openly.

## Summary

- DSA is used for **signing** data, not for encryption.
- It ensures **authenticity** and **integrity** of messages.
- Relies on a private/public key pair.

---

**Tip:**  
If you need to verify a message's origin and integrity, DSA is a standard choice for digital signatures.

```

