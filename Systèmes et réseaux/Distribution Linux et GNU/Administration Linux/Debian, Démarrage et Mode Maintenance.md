---
share: true
---
## 1. Les Branches et Versions de Debian

* **Stable :** version figée ne recevant que des correctifs de sécurité. C'est la version recommandée pour les environnements de **production**.
* **Testing :** future version stable intégrant uniquement les paquets jugés suffisamment matures depuis la branche *Unstable*.
* **Unstable (toujours appelée *Sid*) :** version en constante évolution alimentée en continu par de nouveaux paquets et mises à jour (*Rolling release*).

---

## 2. Installation de Debian et Partitionnement

### Modes d'installation
* **Netinstall (*Network Install*) :** image d'installation minimale contenant uniquement le strict nécessaire pour démarrer le système ; les paquets choisis sont ensuite téléchargés directement depuis les dépôts en ligne durant l'installation.

### Espaces de stockage obligatoires
Linux nécessite au minimum deux espaces de stockage distincts :
* **La racine (`/`) :** contient l'ensemble des répertoires nécessaires au système d'exploitation.
* **La partition d'échange (`swap`) :** espace disque utilisé comme mémoire virtuelle de secours lorsque la RAM est saturée afin d'éviter un plantage du système. Elle sert également à stocker le contenu de la RAM lors de la mise en veille prolongée (*hibernation*).
  * *Dimensionnement classique :* généralement $2\text{ Go}$ ou plus selon les besoins (jusqu'à $2 \times \text{RAM}$ si l'hibernation est utilisée).

---

## 3. Le Démarrage du Système

### Le chargeur d'amorçage (*Boot Loader* — GRUB2)
Premier programme exécuté par le BIOS (Legacy) ou l'UEFI pour charger le noyau Linux. Sous Debian, il s'agit de **GRUB2**, découpé en plusieurs étapes (*stages*) :
* **Stage 1 :** situé dans le MBR (*Master Boot Record*), dans les tout premiers secteurs du disque.
* **Stage 1.5 :** situé au début du disque, juste avant les données de la première partition.
* **Stage 2 :** situé dans le répertoire `/boot/grub/` du système de fichiers.

*(Note : GRUB est rarement modifié manuellement en production, mais permet de gérer le multiboot sur un poste personnel).*

### Le noyau Linux (*Kernel*)
Assure l'interface et le dialogue direct entre le matériel (via le BIOS/UEFI) et le système d'exploitation.

### Le gestionnaire de système : `systemd`

#### Les cibles (*targets*)
`systemd` utilise des cibles regroupant des ensembles de services pour définir l'état du système :
* `poweroff.target` : arrête le système.
* `reboot.target` : redémarre le système.
* `rescue.target` : bascule en mode maintenance (mono-utilisateur).
* `multi-user.target` : démarrage en mode console (sans interface graphique).
* `graphical.target` : démarrage en mode graphique (ou console sur un serveur dépourvu d'interface graphique).

#### Commandes de gestion `systemctl`
```bash
systemctl status <service>        # Vérifier l'état d'un service
systemctl start / stop <service>  # Démarrer ou arrêter un service immédiatement
systemctl restart <service>       # Redémarrer complètement un service (coupe le service)
systemctl reload <service>        # Recharger la configuration sans interrompre le service
systemctl enable <service>        # Activer le démarrage automatique au boot
systemctl disable <service>       # Désactiver le démarrage automatique au boot
systemctl enable --now <service>  # Activer au boot ET démarrer immédiatement
systemctl disable --now <service> # Désactiver au boot ET arrêter immédiatement
```

---

## 4. Mode Maintenance au Démarrage

*(Rappel : au démarrage dans GRUB ou en mode secours, le clavier est configuré par défaut en **QWERTY**).*

### Méthode 1 : Via GRUB avec l'option `single`
Permet de démarrer en mode maintenance (`rescue.target`).
* *Prérequis :* nécessite de connaître le mot de passe `root` (ne fonctionne pas si le compte `root` est verrouillé / système uniquement en `sudo`).
* **Procédure :**
  1. Au menu GRUB, sélectionner le noyau avec les flèches et appuyer sur `e` pour éditer.
  2. Sur la ligne `linux /vmlinuz-...`, remplacer `quiet` par `single` :
     ```text
     linux /vmlinuz-6.1.0-13-amd64 root=/dev/mapper/debian--vg-lv--root ro single
     ```
  3. Démarrer avec `Ctrl + X` ou `F10`.
  4. Quitter le mode maintenance avec `Ctrl + D`.

### Méthode 2 : Via GRUB avec `init=/bin/bash` (contournement mot de passe root)
Méthode brutale donnant directement un shell `root` sans authentification (idéale si le mot de passe `root` est perdu ou désactivé).
* **Procédure :**
  1. Éditer la ligne du noyau dans GRUB (`e`) en remplaçant `quiet` par `init=/bin/bash` :
     ```text
     linux /vmlinuz-6.1.0-13-amd64 root=/dev/mapper/debian--vg-lv--root ro init=/bin/bash
     ```
  2. Démarrer avec `Ctrl + X` ou `F10`.
  3. Le système est monté en lecture seule (`ro`). Le remonter en lecture/écriture :
     ```bash
     mount -o remount,rw /
     ```
  4. Effectuer les réparations (ex. `passwd root`).
  5. Synchroniser le cache disque avant d'éteindre électriquement la machine (car `systemd` n'est pas chargé) :
     ```bash
     sync
     ```

### Méthode 3 : Via le média d'installation (CD/ISO)
1. Booter sur le média d'installation Debian (sous VMware : `Ctrl + Alt + Inser` pour redémarrer, puis appuyer rapidement sur `Échap` pour ouvrir le menu de boot).
2. Choisir **Advanced options** > **Rescue mode**.