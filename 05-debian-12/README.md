Debian 12 – Serveur applicatif

Ce dossier documente la mise en place d’un serveur Debian 12 utilisé pour héberger une application web interne au sein de l’infrastructure Active Directory du laboratoire.

L’objectif principal est de centraliser l’hébergement de l’application sur un serveur Linux, tout en permettant un accès simple et contrôlé depuis les postes clients Windows intégrés au domaine.

Rôle dans l’infrastructure

Le serveur Debian assure les fonctions suivantes :

hébergement d’un service web interne basé sur Nginx

mise à disposition d’une application accessible uniquement depuis le réseau local

séparation claire entre hébergement serveur et utilisation côté poste client

L’application est accessible via l’URL interne :

http://app.entreprise.local

Cette adresse est résolue par le service DNS Active Directory, garantissant un accès stable et indépendant de l’adresse IP du serveur.

Principe d’architecture

L’architecture repose sur une approche simple et réaliste :

un serveur Debian dédié à l’hébergement applicatif

une résolution de nom assurée par le DNS du domaine

un accès utilisateur réalisé via navigateur web depuis un poste Windows

une possibilité future de distribution ou de restriction d’accès via GPO

Cette organisation correspond à un déploiement classique dans un environnement de type PME.

Contenu du dossier

Le dossier comprend :

la description des étapes de déploiement du serveur web

les méthodes de validation du fonctionnement côté serveur et côté client

les captures d’écran attestant du bon fonctionnement du service