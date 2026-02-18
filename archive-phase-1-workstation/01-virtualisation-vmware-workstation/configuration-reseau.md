# Configuration réseau globale

Cette section décrit l’architecture réseau générale du lab,
indépendamment des rôles applicatifs installés sur les serveurs.

Le réseau est conçu pour reproduire une **infrastructure de type PME**
dans un environnement virtualisé local.

---

## Type de réseau virtualisé

Le lab repose sur un **LAN Segment VMware Workstation**.

Le LAN Segment permet :
- Une isolation complète du réseau
- Aucun accès direct au réseau physique
- Un contrôle total des communications internes

Ce choix est particulièrement adapté à un lab d’apprentissage,
car il reproduit un LAN d’entreprise fermé.

---

## Plan d’adressage IP

Le LAN principal utilise un adressage privé :

- **Réseau** : `192.168.11.0/24`
- **Passerelle** : pare-feu virtuel pfsense
- **Serveurs** : adresses IP fixes
- **Clients** : adresses IP dynamiques (DHCP)

Ce plan d’adressage est volontairement simple
afin de faciliter la compréhension et le dépannage.

---

## Services présents sur le réseau

Le réseau héberge :

- Des contrôleurs de domaine Active Directory
- Des serveurs DNS
- Des serveurs DHCP
- Des postes clients
- Des serveurs applicatifs

Les services critiques sont redondés
lorsque cela est pertinent dans un contexte PME.
