# Infrastructure virtualisée – Laboratoire VMware ESXi

## Objectif du projet

Ce laboratoire a pour objectif de concevoir et exploiter une infrastructure virtualisée réaliste, hébergée sous **VMware ESXi**, afin de travailler concrètement :

- l’administration systèmes Windows et Linux  
- la gestion réseau en environnement virtualisé  
- le déploiement d’un serveur applicatif Linux  
- la mise en place d’une stratégie de sauvegarde et de restauration  
- l’application de bonnes pratiques d’exploitation  

L’approche retenue est volontairement simple, cohérente et proche d’une petite PME, afin de privilégier la compréhension réelle de l’infrastructure plutôt que la complexité artificielle.

---

## Architecture cible

L’environnement repose sur plusieurs machines virtuelles hébergées sous ESXi, chacune assurant un rôle précis dans l’infrastructure.

### Windows Server – Services d’infrastructure

Une machine virtuelle Windows Server fournit les services réseau essentiels :

- DHCP : attribution automatique des adresses IP  
- DNS : résolution de noms interne  

Ces services permettent de simuler un socle réseau minimal d’entreprise sans déployer d’Active Directory complet, afin de rester concentré sur :

- l’exploitation système  
- la configuration réseau  
- la gestion des dépendances entre services  

---

### Debian 12 – Serveur applicatif Linux

Une machine virtuelle Debian 12 joue le rôle de serveur applicatif.

Fonctions principales :

- hébergement d’une application web  
- déploiement via Docker  
- exposition du service via NGINX  
- tests de connectivité réseau interne (DNS, passerelle, firewall)  

Objectif :

Manipuler un environnement Linux proche de la production et comprendre la gestion complète d’un service applicatif.

---

## Architecture réseau

L’infrastructure réseau s’appuie sur :

- Hyperviseur : VMware ESXi  
- Pare-feu : pfSense  
- Réseau LAN interne virtualisé  

Fonctionnement :

- attribution des adresses IP via DHCP Windows  
- résolution DNS interne via Windows Server  
- filtrage et séparation des flux via pfSense  

Le pare-feu assure :

- la séparation WAN / LAN  
- le contrôle des règles réseau  
- la protection minimale de l’infrastructure virtualisée  

---

## Sauvegarde et reprise d’activité

La protection de l’environnement repose sur :

- Veeam Backup & Replication  

Objectifs :

- sauvegarder les machines virtuelles critiques  
- tester des restaurations complètes  
- valider le fonctionnement des services après récupération  

Tests réalisés :

- restauration d’une VM supprimée  
- vérification des services applicatifs  
- contrôle de la connectivité réseau et des dépendances  

Une évolution vers une stratégie de sauvegarde de type **3-2-1** reste envisageable.

---

## Compétences développées

Ce laboratoire permet de travailler concrètement :

- administration Windows Server  
- configuration DHCP / DNS  
- virtualisation sous VMware ESXi  
- exploitation Linux serveur  
- conteneurisation applicative de base  
- sauvegarde et restauration en contexte entreprise  
- rédaction de documentation technique structurée  

---

## Position dans le projet global

| Phase | Orientation | Statut |
|-------|------------|--------|
| Phase 1 | Infrastructure complète sous VMware Workstation | Terminée |
| Phase 2 | Infrastructure ESXi simplifiée et réaliste | En cours |
| Phase 3 | Optimisation, supervision et PRA avancé | À venir |

---

## Philosophie du laboratoire

L’objectif n’est pas de multiplier les technologies, mais de maîtriser une architecture cohérente et exploitable.

Chaque composant du laboratoire est :

- installé  
- configuré  
- testé  
- documenté  
- restauré après panne simulée  
