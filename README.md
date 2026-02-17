# 🧪 Infrastructure virtualisée – Lab systèmes & réseaux (Phase 2)

## 📌 Présentation

Ce dépôt documente la **phase 2** d’un laboratoire d’infrastructure virtualisée, réalisé dans un objectif de :

- montée en compétences en **administration systèmes et réseaux**
- mise en place d’une **virtualisation bare-metal réaliste**
- expérimentation autour de **Linux serveur, NGINX et sauvegarde**
- reproduction d’un **cas d’usage proche de la production**

La phase 1 (infrastructure PME complète sous VMware Workstation) est désormais **archivée**.  
Cette phase 2 introduit une **architecture simplifiée, cohérente et exploitable**.

---

# 🎯 Objectif de la phase 2

Passer :

- d’un **lab pédagogique complet mais lourd**
- à une **infrastructure minimaliste réaliste**

centrée sur :

- **VMware ESXi 8.x bare-metal**
- un **serveur Linux Debian 12 applicatif**
- l’**hébergement web via NGINX**
- une **stratégie de sauvegarde réelle (Veeam + NAS local)**
- la **sécurisation et l’exploitation système**

👉 L’objectif est de construire un **socle crédible d’infrastructure de production légère**.

---

# 🖥️ Hyperviseur

## SVL-PS-HV-01 — VMware ESXi 8.0.2

- **Type** : bare-metal  
- **Installation** : SSD dédié  
- **Accès** : interface Web sécurisée  
- **Réseau** : vSwitch + Port Groups  
- **Stockage** : datastore local ESXi  

Cette base fournit :

- isolation matérielle complète  
- stabilité supérieure à Workstation  
- compatibilité native avec **Veeam**  
- fondation pour une **exploitation réelle**

---

# 🌐 Architecture actuelle

## 🟥 SVL-PS-APP-01 — Debian 12

### Rôle

- serveur **Linux applicatif**
- hébergement **NGINX (intranet / web)**
- base de travail pour :
  - sécurisation Linux  
  - supervision future  
  - sauvegarde Veeam  
  - optimisation système  

👉 Cette VM constitue désormais **le cœur unique du laboratoire**.

---

# 💾 Sauvegarde & continuité

La stratégie de sauvegarde de la phase 2 repose sur :

- **Veeam Backup & Replication**
- sauvegarde **ciblée de la VM Debian**
- stockage des sauvegardes sur :
  - **NAS personnel local** (sauvegarde primaire)
  - logique inspirée du **3-2-1** à terme

Objectif :

> simuler une **stratégie de sauvegarde réelle** dans un contexte minimaliste.

---

# 🔐 Sécurité mise en place

## Hyperviseur ESXi

- mot de passe **root fort**
- **SSH désactivé** par défaut
- accès **limité au LAN**
- sauvegarde de la **configuration ESXi**
- isolation réseau via **vSwitch**

## Serveur Debian

- durcissement Linux progressif  
- configuration sécurisée **NGINX**  
- séparation des services  
- base pour supervision et journalisation  

---

# 📈 Objectifs pédagogiques

Cette phase permet de travailler concrètement :

- la **virtualisation bare-metal ESXi**
- l’**administration Linux serveur**
- l’**hébergement web sécurisé**
- la **sauvegarde professionnelle avec Veeam**
- la **continuité d’activité**
- la **documentation technique d’infrastructure**

👉 Approche volontairement **minimaliste mais réaliste**.

---

# 🧠 Compétences mises en œuvre

- VMware **ESXi**
- Linux **Debian**
- **NGINX**
- **Veeam Backup & Replication**
- réseau virtuel ESXi
- sécurité système
- diagnostic & troubleshooting
- documentation d’architecture

---

# 🗺️ Historique du projet

| Phase | Description | Statut |
|-------|-------------|--------|
| Phase 1 | Infrastructure PME complète sous VMware Workstation | ✅ Archivée |
| Phase 2 | Architecture ESXi minimaliste centrée Linux | 🚧 En cours |
| Phase 3 | Supervision, sauvegarde avancée, durcissement | 🔄 Prévue |

---

# 👤 Auteur

**Loïck**  
Projet personnel – Administration systèmes & réseaux  
Laboratoire orienté **conditions réelles de production**
