---
share: true
---

## 1. Gestion des Utilisateurs et Informations de Session

* **`passwd` :** Permet de modifier le mot de passe de l'utilisateur courant (ou d'un autre utilisateur avec les droits `root` via `sudo passwd <utilisateur>`).
* **`who` :** Affiche la liste des utilisateurs actuellement connectés au système.
  * `who -Hqu` : Affiche les en-têtes de colonnes (`-H`), le nombre total et le nom des utilisateurs connectés (`-q`), ainsi que des informations sur l'état d'inactivité (`-u`).
* **`w` :** Affiche qui est connecté et quelles commandes/processus sont en cours d'exécution pour chacun.
* **`id` :** Affiche les identifiants numériques de l'utilisateur courant : **UID** (*User ID*), **GID** (*Group ID* principal) et les groupes secondaires associés.
* **`echo $$` :** Affiche le **PID** (*Process ID*) du shell actuel.
* **Ajouter un utilisateur aux administrateurs (`sudo`) :**
  ```bash
  usermod -a -G sudo <username>
  ```
  *(Note : `-a` pour append/ajouter sans écraser les groupes existants, `-G` pour spécifier le groupe secondaire).*

---

## 2. Chemins et Exécution

* **Chemin absolu :** Chemin complet partant toujours de la racine du système `/` (ex : `/home/user30/scripts/monscript.sh`).
* **Chemin relatif :** Chemin défini par rapport au répertoire courant dans lequel on se trouve (ex : `./monscript.sh` ou `../documents`).
* **Lancer un script :** Nécessite de préciser le chemin (souvent `./` pour le dossier courant) et d'avoir les droits d'exécution (`chmod +x`) :
  ```bash
  ./monscript.sh
  ```

---

## 3. Gestion des Fichiers et Répertoires

### Lister le contenu (`ls`)
```bash
ls [-aAlrRt]
```
* `-a` : Affiche tous les fichiers, y compris les fichiers cachés (commençant par `.`).
* `-A` : Comme `-a`, mais masque les entrées `.` (dossier courant) et `..` (dossier parent).
* `-l` : Format d'affichage détaillé (droits, propriétaire, taille, date).
* `-r` : Inverse l'ordre de tri.
* `-R` : Liste récursivement les sous-dossiers.
* `-t` : Trie par date de modification (du plus récent au plus ancien).

### Créer des répertoires (`mkdir`)
```bash
mkdir [-pv] <nom_dossier>
```
* `-p` (*parents*) : Crée l'arborescence complète des dossiers parents si nécessaire sans erreur.
* `-v` (*verbose*) : Affiche un message pour chaque répertoire créé.
* **Exemples :**
  ```bash
  mkdir dossier01
  mkdir -v dossier02
  mkdir -p -v dir02/dir03
  ```

### Supprimer des répertoires vides (`rmdir`)
```bash
rmdir [-pv] <nom_dossier>
```
* `-p` (*parents*) : Supprime le répertoire ainsi que ses dossiers parents devenus vides.
* `-v` (*verbose*) : Affiche une confirmation pour chaque suppression.
* **Exemples :**
  ```bash
  rmdir -v dossier01
  rmdir -pv dir02/dir03
  ```

### Rechercher des fichiers (`find`)
Permet de rechercher des fichiers selon différents critères (ici le nom dans le répertoire courant `.`) :
```bash
find . -name "*.txt"
```