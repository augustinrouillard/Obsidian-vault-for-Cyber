---
share: true
---

## 1. La Carte Réseau et le Profil Réseau

* **Paramètres Réseau et Internet :** accessibles depuis l'icône réseau de la zone de notification ou le menu Démarrer. Ils fournissent des indications sur la connectivité du poste et les connexions détectées.
* **Profils réseau et emplacements :** chaque carte réseau est associée à un emplacement qui détermine le comportement du pare-feu :
  * **Réseau privé :** sur un poste autonome.
  * **Réseau avec domaine :** non modifiable si le poste est joint à un domaine.
  * **Réseau public :** si aucune passerelle n'est définie, si le domaine n'est pas détecté, ou si l'utilisateur refuse la visibilité sur le réseau.
* **Gestion des cartes :** accès direct aux connexions réseau via la commande `ncpa.cpl` pour configurer les cartes ou créer de nouvelles connexions (VPN, accès à distance, etc.).

---

## 2. Configuration de la Carte Réseau

* **Paramètres essentiels :** adresse IP, masque, passerelle (*gateway*), et serveurs DNS (préféré et auxiliaire).
* **Types d'adressage :**
  * **Statique :** configuré manuellement.
  * **Dynamique :** fourni par un serveur DHCP ou via **APIPA**.
  * **APIPA :** mode d'obtention automatique d'une adresse par Windows en l'absence de serveur DHCP (`169.254.0.0/16`), permettant une communication temporaire sur le réseau local.
* **Outils de gestion :**
  * **Graphiques :** zone de notification, composant « Connexions réseau », et l'assistant de résolution des problèmes.
  * **Ligne de commande (les plus précis et efficaces) :**
    * `ipconfig` : affichage de la configuration et interaction avec la pile réseau (DNS, DHCP).
    * `ping` : test de connectivité (attention, bloqué par défaut par le pare-feu Windows).
    * `tracert` : test de la route empruntée par les paquets TCP/IP.
    * `nslookup` : diagnostic de la résolution de noms d'hôte.

---

## 3. Le Pare-Feu Windows

* **Rôle :** délimiter les flux réseau autorisés en entrée et en sortie, protéger le poste contre les accès non autorisés (utilisateurs ou programmes), et s'intégrer dans la stratégie globale de sécurité de l'entreprise.
* **Caractéristiques principales :**
  * Activé par défaut : bloque certains flux en entrée et les autorise tous en sortie.
  * Intègre des règles prédéfinies activables et s'adapte à la situation du poste selon l'emplacement réseau.
  * Administrable de manière centralisée (stratégies, export).
* **Note de terrain :** on privilégie généralement un pare feu matériel à un pare feu logiciel (plus sécurisé).