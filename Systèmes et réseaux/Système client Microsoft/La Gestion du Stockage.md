---
share: true
---


## 1. Le Partitionnement

Partitionner un disque consiste à "séparer" un disque en plusieurs portions étanches et indépendantes. Ces informations sont stockées dans une **table de partitions** au format **MBR** ou **GPT**.

### Table de partitions MBR (Master Boot Record)
* Technologie historique (datant des années 80).
* Lecture du MBR par le BIOS (pose problème si le PC fonctionne en UEFI).
* Stocké sur le premier secteur du disque.
* Limité à **4 partitions maximum**.
* Ne gère pas les partitions de plus de **2,2 To**.

### Table de partitionnement GPT (GUID Partition Table)
* Nouveau format qui gomme les inconvénients du MBR.
* Dupliqué sur plusieurs secteurs du disque.
* Lu par l'UEFI (évolution du BIOS depuis 2013).
* Jusqu'à **128 partitions maximum**.
* Taille maximale d'une partition : **8 Zo** (ou 256 To si NTFS).
* Compatible uniquement avec les systèmes d'exploitation 64-bits et les puces UEFI.

### Disques de Base vs Disques Dynamiques
* **Disque Dynamique :** Permet d'évoluer par rapport au disque de base. Les partitions contenues sur un disque dynamique s'appellent des **volumes**.
* Il est possible d'étendre un volume grâce à l'espace libre du disque source ou d'un disque supplémentaire, permettant de gérer les disques par ensemble (**RAID**).
* *Conversion :* Passer un disque de base en dynamique se fait **sans perte de données**. En revanche, une fois en dynamique, impossible de revenir en standard.

---

## 2. Le Formatage et les Systèmes de Fichiers (FS)

Après le partitionnement, vient le formatage. Formater une partition ou un lecteur logique consiste à installer un système de fichiers dont le rôle est d'organiser le rangement et l'accès aux données. Une partition ou un lecteur formaté s'appelle un **volume**.
* **Formatage rapide :** Supprime uniquement l'index et non les données.
* **Réparation / Scan :** 
  * `chkdsk C: /f /r /x` pour réparer un disque.
  * `sfc /scannow` (en mode admin) pour scanner et résoudre les données corrompues.

### Les principaux Systèmes de Fichiers
* **NTFS :** 
  * Système par défaut chez Microsoft.
  * Nativement sécurisé (ACL), chiffrement intégré (EFS) et compression intégrée.
  * Supporte des tailles de volume jusqu'à 256 To.
* **FAT16 / FAT32 :** 
  * Historique, non sécurisé nativement.
  * Volume maximum : 2 Go / 2 To.
  * Taille maximale d'un fichier : 2 Go / 4 Go.
* **ReFS (Resilient File System) :** 
  * Évolution de NTFS.
  * Taille des volumes quasi illimitée avec correction proactive des erreurs.
* **Autres :** Ext4, VMFS, UDF, etc.

---

## 3. Les Disques Durs Virtuels (VHD / VHDX)
* Fichiers de stockage virtuels (de taille fixe ou dynamique).
* Bootables et utilisés par défaut pour les machines virtuelles (Hyper-V).
* Utilisables sur machines physiques et montables comme des images ISO.
* Manipulables comme de simples fichiers (clonage, déplacement, compression, versioning).

---

## 4. Outils de Gestion du Stockage

### A. Interface Graphique (GUI)
* Console de gestion des disques : `diskmgmt.msc`.

### B. Ligne de Commande (CMD)
* `diskpart` : Outil en ligne de commande très utilisé en production.

### C. PowerShell
Commandes de base pour configurer un disque et un volume :
* `Get-Disk` : Permet de relever le numéro du nouveau disque.
* `Initialize-Disk -Number <ID>` : Initialise le disque (par défaut en GPT ; préciser `-PartitionStyle MBR` pour la rétrocompatibilité).
* `New-Partition -DiskNumber <ID> -UseMaximumSize -AssignDriveLetter` : Crée la partition. *(On peut aussi assigner la lettre après coup avec `Set-Partition`)*.
* `Format-Volume -DriveLetter <Lettre>` : Formate le volume (par défaut en NTFS).

> **Règle d'or :** Ne jamais attribuer les lettres **A** et **B** à un volume, car elles sont historiquement réservées aux anciens lecteurs de disquettes.

---

## 5. Notions de Tolérance de Panne (RAID)

* **RAID 0 (Volume étendu/bande) :** Deux disques (ex: 1 To + 1 To) combinés. Si l'un des disques tombe en panne, on perd des données sans savoir lesquelles.
* **RAID 1 (Mirroring / Miroir) :** Deux disques de 1 To offrent 1 To de stockage utile. Les données sont dupliquées. Si un disque lâche, l'autre prend le relais. *(Note de terrain : lors du remplacement d'un disque dur mécanique défectueux, il faut penser à le "mettre à température" en le laissant un moment dans le serveur pour éviter un choc thermique et une casse immédiate)*.
* **RAID 5 :** Nécessite au moins 3 disques de 1 To pour obtenir 2 To de stockage utile (tolérance de la perte d'un disque). La carte RAID peut reconstruire automatiquement un disque défaillant.