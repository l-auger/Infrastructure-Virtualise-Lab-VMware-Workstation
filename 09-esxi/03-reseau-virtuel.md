# 🌐 Configuration du réseau virtuel – VMware ESXi 8.x

## 🎯 Objectif

Mettre en place une architecture réseau virtuelle **simple, cohérente et exploitable** afin de :

- Segmenter correctement les flux  
- Isoler le réseau de **management ESXi**  
- Fournir un **LAN interne stable pour les VM applicatives**  
- Préparer l’évolution vers **Docker, Kubernetes et Ansible**  
- Se rapprocher d’une **architecture de production légère**  

---

## 🧠 Contexte

Lors de l’installation d’ESXi, un vSwitch par défaut est créé automatiquement :

- **vSwitch0**
- **Port Group par défaut :** VM Network  
- **Interface de management associée**

Cette configuration minimale est fonctionnelle, mais **manque de séparation logique**  
entre l’administration de l’hyperviseur et le réseau des machines virtuelles.

👉 Une organisation réseau plus propre est donc mise en place.

---

## 🏗 1️⃣ Architecture cible (phase 2)

Contrairement à la phase 1, l’architecture réseau est désormais **simplifiée**  
et centrée sur les services réellement exploités.

```
          Réseau physique / Box
                    |
             -----------------
             |               |
        Management ESXi     LAN VM
                               |
                         ----------------
                         |              |
                     Windows DNS/DHCP   Debian / K8s / Apps
```

Objectif :

- garder une **infrastructure lisible**
- éviter une complexité inutile
- rester **cohérent avec un lab personnel réaliste**

---

## ⚙️ 2️⃣ Configuration des vSwitch

### vSwitch0 — Management

**Utilisé pour :**

- Interface de **management ESXi**
- Accès **Web UI** et **SSH**

**Caractéristiques :**

- Connecté à la **carte réseau physique**
- **Uplink actif**
- Réseau **isolé de la partie applicative**

---

### vSwitch1 — LAN interne des VM

Création d’un **vSwitch dédié** pour les machines virtuelles.

**Rôle :**

- Héberger les **VM Windows réseau** et **VM Linux applicatives**
- Fournir un **réseau interne propre**
- Servir de base pour **Kubernetes / conteneurs**

**Caractéristiques :**

- Sans accès direct au management ESXi  
- Configuration simple **sans VLAN** (lab)  
- Évolutif vers **segmentation future** si nécessaire  

---

## 🧩 3️⃣ Port Groups définis

### 🔵 PG-Management

- Administration **ESXi uniquement**
- Accès restreint au **LAN personnel**
- Aucun service applicatif hébergé

---

### 🟢 PG-LAN-VM

Réseau principal des machines virtuelles.

**Héberge :**

- **Windows Server 2025** (DNS / DHCP)  
- **Debian 12** (Docker / Kubernetes / NGINX / apps)  
- Futures **VM de test ou de supervision**

---

## 🧠 Pourquoi cette architecture ?

### 🔐 Sécurité

- Isolation claire entre :
  - **management hyperviseur**
  - **réseau applicatif**
- Réduction de la **surface d’attaque**
- Meilleure maîtrise des flux réseau

---

### 🏢 Approche réaliste

Même en lab personnel :

- séparation **management / production**
- réseau interne dédié aux **services**
- base compatible avec :
  - **conteneurisation**
  - **orchestration Kubernetes**
  - **automatisation Ansible**

👉 Architecture **minimaliste mais crédible**.

---

## 🔎 4️⃣ Vérifications effectuées

- **vSwitch0 et vSwitch1 actifs**
- Uplink physique opérationnel
- Port Groups créés sans erreur
- Accès Web ESXi fonctionnel
- Communication réseau entre VM validée
- Attribution IP via **DHCP Windows** opérationnelle

---

## 🧪 5️⃣ Tests réseau réalisés

- Ping entre **VM Linux et Windows**
- Résolution **DNS interne fonctionnelle**
- Attribution **DHCP correcte**
- Accès Internet depuis les VM
- Accès ESXi stable depuis le LAN

---

## 🧠 Analyse technique

Cette configuration réseau permet :

- une **séparation propre des rôles**
- une base saine pour :
  - **Docker**
  - **Kubernetes**
  - **Ansible**
- une architecture cohérente avec une **production légère**
- une meilleure **lisibilité du laboratoire**

---

## 📌 Prochaine étape

Déploiement de l’infrastructure applicative :

- Installation **Windows Server DNS/DHCP**
- Déploiement **Debian 12**
- Mise en place de **Docker**
- Installation d’un **cluster Kubernetes (k3s)**
- Automatisation via **Ansible**
