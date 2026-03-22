# 🧪 Infrastructure virtualisée – Lab systèmes & réseaux

## 📌 Présentation du projet

Ce projet correspond à un **laboratoire d’infrastructure virtualisée avancé**, réalisé dans un objectif de **montée en compétences en administration systèmes et réseaux**.

L’objectif est de concevoir, déployer et faire évoluer une **infrastructure d’entreprise réaliste**, incluant :

- Un **Active Directory redondé**
- **DNS et DHCP** en haute disponibilité
- Un **pare-feu centralisé (pfSense)**
- Un **poste client joint au domaine**
- Un **serveur applicatif Linux** (Debian + NGINX)
- Une **solution de sauvegarde** (Veeam)
- Une migration vers un **hyperviseur bare-metal** (VMware ESXi)

👉 Ce lab simule une **architecture PME complète**, avec segmentation réseau, sauvegarde et **tests de reprise après incident**.

---

## 📌 État du projet

| Phase   | Description                              | Statut        |
|---------|------------------------------------------|---------------|
| Phase 1 | Infrastructure sous VMware Workstation   | ✅ Terminée    |
| Phase 2 | Migration vers VMware ESXi 8.x           | ✅ Terminée   |
| Phase 3 | Intégration Veeam & PRA                  | 🔄 En déploiement |

---

# 🏗️ Phase 1 – Infrastructure sous VMware Workstation

## 🖥️ Environnement technique

- **Plateforme** : VMware Workstation  
- **Type** : Lab local  

### Réseau

- Segment **LAN personnalisé**
- Toutes les VM sur le **même réseau interne**
- Accès Internet **uniquement via pfSense**

---

## 🌐 Architecture réseau

### 🔥 Pare-feu – `SVL-PS-FWL-01`

- **OS** : pfSense 2.8.0  

**Rôle :**

- Passerelle LAN  
- NAT  
- Filtrage firewall  
- Contrôle centralisé des flux  

**Interfaces :**

- **WAN** : `192.168.56.22/24`  
- **LAN** : `192.168.11.1/24`  

👉 Tout le trafic sortant **transite par le pare-feu**.

---

## 🗄️ Machines virtuelles

### 🟦 `SVL-PS-DC1-01` — Windows Server 2025

- **AD DS**
- **DNS primaire**
- **DHCP (failover)**
- Contrôleur de domaine **principal**

---

### 🟦 `SVL-PS-DC2-01` — Windows Server 2025

- **AD DS (réplication)**
- **DNS secondaire**
- **DHCP (failover)**
- **Redondance** et continuité de service

---

### 🟩 `CL-TS-01` — Windows 11

- Joint au **domaine**
- IP via **DHCP**
- Tests **GPO validés**
- Résolution **DNS fonctionnelle**

**Exemple de GPO testée :**

- Blocage du **panneau de configuration**

---

### 🟥 `SVL-PS-APP-01` — Debian 12

Serveur applicatif hébergeant un **intranet via NGINX**.

**Objectifs pédagogiques :**

- Gestion des **permissions Linux**
- Séparation **utilisateur système / service**
- Diagnostic via **logs**
- Tests **réseau**
- **Sécurisation** du service web

---

### 🟨 `SVL-PS-VEEAM-01`

Serveur de **sauvegarde**.

**Objectifs :**

- Sauvegarde **complète des VM**
- Tests de **restauration**
- Simulation de **PRA**

---

# 🔄 Phase 2 – Migration vers VMware ESXi 8.x

## 📌 Pourquoi migrer ?

L’environnement sous **VMware Workstation** présentait plusieurs limitations :

- Pas d’**hyperviseur dédié**
- Pas d’**API VMware exploitable** pour Veeam
- Réseau virtuel **simplifié**
- Architecture peu représentative d’une **production réelle**

👉 La migration vers **ESXi** permet une architecture **bare-metal** alignée avec les **standards entreprise**.

---

## 🖥️ Hyperviseur – `SVL-PS-HV-01`

- **Hyperviseur** : VMware ESXi 8.x  
- **Type** : Bare-metal  
- **Installation** : SSD dédié  
- **Accès** : Interface Web sécurisée  
- **Gestion** : vSwitch, Port Groups, Datastore centralisé  

---

## ⚙️ Préparation matérielle

**Machine hôte :**

- **CPU** : AMD Ryzen 7 7800X3D  
- **RAM** : 64 Go  
- **SVM** : Activé  
- **IOMMU** : Activé  
- **CSM** : Disabled  
- **Secure Boot** : Disabled  
- **TPM** : Activé (optionnel)  

---

## 🌐 Nouvelle architecture virtualisée

ESXi héberge :

- `SVL-PS-DC1-01`
- `SVL-PS-DC2-01`
- `SVL-PS-FWL-01`
- `SVL-PS-APP-01`
- `SVL-PS-VEEAM-01`
- `CL-TS-01`

**Gestion via :**

- vSwitch  
- Port Groups  
- Snapshots  
- API VMware  

---

## 💾 Intégration Veeam

La migration vers **ESXi** permet :

- Sauvegarde **complète des VM**
- **Snapshots cohérents**
- **Restauration granulaire**
- Simulation de **PRA**
- Exploitation des **API VMware**

👉 Contrairement à Workstation, **ESXi expose les mécanismes nécessaires à une sauvegarde professionnelle**.

---

## 🔐 Sécurité hyperviseur

- Mot de passe **root fort**
- **SSH désactivé** par défaut
- Accès restreint au **LAN**
- Sauvegarde de la **configuration ESXi**
- Segmentation réseau via **vSwitch**
- Isolation des flux via **pfSense**

---

# 📈 Objectifs pédagogiques

Ce lab permet de :

- Comprendre une **architecture d’entreprise complète**
- Mettre en œuvre la **redondance AD / DNS / DHCP**
- Déployer un **serveur Linux sécurisé**
- Configurer un **pare-feu**
- Implémenter une **stratégie de sauvegarde**
- Simuler un **PRA**
- Approfondir la **virtualisation bare-metal**

---

# 🎯 Compétences mises en œuvre

- Administration **Windows Server**
- **Active Directory**
- **DNS / DHCP**
- **Linux (Debian)**
- **NGINX**
- **pfSense**
- **VMware Workstation**
- **VMware ESXi**
- **Veeam Backup & Replication**
- **Diagnostic & troubleshooting**
- **Documentation technique**

---

# 👤 Auteur

**Loïck**  
Projet personnel – **Administration systèmes & réseaux**  
Laboratoire d’apprentissage **avancé**
