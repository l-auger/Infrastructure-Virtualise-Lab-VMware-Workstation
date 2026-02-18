# Active Directory – DC1

## Présentation
DC1 est le contrôleur de domaine principal du domaine `entreprise.local`.
Il héberge Active Directory Domain Services et participe à la réplication
avec le second contrôleur de domaine (DC2).

## Sites et services Active Directory
Les deux contrôleurs de domaine sont présents dans le même site AD
(`Default-First-Site-Name`), permettant une réplication automatique.

![Sites et services AD](screenshots/ad-sites.png)

## Réplication Active Directory
La réplication entre DC1 et DC2 est fonctionnelle et assure la redondance
des données Active Directory.