---
share: true
---
```markdown
# CTF Challenge: Code Injection in a TIFF Image

## Provided File

- The file is a `.tif` image, which typically should be 8 or 12 bytes per pixel.
- In this case, the file size is 64 bytes per pixel, suggesting code injection.

## Analysis

### Hex Inspection

- Using `xxd`, you notice repeating blocks in the file.
- The TIFF file acts as an empty container, holding injected code rather than image data.

### Code Injection

- The code injection is related to the mantissa (floating point representation).
- Geometric shapes resembling a QR code are visible, suggesting a hidden QR code.

## Resolution Discovery

- Calculated the square root of `403240` (≈ 635).
- The generated image appeared skewed, indicating a mismatch between the actual and expected resolution.
- By testing different resolutions, you found that `635` was the correct one.

## Steps to Solve

1. **Inspect the TIFF file with `xxd`**  
   Look for repeating blocks and signs of code injection.

2. **Analyze the image for hidden patterns**  
   Notice geometric shapes that hint at a QR code.

3. **Calculate the correct resolution**  
   - Compute the square root of the file size to estimate the image dimensions.
   - Adjust for skew by testing different resolutions.

4. **Extract the QR code**  
   Once the correct resolution is found, decode the QR code to retrieve the flag.

## Summary

- The challenge involves a TIFF file with code injected via the mantissa.
- The file size and repeating blocks indicate non-standard image data.
- By calculating the square root of the file size and correcting for skew, you reveal a hidden QR code.
- Decoding the QR code provides the flag.

---

**Tips:**
- Use `xxd` or similar tools to inspect image files for anomalies.
- When image data looks suspicious, try reconstructing the image with different resolutions.
- Look for hidden QR codes or other patterns in CTF image challenges.

```