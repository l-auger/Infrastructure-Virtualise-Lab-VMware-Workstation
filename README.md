# 🚀 Évolution du laboratoire – Architecture hybride Windows / Linux

## 🎯 Objectif de cette nouvelle phase

Après la mise en place d’une **infrastructure ESXi minimaliste**,  
le projet évolue vers un laboratoire orienté :

- **déploiement applicatif réel**
- **automatisation**
- **conteneurisation**
- **orchestration moderne**

L’objectif est de manipuler des **technologies concrètement utilisées en entreprise**,  
tout en conservant une architecture **simple, lisible et pédagogique**.

---

# 🧱 Architecture cible

L’infrastructure reposera sur **plusieurs machines virtuelles hébergées sous ESXi** :

## 🪟 Windows Server 2025 – Services d’infrastructure

Une VM Windows sera conservée pour assurer les **services réseau essentiels** :

- **DHCP**
- **DNS**

Rôle :

- fournir la résolution de noms interne  
- distribuer automatiquement les adresses IP  
- simuler un **socle d’infrastructure entreprise minimal**

👉 Aucun Active Directory complet n’est prévu,  
afin de limiter la complexité et rester centré sur l’applicatif.

---

## 🐧 Machines Linux – Couche applicative

Le reste de l’infrastructure sera basé sur **Debian 12** :

### Rôles prévus

- **serveur applicatif principal**
- **nœud(s) Kubernetes**
- **hébergement conteneurisé**
- **tests de résilience et redéploiement**

Cette approche permet de se rapprocher d’un environnement :

> **Linux-first / cloud-native**, courant en production.

---

# 🧰 Technologies déployées

## 🐳 Docker
- conteneurisation des applications  
- isolation des services  
- déploiement rapide et reproductible  

## ☸️ Kubernetes (k3s)
- orchestration des conteneurs  
- redémarrage automatique  
- montée en charge  
- exposition via Ingress  

## 🤖 Ansible
- installation automatisée des VM  
- configuration système reproductible  
- déploiement applicatif sans action manuelle  
- logique **Infrastructure as Code**  

---

# 🌐 Cas d’usage applicatif

Le laboratoire visera à déployer :

- une **application web** (API ou site interne)
- un **reverse proxy NGINX**
- une **base de données conteneurisée**
- éventuellement :
  - supervision
  - stockage persistant
  - tests de reprise

Objectif :

> manipuler un **cycle applicatif complet**  
> déploiement → panne → redéploiement → sauvegarde.

---

# 💾 Sauvegarde

La stratégie reposera sur :

- **Veeam Backup & Replication**
- sauvegarde des **VM critiques**
- stockage sur :
  - **NAS personnel local**
  - évolution possible vers logique **3-2-1**

---

# 📈 Bénéfices pédagogiques

Cette phase permet de :

- combiner **infrastructure Windows minimale** et **écosystème Linux moderne**
- comprendre les bases du **DevOps** et du **cloud-native**
- manipuler **Docker, Kubernetes et Ansible** en conditions réelles
- produire une **documentation technique crédible pour un portfolio**

---

# 🗺️ Position dans le projet global

| Phase | Orientation | Statut |
|-------|-------------|--------|
| Phase 1 | Infrastructure PME complète sous Workstation | ✅ Terminée |
| Phase 2 | ESXi minimaliste + Debian | 🚧 En cours |
| Phase 3 | Architecture hybride + conteneurs + automatisation | 🔜 Démarrage |

Cette évolution constitue la **suite logique du laboratoire**  
vers une infrastructure **moderne, automatisée et proche de la production**.
