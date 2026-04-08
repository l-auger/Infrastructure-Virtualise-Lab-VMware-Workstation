01 — Objectif de sauvegarde avec Veeam Backup & Replication
Contexte
Dans le cadre de ce laboratoire, l'infrastructure repose sur un hyperviseur VMware ESXi hébergeant plusieurs machines virtuelles. Pour assurer la protection des données, la solution Veeam Backup & Replication est déployée afin de gérer l'ensemble des sauvegardes.

Pourquoi Veeam sur ESXi ?
Veeam Backup & Replication est une solution spécifiquement conçue pour les environnements virtualisés. Elle s'intègre nativement avec VMware ESXi grâce aux API VMware (VADP — vStorage APIs for Data Protection), ce qui lui permet de sauvegarder les machines virtuelles sans agent, directement au niveau de l'hyperviseur, sans interrompre leur fonctionnement.
Cela offre plusieurs avantages concrets :

Aucune interruption de service : les VMs restent actives pendant la sauvegarde grâce aux snapshots VMware
Cohérence des données : Veeam s'assure que les données applicatives sont dans un état stable avant de les capturer
Granularité : il est possible de restaurer une VM entière, un seul fichier, ou même un objet applicatif (boîte mail, base de données, etc.)


Fonctionnement général
┌─────────────────────────────────────────────┐
│              VMware ESXi                    │
│                                             │
│   ┌──────────┐   ┌──────────┐               │
│   │   VM 1   │   │   VM 2   │               │
│   └────┬─────┘   └────┬─────┘               │
│        │  snapshot    │  snapshot           │
└────────┼─────────────-┼─────────────────────┘
         │              │
         ▼              ▼
┌─────────────────────────────────────────────┐
│       Veeam Backup & Replication            │
│                                             │
│   - Planification des jobs de backup        │
│   - Compression & déduplication             │
│   - Envoi vers le référentiel de sauvegarde │
└─────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────┐
│         Référentiel de sauvegarde           │
│       (disque local, NAS, etc.)             │
└─────────────────────────────────────────────┘

Objectifs visés
ObjectifDescription💾 Sauvegarde des VMsProtéger l'ensemble des machines virtuelles hébergées sur ESXi⏱️ Planification automatiqueDéfinir des jobs de backup réguliers (quotidien, hebdomadaire)🗜️ Optimisation du stockageRéduire l'espace utilisé via la compression et la déduplication🔄 Restauration rapideÊtre capable de restaurer une VM ou un fichier en cas d'incident✅ Validation des backupsVérifier l'intégrité des sauvegardes via SureBackup

Ce que ce lab permet de mettre en pratique

Installer et configurer Veeam Backup & Replication
Connecter Veeam à un hôte ESXi
Créer et planifier des jobs de sauvegarde
Effectuer une restauration complète de VM
Effectuer une restauration granulaire (fichier unique)