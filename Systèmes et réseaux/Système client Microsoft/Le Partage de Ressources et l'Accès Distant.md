---
share: true
---

## 1. Le Partage de Ressources

* **Principes :** permet d'accéder à une ressource (fichiers, dossiers, imprimantes) hébergée par un serveur ou tout autre système connecté au réseau (poste, smartphone, copieur).
* **Mise en place et accès :**
  * Des **droits administratifs** sont requis pour partager (modification du système).
  * Une **authentification** est obligatoire (compte local ou du domaine).
  * Trois niveaux d'accès définis sur le partage : **Lecture**, **Modifier**, **Contrôle total**.
  * **Double vérification d'identité :** 1) au niveau du partage, puis 2) au niveau des droits NTFS. Les autorisations de partage sont cumulatives et la plus restrictive l'emporte.

---

## 2. Partage de Fichiers

### Accès aux partages sous Windows 11
* **Momentané :** via l'Explorateur avec le chemin UNC `\\serveur\partage`.
* **Durable :** fonctionnalité *Connecter un lecteur réseau* (mappages mémorisés avec le profil).
* **Ligne de commande (CMD) :** `net use z: \\serveur\partage` (la commande `net view` liste les partages).
* **PowerShell :** `New-SmbMapping -LocalPath 'R:' -RemotePath '\\SRV-FIC\Compta'`.

### Méthodes de création de partage
* **Explorateur Windows :** Propriétés de l'élément > onglet *Partage* (préférer le partage avancé au partage simplifié). Par défaut, l'entité *Tout le monde* est en Lecture — **bonne pratique :** remplacer par *Utilisateurs authentifiés*.
* **Console MMC (fsmgmt.msc) :** *Dossiers partagés* pour visualiser les partages actifs, les sessions, les fichiers ouverts et les partages administratifs.
* **Invite de commandes (CMD) :** `net share commun=d:\note_de_service /grant:"utilisateurs authentifiés",FULL`.
* **PowerShell :** `New-SmbShare -Name "VMSFiles" -Path "C:\ClusterStorage\Volume1\VMFiles" -FullAccess "Authenticated Users"`.

---

## 3. Session à Distance (Bureau à Distance)

* **Fonctionnement :** accès distant complet à un poste (nécessite des privilèges spécifiques et un compte valide).
  * Postes clients : 1 seule session active (mode maintenance, pas d'interaction locale simultanée).
  * Serveurs : jusqu'à 2 sessions simultanées avec des comptes différents.
* **Connexion :**
  * Natif : outil *Connexion Bureau à distance* (`mstsc` ou `mstsc /v:serveur`). Permet de mapper les ressources locales.
* **Configuration du poste cible :**
  * Paramètres système avancés > onglet *Utilisation à distance*.
  * Désactivé par défaut. Deux niveaux d'authentification (standard ou **NLA** — *Network Level Authentication*).
  * Protocole **RDP (port 3389)** avec configuration automatique du pare-feu selon l'emplacement réseau.

---

## 4. Assistance à Distance

* **Outil natif (`msra`) :** activé par défaut, très guidé et sécurisé pour l'utilisateur, mais sommaire pour le technicien.
* **Fonctionnement :** création d'une invitation d'assistance (par fichier partagé, e-mail ou internet).
* **Alternatives :** VNC, AnyDesk, TeamViewer, LogMeIn.