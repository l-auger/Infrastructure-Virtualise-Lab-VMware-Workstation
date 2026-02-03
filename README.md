# 🧪 Infrastructure Virtualisée – Lab VMware Workstation

## 📌 Présentation du projet

Ce projet correspond à un **laboratoire d’infrastructure virtualisée** réalisé dans un objectif de **formation, de test et de montée en compétences** autour des environnements systèmes et réseaux en entreprise.

L’infrastructure est entièrement virtualisée sous **VMware Workstation (dernière version)** et repose sur un **segment LAN dédié**, permettant à toutes les machines virtuelles de communiquer entre elles au sein d’un même réseau local, sans utiliser les VMnet par défaut.

Ce lab simule une **infrastructure d’entreprise classique**, incluant :
- Un Active Directory redondé
- Un DNS et DHCP en haute disponibilité
- Un pare-feu pfSense en passerelle
- Un poste client joint au domaine
- Des briques futures (serveur applicatif, sauvegarde)

---

## 🖥️ Environnement technique

- **Hyperviseur** : VMware Workstation (latest)
- **Réseau** :  
  - Segment LAN personnalisé  
  - Toutes les VM connectées au même LAN
  - Isolation complète de l’infrastructure

---

## 🌐 Architecture réseau

### 🔥 Pare-feu – pfSense (version 2.8.0)

pfSense est utilisé comme **passerelle principale**, assurant :
- Le routage
- Le NAT
- Le filtrage firewall
- L’accès Internet de l’ensemble du LAN

**Interfaces réseau :**
- **WAN** : `192.168.56.22/24`
- **LAN** : `192.168.11.1/24`

Tout le trafic sortant passe obligatoirement par pfSense, permettant un contrôle centralisé de la sécurité réseau.

---

## 🗄️ Machines virtuelles

### 🟦 Windows Server 2025 – Contrôleur de domaine (x2)

Deux serveurs Windows Server 2025 sont déployés afin d’assurer une **redondance des services critiques**.

**Rôles installés :**
- Active Directory Domain Services (AD DS)
- DNS
- DHCP (failover activé)

**Fonctionnement :**
- Les deux serveurs sont **synchronisés**
- Le DNS est redondé :
  - DNS principal sur le premier serveur
  - DNS secondaire sur le second serveur
- En cas de panne d’un contrôleur :
  - Le second prend automatiquement le relais
  - La continuité de service est assurée

Le second serveur DNS est configuré avec un **redirecteur externe (8.8.8.8)** afin d’éviter toute coupure de résolution en cas de défaillance interne.

---

### 🟩 Windows 11 – Poste client

Un poste Windows 11 est utilisé comme **client de test utilisateur**.

**Caractéristiques :**
- Joint **manuellement** au domaine Active Directory
- Adresse IP attribuée par DHCP
- Résolution DNS fonctionnelle
- Communication complète avec l’AD

**Tests réalisés :**
- Application et propagation de GPO
- Vérification du bon fonctionnement AD/DNS/DHCP

**Exemple de GPO testée :**
- Blocage de l’accès au panneau de configuration  
➡️ Objectif : valider le bon déploiement des stratégies de groupe dans le LAN.

---

### 🟥 Debian 12 – Serveur Linux (prévu)

Une machine Debian 12 est présente dans l’infrastructure mais **pas encore exploitée**.

**Objectifs futurs :**
- Déploiement d’un **serveur applicatif**
- Tests de déploiement d’applications
- Accès aux applications depuis le poste client Windows 11
- Étude du déploiement d’icônes et services côté utilisateur

Cette machine servira de **brique applicative** dans l’évolution du lab.

---

### 🟨 Veeam Backup – Serveur de sauvegarde (prévu)

Une machine dédiée à **Veeam Backup** est déployée mais **non encore configurée**.

**Objectifs futurs :**
- Mise en place de sauvegardes des VM
- Tests de stratégies de sauvegarde
- Étude de la restauration (restore) de machines

---

## 🔧 Configuration des ressources

Les machines virtuelles ont été configurées avec des **ressources volontairement confortables** afin de faciliter les tests et manipulations.

⚠️ Une phase d’optimisation est prévue :
- Réduction progressive des ressources
- Ajustement CPU / RAM / stockage
- Objectif : se rapprocher d’un environnement réaliste en production

---

## 🚀 Évolutions prévues

- Configuration complète de Veeam Backup
- Mise en production du serveur applicatif Debian
- Ajout de documentation détaillée par VM
- Ajout de captures d’écran (GPO, AD, DHCP, pfSense)
- Tests de sécurité réseau
- Amélioration des règles firewall
- Publication du projet sur LinkedIn

---

## 📎 Objectif pédagogique

Ce lab a pour but de :
- Comprendre les **fondamentaux d’une infrastructure d’entreprise**
- Travailler la **redondance et la haute disponibilité**
- Manipuler Active Directory, DNS, DHCP, GPO
- Approfondir la gestion réseau et firewall
- Documenter proprement une infrastructure technique

---

## 👤 Auteur

**Loïck**  
Projet personnel de laboratoire – Systèmes & Réseaux  
