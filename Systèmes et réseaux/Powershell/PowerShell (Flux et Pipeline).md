---
share: true
---

## 1. La Redirection de Flux

Une cmdlet manipule trois flux standard :
* **Entrée standard (`Stdin` : 0) :** par défaut, le clavier.
* **Sortie standard (`Stdout` : 1) :** par défaut, l'écran (résultats).
* **Sortie d'erreur (`Stderr` : 2) :** par défaut, l'écran (erreurs).

### Syntaxe des redirections
* `Cmdlet > fichier` ou `Cmdlet 1> fichier` : redirige la sortie standard vers un fichier (création ou écrasement).
* `Cmdlet >> fichier` ou `Cmdlet 1>> fichier` : redirige la sortie standard à la fin d'un fichier (ajout).
* `Cmdlet 2> fichier.err` : redirige le flux d'erreur vers un fichier dédié.
* `Cmdlet 2>> fichier.err` : redirige le flux d'erreur à la fin du fichier d'erreur.
* `Cmdlet > fichier 2>&1` : redirige à la fois la sortie standard et la sortie d'erreur dans le même fichier.
* `Cmdlet 2>$null` : redirige le flux d'erreur « dans le vide » (masquage des erreurs).

### Exemple d'utilisation
```powershell
Get-LocalUser > C:\temp\LocalUserList.txt
Get-Content C:\temp\LocalUserList.txt
```

---

## 2. Le Pipeline

Le pipeline (`|`) permet d'enchaîner les cmdlets en transmettant directement le résultat de la sortie standard (`stdout`) d'une commande vers l'entrée standard (`stdin`) de la suivante (`cmdlet1 | cmdlet2 | cmdlet3`).

### Filtrage des propriétés
Utilisé conjointement avec des cmdlets de sélection pour restreindre les informations affichées :
```powershell
Get-NetAdapter | Select-Object Name, Status, LinkSpeed
```