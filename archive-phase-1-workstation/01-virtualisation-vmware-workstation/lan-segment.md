# LAN Segment

Le lab repose sur un **LAN Segment VMware Workstation**
qui simule un réseau local d’entreprise.

---

## Rôle du LAN Segment

Le LAN Segment permet :

- D’isoler totalement les machines virtuelles
- De simuler un réseau interne sans accès externe direct
- De maîtriser précisément les flux réseau

Toutes les machines du lab sont connectées à ce LAN Segment.

---

## Machines connectées

Le LAN Segment héberge :

- Les contrôleurs de domaine (DC1 et DC2)
- Les serveurs DNS et DHCP
- Les serveurs applicatifs
- Les postes clients

Chaque machine possède :
- Une adresse IP fixe (serveurs)
- Ou une adresse IP dynamique (clients)

---

## Avantages du choix

Ce choix permet :

- Une architecture simple et lisible
- Une reproduction fidèle d’un LAN PME
- Une évolution future vers une segmentation plus avancée
