---
share: true
---
```markdown
# Note: Useful Nmap Commands

## 1. Default Script Scan

- Use `-sC` to run Nmap’s default scripts (useful for basic service enumeration):

```bash
nmap -sC [target]
```

## 2. Scan a Specific Port with a Module

- To scan a specific port and service, use:

```bash
nmap -p [port] --script [module] [ip]
```

- Example for FTP on port 21:

```bash
nmap -p 21 --script ftp [ip]
```

## 3. Scan a Subdomain

- To scan a subdomain with service/version detection and default scripts:

```bash
nmap -sV -sC s3.thetoppers.htb
```

- `-sV`: Service and version detection
- `-sC`: Default scripts

## 4. Full Port Scan with Verbose Output

- To scan all ports with detailed output:

```bash
nmap -sV -sC -vv -p- 10.129.25.49
```

- `-vv`: Very verbose output
- `-p-`: Scan all 65535 ports

## Tips

- Combine `-sC` and `-sV` for a thorough initial scan.
- Use `-p-` to ensure you don’t miss services running on non-standard ports.
- Use subdomain targets for web services or cloud buckets.

---

**Summary:**  
- Use `-sC` for default scripts.
- Use `-p [port] --script [module]` for specific services.
- Use `-sV -sC` for service detection and scripts.
- Use `-p-` for full port scans.
