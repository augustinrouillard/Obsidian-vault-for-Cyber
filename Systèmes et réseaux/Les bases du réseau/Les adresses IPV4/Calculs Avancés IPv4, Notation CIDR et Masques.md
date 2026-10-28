---
share: true
---

## 1. Calcul du Préfixe CIDR à partir d'un Masque de Sous-Réseau

- **Principe :** On fait la somme du nombre de bits à `1` (bits de l'ID Réseau) sur l'ensemble des 4 octets du masque.
- _Exemple :_ Un masque `255.255.248.0` donne en binaire `11111111.11111111.11111000.00000000`, soit $8 + 8 + 5 + 0 = 21$ bits $\rightarrow$ **`/21`**.

---

## 2. Calcul du Masque de Sous-Réseau à partir d'un Préfixe

Exemple pratique basé sur un préfixe **`/22`** :

1. **Identifier l'octet concerné :** 22 étant supérieur à 16, le changement se situe sur le **3ème octet**.
2. **Calculer les bits de l'octet :** On soustrait les octets pleins précédents au CIDR ($22 - 16 = 6$). Il y a donc $6$ bits à `1` dans cet octet.
3. **Convertir en binaire :** 
   - Pour l'adresse réseau (bits à `0` à la fin) : `11111100`
   - Pour l'adresse de diffusion (bits à `1` à la fin) : `11111111`
4. **Calculer la valeur décimale :** 
   - Réseau : $128 + 64 + 32 + 16 + 8 + 4 = \mathbf{252}$
   - Diffusion : $128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = \mathbf{255}$
5. **Résultat du masque :** `255.255.252.0` (car le 4ème octet est à `0`).
6. **Calculer le nombre d'hôtes :** 
   $$\text{Nombre de bits d'hôtes} = 32 - 22 = 10$$
   $$\text{Nombre d'hôtes max} = 2^{10} - 2 = 1022\text{ hôtes}$$

---

## 3. Déduction d'une Adresse Réseau, Masque et CIDR depuis une Plage d'Adresses

Exemple : Traitement de la plage `16.0.0.1 - 31.255.255.254`

1. **Analyser les adresses :** On compare les octets pour trouver les similitudes. Ici, le premier octet change ($16$ et $31$).
2. **Trouver l'adresse réseau :** 
   - On convertit le premier nombre ($16$) en binaire pour identifier la partie réseau.
   - 16 correspond à un `1` dans la colonne $16$ (`00010000`).
   - L'adresse réseau de départ est donc **`16.0.0.0`** (en remplaçant les octets suivants par `0`).
3. **Calculer le CIDR :**
   - Les octets précédents l'octet étudié sont pleins ($8 \times 3 = 24$ bits).
   - Dans le premier octet, les bits réseau occupent une certaine portion (ici $4$ bits).
   - Total des bits réseau = $28$ bits $\rightarrow$ Le CIDR est de **`/4`** ($32 - 28 = 4$ bits d'hôtes).
4. **Obtenir le masque de sous-réseau :**
   - On pose les $4$ premiers bits à `1` sur l'ensemble des 4 octets (ou plutôt on remplit le premier octet selon le CIDR) : `1111 0000` $\rightarrow$ **`240.0.0.0`**.

---

## Résumé des Formules Clés

- **Masque $\rightarrow$ CIDR :** Somme de tous les bits à `1` du masque.
- **CIDR $\rightarrow$ Masque :** Conversion en binaire en posant $X$ bits à `1` en partant de la gauche, puis conversion en décimal.
- **Nombre d'hôtes :** $2^{(32 - \text{CIDR})} - 2$.