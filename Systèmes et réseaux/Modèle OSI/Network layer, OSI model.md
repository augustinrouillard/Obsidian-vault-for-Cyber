---
share: true
---

Le modèle OSI :

```
`7) Couche Application`
```

Comprend les protocoles : http, smtp (simple mail transfer protocole)
Il s'agit de la couche qui interagit directement avec les données de l'utilisateur. Les applications logicielle clientes ne sont pas comprises ici.

```
`6) Couche Présentation`
```

Cette couche prépare les données afin qu'elles puissent être utilisées par la couche application. Ce niveau fait la traduction, la compression et l'encryption des données.

```
`5) Couche Session`
```

Il s'agit de la couche responsable de l'ouverture et de la fermeture de la communication entre les deux appareils. L'intervalle entre l'ouverture et la fermeture de la communication est appelé session. La couche session garantit que la session reste ouverte suffisamment longtemps pour transférer toutes les données échangées, puis ferme rapidement la session afin d'éviter le gaspillage de ressources.

```
`4) Couche Transports`
```

Cette couche est responsable de la communication de bout en bout entre les deux appareils. Cela inclut la récupération des données de la couche session et leur division en fragments appelés segments avant leur transmission à la couche.
La couche transport est également chargée du contrôle des flux et des erreurs. Le contrôle de flux détermine une vitesse de transmission optimale afin d'éviter qu'un appareil émetteur doté d'une connexion rapide ne submerge un appareil récepteur doté d'une connexion lente.

```
`3) Couche Réseau`
```

La couche réseau est chargée de faciliter le transfert de données entre deux réseaux différents. Si les deux appareils communiquant entre eux se situent sur le même réseau, la couche réseau est inutile. La couche réseau divise les segments de la couche transport en unités plus petites, appelées paquets, sur l'appareil de l'expéditeur, et réassemble ces paquets sur l'appareil recevant les données. La couche réseau trouve également le meilleur chemin physique pour assurer que les données atteignent leur destination. Cette opération est appelée routage.

Protocoles utilisés : ICMP, IGMP, IPsec

```
`2) Couche liaison
```

La couche liaison de données est très similaire à la couche réseau, si ce n'est qu'elle facilite le transfert de données entre deux appareils sur le _même_ réseau. La couche liaison de données prend les paquets de la couche réseau et les décompose en fragments plus petits, appelés trames. À l'instar de la couche réseau, la couche liaison de données est également responsable du contrôle des flux et des erreurs dans les communications intra-réseau.

```
`1) Couche Physique`
```

Cette couche inclut les équipements physiques impliqués dans le transfert de données, comme les câbles et les commutateurs. C'est également la couche où les données sont converties en séquence binaire, c'est-à-dire en chaîne de 0 et de 1.