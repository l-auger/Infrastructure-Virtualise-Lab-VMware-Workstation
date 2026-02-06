# Debian 12 – Serveur applicatif

Ce dossier documente la mise en place d’un **serveur Debian 12** utilisé comme
serveur applicatif au sein de l’infrastructure Active Directory.

L’objectif est d’héberger une application de manière centralisée sur un serveur Linux,
tout en permettant son utilisation depuis des postes clients Windows intégrés au domaine.

---

## Objectifs

- Héberger une application de façon persistante (« en dur » sur le serveur)
- Centraliser l’accès à l’application
- Préparer un déploiement ou un accès contrôlé depuis les postes clients
- S’intégrer proprement dans une infrastructure de type PME

---

## Rôle du serveur Debian

Le serveur Debian 12 joue le rôle de :

- Serveur applicatif
- Support de services (web / applicatif)
- Point central d’hébergement de l’application

L’application **n’est pas installée sur les postes clients**, mais hébergée sur le serveur,
ce qui permet :
- une maintenance centralisée
- une meilleure sécurité
- une administration simplifiée

---

## Intégration avec Active Directory (objectif)

Dans la suite du lab, l’accès à l’application pourra être :

- facilité via une GPO (raccourci, accès réseau, URL)
- restreint selon les utilisateurs ou groupes AD
- contrôlé depuis le domaine sans installer l’application localement

---

## Structure du dossier

```bash
05-debian-12
├── README.md
├── etat-actuel.md
├── services-prevu.md
└── evolutions.md
```


