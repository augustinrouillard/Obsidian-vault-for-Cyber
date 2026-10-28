---
share: true
---

## 1. Connaître l'Adresse IPv4

- **Définition :** Une adresse IPv4 est composée de **32 bits** découpés en **4 octets** distincts. Elle est structurée en deux parties : 
  $$\text{Adresse IP} = \text{ID Réseau} + \text{ID Hôtes}$$
- **Éléments nécessaires :** Pour communiquer avec d'autres hôtes, un équipement a besoin d'une **adresse IP** et d'un **masque de sous-réseau**.
- **Rôle du masque :** Les `1` du masque définissent la partie de l'IP qui correspond à l'**ID Réseau** (en rouge), tandis que la partie restante correspond à l'**ID Hôte** unique (en vert).
  - _Exemple :_ Si le masque est `255.255.0.0`, l'identifiant réseau commun pour `10.104.x.x` est `10.104`. Tous les équipements du réseau partageront ce début d'adresse.

---

## 2. Les Classes d'Adresses IPv4

Le premier octet de l'adresse IP détermine sa classe :

| **Classe** | **Plage du 1er octet** | **Masque par défaut** | **Nombre d'hôtes max** |
| :--- | :--- | :--- | :--- |
| **Classe A** | $1 - 126$ | `255.0.0.0` | $2^{24} - 2 = 16\,777\,214$ |
| **Classe B** | $128 - 191$ | `255.255.0.0` | $2^{16} - 2 = 65\,534$ |
| **Classe C** | $192 - 223$ | `255.255.255.0` | $2^8 - 2 = 254$ |
| **Classe D (Multicast)** | $224 - 239$ | `240.0.0.0` | $0$ |

- **Cas particuliers :** En classe A, les réseaux `0.0.0.0` et `127.0.0.0` sont réservés et inutilisables.
- **Formule du nombre d'hôtes :** 
  $$\text{Nombre d'hôtes} = 2^{\text{nombre de bits de l'ID hôte}} - 2$$
  *(On retire toujours 2 : une adresse pour le réseau et une adresse pour la diffusion).*

---

## 3. Les Différents Types de Trafic

- **Unicast :** Communication d'un émetteur vers un seul récepteur spécifique (1 vers 1).
- **Broadcast :** Communication d'un émetteur vers tous les hôtes du réseau (1 vers tous, ex. : requête ARP).
- **Multicast :** Communication d'un émetteur vers un groupe d'hôtes spécifique.
- **Anycast :** Communication vers le nœud le plus proche d'un groupe d'hôtes.

---

## 4. Calculs des Adresses IPv4

### A. Calcul de l'Adresse Réseau Logique
- **Principe :** Résultat de l'association entre le masque de sous-réseau et l'adresse IP en utilisant l'opérateur logique **ET (&)**.
- **Astuce pratique :** Plutôt que de multiplier chaque bit de chaque octet, on remplace toute la partie **ID Hôte** par des zéros (`0000 0000`). Cette adresse correspond à l'adresse de réseau et n'est pas attribuable à une machine.

### B. Calcul de l'Adresse de Diffusion (Broadcast)
- **Principe :** C'est la dernière adresse du réseau. La partie **ID Hôte** y est entièrement remplie de `1` (`1111 1111` / `255`). Elle n'est pas attribuable à un hôte.

---

## 5. Méthode Pratique (TP) : Étapes de Calcul

Pour un hôte donné (ex. : `@IP : 192.168.76.150` avec le masque `255.255.255.0`) :

1. **Analyser le masque** pour identifier la partie réseau et la partie hôte.
2. **Calculer l'adresse réseau :** Conserver la partie réseau et compléter la partie hôte avec des `0`.
3. **Calculer l'adresse de diffusion :** Conserver la partie réseau et compléter la partie hôte avec des `255` (ou des `1` en binaire).
4. **Calculer le nombre d'hôtes :** Appliquer la formule $(2^{\text{partie hôte}} - 2)$.

---

## 6. La Notation CIDR

- **Définition :** La notation CIDR remplace le masque de sous-réseau classique.
- **Format :** Elle s'écrit sous la forme d'un slash (`/`) suivi du nombre de bits de l'**ID Réseau** (les bits invariables).
- **Équivalences usuelles :**
  - Classe A = `/8`
  - Classe B = `/16`
  - Classe C = `/24`