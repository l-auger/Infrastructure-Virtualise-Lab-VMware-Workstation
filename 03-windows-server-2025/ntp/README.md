# Synchronisation de l’heure (NTP) – Active Directory

## Pourquoi le NTP est critique

Dans un environnement Active Directory, une mauvaise synchronisation
de l’heure peut provoquer :
- des erreurs Kerberos
- des échecs d’authentification
- des problèmes de GPO
- des incohérences entre contrôleurs de domaine

## Principe de fonctionnement

La synchronisation de l’heure repose sur une hiérarchie :

Internet (serveurs NTP publics)
↓
PDC Emulator (SRV-AD02)
↓
Autres contrôleurs de domaine
↓
Postes clients et serveurs membres

Un seul serveur communique avec Internet : le PDC Emulator.

## Structure de la documentation

- `pdc-emulator.md` : configuration complète du PDC
- `autres-machines.md` : DC secondaires et clients
- `verification.md` : contrôles et dépannage
