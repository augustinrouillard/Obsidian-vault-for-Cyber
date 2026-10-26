---
share: true
---

## 1. L'Adresse MAC (_Media Access Control_)

- **Définition :** C'est l'adresse physique unique d'un nœud réseau.
- **Format :** Codée sur **6 octets**.
- **Structure :**
  - **3 premiers octets :** ID constructeur.
  - **3 derniers octets :** ID du périphérique.

---

## 2. Les Protocoles Clés

- **ARP (_Address Resolution Protocol_) :** Permet la résolution d'adresse (trouver l'adresse MAC d'une machine à partir de son adresse logique IP).
- **DHCP (_Dynamic Host Configuration Protocol_) :** 
  - Fournit une configuration réseau complète aux postes clients (et non pas seulement une adresse IP, car il transmet aussi le masque de sous-réseau, la passerelle par défaut, etc.).
  - **Concept de bail (_lease_) :** L'adresse IP est attribuée pour une durée limitée.
- **PXE (_Preboot Execution Environment_) :** Permet à un ordinateur de démarrer (_boot_) directement via le réseau en récupérant une image depuis un serveur distant.

---

## Résumé

- **Adresse MAC :** 6 octets (3 constructeur + 3 périphérique).
- **ARP :** Associe IP $\rightarrow$ MAC.
- **DHCP :** Attribue une configuration réseau temporaire (durée de bail).
- **PXE :** Démarrage réseau d'une machine.