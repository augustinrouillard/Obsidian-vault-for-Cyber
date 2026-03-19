---
share: true
---
```markdown
# CTF Challenge: Hidden Data in a PNG Image

## Provided File

- `challenge.png`

## Initial Analysis

### Strings Search

```bash
strings challenge.png | grep -i "apoor"
```
- No results found.

### Clue

- **Comment:**  
  > "Not all colors make it to the page. In Gotham, only the red light tells the truth."
- **Format:**  
  - PNG file, contains "IHDR" and "PLTE" chunks.

### Hex Inspection

- Using `hexedit` or `xxd`, you observe:
  - Standard PNG headers (`.PNG`, `IHDR`, `PLTE`)
  - Large palette data
  - No obvious anomalies in the header

### Metadata

```bash
exiftool challenge.png
```
- **File Type:** PNG
- **Image Size:** 1920x1200
- **Bit Depth:** 8
- **Color Type:** Palette
- **Artist:** The Collector
- **Comment:** "Not all colors make it to the page. In Gotham, only the red light tells the truth."

## Investigation Steps

### 1. Steganography Tools

- Used Stegonline to browse bit planes, focusing on the red channel (bits 0-7).
- No obvious hidden data found.

### 2. Parameter Exploration

- Tried changing various parameters and color channels to reveal hidden information.
- No immediate results.

### 3. New Approach

- Inspired by Gemini:  
  > "Can we extract only red bytes and convert them to ASCII?"

## Solution Strategy

1. **Focus on the Red Channel**  
   - The clue suggests that only the red channel contains the truth.
   - Extract the red values from each pixel.

2. **Convert Red Values to ASCII**  
   - Treat the red channel as a stream of bytes.
   - Convert these bytes to ASCII to reveal hidden text or the flag.

3. **Automate Extraction**  
   - Use a script (e.g., Python with PIL or OpenCV) to extract the red channel and convert to ASCII.

```

## Summary

- The challenge involves a PNG image with a hidden message in the red channel.
- The clue points to extracting only the red values.
- By converting the red bytes to ASCII, you can reveal the hidden flag or message.

---

**Tips:**
- Always check image metadata and comments for clues.
- Try extracting individual color channels when hints reference colors.
- Use scripting to automate extraction and conversion.

```