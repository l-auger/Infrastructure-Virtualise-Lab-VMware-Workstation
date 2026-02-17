# 🧪 Infrastructure virtualisée – Lab systèmes & réseaux

## 📌 Présentation

Ce dépôt documente un **laboratoire d’infrastructure virtualisée** réalisé dans un objectif de :

- montée en compétences en **administration systèmes et réseaux**
- reproduction d’**architectures d’entreprise réalistes**
- expérimentation autour de la **virtualisation, Linux et sauvegarde**

Le projet est organisé en **plusieurs phases évolutives** correspondant à l’évolution réelle du lab.

---

# 🔀 Organisation du projet par branches

## 🌿 Branche principale – Infrastructure VMware Workstation (Phase 1)

La branche actuelle correspond à la **première version complète du laboratoire**, basée sur :

- **VMware Workstation**
- une **architecture PME complète** :
  - Active Directory redondé (DC1 / DC2)
  - DNS / DHCP
  - pare-feu **pfSense**
  - client Windows joint au domaine
  - serveur applicatif **Debian + NGINX**
  - serveur de sauvegarde **Veeam**

👉 Cette phase est **terminée** et conservée à des fins :

- pédagogiques  
- historiques  
- documentaires  

Elle représente la **fondation du projet**, mais **n’est plus l’architecture cible actuelle**.

---

## 🌿 Branche 2 – Architecture ESXi minimaliste (Phase 2)

La suite du projet se poursuit sur une **nouvelle branche dédiée**.

➡️ **Merci de basculer sur la branche :**

```
phase-2-esxi
```

Cette branche contient :

- la **migration vers VMware ESXi 8.x bare-metal**
- la **simplification volontaire de l’infrastructure**
- la conservation d’un **seul serveur Debian 12 applicatif**
- la mise en place d’une **stratégie de sauvegarde réaliste**
- une approche **plus proche d’un environnement de production réel**

### 🎯 Objectif de la phase 2

Passer :

- d’un **lab pédagogique complet**
- à une **architecture minimaliste, crédible et exploitable**

centrée sur :

- **VMware ESXi**
- **Linux serveur**
- **NGINX**
- **sauvegarde Veeam**
- **NAS local**
- **sécurité et exploitation système**

---

# 🧭 État global du projet

| Phase | Description | Statut |
|-------|-------------|--------|
| Phase 1 | Infrastructure complète sous VMware Workstation | ✅ Terminée |
| Phase 2 | Migration ESXi + Debian unique | 🚧 En cours |
| Phase 3 | Sauvegarde avancée & optimisation | 🔄 À venir |

---

# 📚 Structure documentaire

Le dépôt est organisé en dossiers numérotés correspondant aux briques techniques :

- `00-architecture` → vue d’ensemble  
- `01-virtualisation-vmware-workstation` → hyperviseur Workstation  
- `02-pfsense` → pare-feu  
- `03-windows-server-2025` → Active Directory  
- `04-windows-11-client` → poste client  
- `05-debian-12` → serveur Linux applicatif  
- `06-veeam-backup` → sauvegarde  
- `07-securite` → durcissement  
- `08-evolutions` → perspectives  
- `09-esxi` → **début de la transition vers la phase 2**

👉 La **suite réelle du projet** se trouve désormais sur la **branche phase-2-esxi**.

---

# 👤 Auteur

**Loïck**  
Projet personnel – Administration systèmes & réseaux  
Laboratoire d’apprentissage orienté **conditions réelles de production**

---

**La phase 1 reste disponible pour consultation,  
mais le développement actif continue en phase 2.**
