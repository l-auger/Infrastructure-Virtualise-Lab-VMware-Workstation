🧪 Infrastructure Virtualisée – Lab Systèmes & Réseaux
📌 Présentation du projet

Ce projet correspond à un laboratoire d’infrastructure virtualisée réalisé dans un objectif de formation, de test et de montée en compétences autour des environnements systèmes et réseaux en entreprise.

L’objectif est de simuler une infrastructure d’entreprise réaliste, en reproduisant :

Un Active Directory redondé

DNS et DHCP en haute disponibilité

Un pare-feu en passerelle (pfSense)

Un poste client joint au domaine

Un serveur applicatif Debian (NGINX – Intranet)

Une solution de sauvegarde (Veeam)

Une évolution vers un hyperviseur bare-metal (ESXi)

📌 État du projet

✅ Phase 1 : Infrastructure sous VMware Workstation

🚧 Phase 2 : Migration vers VMware ESXi 8.x

🏗️ Phase 1 – Infrastructure sous VMware Workstation
🖥️ Environnement technique

Plateforme de virtualisation : VMware Workstation

Type d’environnement : Lab local

Réseau :

Segment LAN personnalisé

Toutes les VM sur le même réseau interne

Accès Internet exclusivement via pfSense

🌐 Architecture réseau

🔥 Pare-feu – SVL-PS-FWL-01

OS : pfSense 2.8.0

Rôle :

Passerelle LAN

NAT

Filtrage firewall

Point de sortie Internet unique

Interfaces :

WAN : 192.168.56.22/24

LAN : 192.168.11.1/24

Tout le trafic sortant du LAN transite par le pare-feu, permettant un contrôle centralisé.

🗄️ Machines virtuelles
🟦 SVL-PS-DC1-01 – Windows Server 2025

AD DS

DNS (primaire)

DHCP (failover)

Contrôleur de domaine principal.

🟦 SVL-PS-DC2-01 – Windows Server 2025

AD DS (réplication)

DNS (secondaire)

DHCP (failover)

Assure la redondance et la continuité de service.

🟩 CL-TS-01 – Windows 11

Poste client joint au domaine

IP via DHCP

Tests GPO validés

Résolution DNS fonctionnelle

Exemple GPO testée :
Blocage du panneau de configuration.

🟥 SVL-PS-APP-01 – Debian 12

Serveur applicatif hébergeant un intranet via NGINX.

Objectifs :

Hébergement web interne

Tests de permissions Linux

Séparation utilisateur système / service

Diagnostic via logs

Tests réseau

🟨 SVL-PS-VEEAM-01

Serveur de sauvegarde.

Objectifs :

Sauvegarde VM complète

Tests restauration

Simulation PRA

🔧 Configuration des ressources

Les VM ont été configurées avec des ressources confortables pour faciliter les tests.

Une optimisation progressive est prévue afin de se rapprocher d’un environnement production réaliste.

🔄 Phase 2 – Migration vers VMware ESXi 8.x
📌 Pourquoi migrer ?

L’environnement Workstation présente certaines limitations :

Pas d’hyperviseur centralisé

Support limité pour Veeam

Pas d’API VMware exploitable

Pas de gestion avancée des vSwitch

Architecture peu représentative d’une production réelle

La migration vers ESXi permet une architecture bare-metal alignée avec les standards entreprise.

🖥️ Hyperviseur – SVL-PS-HV-01

Hyperviseur : VMware ESXi 8.x

Type : Bare-metal

Installation : SSD dédié

Accès : Interface Web (https://IP_ESXI)

⚙️ Préparation matérielle

Machine hôte :

CPU : AMD Ryzen 7 7800X3D

RAM : 64 Go

Virtualisation SVM : Activée

IOMMU : Activé

CSM : Disabled

Secure Boot : Disabled

TPM : Activé (optionnel)

🌐 Nouvelle architecture virtualisée

ESXi héberge désormais :

SVL-PS-DC1-01

SVL-PS-DC2-01

SVL-PS-FWL-01

SVL-PS-APP-01

SVL-PS-VEEAM-01

CL-TS-01

Gestion via :

vSwitch

Port Groups

Datastore centralisé

Snapshots

API VMware

💾 Intégration Veeam

La migration vers ESXi permet :

Sauvegarde VM complète

Snapshot cohérent

Restauration granulaire

Tests de PRA

Exploitation de l’API VMware

Contrairement à Workstation, ESXi expose les mécanismes nécessaires à une sauvegarde professionnelle.

🔐 Sécurité hyperviseur

Mot de passe root fort

SSH désactivé par défaut

Accès restreint au LAN

Sauvegarde de la configuration ESXi

Segmentation réseau via vSwitch

📈 Objectifs pédagogiques

Ce lab permet de :

Comprendre une architecture d’entreprise complète

Mettre en œuvre la redondance AD/DNS/DHCP

Déployer un serveur Linux sécurisé

Gérer un pare-feu

Implémenter une stratégie de sauvegarde

Simuler un Plan de Reprise d’Activité

Approfondir la virtualisation bare-metal

👤 Auteur

Loïck
Projet personnel – Systèmes & Réseaux
Laboratoire d’apprentissage avancé
