---
share: true
---
```markdown
# Note: Creating Temporary Directories in Bash

## How to Create a Temporary Directory

Use the `mktemp` command to create a temporary directory and store its path in a variable:

```bash
temp_dir=$(mktemp -d)
echo $temp_dir
```

- `mktemp -d` creates a new, unique temporary directory.
- The path to this directory is stored in the variable `temp_dir`.
- You can use `$temp_dir` in your script to reference this temporary location.

## Why Use Temporary Directories?

- Useful for storing temporary files during script execution.
- Ensures files do not conflict with others and are cleaned up after use.
- Improves security by using unique, unpredictable directory names.

## Tips

- Remember to clean up (delete) the temporary directory when your script is done:

  ```bash
  rm -rf "$temp_dir"
  ```

- You can specify a custom prefix:

  ```bash
  temp_dir=$(mktemp -d /tmp/mytempdir.XXXXXX)
  ```

---

**Summary:**  
Use `mktemp -d` to safely create and use temporary directories in your scripts.
