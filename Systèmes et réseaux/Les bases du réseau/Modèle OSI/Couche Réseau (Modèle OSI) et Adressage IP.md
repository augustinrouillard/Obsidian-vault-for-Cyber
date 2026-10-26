---
share: true
---
---

## 1. Rôle et Principes de la Couche Réseau

- **Rôle principal :** Transmission de bout en bout entre les PC et routage (choix de la meilleure route).
- **Adresse logique :** Identifie un nœud réseau sous la forme d'un couple $\text{ID\_Réseau} + \text{ID\_Hôte}$ (unique sur un réseau logique).
- **Communication inter-postes :** Permet à tous les postes d'un réseau de communiquer entre eux.
- **Calcul de réseau :** 
  $$\text{Adresse IP} + \text{Masque de sous-réseau} = \text{Adresse de réseau logique}$$
  Cette association utilise l'opérateur logique **ET (&)**.

---

## 2. Exemple de Communication (Ping entre le poste A et le poste B)

Exemple d'échanges d'adresses MAC et logiques (IP) lors d'une requête et d'une réponse de type Ping dans un même réseau :

### Envoi de la requête de A vers B
- **Adresse MAC :** Destination $\rightarrow$ `00:1A:2B:3C:4D:5E` | Source $\rightarrow$ `00:11:22:33:44:55`
- **Adresse Logique (IP) :** Destination $\rightarrow$ `@IP: 1B` | Source $\rightarrow$ `@IP: 1A`

### Envoi de la réponse de B vers A
- **Adresse MAC :** Destination $\rightarrow$ `00:11:22:33:44:55` | Source $\rightarrow$ `00:1A:2B:3C:4D:5E`
- **Adresse Logique (IP) :** Destination $\rightarrow$ `@IP: 1A` | Source $\rightarrow$ `@IP: 1B`

---

## Résumé

- **Couche Réseau :** Assure le routage et l'adressage logique (IPv4 / IPv6).
- **Structure IP :** $\text{ID\_Réseau} + \text{ID\_Hôte}$.
- **Masque de sous-réseau :** Permet de déterminer l'adresse du réseau logique grâce à l'opération ET logique.