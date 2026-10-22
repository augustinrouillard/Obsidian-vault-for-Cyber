---
share: true
---
# Notes : Réseau, Ports et Dépannage Outlook

## 1. Notions Réseau & Fichiers Système

### Définitions

- **SMTP (Simple Mail Transfer Protocol) :** Protocole standard d'Internet utilisé pour envoyer et acheminer les courriers électroniques.
    
- **DNS (Domain Name System) :** L'annuaire d'Internet (associe un nom de domaine à une adresse IP).
    

### Emplacement des Ports Windows

Pour consulter la liste complète des ports connus attribués sur Windows, ouvrez le fichier : `C:\Windows\System32\drivers\etc\services`

## 2. Ports et Protocoles Courants

|   |   |   |
|---|---|---|
|**Protocole**|**Port non sécurisé**|**Port sécurisé (TLS/SSL)**|
|**HTTP**|`80`|`443` (HTTPS)|
|**POP3**|`110`|`995`|
|**IMAP**|`143`|`993`|
|**SMTP**|`25`|`465` / `587`|
|**Soumission Client SMTP**|`2525`|`587`|

## 3. Commandes Utiles

- **Lister les connexions actives sur Windows :**
    
    ```
    netstat -an
    ```
    

## 4. Dépannage et Astuces Outlook

### Raccourcis Utiles (Icône Outlook en zone de notification)

- **Test d'Autodiscover :** `Ctrl` + `Clic droit` sur l'icône Outlook $\rightarrow$ **Tester la configuration automatique du messagerie**.
    
    - Saisir l'identifiant et le mot de passe, décocher **Guessmart**, puis analyser le code/XML renvoyé.
        
- **État de la connexion :** `Ctrl` + `Clic droit` sur l'icône Outlook $\rightarrow$ **Statut de la connexion**.
    

### Diagnostics & Outils

- **Lancer une application en mode sans échec :**
    
    - Appuyez sur `Win + R`, puis saisissez : `outlook.exe /safe`
        
    - _Note :_ Si le problème disparaît, le souci provient probablement d'un complément d'extension (désactivable via **Fichier** $\rightarrow$ **Options** $\rightarrow$ **Compléments**).
        
- **Scanpst.exe :** Outil de réparation des fichiers de données Outlook (`.pst` / `.ost`) pour analyser et corriger les erreurs.
    
- **Réinitialisation de profil :**
    
    - **Panneau de configuration** $\rightarrow$ **Courrier** $\rightarrow$ **Afficher les profils**.
        
    - Supprimer puis récréer le profil (résout une grande majorité des dysfonctionnements).
        
- **Outil de dépannage en ligne :** [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/ "null")
    

### Fonctionnalités

- **Affichage en conversation :** Se configure dans l'onglet **Affichage** pour regrouper les messages par fil de discussion.
    

## Résumé

- Fichier des ports : `C:\Windows\System32\drivers\etc\services`
    
- Mode sans échec : `outlook /safe` (pour isoler un problème de complément)
    
- Réparation profil : Panneau de configuration $\rightarrow$ Courrier
    
- Diagnostic réseau Outlook : `Ctrl` + `Clic droit` sur l'icône en barre des tâches