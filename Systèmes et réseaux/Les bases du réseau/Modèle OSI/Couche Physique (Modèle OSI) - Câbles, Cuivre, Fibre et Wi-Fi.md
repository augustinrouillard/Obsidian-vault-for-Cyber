---
share: true
---
---

## 1. Les Médias Cuivre et Paires Torsadées

- **Câble RJ45 de base :** Débit faible et sensibilité potentielle aux interférences. Ne jamais descendre en dessous de la **catégorie 6**.
- **Types de câbles :** 
  - **Câbles droits** vs **Câbles croisés** (ces derniers tendent à disparaître grâce à la fonction Auto-MDI/MDIX des switchs modernes).
- **PoE (_Power over Ethernet_) :** Le câble transporte à la fois les données et l'électricité. **Attention :** nécessite un switch compatible PoE.
- **Contrainte de distance :** La résistance du cuivre réduit la puissance du signal sur de longues distances (règle des **80 mètres**). Un switch ou répéteur peut être posé pour amplifier le signal.

### Blindage des paires torsadées (Norme ISO 11801)

| **Désignation ISO** | **Blindage du câble** | **Blindage de paire** | **Type de protection visuel** |
| :--- | :--- | :--- | :--- |
| **U/UTP** | Aucun | Aucun | Pas de blindage |
| **U/FTP** | Aucun | Feuillard | Blindage de paire |
| **F/UTP** | Feuillard | Aucun | Blindage du câble |
| **S/UTP** | Tresse | Aucun | Blindage du câble |
| **SF/UTP** | Tresse, feuillard | Aucun | Blindage du câble |
| **F/FTP** | Feuillard | Feuillard | Blindage du câble + des paires |
| **S/FTP** | Tresse | Feuillard | Blindage du câble + des paires |
| **SF/FTP** | Tresse, feuillard | Feuillard | Blindage du câble + des paires |

---

## 2. La Fibre Optique

Comparaison des différents types de fibres optiques :

- **Multimode à saut d'indice :** 
  - Débit : Gigabit | Portée max : $\sim 200\text{ m}$
  - Émission : par D.E.L. | Plusieurs signaux / modes
- **Multimode à gradient d'indice :** 
  - Débit : Gigabit | Portée max : $\sim 275\text{ m}$
  - Émission : par D.E.L. | Plusieurs signaux
- **Monomode :** 
  - Débit : Gigabit | Portée max : $\sim 10\text{ km}$
  - Émission : par laser | Un seul signal / mode direct

_Astuce :_ Utiliser **Geotraceroute** pour visualiser le parcours réel des câbles sous-marins mondiaux.

---

## 3. Réseaux Sans Fil (Wi-Fi)

- **Norme principale :** IEEE **802.11**.
- **Bandes de fréquences :**
  - **2,4 GHz :** Grande portée, mais fréquence rapidement saturée.
  - **5 GHz :** Débit important, mais sur une distance plus restreinte.

---

## Résumé

- **Cuivre :** Règle des $\sim 80\text{m}$, attention au choix de la catégorie ($\ge 6$) et du blindage (UTP, FTP, STP...).
- **PoE :** Alimentation électrique via le câble réseau (nécessite un switch compatible).
- **Fibre :** Multimode (courte/moyenne distance, D.E.L.) vs Monomode (longue distance, laser).
- **Wi-Fi (802.11) :** 2,4 GHz (portée) vs 5 GHz (débit).