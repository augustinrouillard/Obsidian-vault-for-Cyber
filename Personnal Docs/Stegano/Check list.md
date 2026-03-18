---
share: true
---
```markdown
# Note: Steganography Checklist

## Basic Tools to Analyze Files

- **hexedit**  
  View and edit the raw hexadecimal content of a file.

- **binwalk**  
  Scan for embedded files and data within binaries (great for firmware, images, etc.).

- **exiftool**  
  Extract metadata from images and many other file types.

- **strings**  
  Search for printable strings inside binary files.

## If Nothing is Found, Try These Specific Commands

### 1. zsteg (for PNG and BMP steganography)

```bash
zsteg -a yourfile
```

- Detects hidden data in PNG and BMP files using various steganography techniques.

### 2. pngcheck (for PNG files)

```bash
pngcheck -v yourfile.png
```

- Verifies the integrity of PNG files and lists all chunks (can reveal hidden or non-standard data).

### 3. PDF: Decompress for Easier Analysis

To make a PDF more readable and easier to analyze:

```bash
qpdf --qdf --object-streams=disable Capture_the_flag.pdf decompressed.pdf
```

- This decompresses the PDF, making its structure and objects easier to inspect.

---

**Summary:**  
Start with `hexedit`, `binwalk`, `exiftool`, and `strings` for steganography analysis.  
If nothing is found, use `zsteg` for images, `pngcheck` for PNGs, and `qpdf` to decompress PDFs for deeper inspection.