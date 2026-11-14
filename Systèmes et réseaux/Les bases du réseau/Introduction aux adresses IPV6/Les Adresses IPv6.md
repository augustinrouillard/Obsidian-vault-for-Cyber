---
share: true
---

## 1. Pourquoi l'IPv6 ?
* **Épuisement d'IPv4 :** Développé par l'IETF (*Internet Engineering Task Force*) pour faire face à la pénurie mondiale d'adresses IPv4.
* **Performance réseau :** Conçu avec des en-têtes plus simples et plus efficaces, réduisant la charge de traitement sur les équipements réseau pour une latence plus faible et de meilleures performances globales.

---

## 2. Format et Structure
* **Longueur :** 128 bits (contre 32 bits pour l'IPv4), offrant un espace d'adressage quasi infini.
* **Représentation :** Écriture sous forme de 8 blocs de 16 bits en hexadécimal, séparés par des deux-points (`:`).
* **Exemple complet :** `2001:0db8:0000:0000:0000:ff00:0042:8329`

---

## 3. Règles d'Écriture et de Compression
* **Suppression des zéros non significatifs :** Il est possible d'omettre les zéros situés au début d'un bloc (ex : `0db8` devient `db8`).
* **Compression des zéros consécutifs :** Une ou plusieurs suites consécutives de blocs de zéros peuvent être remplacées par une double occurrence de deux-points (`::`). Cette simplification ne peut être utilisée qu'**une seule fois** par adresse pour éviter toute ambigüité.