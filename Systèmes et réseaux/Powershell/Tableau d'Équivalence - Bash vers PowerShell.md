---
share: true
---
---

| Bash (Linux) | PowerShell (Windows - Commandes & Raccourcis) | Description rapide |
| :--- | :--- | :--- |
| `pwd` | `pwd` ou `Get-Location` *(alias : `sl`)* | Afficher le répertoire courant |
| `cd <dossier>` | `cd <dossier>` ou `Set-Location` *(alias : `sl`, `chdir`)* | Changer de répertoire |
| `ls` | `ls`, `dir` ou `Get-ChildItem` *(alias : `gci`)* | Lister le contenu d'un répertoire |
| `ls -R` / `find .` | `Get-ChildItem -Recurse` *(ou `gci -r`)* | Lister le contenu de manière récursive |
| `mkdir <dossier>` | `mkdir` ou `New-Item -ItemType Directory` *(alias : `ni`)* | Créer un nouveau dossier / répertoire |
| `touch <fichier>` | `New-Item` ou `New-Item -ItemType File` *(alias : `ni`)* | Créer un fichier vide |
| `cp <src> <dest>` | `cp`, `copy` ou `Copy-Item` *(alias : `cpi`)* | Copier un fichier ou un dossier |
| `cat <fichier>` | `cat`, `type` ou `Get-Content` *(alias : `gc`)* | Afficher le contenu d'un fichier texte |
| `xdg-open` / `open` | `notepad <fichier>` ou `Invoke-Item` *(alias : `ii`)* | Ouvrir un fichier avec son application par défaut |
| `commande > fichier` | `commande > fichier` *(ou `Out-File`)* | Rediriger la sortie en créant/écrasant un fichier |
| `commande >> fichier` | `commande >> fichier` | Rediriger la sortie en l'ajoutant à la fin du fichier |
| `man <cmd>` / `<cmd> --help` | `Get-Help <cmd>` *(alias : `help`, `man`)* | Afficher la documentation/l'aide d'une commande |
| — | `Update-Help` | Mettre à jour l'aide PowerShell depuis Internet ou un dépôt local |
| `type` / `which` | `Get-Command` *(alias : `gcm`)* | Découvrir et lister toutes les commandes ou filtrer par motif (ex: `Get-Command get-*`) |
| `awk` / `cut` | `Select-Object` *(alias : `select`)* | Sélectionner et afficher des propriétés spécifiques d'un objet (ex: `| select nom, taille`) |
| — | `New-`, `Set-`, `Remove-` *(ex: `New-LocalUser`)* | Verbes fondamentaux pour créer, modifier ou supprimer des objets et ressources |
| `alias` | `Get-Alias` *(alias : `gal`)* | Afficher ou gérer les alias de commandes |
| `uname -a` | `$PSVersionTable` | Afficher les informations de version du système/shell |