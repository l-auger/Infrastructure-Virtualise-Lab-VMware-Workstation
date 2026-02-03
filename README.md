# 🧪 Infrastructure Virtualisée – Lab VMware Workstation

## 📌 Présentation du projet

Ce projet correspond à un **laboratoire d’infrastructure virtualisée** réalisé dans un objectif de **formation, de test et de montée en compétences** autour des environnements systèmes et réseaux en entreprise.

L’infrastructure est déployée sur **VMware Workstation (dernière version)** et repose sur un **segment LAN dédié**, permettant à l’ensemble des machines virtuelles de communiquer entre elles au sein d’un même réseau local, sans utiliser les VMnet par défaut.

Ce lab simule une **infrastructure d’entreprise classique**, incluant :
- Un Active Directory redondé
- Un DNS et DHCP en haute disponibilité
- Un pare-feu pfSense en passerelle
- Un poste client joint au domaine
- Des briques futures (serveur applicatif, sauvegarde)

---

## 🖥️ Environnement technique

- **Plateforme de virtualisation** : VMware Workstation
- **Type d’environnement** : Lab / environnement de test
- **Réseau** :
  - Segment LAN personnalisé
  - Toutes les VM connectées au même LAN
  - Accès Internet exclusivement via le pare-feu

---

## 🌐 Architecture réseau

### 🔥 Pare-feu – `SVL-PS-FWL-01`

- **OS** : pfSense
- **Version** : 2.8.0
- **Rôle** :
  - Passerelle réseau du LAN
  - NAT
  - Filtrage firewall
  - Point de sortie Internet unique

**Interfaces réseau :**
- **WAN** : `192.168.56.22/24`
- **LAN** : `192.168.11.1/24`

L’ensemble du trafic sortant du LAN transite obligatoirement par ce pare-feu, permettant un **contrôle centralisé de la sécurité réseau**.

---
![Aperçu du projet](architecture/schema-reseau.png)
---

## 🗄️ Machines virtuelles

### 🟦 `SVL-PS-DC1-01` – Windows Server 2025 (Contrôleur de domaine)

- **OS** : Windows Server 2025
- **Rôles installés** :
  - Active Directory Domain Services (AD DS)
  - DNS (primaire)
  - DHCP (failover)

Ce serveur assure le rôle de **contrôleur de domaine principal** et héberge les services critiques du domaine.

---

### 🟦 `SVL-PS-DC2-01` – Windows Server 2025 (Contrôleur de domaine secondaire)

- **OS** : Windows Server 2025
- **Rôles installés** :
  - AD DS (réplication)
  - DNS (secondaire)
  - DHCP (failover)

**Fonctionnement :**
- Synchronisation complète avec `SVL-PS-DC1-01`
- Redondance DNS et DHCP assurée
- Continuité de service en cas de panne du DC principal

Le serveur DNS secondaire est configuré avec un **redirecteur externe (8.8.8.8)** afin de garantir la résolution de noms même en cas de défaillance interne.

---

### 🟩 `CL-TS-01` – Poste client Windows 11

- **OS** : Windows 11
- **Rôle** : Poste client de test utilisateur

**Fonctionnalités validées :**
- Jonction **manuelle** au domaine Active Directory
- Attribution IP via DHCP
- Résolution DNS fonctionnelle
- Communication complète avec les contrôleurs de domaine

**Tests réalisés :**
- Déploiement et application de GPO
- Exemple de GPO testée :
  - Blocage de l’accès au panneau de configuration  
  ➜ Objectif : valider la propagation correcte des stratégies de groupe dans le LAN.

---

### 🟥 `SVL-PS-APP-01` – Debian 12 (Serveur applicatif – prévu)

- **OS** : Debian 12
- **État actuel** : VM installée mais non encore exploitée

**Objectifs futurs :**
- Déploiement d’un serveur applicatif
- Tests de déploiement d’applications
- Accès aux applications depuis le poste client `CL-TS-01`
- Étude du déploiement d’icônes et services côté utilisateur

Cette machine constituera la **brique applicative** du lab.

---

### 🟨 `SVL-PS-VEEAM-01` – Serveur de sauvegarde (prévu)

- **Solution** : Veeam Backup
- **État actuel** : VM déployée mais non configurée

**Objectifs futurs :**
- Mise en place de sauvegardes des machines virtuelles
- Tests de stratégies de sauvegarde
- Tests de restauration (VM complète / fichiers)

---

## 🔧 Configuration des ressources

Les machines virtuelles ont été configurées avec des **ressources volontairement confortables** afin de faciliter les phases de test et de manipulation.

⚠️ Une phase d’optimisation est prévue :
- Réduction progressive des ressources CPU / RAM
- Ajustement du stockage
- Objectif : se rapprocher d’un environnement réaliste en conditions de production

---

## 🚀 Évolutions prévues

- Configuration complète de `SVL-PS-VEEAM-01`
- Mise en production du serveur applicatif `SVL-PS-APP-01`
- Ajout de documentation détaillée par machine virtuelle
- Ajout de captures d’écran (AD, DNS, DHCP, GPO, pfSense)
- Tests de sécurité réseau
- Renforcement des règles firewall
- Publication du projet sur LinkedIn

---

## 📎 Objectif pédagogique

Ce lab a pour objectif de :
- Comprendre les **fondamentaux d’une infrastructure d’entreprise**
- Mettre en œuvre la **redondance et la haute disponibilité**
- Manipuler Active Directory, DNS, DHCP et GPO
- Approfondir la gestion réseau et la sécurité
- Apprendre à **documenter proprement une infrastructure technique**

---

## 👤 Auteur

**Loïck**  
Projet personnel de laboratoire – Systèmes & Réseaux
