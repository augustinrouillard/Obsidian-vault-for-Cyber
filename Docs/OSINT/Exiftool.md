---
share: true
---
```markdown
# Note: Using exiftool to Inspect File Metadata

## What is exiftool?

- `exiftool` is a powerful command-line tool for reading, writing, and editing metadata in files (especially images, but also many other formats).

## How to Use

To display all metadata of a file:

```bash
exiftool <file_path>
```

- Replace `<file_path>` with the path to your file.
- This command will print all available metadata (EXIF, IPTC, XMP, etc.) for the file.

## Why Use exiftool?

- To view hidden information such as:
  - Author, creation date, camera model, GPS coordinates, software used, comments, etc.
- Useful for digital forensics, CTFs, and privacy checks.

## Tips

- To extract only a specific tag:

  ```bash
  exiftool -TAG <file_path>
  ```

  Example:

  ```bash
  exiftool -Comment image.jpg
  ```

- To write or edit metadata, use the `-TAG=VALUE` syntax (be careful!):

  ```bash
  exiftool -Author="Your Name" <file_path>
  ```

---

**Summary:**  
Use `exiftool <file_path>` to display all metadata of a file for analysis or investigation.