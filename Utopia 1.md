---
share: true
---
```markdown
# CTF Challenge: Conspiracy Theorist & Predictive Art

## Challenge Description

- **Flag format:**  
  `apoorvctf{artist'sName_diseaseName}`
- **Author:** Ellie

## Steps to Solve

### 1. Username Investigation

- Used Sherlock to search for `johnbuck69420` across platforms:
  - Envato Forum
  - Snapchat
  - YouTube
- No useful information found.

### 2. Google Research

- Found the X (Twitter) account: [x.com/JohnBuck69420](https://x.com/JohnBuck69420)
- Challenge name: **Utopia**
  - Reference to the comic/show "Utopia" where comics predict disease outbreaks.

### 3. Artist Identification

- Clues:
  - Instagram handle similar to `plague_bunny_`
  - Posted about anthropomorphic grasshopper
  - Posted about a bat before the COVID pandemic (between August and November 2019), but later removed it.

- Found an Instagram account: `plague_bunny_`
- Found the artist: **BlessonLal**

### 4. Disease Identification

- First artwork: Grasshopper image, possibly referencing the disease **Nosema locustae** (a disease affecting grasshoppers).
- Also found references to "hanahaki" (a fictional flower disease) and "black iris" in the artist's illustrations.

### 5. Flag Construction

- Tried various combinations based on artist and disease names:
  - `apoorvctf{blessonlal_nosemalocustae}`
  - `apoorvctf{blessonlal_hanahaki}`
  - `apoorvctf{blessonlal_blackiris}`

- The correct flag is:
  ```
  apoorvctf{blessonlal_blackiris}
  ```

## Summary

- Investigated the username and social media clues.
- Identified the artist as **BlessonLal**.
- Determined the disease referenced in the artwork as **blackiris**.
- Constructed the flag in the required format.

---

**Flag:**  
`apoorvctf{blessonlal_blackiris}`

---

**Tips:**
- Use tools like Sherlock for username searches.
- Pay attention to clues in social media posts and artwork descriptions.
- Try different combinations and spellings for the flag format.

```
