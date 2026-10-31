---
share: true
---

## 1. Calcul des Réseaux Logiques
- Le poste source calcule sa propre adresse de réseau logique à l'aide de sa propre adresse IP et de son masque de sous-réseau (via l'opération logique ET).
- Le poste source applique ensuite son propre masque de sous-réseau à l'adresse IP de la machine cible pour déterminer le réseau logique de destination.
- 
---

## 2. Comparaison des Réseaux (Local ou Distant)
- **Si les adresses de réseau logiques sont identiques :** Le poste en déduit que la cible est sur le **même segment réseau**. La communication est directe (pas besoin de routeur).
- **Si les adresses de réseau logiques sont différentes :** Le poste en déduit que la cible est sur un **réseau distant**. La communication nécessite obligatoirement l'utilisation de la **passerelle par défaut**.

---

## 3. Cas A : La cible est sur le MÊME réseau (Communication Directe)
1. **Vérification ARP :** Le poste source consulte sa table ARP locale pour voir s'il connaît déjà l'adresse MAC associée à l'adresse IP cible.
2. **Requête ARP (si inconnue) :** 
   - Si l'adresse MAC n'est pas en cache, le poste émet une requête ARP en **broadcast** sur le réseau local : _« Qui a cette adresse IP ? Donnez-moi votre adresse MAC. »_
   - Le poste cible répond en unicast avec sa propre adresse MAC.
3. **Encapsulation et Envoi :** Le paquet est encapsulé avec l'adresse MAC de destination et envoyé directement sur le média physique.

---

## 4. Cas B : La cible est sur un RÉSEAU DISTANT (Via Routeur)
### Étapes de communication et de routage d'un paquet

### Les étapes de routage d'un paquet (version simple)

1. **La passerelle :** Le PC voit que la cible n'est pas sur son réseau. Il envoie le paquet à son routeur (la passerelle).
2. **Adresse MAC :** Le PC demande l'adresse MAC du routeur pour pouvoir lui parler directement.
3. **Envoi :** Le paquet arrive sur le routeur.
4. **Le travail du routeur :** 
   * Il lit l'adresse IP de destination.
   * Il applique son masque de sous-réseau (ET logique) pour voir s'il connaît ce réseau.
   * Il cherche dans sa table de routage le meilleur chemin et la bonne sortie.
   * Il retrouve la MAC du destinataire suivant et réenvoie le paquet.
5. **En cas d'erreur :** Si le routeur ne trouve pas le chemin, il supprime le paquet et prévient l'émetteur.