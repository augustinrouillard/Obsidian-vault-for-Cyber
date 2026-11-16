---
share: true
---

## 1. Chronologie : D'Unix à GNU/Linux

* **1969 / 1970 :** Création du système d'exploitation *Unics* par Ken Thompson, Dennis Ritchie et Brian Kernighan.
* **1971 :** Première version officielle d'**Unix**.
* **1972 :** Dennis Ritchie crée le **langage C**.
* **1973 :** Réécriture du noyau Unix en langage C (facilitant sa portabilité). L'université de Berkeley est la première à en obtenir le code source.
* **1976 :** Sortie d'*Unix Time-Sharing System V6*.
* **1977 - 1979 :** Bill Joy développe **1BSD** (sur base Unix V6), puis **2BSD** intégrant le *C Shell* (`csh`) et l'éditeur **vi**.
* **1983 :** Richard Matthew Stallman lance le **projet GNU** (*GNU's Not Unix*).
* **1987 :** Création de **Minix** par Andrew Tanenbaum à des fins pédagogiques.
* **1991 :** Le 25 août, **Linus Torvalds** annonce le développement d'un noyau libre (Linux).
* **1992 :** Sortie de la première distribution GNU/Linux : **SLS** (*Softlanding Linux System*).
* **1993 :** SLS laisse place à **Slackware** ; création de **Debian**.
* **1994 :** Création de **Red Hat Linux** et de **SuSE Linux**.
* **1996 :** Naissance de **Tux** (la mascotte) et création de l'environnement graphique **KDE**.
* **1997 :** Création de l'environnement graphique **GNOME**.
* **2004 :** Création d'**Ubuntu** par Mark Shuttleworth.
* **2011 :** Décès de Steve Jobs (5 octobre) et de Dennis Ritchie (11 octobre).

---

## 2. Arborescence du Système de Fichiers Linux (`/`)

* **`/bin` :** Binaires essentiels accessibles à tous les utilisateurs (*User Binaries*).
* **`/sbin` :** Binaires d'administration système (*System Binaries*).
* **`/etc` :** Fichiers de configuration du système et des services (*Config Files*).
* **`/dev` :** Fichiers spéciaux représentant les périphériques matériels (*Device Files*).
* **`/proc` :** Système de fichiers virtuel exposant les informations sur les processus et le noyau en temps réel (*Process Files*).
* **`/var` :** Données variables (journaux/logs, files d'attente, bases de données, caches) (*Variable Files*).
* **`/tmp` :** Fichiers temporaires, généralement purgés au redémarrage (*Temporary Files*).
* **`/usr` :** Programmes et ressources des utilisateurs (*User Programs*).
* **`/home` :** Répertoires personnels des utilisateurs (*Home Directory*).
* **`/boot` :** Fichiers nécessaires au démarrage du système (noyau, initramfs, GRUB) (*Boot Files*).
* **`/lib` :** Bibliothèques partagées essentielles au système et aux modules du noyau (*System Libraries*).
* **`/opt` :** Applications tierces ou optionnelles (*Optional Apps*).
* **`/mnt` :** Point de montage temporaire pour les systèmes de fichiers (*Mount Directory*).
* **`/media` :** Point de montage automatique pour les supports amovibles (clés USB, CD) (*Removable Media*).
* **`/srv` :** Données hébergées par les services du serveur (web, FTP, etc.) (*Service Data*).

---

## 3. Notions Clés et Commandes de Base

### Gestion des utilisateurs (UID)
* **UID (*User Identifier*) :** Identifiant numérique unique attribué à chaque compte ; cette valeur est fixe sur le système.
* **Plages d'UID :** Les UID inférieurs à `1000` (de `0` à `999`) sont réservés au système et aux comptes de services (`0` étant `root`). Les utilisateurs standards commencent à `1000`.
