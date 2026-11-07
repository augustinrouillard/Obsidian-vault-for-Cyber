---
share: true
---

## 1. La Sécurité NTFS et les ACL
* Sur un volume formaté en NTFS, tous les répertoires et fichiers sont soumis à la sécurité NTFS via des autorisations qui définissent les privilèges d'accès.
* L'utilisateur présente son jeton d'accès, qui est filtré par la ressource. Les autorisations sont stockées dans l'index du système de fichiers et sont consultables/modifiables dans l'onglet **Sécurité** des propriétés d'un objet.
* **Définitions clés :**
  * **ACL (*Access Control List*) :** Liste des ACE propres à l'objet pour des groupes ou des utilisateurs.
  * **ACE (*Access Control Entry*) :** Privilège d'accès ou de refus (autoriser/refuser) d'un groupe ou d'un utilisateur sur un objet.
  * **DACL (*Discretionary Access Control List*) :** Liste de contrôle d'accès discrétionnaire qui contient les utilisateurs et les groupes (règle générale : éviter d'intégrer des utilisateurs individuels, privilégier les groupes).

---

## 2. Niveaux d'Autorisations et Règles de Priorité

### Les autorisations de base (cumulatives)
* **Lecture :** Affichage du contenu du dossier, lecture, lecture et exécution.
* **Modification :** Écriture et modification (en plus des droits de lecture).
* **Contrôle total :** Tous les droits.
* *Note :* Des autorisations spéciales plus fines (création de fichiers, suppression de sous-dossiers, etc.) sont configurables depuis le menu Avancé.

### Règles de fonctionnement et de priorité
* **Refus implicite :** Un groupe absent de la DACL se voit l'accès refusé.
* **Cumul :** Plusieurs règles d'accès s'appliquant à un même utilisateur se cumulent (la règle la plus permissive l'emporte).
* **Priorité absolue du refus :** Le **refus explicite l'emporte sur l'autorisation** et prend la priorité sur tout.

---

## 3. Les Mécanismes d'Héritage et Comportements de Copie/Déplacement

### L'héritage
* Par défaut, un répertoire propage ses autorisations à ses objets enfants (les autorisations héritées apparaissent grisées et ne sont pas modifiables directement).
* Pour les modifier, il faut agir sur le dossier parent ou **casser l'héritage** (à effectuer avec précaution). Une autorisation d'accès locale l'emporte sur un refus explicite hérité.

### Comportement lors de la copie ou du déplacement d'un fichier/dossier
| Action | Au sein d'une même partition / volume | Entre deux partitions / volumes |
| :--- | :--- | :--- |
| **Déplacement** | **Conservation** des autorisations d'origine | **Héritage** du nouveau dossier parent |
| **Copie** | **Héritage** du nouveau dossier parent | **Héritage** du nouveau dossier parent |

---

## 4. Vérification, Gestion et Bonnes Pratiques

### Vérification des accès
* Utiliser l'onglet **Accès effectif** (dans le menu *Avancé*) pour tester et afficher les autorisations effectives d'un compte utilisateur, de groupe ou de périphérique.

### Bonnes pratiques d'administration
* Privilégier au maximum les groupes dans les DACL (bannir l'assignation directe à des utilisateurs unitaires pour éviter le chaos).
* Utiliser en priorité les ACE de base et s'appuyer sur l'héritage.
* Attention au double jeton d'accès des administrateurs ( géré par l'UAC). Il est possible de désactiver le mode d'approbation administrateur via les Stratégies de sécurité locale (`secpol.msc` > *Paramètres de sécurité > Stratégies locales > Options de sécurité* > *Contrôle de compte d'utilisateur : exécuter les comptes d'administrateurs en mode d'approbation d'administrateur*).