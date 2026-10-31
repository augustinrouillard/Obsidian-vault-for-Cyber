---
share: true
---
```markdown
# Note: Understanding Bit Depth in Images (Exiftool vs. pngcheck)

## 1. Exiftool's Perspective: "Bit Depth" (Per Channel)

- When `exiftool` shows `Bit Depth : 8`, it refers to the **bit depth per color channel**.
- In an RGB image, there are 3 channels: **Red**, **Green**, and **Blue**.
- Each channel is encoded on **8 bits** (values from 0 to 255).
- This is the standard for most JPEG and PNG images.

## 2. pngcheck's Perspective: "24-bit RGB" (Total Per Pixel)

- When `pngcheck` displays `24-bit RGB`, it gives you the **total bit depth per pixel**.
- Calculation:
  - 8 bits (Red) + 8 bits (Green) + 8 bits (Blue) = **24 bits per pixel**
- This is simply the sum of the bit depth of all three channels.

---

**Summary:**  
- **Exiftool** reports bit depth **per channel** (e.g., 8 bits for each R, G, B).
- **pngcheck** reports the **total bit depth per pixel** (e.g., 24 bits for RGB).

```