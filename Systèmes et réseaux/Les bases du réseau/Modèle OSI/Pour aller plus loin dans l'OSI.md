---
share: true
---

# Bases du Réseau, Encapsulation et Protocoles

## 1. Terminologie Fondamentale

- **Modèle OSI :** Composé de 7 couches indépendantes mais communicantes (_Open Systems Interconnection_).
- **SDU (_Service Data Unit_ - Unité de données de service) :** Données brutes transmises d'une couche supérieure vers une couche inférieure.
- **PCI (_Protocol Control Information_ - Information de contrôle de protocole) :** Informations de contrôle (en-têtes ou queues) ajoutées par une couche.
- **PDU (_Protocol Data Unit_ - Unité de données de protocole) :** Résultat de l'association entre le PCI et le SDU ($\text{PDU} = \text{PCI} + \text{SDU}$).

---

## 2. Processus d'Encapsulation et de Désencapsulation

- **Encapsulation (Envoi de données) :** 
  - S'effectue du haut vers le bas (de la couche Application vers la couche Physique).
  - À chaque couche, un en-tête ($\text{PCI}$) est ajouté au SDU provenant de la couche supérieure pour former un nouveau PDU, qui devient à son tour le SDU de la couche inférieure.
- **Désencapsulation (Réception de données) :** 
  - S'effectue du bas vers le haut (de la couche Physique vers la couche Application).
  - Le récepteur retire successivement les en-têtes ($\text{PCI}$) à chaque étape pour retrouver les données initiales.

---

## 3. Les PDU selon les Couches du Modèle OSI

| **Couche OSI** | **Nom du PDU / Unité** |
| :--- | :--- |
| **7. Application** | APDU (Données initiales) |
| **6. Présentation** | PPDU |
| **5. Session** | SPDU |
| **4. Transport** | TPDU ou **Segment** |
| **3. Réseau** | RPDU ou **Paquet** |
| **2. Liaison** | LPDU ou **Trame** |
| **1. Physique** | **Bits** |

---

## 4. Transport : UDP vs TCP

- **TCP (_Transmission Control Protocol_) :** Protocole orienté connexion qui garantit la livraison des données, vérifie qu'elles arrivent bien à destination et gère le contrôle d'erreur.
- **UDP (_User Datagram Protocol_) :** Protocole non orienté connexion qui envoie des données sans vérifier si elles arrivent (plus rapide, idéal pour le streaming ou le jeu en ligne).

---

## Résumé

- **Encapsulation :** Descente des couches (Ajout de $\text{PCI}$ au $\text{SDU}$ $\rightarrow$ Création du $\text{PDU}$).
- **Désencapsulation :** Remontée des couches (Retrait des en-têtes).
- **TCP :** Fiable, vérifie la bonne réception des données.
- **UDP :** Rapide, envoie sans vérifier la réception.