---
share: true
---
---
share: true
---

# Tableau d'Équivalences : Bash (Linux) vs PowerShell (Windows)

| Bash (Linux) | PowerShell (Windows - Commandes & Raccourcis) | Description rapide |
| :--- | :--- | :--- |
| `pwd` | `pwd` ou `Get-Location` *(alias : `gl`)* | Afficher le répertoire courant |
| `cd <dossier>` | `cd <dossier>` ou `Set-Location` *(alias : `sl`, `chdir`)* | Changer de répertoire |
| `ls` / `ls -a` | `ls`, `dir` ou `Get-ChildItem` *(alias : `gci`)* / `gci -Force` | Lister le contenu d'un répertoire (et les fichiers cachés avec `-Force`) |
| `ls -R` / `find . -name "*.txt"` | `Get-ChildItem -Recurse -Filter "*.txt"` *(ou `gci -r`)* | Lister le contenu de manière récursive et rechercher par nom |
| `mkdir <dossier>` / `mkdir -p` | `mkdir` ou `New-Item -ItemType Directory` *(alias : `ni`)* | Créer un dossier ou une arborescence complète (natif avec `New-Item`) |
| `rmdir <dossier>` / `rm -r` | `rmdir` ou `Remove-Item` *(alias : `ri`, `rm`, `del`)* | Supprimer un répertoire vide ou récursivement (`-Recurse`) |
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
| `grep` | `Where-Object` *(alias : `where`, `?`)* ou `Select-String` *(alias : `sls`)* | Filtrer des objets ou rechercher une chaîne de caractères |
| — | `New-`, `Set-`, `Remove-` *(ex: `New-LocalUser`)* | Verbes fondamentaux pour créer, modifier ou supprimer des objets et ressources |
| `alias` | `Get-Alias` *(alias : `gal`)* | Afficher ou gérer les alias de commandes |
| `history` | `Get-History` *(alias : `h`, `ghy`)* | Afficher l'historique des commandes de la session |
| `uname -a` | `$PSVersionTable` ou `Get-ComputerInfo` | Afficher les informations de version du système/shell |
| `whoami` / `id` | `whoami` ou `[System.Security.Principal.WindowsIdentity]::GetCurrent()` | Afficher l'utilisateur courant, son SID et ses groupes |
| `who` / `w` | `query user` *(ou `quser`)* | Afficher les utilisateurs actuellement connectés à la machine |
| `passwd` | `Set-LocalUser -Name <user> -Password ...` *(ou `net user`)* | Modifier le mot de passe d'un utilisateur local |
| `usermod -a -G sudo <user>` | `Add-LocalGroupMember -Group "Administrateurs" -Member <user>` | Ajouter un utilisateur au groupe des administrateurs locaux |
| `echo $$` | `$PID` | Afficher l'identifiant du processus (PID) du shell en cours |
| `tar xzvf <archive>` | `Expand-Archive -Path <archive.zip> -DestinationPath <dest>` | Extraire une archive compressée |
| `ssh user@ip` | `ssh user@ip` *(natif sous Windows 10/11)* ou `Enter-PSSession` | Se connecter à distance en ligne de commande |