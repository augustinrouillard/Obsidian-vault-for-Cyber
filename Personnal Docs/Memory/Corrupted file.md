---
share: true
---
```markdown
# Note: Repairing Corrupted Files with Hex Editors

## When to Use

- If a file is corrupted or has an unknown format, you can try to repair it by editing its **magic number** (file signature) using a hex editor.

## Steps

1. **Open the File with a Hex Editor**

   ```bash
   hexedit file_name
   ```

   - This allows you to view and edit the raw bytes of the file.

2. **Identify and Change the Magic Number**

   - The **magic number** is usually found at the very beginning of the file (first few bytes).
   - Replace the existing bytes with the magic number of a known file type (e.g., PNG, JPG, PDF, ZIP, etc.).

   | File Type | Magic Number (Hex) | ASCII         |
   |-----------|--------------------|---------------|
   | PNG       | 89 50 4E 47 0D 0A 1A 0A | .PNG....    |
   | JPG       | FF D8 FF           | ÿØÿ           |
   | PDF       | 25 50 44 46        | %PDF          |
   | ZIP       | 50 4B 03 04        | PK..          |

3. **Save the File**

   - After editing, save the file and try to open it with the appropriate application.

## Tips

- Always make a backup before editing a file in a hex editor.
- If you know the original file type, use its magic number.
- This technique can help recover files with damaged headers or wrong extensions.

---

**Summary:**  
Use `hexedit` to open a corrupted file and change its magic number to match a known file type. This can help the system recognize and open the file.

```