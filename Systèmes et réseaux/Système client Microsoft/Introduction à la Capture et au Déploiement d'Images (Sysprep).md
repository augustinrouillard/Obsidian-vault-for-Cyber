---
share: true
---

## 1. Dépannage et Astuces Préliminaires
* **Outils de secours :** en cas de défaillance des outils natifs, possibilité de booter sur l'ISO de Windows 11 pour utiliser `diskpart`, WinRE ou la restauration système.
* **Dossier partagé Hôte/VM :** éteindre la machine virtuelle, puis dans les paramètres aller sur *Option > Dossier partagé > Enable*.
* **Ventoy :** solution recommandée pour regrouper tous les fichiers ISO.
* **Partage SMB 3.0 :** réactiver le composant en cas de dysfonctionnement récurrent, notamment avec les copieurs et les imprimantes.

---

## 2. Préparation du Master
* **Objectif :** concevoir un modèle à dupliquer.
* **Étapes clés :**
  * Installation du poste de référence.
  * Configuration initiale du système d'exploitation.
  * Installation des applications validées par la DSI.
  * Préparation au clonage à l'aide de l'outil `sysprep`.

---

## 3. L'Outil Sysprep

### Paramètres et exécution
* **Paramètres essentiels :**
  * **OOBE (*Out-of-Box Experience*) :** gère l'interaction utilisateur au premier redémarrage.
  * **Généraliser :** supprime les données spécifiques au matériel pour permettre le déploiement sur d'autres machines.
  * **Arrêter le système :** éteint la machine après généralisation.
* **Ligne de commande :** 
  ```cmd
  C:\Windows\System32\sysprep\sysprep.exe /oobe /generalize /shutdown