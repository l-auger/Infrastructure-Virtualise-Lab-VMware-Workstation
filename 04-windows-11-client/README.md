# Windows 11 – Poste client du domaine

Ce dossier documente la configuration d’un poste **Windows 11** intégré au domaine **Active Directory entreprise.local**.

Ce poste client permet de valider le bon fonctionnement global de l’infrastructure mise en place dans ce laboratoire virtualisé.

## Rôle du poste client

Le poste Windows 11 joue le rôle de poste utilisateur standard et permet de vérifier :

- l’intégration au domaine Active Directory
- la résolution DNS via des contrôleurs de domaine redondés
- l’attribution d’adresses IP via DHCP avec basculement
- l’application des stratégies de groupe (GPO)

Il constitue le point de validation final du bon fonctionnement de l’infrastructure.

## Services consommés

Le poste dépend directement des services suivants :
- **Active Directory** : authentification et gestion des comptes
- **DNS** : résolution de noms interne au domaine
- **DHCP** : attribution dynamique des adresses IP
- **GPO** : application des politiques de sécurité et de configuration

## Contenu du dossier

- `jonction-domaine.md` : procédure et validation de la jonction au domaine
- `gpo-appliquees.md` : vérification de l’application des GPO
- `screenshots/` : captures de preuve (jonction, réseau, GPO)

Ce poste client est volontairement maintenu simple afin de représenter un poste utilisateur classique en environnement d’entreprise.
