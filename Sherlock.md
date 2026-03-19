---
share: true
---
```markdown
# Note: OSINT with Sherlock

## What is Sherlock?

- **Sherlock** is an OSINT tool that helps you find accounts by username across over 400 web platforms.
- Useful for investigations, CTFs, and digital footprint analysis.

## Installation

- Recommended: Use a virtual environment and `pipx` for isolated installation.

```bash
pipx install sherlock-project
```

- Or, clone the repository from [GitHub](https://github.com/sherlock-project/sherlock) and install manually.

## How to Use

- To search for a username (e.g., `user123`) across all supported platforms:

```bash
sherlock user123
```

- Sherlock will check the username on hundreds of sites and report where it is found.

## Tips

- Results may include social networks, forums, developer platforms, and more.
- You can specify multiple usernames or use options for output formats (e.g., CSV, JSON).
- Always use a virtual environment to avoid conflicts with other Python packages.

---

**Summary:**  
Sherlock is a powerful OSINT tool to find where a username is registered across 400+ platforms.  
Install with `pipx` and run `sherlock <username>` to start your search.
