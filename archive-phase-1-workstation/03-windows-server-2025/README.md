# Windows Server 2025 – Active Directory & Services Réseau

Ce dossier documente la mise en place d’une infrastructure **Active Directory redondée**
basée sur **Windows Server 2025**, déployée dans un lab **VMware Workstation**.

L’objectif est de fournir une base **fiable, compréhensible et reproductible**
pour une infrastructure réseau de type **PME**.

---

## Architecture générale

L’infrastructure repose sur **deux contrôleurs de domaine** :

- **DC1** : contrôleur de domaine principal
- **DC2** : contrôleur de domaine secondaire (redondance)

Les services critiques sont redondés afin d’assurer la continuité de service :

- Active Directory Domain Services (AD DS)
- DNS
- DHCP
- GPO

---

## Structure du dossier

```bash
03-windows-server-2025
├── dc1
│   ├── screenshots
│   ├── ad.md
│   ├── dns.md
│   ├── dhcp.md
│   ├── gpo.md
│   └── roles.md
│
├── dc2
│   ├── screenshots
│   ├── dns.md
│   ├── dhcp-failover.md
│   └── roles.md
│
├── ntp
│   └── ntp.md
│
└── README.md
```
DC1 – Contrôleur de domaine principal
Le serveur DC1 héberge les rôles principaux de l’infrastructure :
Active Directory Domain Services (AD DS)
DNS (zones intégrées à Active Directory)
DHCP (serveur principal)
Gestion des stratégies de groupe (GPO)

DC1 constitue le point de référence pour :
l’authentification
la résolution DNS
la distribution des adresses IP
l’application des stratégies de sécurité

📁 La configuration détaillée de chaque rôle est disponible dans le dossier dc1.

DC2 – Contrôleur de domaine secondaire
Le serveur DC2 assure la redondance des services critiques :
Contrôleur de domaine supplémentaire
DNS répliqué via Active Directory
DHCP en haute disponibilité avec DC1 (Failover)
La synchronisation entre DC1 et DC2 est assurée automatiquement par Active Directory.

📁 Les détails sont documentés dans le dossier dc2.

DNS – Redondance
Le service DNS repose sur un modèle multi-maître :
Zones DNS intégrées à Active Directory
Réplication native via AD
Les clients utilisent plusieurs serveurs DNS
Il n’existe pas de mécanisme HA actif/passif :
la haute disponibilité est assurée par la réplication Active Directory.

DHCP – Haute disponibilité
Le service DHCP est configuré en basculement (Failover) :
Mode : Équilibrage de charge
Synchronisation automatique des baux
Continuité de service en cas de panne d’un serveur

Synchronisation horaire (NTP)
La synchronisation de l’heure est centralisée :
Le contrôleur de domaine principal fait autorité
Les autres serveurs et clients se synchronisent via Active Directory

📁 La configuration NTP est documentée dans le dossier ntp.

Objectifs pédagogiques
Comprendre le fonctionnement d’Active Directory
Mettre en place une redondance réaliste
Documenter une infrastructure comme en environnement professionnel
Préparer une base solide pour des évolutions futures :
sécurité
supervision
sauvegarde