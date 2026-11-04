---
share: true
---

## 1. Interagir avec Windows 11

- **Caractéristiques :** Système d'exploitation multi-utilisateur et multitâche.
- **Éléments de l'interface graphique :**
  - **Le Bureau :** Personnalisable, gestion de plusieurs bureaux supplémentaires.
  - **Le Menu Démarrer :** 
    - Clic gauche : tuiles et applications.
    - Clic droit : accès aux principaux raccourcis d'administration.
    - Zone de recherche indexée (permet d'accéder aux *Paramètres* ou au *Panneau de configuration* qui reste toujours présent).
  - **La Barre des tâches :** 
    - Raccourci `Windows + Tab` : affichage de la **TimeLine** (historique des actions) et des bureaux virtuels.
    - Gestionnaire des tâches et gestion des applications au démarrage.
  - **La Zone de notification (en bas à droite) :** Calendrier, horloge, applications en arrière-plan, état de la connectivité réseau et accès à « Tous les paramètres ».

### Raccourcis et Commandes Utiles
- `Windows + I` : Ouvre les **Paramètres**.
- `Windows + R` puis `mrt` : Lance l'outil de suppression de logiciels malveillants Windows.
- `Windows + R` puis `mmc` : Ouvre une **Console de gestion Microsoft (MMC)** personnalisée (*Fichier > Ajouter/Supprimer un composant logiciel enfichable*). Les consoles préconfigurées s'obtiennent via un clic droit sur le menu Démarrer.

---

## 2. Prise en main de l'Interface Graphique et de la CLI

- **Contexte :** Windows est historiquement orienté **GUI** (Interface Graphique), mais la **CLI** (Ligne de commande) reste indispensable pour des actions spécifiques, l'administration avancée et l'automatisation (scripts).
- **Le Terminal Windows :** Regroupe les principaux shells Microsoft :
  - `cmd.exe` : Basée sur l'historique `command.com` (MS-DOS).
  - **PowerShell :** Présent nativement depuis Windows Server 2008.
  - **Azure Cloud Shell :** Pour gérer des infrastructures cloud Azure.

---

## 3. Le Shell `cmd.exe` (Command Prompt)

### Règles de syntaxe de base
- **Premier mot :** Toujours la commande à exécuter.
- **Espace :** Caractère spécial faisant office de séparateur entre chaque élément.
- **Options :** Généralement identifiées par le préfixe `/`.
- **Caractères spéciaux :** Utiliser des guillemets (`'...'` ou `"..."`) pour convertir des chaînes avec espaces en caractères alphanumériques (ex: `'Mes Documents'`).
- **Redirection des flux :**
  - `>` : Crée ou écrase un fichier avec le résultat de la commande.
  - `>>` : Ajoute le résultat à la fin d'un fichier existant.
  - *Exemple :* `help shutdown > aide.txt`

### Comprendre la syntaxe de l'aide (`help`)
Pour comprendre comment lire l'aide d'une commande (ex: `help copy`), voici la signification des notations standards :


## 4. Présentation de PowerShell et Manipulation des Objets

### Présentation de PowerShell
* PowerShell est le dernier shell en date chez Microsoft, agissant comme un interpréteur de commande et un langage de script orienté objet.
* Il s'appuie sur les bibliothèques du .NET Framework.
* On y accède via la console texte native (avec droits administrateurs), la console graphique **ISE** (*Integrated Scripting Environment*) orientée création de scripts, ou **Windows Terminal**.

### Les Commandes : Les Cmdlets
* En PowerShell, on ne parle pas de commandes mais de **cmdlets**.
* Elles sont constituées d'un **verbe** et d'un **nom** séparés par un tiret (`Verbe-Nom`) et ne sont pas sensibles à la casse.
* Les verbes les plus courants sont : `Get`, `Set`, `Remove`, `Add`, `New`.
* Les cmdlets comportent des paramètres (optionnels ou obligatoires) accompagnés ou non d'arguments, et peuvent posséder des alias. Exemple : `Get-ChildItem -path C:\users`.
* La variable `$PSVersionTable` permet d'afficher un tableau des versions (avec `PSVersion` et `PSCompatibleVersions`).

### Le Système d'Aide Intégré
* Il permet d'obtenir des informations sur l'usage des commandes et les concepts de PowerShell.
* L'aide est accessible via plusieurs commandes :
  * `Get-Help` ou `Help` (affichage page par page).
  * `Man` (alias de `Help`).
  * L'option `-?` disponible directement depuis toutes les cmdlets.
* Commandes et options d'aide utiles :
  * `Get-help <cmdlet>` : Affiche l'aide de la cmdlet ciblée.
  * `Help about` : Affiche la liste des concepts disponibles.
  * `Get-Help -Examples` : N'affiche que les exemples d'utilisation de la cmdlet.
  * `Get-Help -ShowWindow` : Affiche l'aide complète dans une fenêtre séparée.
  * `Get-Help -Online` : Ouvre l'aide détaillée sur les serveurs de Microsoft.
* Pour les versions récentes (v3 et plus), l'aide peut être téléchargée et mise à jour localement via `Update-Help` (nécessite un dépôt local pour les systèmes déconnectés).

### Les Objets PowerShell
* Issus de la programmation, les éléments manipulés (carte réseau, disque dur, utilisateur, fichier, etc.) sont des **objets**.
* Un objet est constitué de :
  * **Propriétés** : Ses caractéristiques (ex: forme, dimensions, masse).
  * **Méthodes** : Les actions réalisables sur l'objet (ex: lancer, gonfler).
* **Commandes de découverte et d'affichage :**
  * `Get-Command` : Liste l'ensemble des commandes disponibles (permet l'utilisation de jokers comme `Get-Command get-*` ou `Get-Command *printer*`).
  * `Get-Objet` : Affiche certaines propriétés principales (les autres étant masquées pour faciliter la lecture).
  * `Get-Objet | select *` : Affiche l'intégralité des propriétés et leurs valeurs.
  * `Get-Objet | select prop1, prop2` ou `(Get-Objet).propriété` : Affiche des propriétés spécifiques ciblées.
* **Manipulation et modification des objets (Verbes d'action) :**
  * Création : `New-Objet -Paramètre "Valeur"`.
  * Modification : `Set-Objet -Paramètre "Valeur"`.
  * Suppression : `Remove-Objet -Paramètre "Valeur"`.