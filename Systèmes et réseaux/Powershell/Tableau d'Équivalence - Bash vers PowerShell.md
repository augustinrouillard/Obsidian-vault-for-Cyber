---
share: true
---

| Bash (Linux)                 | PowerShell (Windows - Commandes & Raccourcis)              | Description                                           |
| :--------------------------- | :--------------------------------------------------------- | :---------------------------------------------------- |
| `pwd`                        | `pwd` ou `Get-Location` *(alias : `sl`)*                   | Afficher le répertoire courant                        |
| `cd <dossier>`               | `cd <dossier>` ou `Set-Location` *(alias : `sl`, `chdir`)* | Changer de répertoire                                 |
| `ls`                         | `ls`, `dir` ou `Get-ChildItem` *(alias : `gci`)*           | Lister le contenu d'un répertoire                     |
| `ls -R` / `find .`           | `Get-ChildItem -Recurse` *(ou `gci -r`)*                   | Lister le contenu de manière récursive                |
| `mkdir <dossier>`            | `mkdir` ou `New-Item -ItemType Directory` *(alias : `ni`)* | Créer un nouveau dossier / répertoire                 |
| `touch <fichier>`            | `New-Item` ou `New-Item -ItemType File` *(alias : `ni`)*   | Créer un fichier vide                                 |
| `cp <src> <dest>`            | `cp`, `copy` ou `Copy-Item` *(alias : `cpi`)*              | Copier un fichier ou un dossier                       |
| `cat <fichier>`              | `cat`, `type` ou `Get-Content` *(alias : `gc`)*            | Afficher le contenu d'un fichier texte                |
| `xdg-open` / `open`          | `notepad <fichier>` ou `Invoke-Item` *(alias : `ii`)*      | Ouvrir un fichier avec son application par défaut     |
| `commande > fichier`         | `commande > fichier` *(ou `Out-File`)*                     | Rediriger la sortie en créant/écrasant un fichier     |
| `commande >> fichier`        | `commande >> fichier`                                      | Rediriger la sortie en l'ajoutant à la fin du fichier |
| `man <cmd>` / `<cmd> --help` | `Get-Help <cmd>` *(alias : `help`, `man`)*                 | Afficher la documentation/l'aide d'une commande       |
| `alias`                      | `Get-Alias` *(alias : `gal`)*                              | Afficher ou gérer les alias de commandes              |
| `uname -a`                   | `$PSVersionTable`                                          | Afficher les informations de version du système/shell |

