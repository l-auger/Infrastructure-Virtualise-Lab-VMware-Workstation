# Rôles – DC2

Le serveur **DC2** est un contrôleur de domaine secondaire du domaine `entreprise.local`.
Il assure la redondance des services critiques fournis par DC1.

---

## Active Directory (AD DS)

- Contrôleur de domaine secondaire
- Réplique automatiquement les données Active Directory depuis DC1
- Permet l’authentification des utilisateurs en cas d’indisponibilité de DC1

---

## DNS

- Serveur DNS intégré à Active Directory
- Zones DNS répliquées automatiquement
- Participe à la résolution de noms du domaine
- Fonctionnement en **DNS redondant** (pas de HA actif/passif)

---

## DHCP (Failover)

- Participe à la haute disponibilité du service DHCP
- Réception et synchronisation des étendues depuis DC1
- Mode : **équilibrage de charge**
- Garantit la continuité de l’attribution des adresses IP

---

## Résumé

DC2 renforce la résilience de l’infrastructure en assurant :
- la continuité de l’authentification
- la redondance DNS
- la disponibilité du service DHCP
