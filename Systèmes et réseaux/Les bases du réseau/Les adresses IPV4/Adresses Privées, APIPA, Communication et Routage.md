---
share: true
---
---

## 1. Les Adresses Privées

- **Utilisation :** Uniquement dans les réseaux locaux privés, non routables sur Internet.
- **NAT (_Network Address Translation_) :** Permet de faire communiquer un poste en adresse privée avec le monde extérieur (Internet).

### Plages d'adresses privées

- **Classe A :** 
  - Plage globale : `10.0.0.0` à `10.255.255.255`
  - Masque de sous-réseau : `255.0.0.0` (Notation CIDR : **`/8`**)
- **Classe B :** 
  - Plage globale : `172.16.0.0` à `172.31.255.255`
  - Masque de sous-réseau : `255.240.0.0` (Notation CIDR : **`/12`**)
- **Classe C :** 
  - Plage globale : `192.168.0.0` à `192.168.255.255`
  - Masque de sous-réseau : `255.255.0.0` (Notation CIDR : **`/16`**)

---

## 2. Les Adresses APIPA (_Automatic Private IP Addressing_)

- **Définition :** Adressage Privé IP Automatique.
- **Format :** Adresse de réseau logique `169.254.0.0 /16`.
- **Fonctionnement :** Attribué automatiquement lorsqu'un ordinateur ne reçoit pas de configuration IP. Dès qu'un serveur DHCP devient joignable, il remplace cette adresse par une configuration valide.
- **Alerte (Problème DHCP) :** Si une machine possède une adresse APIPA, cela indique généralement :
  - Une panne physique
  - Un manque de baux disponibles sur le serveur
  - Une absence de serveur DHCP sur le réseau

---

## 3. La Création de Sous-Réseaux

**Principe Fondamental** - On modifie la frontière de l'adresse IP en empruntant des bits à la partie **ID Hôtes** pour constituer un **ID Sous-Réseau**. - **Conséquence directe :** Le masque de sous-réseau s'allonge et le préfixe CIDR augmente (par exemple, passage d'un `/16` à un `/19`).

**Méthode de découpage**

Si nous avons par exemple une adresse 199.210.15.0 `/24`.
Pour constituer un sous réseau nous pouvons séparer ce réseau en deux.
Dans ce cas, nous pouvons imaginer le dernier octet comme un cercle de 256 bits. Le diviser par deux revient à faire deux blocs de 128 bits. L'une sera 199.210.15.0 `/25`et l'autre 199.210.15.128 `/26`. Le CIDR change car nous avons ajouté 1 bits pour pouvoir créer une nouvelle plage d'adresses réseaux.
En divisant une seconde fois un coté en deux parts de 64 bits (nous incrémentons encore le CIDR) la nouvelle adresse sera 199.210.15.192 car 128+64 = 192. Si nous avions divisé en 4 le CIDR aurait augmenté de 2 car il aurait fallu 2 bits (2 puissance2) pour créer 4 sous réseaux. 

---

## 4. Communication et Domaine de Diffusion

- **Vérification préalable :** Avant de communiquer avec une autre machine, l'ordinateur calcule les deux réseaux logiques pour vérifier s'ils sont sur le même réseau.
- **Passerelle par défaut :** Utilisée si la cible est sur un réseau différent. Une passerelle possède au moins deux adresses réseau logiques différentes.
- **Domaine de diffusion :** Étendue de propagation des diffusions (comme les requêtes ARP). Les routeurs permettent de segmenter ces domaines.

---

## 5. Le Routage

- **Table de routage :** Indique l'adresse IP du routeur vers laquelle acheminer le paquet pour atteindre un réseau logique cible. Le routeur prend ensuite l'initiative d'acheminer la requête.
- **Métrique :** Représente le nombre d'équipements à traverser pour atteindre la cible (l'équipement s'inclut lui-même dans le décompte).
- **Redondance :** La mise en place de chemins alternatifs (comme un routeur de secours R4) permet d'assurer la continuité de la communication dans les deux sens en cas de panne.