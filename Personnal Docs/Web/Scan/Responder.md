---
share: true
---
```markdown
# Note: Using Responder for Network Poisoning

## What is Responder?

- **Responder** is a network poisoning tool used to intercept and respond to LLMNR, NBT-NS, and MDNS requests.
- Its main goal is to capture authentication hashes (especially NTLM) from Windows networks.
- Commonly used in internal penetration testing and red teaming.

## Basic Usage

To start Responder on a specific network interface:

```bash
sudo responder -I <interface>
```

- `-I <interface>`: Specify the network interface to listen on (e.g., `eth0`, `tun0`, `wlan0`).

## How It Works

- Responder listens for name resolution requests on the local network.
- When a machine tries to resolve a name (e.g., via LLMNR, NBT-NS, or MDNS), Responder replies and tricks the machine into sending authentication data.
- Captured hashes can then be cracked offline.

## Tips

- Run as root or with sudo for proper network access.
- Use `ifconfig` or `ip a` to list available network interfaces.
- Captured hashes are usually stored in the `Responder/logs/` directory.

---

**Summary:**  
Responder is a powerful tool for capturing authentication hashes by poisoning LLMNR, NBT-NS, and MDNS requests.  
Use `sudo responder -I <interface>` to start listening on your chosen network interface.