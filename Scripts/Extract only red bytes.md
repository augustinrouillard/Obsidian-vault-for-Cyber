---
share: true
---

```markdown
from PIL import Image

def extract_red_palette(image_path):
    img = Image.open(image_path)
    # Récupère la palette (liste de 768 valeurs : R, G, B, R, G, B...)
    palette = img.getpalette()
    
    if not palette:
        print("Pas de palette trouvée.")
        return

    # On ne garde que le canal Rouge (index 0, 3, 6, 9...)
    red_channel = palette[0::3]
    
    # On convertit en caractères ASCII si possible
    decoded = "".join([chr(b) for b in red_channel if 32 <= b <= 126])
    print(f"Extrait ASCII (Rouge) : {decoded}")

extract_red_palette("challenge.png")
```
