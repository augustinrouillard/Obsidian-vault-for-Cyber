---
share: true
---
```markdown
# CTF Challenge: Python Script Memory Overload & Binary Extraction

## Provided File

- A Python script (CTF challenge)

## Initial Clue

- **Comment:**  
  > "just run it bro"

## Analysis

### Attempt to Run

- Running the script filled up the computer's memory and crashed the process.

### Script Structure

- The script is organized in blocks.
- Each block appends the result of a mysterious process to a chain of empty strings.
- After completion, the chain is converted to an integer and added to a list (`[]`).
- Finally, the list is converted into a `.jpg` image.

### Investigation

- Examined the script to understand the mysterious process.
- The process uses the Python `is` operator to generate binary values.
  - The `is` operator compares memory locations, not values.
  - Returns `True` if both variables point to the same object, `False` otherwise.

### Problem

- The script is too large and causes memory overload.
- Direct execution is not feasible.

## Solution Strategy

1. **Manual Extraction**
   - Read the file using a separate Python script.
   - Apply the rule:  
     - If `X <= 256`, then bit = `'1'`
     - Otherwise, bit = `'0'`

2. **Convert to Image**
   - After extracting the binary data, convert it to a `.jpg` file.

## Example Python Snippet

```python
# Pseudocode for extracting bits and converting to image
data = []  # Assume this is the list extracted from the script

bits = ['1' if x <= 256 else '0' for x in data]
# Convert bits to bytes, then to image as needed
# (Implementation depends on the actual data structure)
```

## Result

- After applying the extraction rule and converting to `.jpg`, the flag was revealed:

**Flag:**  
`MCTF{Is0r1sN0tThatIsTheQuest10n!?}`

---

## Summary

- The challenge script was intentionally designed to overload memory.
- The key was to analyze the script logic, especially the use of the `is` operator.
- By manually extracting binary values based on the rule (`X <= 256`), you could reconstruct the image and find the flag.

---

**Tips:**
- When a script is too large or resource-intensive, analyze its logic instead of running it directly.
- Understand Python operators (`is` vs `==`) for potential CTF tricks.
- Use custom scripts to extract and process data efficiently.
