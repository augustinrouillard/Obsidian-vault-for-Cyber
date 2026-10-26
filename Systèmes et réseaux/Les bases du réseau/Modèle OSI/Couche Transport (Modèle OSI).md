---
share: true
---

## 1. Rôles et Fonctions Principales

- **Segmentation et numérotation** des données provenant de la couche supérieure.
- **Gestion des ports** pour identifier les applications concernées :
  - **Port de destination :** application à contacter.
  - **Port local d'écoute :** port local aléatoire ouvert pour recevoir la réponse.

---

## 2. Les Deux Protocoles Majeurs

- **TCP (_Transmission Control Protocol_) :** Mode connecté avec accusé de réception (fiable).
- **UDP (_User Datagram Protocol_) :** Mode non connecté sans accusé de réception (rapide, sans garantie de livraison).

---

## 3. Communication entre Postes et Notions de Sockets

- **Rôles :** Un poste joue le rôle de **client** et l'autre de **serveur**.
- **Communications simultanées :** Utilisation des **sockets** pour permettre à un même poste de gérer plusieurs flux en même temps.
- **Composition d'un socket :** 
  $$\text{Socket} = \text{Adresse IP} + \text{Protocole de couche 4 (TCP/UDP)} + \text{Port}$$
- **Exemple concret :** 
  - Connexion vers une application distante : ex. `173.194.34.31 : TCP : 80`.
  - Attente de la réponse sur un port local aléatoire (> 1024) : ex. `80.10.20.30 : TCP : 44800`.

---

## 4. Outils d'Analyse

- **Commandes pour lister les connexions actives :** `netstat` ou `ss`.

---

## Résumé

- **TCP :** Fiable, orienté connexion (avec accusé de réception).
- **UDP :** Rapide, non orienté connexion (sans accusé de réception).
- **Socket :** Association $\text{IP} + \text{Protocole} + \text{Port}$.
- **Outils :** `netstat` / `ss` pour l'analyse des connexions.