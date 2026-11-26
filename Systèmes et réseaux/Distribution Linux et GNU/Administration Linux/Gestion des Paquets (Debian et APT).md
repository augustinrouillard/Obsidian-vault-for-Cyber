---
share: true
---

---


## 1. Astuces Configuration et Édition

* **Éditeur `vi` minimaliste (`vim-tiny`) :** pour retrouver un comportement standard (touches fléchées fonctionnelles en mode insertion, etc.), exécuter la commande `:set nocompatible` (ou l'ajouter dans `~/.vimrc`).
* **Sauvegarde avant modification :** toujours faire une copie de sauvegarde avant d'éditer un fichier de configuration critique.
  ```bash
  cp /etc/apt/sources.list{,.old}
  # Équivalent à : cp /etc/apt/sources.list /etc/apt/sources.list.old
  ```

---

## 2. Les Releases Debian

Debian s'articule autour de quatre branches principales (plus de 50 000 paquets maintenus) :

* **Experimental :** paquets en cours de développement pouvant déstabiliser le système. Réservée aux développeurs et testeurs avertis.
* **Unstable (toujours surnommée *Sid*) :** *Rolling release* en constante évolution. Les paquets sont compilés pour chaque architecture par des *autobuilders*.
* **Testing :** future version stable. Intègre automatiquement les paquets d'*Unstable* après une période de quarantaine sans bogue grave.
* **Stable :** version figée et recommandée en **production**. Ne reçoit que des correctifs de sécurité (promotion validée par le *Release Manager*).

---

## 3. Gestion des Dépôts (`/etc/apt/sources.list`)

Les dépôts (*repositories*) centralisent les logiciels et leurs dépendances sur des serveurs distants, garantissant des mises à jour automatisées et sécurisées.

### Structure du fichier `/etc/apt/sources.list`
```text
deb http://ftp.fr.debian.org/debian/ bookworm main non-free-firmware
deb-src http://ftp.fr.debian.org/debian/ bookworm main non-free-firmware

deb http://security.debian.org/debian-security bookworm-security main non-free-firmware
deb http://ftp.fr.debian.org/debian/ bookworm-updates main non-free-firmware
```

* **1er champ (Type de paquet) :**
  * `deb` : paquets binaires prêts à être installés (utilisés en production).
  * `deb-src` : code source des paquets (pour audit ou recompilation).
* **2e champ (Source / Protocole) :** `http://`, `ftp://`, `file://` (dossier local), `cdrom:[...]` (média optique). *(Note : l'ordre des lignes détermine la priorité).*
* **3e champ (Branche / Version) :** `oldstable`, `stable`, nom de code (ex. `bookworm`), `testing`, `unstable`, `experimental`.
* **4e champ (Composants) :** `main` (logiciels libres officiels), `non-free-firmware` (micrologiciels propriétaires nécessaires au matériel).

---

## 4. Gestion Courante des Paquets (`apt` vs `apt-get`)

* **Outils disponibles :**
  * **`dpkg` :** outil bas niveau manipulant directement les fichiers `.deb` (ne gère pas le téléchargement des dépendances).
  * **`apt-get` / `apt-cache` :** outils historiques en ligne de commande.
  * **`apt` :** outil moderne unifié, recommandé aujourd'hui (meilleure gestion de la suppression des dépendances orphelines). *Éviter de mélanger `apt` et `apt-get` sur un même système.*
  * **`aptitude` :** interface semi-graphique en console (non installée par défaut).
* **Privilèges :** la recherche et la consultation (`search`, `show`) s'effectuent en simple utilisateur ; toute modification du système (`update`, `install`, `remove`, `upgrade`) requiert les droits `root` (`sudo`).
* **Astuce :** le paquet `bash-completion` permet l'autocomplétion des noms de paquets et options avec la touche `Tab`.

### Tableau des commandes essentielles

| Action | Commande moderne (`apt`) | Commande historique (`apt-get` / `apt-cache`) |
| :--- | :--- | :--- |
| **Mettre à jour la liste des paquets** *(rapatrie l'index des versions disponibles depuis les dépôts distants)* | `apt update` | `apt-get update` |
| **Mettre à jour les paquets** *(sans en supprimer)* | `apt upgrade` | `apt-get upgrade` |
| **Mettre à jour complètement** *(autorise la suppression/remplacement de paquets)* | `apt full-upgrade` | `apt-get dist-upgrade` |
| **Installer un paquet** | `apt install <paquet>` | `apt-get install <paquet>` |
| **Désinstaller un paquet** *(conserve les fichiers de configuration)* | `apt remove <paquet>` | `apt-get remove <paquet>` |
| **Purger un paquet** *(supprime aussi les fichiers de configuration)* | `apt purge <paquet>` | `apt-get purge <paquet>` |
| **Vider le cache local** *(supprime les `.deb` téléchargés)* | `apt clean` | `apt-get clean` |
| **Rechercher un paquet** *(par mot-clé ou regex)* | `apt search <motif>` | `apt-cache search <motif>` |
| **Afficher les détails d'un paquet** | `apt show <paquet>` | `apt-cache show <paquet>` |