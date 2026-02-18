# DHCP – DC1

## Présentation
Le service DHCP est installé sur DC1 et configuré en haute disponibilité
avec DC2 grâce au mécanisme de basculement DHCP (Failover).

## Étendue DHCP
Une étendue IPv4 est configurée pour le réseau LAN.
Elle est active et permet la distribution automatique des adresses IP.

![Étendue DHCP](screenshots/dhcp-scope.png)

## Options DHCP
Les options DHCP fournissent automatiquement aux clients :
- la passerelle par défaut
- les serveurs DNS
- le nom de domaine Active Directory

![Options DHCP](screenshots/dhcp-options.png)

## Basculement DHCP (Failover)
Le DHCP est configuré en **mode équilibrage de charge (Load Balancing)** :
- Répartition 50 / 50
- État : Normal
- Communication active entre DC1 et DC2

![Failover DHCP](screenshots/dhcp-failover.png)

## Conclusion
La configuration DHCP assure une continuité de service.
En cas de défaillance d’un serveur, les clients continuent
à obtenir des adresses IP sans interruption.
