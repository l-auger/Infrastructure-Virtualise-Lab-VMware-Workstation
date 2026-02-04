# Règles de pare-feu pfSense

Les règles de pare-feu ont été volontairement maintenues simples afin de garantir la stabilité et la lisibilité de l’infrastructure.

Les règles sont appliquées sur l’interface LAN, conformément au fonctionnement de pfSense (filtrage entrant par interface).

![Règles firewall LAN](screenshots/firewall-rules-lan.png)

## Description des règles

### Anti-Lockout Rule
- Règle automatique pfSense
- Autorise l’accès à l’interface d’administration (ports 80 et 443)
- Empêche tout verrouillage administratif

### Default allow LAN to any (IPv4)
- Autorise les machines du LAN à accéder aux autres réseaux et à Internet
- Indispensable au bon fonctionnement :
  - Active Directory
  - DNS
  - DHCP

### Default allow LAN IPv6 to any
- Règle par défaut non exploitée dans ce lab
- Conservée pour cohérence avec la configuration pfSense

## Choix de sécurité

Cette configuration minimaliste est volontaire :
- Environnement de test contrôlé
- Lisibilité maximale
- Base saine pour des évolutions futures (VLAN, filtrage inter-réseaux)
