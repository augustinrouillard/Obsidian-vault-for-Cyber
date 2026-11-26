---
share: true
---

## 1. Bonnes Pratiques Système et Sécurité SSH

* **Démarrage en mode maintenance (`init=/bin/bash`) :** seule la partition racine `/` est montée au démarrage ; les autres partitions ne sont pas chargées tant qu'elles ne sont pas montées manuellement.
* **Extinction du système :** utiliser `shutdown now` uniquement en environnement console (sans interface graphique). Sur un bureau graphique, éteindre la machine virtuelle via le menu système.
* **Empreinte SSH (*Host Key Fingerprint*) :** lors de la première connexion SSH (`ssh root@10.102.200.38`), le client demande de valider l'empreinte publique du serveur (`ED25519 key fingerprint`). Cette vérification protège contre l'usurpation d'identité (*IP spoofing* / attaque de l'homme du milieu).

---

## 2. Commandes Réseau et Nom d'Hôte

| Commande / Fichier | Rôle |
| :--- | :--- |
| `ip a` ou `ip -c -4 -br a` | Afficher les interfaces réseau (ex. `ens33`) et leurs adresses IPv4 |
| `ip r` | Afficher la table de routage (passerelle par défaut) |
| `cat /etc/resolv.conf` | Consulter les serveurs DNS (`nameserver`) et les suffixes de recherche (`search`) |
| `hostnamectl` ou `vi /etc/hostname` | Consulter ou modifier le nom de la machine (*hostname*) |
| `dig <nom_domaine>` | Interroger directement un serveur DNS et analyser les enregistrements retournés (`A`, `CNAME`) |

---

## 3. Configuration de l'Adressage IP sous Debian

Deux gestionnaires réseau coexistent sur Debian :
* **`NetworkManager` :** utilisé par défaut sur les systèmes avec **interface graphique** (paramètres réseau GNOME ou via l'outil en mode texte `nmtui`). Il prend le dessus sur la configuration manuelle s'il est actif.
* **`networking` :** service historique utilisé sur les **serveurs en mode console** (sans interface graphique), configuré via le fichier `/etc/network/interfaces`.

### Configuration via `NetworkManager` (Graphique ou `nmtui`)
* Permet de basculer entre **Automatique (DHCP)** et **Manuel** (IP, masque CIDR ex. `/16`, passerelle, serveurs DNS séparés par des virgules).
* **`nmtui` (*NetworkManager Text User Interface*) :** interface semi-graphique en console permettant de configurer l'IP, les passerelles et les suffixes DNS sans environnement de bureau.

### Configuration statique via `/etc/network/interfaces` (Serveur console)
1. Éditer le fichier `/etc/network/interfaces` :
   ```text
   # Interface de bouclage (Loopback)
   auto lo
   iface lo inet loopback

   # Interface réseau principale (ens33)
   auto ens33
   iface ens33 inet static
       address 10.102.5.1
       netmask 255.255.0.0
       gateway 10.102.255.254
   ```
2. Appliquer les modifications en redémarrant le service réseau :
   ```bash
   systemctl restart networking
   ```

---

## 4. Résolution de Noms et Fonctionnement DNS

### Ordre de résolution sur un client Linux
Lorsqu'une machine tente de joindre un hôte par son nom (ex. `ping repos.eni-ecole.net` ou un nom court comme `sr1`) :
1. **Consultation locale :** le système vérifie d'abord le fichier `/etc/hosts`.
2. **Ajout du suffixe DNS :** si un nom court est utilisé, le système lui ajoute automatiquement le suffixe défini dans `/etc/resolv.conf` (ex. `ad.campus-eni.fr`) pour former un **FQDN** (*Fully Qualified Domain Name*).
3. **Interrogation du serveur DNS :** le client interroge les serveurs listés dans `/etc/resolv.conf` **dans l'ordre exact où ils sont déclarés** (ils sont testés un par un).

### Mécanisme de résolution avec `dig` (Exemple `repos.eni-ecole.net`)
* Le client interroge le serveur DNS (`10.100.0.3` sur le port `53/UDP`).
* **Enregistrement `CNAME` (alias) :** `repos.eni-ecole.net` pointe vers le nom canonique `ntp44.ad.campus-eni.fr`.
* **Enregistrement `A` (adresse IPv4) :** `ntp44.ad.campus-eni.fr` est résolu vers l'adresse IP `10.64.0.3`.
* Une fois l'adresse IP obtenue, le client envoie sa requête réseau (ex. `ping` en protocole **ICMP**) vers `10.64.0.3`.