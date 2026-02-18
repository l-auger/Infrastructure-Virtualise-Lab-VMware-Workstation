# Lab Infrastructure Virtualisée – VMware Workstation

Ce dépôt présente un **lab d’infrastructure système et réseau** réalisé sous **VMware Workstation**.  
Il a pour objectif de reproduire une **infrastructure de type PME**, documentée et structurée,
dans un but pédagogique et professionnalisant.

---

## 🎯 Objectifs du lab

- Comprendre le fonctionnement d’une infrastructure Active Directory
- Mettre en place des services réseau essentiels (DNS, DHCP)
- Assurer une redondance logique des services critiques
- Documenter clairement chaque composant de l’infrastructure

---

## 🖥️ Environnement technique

- **Hyperviseur** : VMware Workstation
- **Type de réseau** : LAN Segment (réseau isolé)
- **Systèmes** :
  - Windows Server 2025
  - Windows 11 (clients)
  - Debian 12 (serveurs Linux)

---

## 🌐 Architecture réseau

- **Réseau LAN** : `192.168.11.0/24`
- **Serveurs** : adresses IP fixes
- **Clients** : adresses IP dynamiques (DHCP)
- **Isolation complète** via LAN Segment VMware

---

## 🧱 Infrastructure Active Directory

### Contrôleurs de domaine
- **DC1** : contrôleur principal
- **DC2** : contrôleur secondaire (redondance)

### Services intégrés
- Active Directory Domain Services
- DNS intégré à l’AD (zones AD-integrated)
- Réplication automatique entre DC1 et DC2

---

## 📡 DNS

- DNS installé sur **DC1 et DC2**
- Zones intégrées à Active Directory
- Réplication automatique des enregistrements
- Les clients utilisent **les deux serveurs DNS**

> Il ne s’agit pas de HA DNS au sens cluster,
mais d’une **redondance logique native Active Directory**.

---

## 📦 DHCP

- DHCP installé sur **DC1 et DC2**
- Étendue unique pour le LAN
- **DHCP Failover configuré**
  - Mode : Équilibrage de charge
  - Synchronisation automatique des baux
- Continuité du service en cas d’indisponibilité d’un serveur

---

## 📁 Organisation du dépôt
```bash
-INFRASTRUCTURE-VIRTUALISEE-LAB-VMWARE/
│
├── 00-architecture/
│   ├── plan-adressage.md
│   ├── schema-reseau.png
│   └── README.md
│
├── 01-virtualisation-vmware-workstation/
│   ├── configuration-reseau.md
│   ├── lan-segment.md
│   ├── limite-et-choix.md
│   └── README.md
│
├── 02-pfsense/
│   ├── filtrage-pfsense.md
│   └── README.md
│
├── 03-windows-server-2025/
│   ├── dc1/
│   │   ├── screenshots/
│   │   │   ├── ad-sites.png
│   │   │   ├── dhcp-failover.png
│   │   │   ├── dhcp-options.png
│   │   │   ├── dhcp-scope.png
│   │   │   ├── dns-dc-records.png
│   │   │   ├── dns-msdcs.png
│   │   │   └── dns-zone-properties.png
│   │   ├── ad.md
│   │   ├── dhcp.md
│   │   ├── dns.md
│   │   ├── gpo.md
│   │   └── roles.md
│   │
│   ├── dc2/
│   │   ├── screenshots/
│   │   │   ├── dhcp-failover.png
│   │   │   └── dns.png
│   │   ├── dhcp-failover.md
│   │   ├── dns.md
│   │   └── roles.md
│   │
│   └── README.md
│
├── 04-windows-11-client/
│   ├── client-config.md
│   └── screenshots/
│
├── 05-debian-12/
│   ├── base-installation.md
│   └── README.md
│
├── 06-veeam-backup/
│   ├── sauvegarde.md
│   └── README.md
│
├── 07-securite/
│   ├── bonnes-pratiques.md
│   ├── axes-amelioration.md
│   └── README.md
│
├── 08-evolutions/
│   ├── roadmap.md
│   ├── perspectives.md
│   └── README.md
│
├── .gitattributes
└── README.md
```

Chaque dossier contient :
- Des fichiers `.md` explicatifs
- Des captures d’écran de configuration

---

## 🧠 Approche pédagogique

- Infrastructure volontairement simple
- Priorité à la compréhension des mécanismes
- Documentation pensée pour une **relecture technique ou académique**
- Base évolutive pour des ajouts futurs (sécurité, supervision, segmentation)

---

## 🚀 Évolutions possibles

- Supervision (Grafana, Centreon)
- Sécurité avancée (GPO, firewalling, audits)
- Sauvegarde et PRA

---

## 📌 Conclusion

Ce lab constitue une **base solide et réaliste** pour comprendre,
déployer et documenter une infrastructure système et réseau
dans un contexte PME.