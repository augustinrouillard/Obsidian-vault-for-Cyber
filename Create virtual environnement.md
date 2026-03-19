---
share: true
---

```markdown
# Note: Using Python Virtual Environments (venv)

## 1. Create a Virtual Environment

To create a new Python virtual environment:

```bash
python3 -m venv my_env
```

- This creates a directory called `my_env` containing the isolated Python environment.

## 2. Activate the Virtual Environment

To activate the virtual environment:

```bash
source my_env/bin/activate
```

- After activation, the environment name (e.g., `(my_env)`) should appear in your terminal prompt.
- All Python packages you install now will be local to this environment.

## 3. Tips

- **No need for `sudo`:**  
  You should **not** use `sudo` inside a virtual environment. All installations are user-local and do not require elevated privileges.
- To deactivate the virtual environment and return to the global Python environment:

  ```bash
  deactivate
  ```

## Summary

- Use `python3 -m venv <env_name>` to create a virtual environment.
- Use `source <env_name>/bin/activate` to activate it.
- Avoid using `sudo` inside the venv.
- Deactivate with `deactivate` when done.