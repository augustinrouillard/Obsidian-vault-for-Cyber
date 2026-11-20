---
share: true
---

## 1. Connexion, Système et Aide

| Commande | À quoi elle sert |
| :--- | :--- |
| `ssh login@ip` | Se connecter au serveur depuis Windows |
| `scp source destination` | Copier entre Windows et le serveur (lancé depuis Windows) |
| `exit` ou `Ctrl+D` | Se déconnecter |
| `whoami`, `id` | Savoir qui je suis, mon UID et mes groupes |
| `hostname`, `uptime` | Afficher le nom de la machine et depuis quand elle est allumée |
| `who`, `tty` | Voir qui est connecté et sur quel terminal |
| `date +FORMAT`, `cal` | Afficher la date/heure au format voulu, afficher le calendrier |
| `commande --help` | Afficher l'aide rapide d'une commande |
| `man commande` | Ouvrir le manuel complet (`/` pour chercher, `q` pour quitter) |

---

## 2. Shell, Raccourcis et Variables

| Commande | À quoi elle sert |
| :--- | :--- |
| `Tab`, `Tab Tab` | Compléter automatiquement, voir les choix possibles |
| `↑`, `history`, `Ctrl+R` | Retrouver une commande précédente |
| `Ctrl+C` | Interrompre une commande en cours |
| `nom=valeur` | Créer une variable locale (sans espaces autour du `=`) |
| `echo $VARIABLE`, `env` | Afficher la valeur d'une variable, lister toutes les variables d'environnement |
| `export VAR`, `$(commande)` | Transmettre une variable aux sous-processus, utiliser le résultat d'une commande |
| `echo $PATH`, `~/bin` | Afficher les dossiers où le shell cherche les exécutables |
| `alias nom='commande'`, `type` | Créer un raccourci, connaître la nature d'une commande |
| `~/.bashrc`, `source ~/.bashrc` | Fichier des réglages permanents du shell, recharger ce fichier |

---

## 3. Navigation et Disques

| Commande | À quoi elle sert |
| :--- | :--- |
| `pwd` | Afficher le répertoire courant (où suis-je) |
| `cd chemin`, `cd ..`, `cd -`, `cd` | Aller ailleurs, dossier parent, dossier précédent, répertoire personnel (`~`) |
| `ls -l`, `ls -a`, `ls -lS`, `ls -lt`, `ls -R` | Lister : en détail, fichiers cachés, par taille, par date, récursif |
| `tree dossier` | Dessiner l'arborescence d'un dossier |
| `lsblk`, `df -h` | Lister les disques/partitions, afficher l'espace libre |
| `du -sh` | Afficher la place réellement occupée par un fichier ou dossier |

---

## 4. Gestion des Fichiers, Dossiers et Liens

| Commande | À quoi elle sert |
| :--- | :--- |
| `mkdir -p chemin`, `rmdir dossier` | Créer un dossier (et ses parents), supprimer un dossier vide |
| `cp source dest`, `cp -r source dest` | Copier un fichier, copier un dossier |
| `mv source dest` | Déplacer ou renommer un fichier/dossier |
| `rm fichier`, `rm -r dossier`, `rm -i` | Supprimer définitivement, supprimer un dossier, supprimer avec confirmation |
| `touch fichier` | Créer un fichier vide (ou mettre à jour sa date) |
| `file fichier`, `ls -i`, `stat` | Connaître le vrai type, le numéro d'inode, la fiche détaillée d'un fichier |
| `ln cible nom`, `ln -s cible nom` | Créer un lien physique, créer un lien symbolique |
| `ls -l`, `chmod +x` | Lire les droits d'accès, rendre un fichier exécutable |
| `tar -czf archive.tar.gz -C dossier element` | Créer une archive compressée |
| `tar -tzf archive`, `tar -xzf archive -C dest` | Lister le contenu d'une archive, extraire une archive |
| `*`, `?`, `[abc]` | Jokers : n'importe quelle chaîne, un seul caractère, un caractère parmi la liste |
| `{a,b}`, `{01..12}` | Expansion d'accolades pour fabriquer des noms en série |

---

## 5. Lecture, Flux et Redirections

| Commande | À quoi elle sert |
| :--- | :--- |
| `cat`, `less`, `head`, `tail`, `tail -f` | Lire un fichier : entier, page par page, début, fin, en direct |
| `head -n 3 fichier` | Afficher les 3 premières lignes d'un fichier |
| `wc -l`, `diff a b` | Compter le nombre de lignes, comparer deux fichiers |
| `>`, `>>`, `|`, `2>/dev/null` | Rediriger vers un fichier, ajouter à la fin, envoyer vers une commande, ignorer les erreurs |
| `>`, `2>`, `2>&1`, `<`, `tee fichier` | Rediriger sortie standard, erreurs, les deux, entrée standard, afficher et enregistrer |
| `cat -A`, `:set ff=unix` | Voir les caractères de fin de ligne, convertir au format Linux (sous `vi`) |

---

## 6. Recherche et Expressions Régulières

| Commande | À quoi elle sert |
| :--- | :--- |
| `grep motif fichier` | Afficher les lignes contenant le motif |
| `grep -i`, `-c`, `-n`, `-v`, `-r`, `-l`, `-o`, `-E` | Casse ignorée, compter, numéroter, inverser, récursif, noms de fichiers, extraire, regex étendue |
| `find où -name "motif"` | Trouver des fichiers par nom |
| `find ... -type f`, `-size +100M`, `-mtime +365` | Filtrer par type (fichier), par taille (> 100 Mo), par date (> 365 jours) |
| `find ... -delete` | Supprimer ce qui a été trouvé *(toujours lister sans `-delete` avant)* |
| `^`, `$`, `.`, `[0-9]`, `*`, `{n}`, `|` | Regex : début, fin, un caractère, un chiffre, répété, *n* fois, ou logique |

---

## 7. Éditeur `vi` / `vim`

| Commande | À quoi elle sert |
| :--- | :--- |
| `vi fichier` | Éditer un fichier (`i` insertion, `Échap` mode normal, `:wq` sauver/quitter, `:q!` quitter sans sauver) |
| `dd`, `dw`, `cw`, `yy`, `p`, `u`, `.` | Supprimer ligne, supprimer mot, changer mot, copier ligne, coller, annuler, répéter |
| `:g/motif/d`, `:%s/ancien/nouveau/g` | Supprimer les lignes contenant le motif, remplacer partout dans le fichier |

---

## 8. Processus et Scripts

| Commande | À quoi elle sert |
| :--- | :--- |
| `ps -f`, `ps -u $USER --forest`, `top` | Voir les processus en cours, en arborescence, en temps réel |
| `commande &`, `Ctrl+Z`, `bg`, `fg`, `jobs` | Lancer en arrière-plan, suspendre, reprendre en arrière-plan, au premier plan, lister les tâches |
| `kill PID`, `kill %1`, `kill -9 PID` | Arrêter un processus ou une tâche (`-9` pour forcer en dernier recours) |
| `#!/bin/bash` | *Shebang* : première ligne obligatoire d'un script Bash |