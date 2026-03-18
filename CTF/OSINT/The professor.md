---
share: true
---
```markdown
# CTF Challenge: Research Paper & Scientist Identification

## Challenge Description

You are given clues about a research paper on deep packet inspection in smart grids, co-authored by a scientist whose last name matches a famous luxury footwear designer.  
You need to find:

- **x**: Number of times the scientist was cited in 2013
- **y**: Page range of their first research paper published in a larger volume
- **c**: Name of the conference where the paper was presented (all lowercase)
- **p**: City where the conference was held (all lowercase)

The flag format is:

```
BITSCTF{x_y_c_p}
```

## Solution Steps

### 1. Identify the Scientist

- The scientist’s last name matches a luxury footwear designer.
- Example: **Abdelkader Lahmadi** (Lahmadi ~ Louboutin, a famous shoe designer)
- Another example: **Kim-Kwang Raymond Choo** (Choo ~ Jimmy Choo, luxury footwear brand)

### 2. Gather Required Information

#### For Abdelkader Lahmadi

- **x**: Number of citations in 2013 → `76`
- **y**: Page range of the paper in the larger volume → `146-156`
- **c**: Conference name → `dsom`
- **p**: City → `barcelona`

#### For Kim-Kwang Raymond Choo

- **x**: Number of citations in 2013 → `127`
- (You would need to find the rest of the details for this scientist.)

### 3. Flag Construction

- All letters are lowercase.
- Use underscores to separate the fields.

**Example Flag:**

```
BITSCTF{76_146-156_dsom_barcelona}
```

## Other Possible Flags

Depending on the scientist and their papers, other flags could be:

- `BITSCTF{484_202-211_isw_saopaulo}`
- `BITSCTF{118_53-61_secau_perth}`
- `BITSCTF{76_340-345_iscc_rhodes}`
- `BITSCTF{413_345-356_acisp_adelaide}`
- `BITSCTF{138_363-377_acisp_sydney}`
- `BITSCTF{127_<page-range>_<conference>_<city>}` (for Kim-Kwang Raymond Choo, fill in the missing details)

## Summary

- Identify the scientist based on the luxury footwear brand clue.
- Find their citation count in 2013, the page range of their first paper, the conference name, and the city.
- Construct the flag in the format:  
  `BITSCTF{x_y_c_p}`

---

**Tips:**
- Use Google Scholar to find citation counts.
- Search for the scientist’s earliest papers and note the conference and city.
- Double-check spelling and formatting (all lowercase, underscores).

```