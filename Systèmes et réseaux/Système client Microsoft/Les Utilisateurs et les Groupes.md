---
share: true
---

## 1. La Notion d'Utilisateur
* Le système d'exploitation client Windows est une porte ouverte sur le système d'information (SI) de l'entreprise.
* **Validation de l'accès au SI :**
  * Couple identifiant + mot de passe.
  * Biométrie (Windows Hello).
  * Objet tiers (carte à puce, badge).
  * Seconde authentification possible selon les contextes (SMS, lien de validation, etc.).
* 1 collaborateur de l'entreprise = 1 utilisateur du SI.

---

## 2. Gestion des Utilisateurs

### Utilisateur local
* Propre à chaque ordinateur (bonne pratique, bien que pas toujours respectée).
* Stocké dans la base de données locale **SAM** (*Security Account Manager*).
* L'utilisateur ne peut exploiter que les ressources de l'ordinateur source.

### Utilisateur du domaine
* Stocké dans une base de données commune (annuaire **Active Directory**) sur un serveur de l'entreprise (contrôleur de domaine) ou externalisé (Microsoft Azure, etc.).
* Authentification **Kerberos** sécurisée par le réseau.
* Permet d'ouvrir une session sur tous les ordinateurs du domaine.

### Le SID (*Security IDentifier*)
* Identifiant unique attribué par le système à chaque utilisateur et groupe.

### Ouverture de session
* **Utilisateurs locaux :** Compte présent dans la base SAM, affiché par défaut sur l'écran d'accueil.
* **Utilisateurs du domaine :** Jonction préalable du poste au domaine indispensable. Le domaine est sélectionné par défaut. *Attention :* la liste des utilisateurs locaux n'apparaît plus une fois l'ordinateur joint au domaine de l'entreprise.

---

## 3. Les Catégories d'Utilisateurs
* **Standard :** Membre du groupe « Utilisateurs », pour utiliser les ressources de l'ordinateur.
* **Administrateur :** Membre du groupe « Administrateurs », pour utiliser et modifier les ressources. Le compte créé à l'installation est administrateur, mais le compte administrateur intégré est désactivé par défaut.
* **Compte Invité :** Utilisation restreinte, sans mot de passe, désactivé par défaut.

---

## 4. La Gestion des Profils
* Création d'un profil personnel dans `C:\Users` lors de la première ouverture de session (contient : Documents, Téléchargements, Bureau, Images, etc.).
* **Profils spécifiques :**
  * **Profil public :** Commun et disponible pour tous les utilisateurs.
  * **Profil par défaut (caché) :** Modèle pour la création des futurs profils (accès restreint au système).
* Un utilisateur de base ne peut pas installer de logiciels.
* **Gestion des profils :** La suppression manuelle dans `C:\Users` est à proscrire. Passer par `sysdm.cpl` (onglet « Paramètres systèmes avancés ») pour supprimer ou modifier les profils proprement.

---

## 5. Gestion des Groupes
* Tout utilisateur doit appartenir à au moins un groupe.
* Le groupe possède un **SID** qui s'ajoute au jeton d'accès de l'utilisateur.
* **Types de groupes :**
  * **Groupes locaux :** Pour configurer les autorisations d'accès aux ressources et les privilèges d'administration.
  * **Groupes prédéfinis :** Présents nativement (ex. : Administrateurs, Opérateurs de sauvegarde).
  * **Entités intégrées de sécurité :** Non visibles dans les consoles, affectation automatique par le système (ex. : Tout le monde, Utilisateurs authentifiés).

---

## 6. Outils de Configuration (Utilisateurs et Groupes Locaux)

### A. Interface Graphique (GUI)
* `lusrmgr.msc` : Gestion des utilisateurs et groupes locaux.
* `compmgmt.msc` : Gestion de l'ordinateur.
* Panneau de configuration > Comptes d'utilisateurs.

### B. Ligne de Commande (CMD)
* `net user` (`net help user` pour l'aide).
* `net localgroup` (`net help localgroup`).

### C. PowerShell
* **Utilisateurs (`*-LocalUser`) :**
  * `Get-LocalUser` : Afficher la liste des utilisateurs.
  * `New-LocalUser` : Créer un nouvel utilisateur.
  * `Set-LocalUser` : Modifier un utilisateur existant.
  * `Rename-LocalUser` : Renommer un utilisateur.
  * `Enable-LocalUser` : Activer un utilisateur.
  * `Disable-LocalUser` : Désactiver un utilisateur.
  * `Remove-LocalUser` : Supprimer un utilisateur.
* **Groupes et membres (`*-LocalGroup` / `*-LocalGroupMember`) :**
  * Manipulation via les verbes `Get`, `New`, `Set`, `Remove` combinés à `-LocalGroup` ou `-LocalGroupMember`.

---

## 7. Contrôle de Comptes d'Utilisateur (UAC)
* Système qui n'accorde les privilèges administratifs qu'en cas de nécessité, même pour un administrateur.
* **Fonctionnement :** Élévation de pouvoir symbolisée par l'icône du bouclier. Validation requise pour un administrateur, authentification pour un utilisateur standard.
* **Rôle :** Lutter contre les programmes malveillants et avertir lors de modifications sensibles. Il est fortement déconseillé de désactiver l'UAC.
* **Configuration :** 
  * Panneau de configuration.
  * Stratégie de sécurité locale via `secpol.msc` (*Stratégies locales > Options de sécurité*).
  * Utilisation du clic droit : « Exécuter en tant qu'administrateur ».

---

## 8. Récapitulatif et Bonnes Pratiques
* **Structure d'un utilisateur :** Nom d'ouverture de session, mot de passe, profil local, SID, et appartenances de groupe constituant le **jeton d'accès** (consultable avec la commande `whoami`).
* **Bonnes pratiques d'administration :**
  * Éviter les caractères spéciaux de la langue française dans la nommage des postes et des comptes.
  * Ne jamais créer un utilisateur à partir de zéro : toujours copier un utilisateur existant.