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

| Notation | Description |
| :--- | :--- |
| **Texte sans crochet ni accolade** | Élément obligatoire à saisir ou à choisir |
| **[texte entre crochets]** | Élément facultatif |
| **{texte entre accolades}** | Choix obligatoire parmi les éléments proposés |
| **Barre verticale (`\|`)** | Séparateur ou choix exclusif / alternatif |
| **Points de suspension (`...`)** | Éléments pouvant être répétés plusieurs fois |