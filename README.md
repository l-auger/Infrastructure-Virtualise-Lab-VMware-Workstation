# 🧪 Infrastructure virtualisée – Lab systèmes & réseaux

## 📌 Présentation du projet

Ce projet correspond à un **laboratoire d’infrastructure virtualisée avancé**, réalisé dans un objectif de **montée en compétences en administration systèmes et réseaux**.

L’objectif initial était de concevoir une **infrastructure PME complète** incluant :

- Active Directory redondé  
- DNS / DHCP en haute disponibilité  
- Pare-feu centralisé (**pfSense**)  
- Poste client joint au domaine  
- Serveur applicatif Linux (**Debian + NGINX**)  
- Solution de sauvegarde (**Veeam**)  
- Migration vers un hyperviseur **bare-metal VMware ESXi**

👉 Suite à l’évolution du projet, seule la **brique applicative Linux** est désormais conservée et migrée vers ESXi,  
le reste de l’infrastructure étant **décommissionné** afin de simplifier l’architecture et de se concentrer sur :

- la virtualisation bare-metal  
- l’hébergement applicatif Linux  
- la sauvegarde ciblée  
- la logique de production minimale réaliste  

---

## 📌 État du projet

| Phase | Description | Statut |
|-------|-------------|--------|
| Phase 1 | Infrastructure complète sous VMware Workstation | ✅ Terminée |
| Phase 2 | Migration vers VMware ESXi 8.0.2 (Debian uniquement) | 🚧 En cours |
| Phase 3 | Sauvegarde Veeam ciblée + optimisation | 🔄 À venir |

---

# 🏗️ Phase 1 – Infrastructure sous VMware Workstation

## 🖥️ Environnement technique initial

- **Plateforme** : VMware Workstation  
- **Type** : Lab local complet  
- **Réseau** :
  - LAN personnalisé  
  - Accès Internet via **pfSense**  
  - Toutes les VM interconnectées  

Cette phase avait pour objectif de **reproduire une PME complète**.

---

## 🗄️ Machines virtuelles initiales

- **DC1 / DC2** – Active Directory, DNS, DHCP  
- **pfSense** – Pare-feu et passerelle  
- **Client Windows 11** – Poste utilisateur domaine  
- **Debian 12 (NGINX)** – Serveur applicatif intranet  
- **Veeam** – Sauvegarde et PRA  

👉 Cette architecture a servi de **socle pédagogique**, mais n’est plus maintenue.

---

# 🔄 Phase 2 – Migration vers VMware ESXi 8.0.2

## 📌 Changement de stratégie

L’objectif n’est plus de migrer **toute l’infrastructure**, mais uniquement :

➡️ **le serveur applicatif Debian 12**

Les autres composants ont été :

- **arrêtés**
- **non migrés**
- **décommissionnés volontairement**

### 🎯 Pourquoi ce choix ?

- Simplifier l’architecture  
- Se concentrer sur la **virtualisation ESXi réelle**  
- Travailler un **cas d’usage production minimal**  
- Réduire la complexité inutile d’un AD en lab local  
- Mettre l’accent sur **Linux, NGINX et la sauvegarde**  

---

## 🖥️ Hyperviseur – SVL-PS-HV-01

- **Hyperviseur** : VMware ESXi 8.0.2  
- **Type** : Bare-metal  
- **Installation** : SSD dédié  
- **Accès** : Interface Web sécurisée  
- **Gestion** :
  - vSwitch  
  - Port Groups  
  - Datastore local  

---

## 🌐 Architecture virtualisée actuelle

### VM conservée et migrée

#### 🟥 SVL-PS-APP-01 — Debian 12

**Rôle :**

- Serveur applicatif Linux  
- Hébergement **NGINX intranet / web**  
- Base de travail pour :
  - sécurité Linux  
  - supervision  
  - sauvegarde  
  - optimisation système  

👉 Cette VM constitue désormais **le cœur du lab**.

---

## 💾 Sauvegarde et continuité

La nouvelle stratégie prévoit :

- Sauvegarde **ciblée** de la VM Debian  
- Utilisation de **Veeam** uniquement pour cette charge utile  
- Stockage des sauvegardes sur :
  - **NAS personnel local** (sauvegarde locale primaire)
  - logique inspirée du **3-2-1** à terme  

Objectif : simuler une **production légère mais réaliste**.

---

## 🔐 Sécurité de l’hyperviseur

- Mot de passe **root fort**  
- **SSH désactivé** par défaut  
- Accès **restreint au LAN**  
- Sauvegarde de la **configuration ESXi**  
- Isolation réseau via **vSwitch**  

---

# 📈 Objectifs pédagogiques actuels

Ce lab est désormais centré sur :

- la **virtualisation bare-metal ESXi**  
- l’**administration Linux serveur**  
- l’**hébergement web NGINX**  
- la **stratégie de sauvegarde réelle**  
- la **sécurisation système**  
- la **documentation technique professionnelle**  

👉 Approche volontairement **minimaliste mais réaliste**.

---

# 🎯 Compétences mises en œuvre

- VMware **ESXi**
- Administration **Linux (Debian)**
- **NGINX**
- Sauvegarde **Veeam**
- Réseau virtuel ESXi
- Sécurité système
- Diagnostic & troubleshooting
- Documentation d’infrastructure

---

# 👤 Auteur

**Loïck**  
Projet personnel – **Administration systèmes & réseaux**  
Laboratoire d’apprentissage **orienté production réelle**
