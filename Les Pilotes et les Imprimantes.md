---
share: true
---

## 1. Les Pilotes (Drivers)

* Prise en charge du matériel :
  * **Plug and Play :** prise en charge « à chaud ».
  * **Non Plug and Play :** nécessite un redémarrage (plus rare).
* Modes de prise en charge : détection et installation automatique ou manuelle.
* Outil de gestion : Gestionnaire de périphériques (`devmgmt.msc`) pour afficher les composants, mettre à jour, désactiver, désinstaller, restaurer un pilote ou consulter les détails.

### Identifiants matériels
* **ID compatible :** utilisé par Windows pour identifier des pilotes compatibles en l'absence de pilote spécifique.
* **Numéro d'identification matériel :** chaîne unique identifiant précisément un composant pour assurer une correspondance exacte.

### Windows et les spécificités des pilotes
* Spécifiques à l'architecture : 32 bits (`x86`) ou 64 bits (`x64` / `AMD64`).
* **Pilotes signés :** privilégiés par Microsoft (certificats Microsoft ou tiers de confiance) pour garantir la stabilité ; obligatoires en 64 bits.
* **Fichiers principaux :**
  * `.inf` : définition du pilote au format texte.
  * `.sys` : le pilote lui-même.
  * `.cat` : certificat de sécurité.
  * `.exe`, `.dll`, `.xml` : fichiers complémentaires selon les besoins.
* **Emplacements et stockage :**
  * `C:\Windows\inf` : tous les fichiers d'information (`oemXX.inf` pour les pilotes installés manuellement).
  * `C:\Windows\system32` et `C:\Windows\sysWOW64` : fichiers binaires complémentaires.
  * Magasin de pilotes (*DriverStore*) : situé dans `C:\Windows\System32\DriverStore` pour une prise en charge immédiate lors de l'installation du système.

### Commandes et outils CLI
* `msinfo32` : informations détaillées sur le matériel.
* `driverquery` : liste les pilotes installés (`driverquery /SI` pour les pilotes signés).
* `pnputil` : gestion du magasin de pilotes :
  * `pnputil /enum-drivers` : liste les pilotes tiers (`oemXX.inf`).
  * `pnputil /add-driver pilote.inf` : ajoute un pilote au magasin.

---

## 2. Les Imprimantes (Périphériques d'Impression)

### Vocabulaire et distinctions
* **Périphérique d'impression :** le matériel physique (moteur permettant de sortir la feuille).
* **Imprimante :** l'objet logiciel (pilote, file d'attente, port d'impression). Le **service spouleur** assure la conversion numérique et l'envoi du travail vers le port d'impression.
* **Imprimante locale :** directement reliée à l'ordinateur via un port local.
* **Imprimante partagée :** imprimante locale partagée sur le réseau via l'OS (disponible uniquement si l'ordinateur hôte est allumé).
* **Imprimante réseau :** périphérique indépendant doté de son propre système, d'une interface réseau et d'un service web de configuration.
* *Note de terrain :* en cas de dysfonctionnement, on ne redémarre pas tout le serveur d'impression, mais seulement le service de la file d'attente (spouleur).

### Les imprimantes locales
* Reconnues directement ou via l'installation du pilote constructeur signé.
* **Sécurité NTFS :** des droits d'accès spécifiques peuvent être configurés via l'onglet *Sécurité* des propriétés de l'imprimante.
* Gestion via le Panneau de configuration (file d'attente, options avancées comme les horaires ou les priorités, et partage sur le réseau via le chemin UNC `\\serveur\imprimante`). Partager une imprimante locale partage automatiquement son pilote, mais nécessite que l'hôte reste allumé.

### Les imprimantes réseau
* Raccordées directement au réseau de l'entreprise.
* Utilisation du rôle Windows **Serveur d'impression** pour centraliser la gestion et le partage de plusieurs imprimantes.
* Accès pour les clients distants via le chemin UNC du serveur d'impression, puis connexion.