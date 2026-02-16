# 🔄 Migration des machines virtuelles vers ESXi

## 🎯 Objectif

Migrer l’infrastructure initialement déployée sous **VMware Workstation** vers l’hyperviseur **ESXi 8.x** afin de :

- Centraliser la gestion des machines virtuelles  
- Supprimer la dépendance au système hôte Windows  
- Permettre l’intégration de **Veeam**  
- Se rapprocher d’une architecture d’entreprise réaliste  

---

## 🧠 Stratégie de migration

Deux approches étaient possibles :

### ❌ Export OVA depuis Workstation

**Avantages :**

- Rapide  
- Peu de configuration  

**Inconvénients :**

- Risque d’erreurs réseau  
- Problèmes de pilotes  
- Configuration héritée non optimisée  
- Mauvaise pratique pédagogique  

---

### ✅ Recréation propre des VM

**Approche retenue.**

**Avantages :**

- Configuration optimisée pour ESXi  
- Contrôle total du matériel virtuel  
- Meilleure compréhension technique  
- Nettoyage des anciennes configurations  

👉 **Choix pédagogique et professionnel : recréation complète.**

---

## 📋 Ordre de migration

L’ordre de migration est essentiel pour éviter les incohérences réseau ou domaine.

### 1️⃣ pfSense

**Pourquoi en premier ?**

- Passerelle principale du LAN  
- Gestion du **NAT** et de l’accès Internet  
- Conditionne la connectivité des autres VM  

---

### 2️⃣ DC1 — Contrôleur de domaine principal

- **Active Directory**  
- **DNS primaire**  
- **DHCP** (si configuré)  

Sans lui :

- Le domaine ne fonctionne pas  

---

### 3️⃣ DC2 — Contrôleur secondaire

- Réplication **Active Directory**  
- **DNS secondaire**  
- Haute disponibilité  

---

### 4️⃣ Serveur applicatif Debian (NGINX)

- Hébergement de l’**intranet**  
- Dépendance au **DNS interne**  

---

### 5️⃣ Poste client Windows 11

Validation finale :

- Test des **GPO**  
- Accès intranet  
- Résolution DNS  

---

## ⚙️ Méthodologie technique

Pour chaque VM :

1. Création d’une **nouvelle VM** sur ESXi  
2. Allocation **CPU / RAM** adaptée  
3. Sélection du **bon Port Group**  
4. Installation propre du système d’exploitation  
5. Reconfiguration **IP**  
6. Réintégration au **domaine** si nécessaire  
7. **Tests de validation**  

---

## 🌐 Configuration réseau des VM

Attribution des interfaces réseau :

- **pfSense WAN** → Port Group `WAN`  
- **pfSense LAN** → Port Group `LAN`  
- **DC / APP / Client** → Port Group `LAN`  

---

## 🔎 Vérifications après migration

Pour chaque machine :

- Ping vers la **passerelle**  
- Ping vers le **contrôleur de domaine**  
- **Résolution DNS** fonctionnelle  
- **Accès Internet** validé  
- **Accès intranet** opérationnel  
- **GPO appliquées**  
- **Réplication AD** fonctionnelle  

---

## 🧪 Tests globaux

### Checklist complète

- **Active Directory** opérationnel  
- **DNS primaire et secondaire** fonctionnels  
- **DHCP** attribue correctement les adresses IP  
- **pfSense** filtre correctement le trafic  
- **Intranet** accessible  
- Aucun **conflit IP**  
- Aucune **VM isolée**  

---

## 🧠 Analyse technique

La migration vers **ESXi** permet :

- Une **gestion centralisée** des VM  
- Un **meilleur contrôle des ressources**  
- Une **isolation claire des flux réseau**  
- Une **compatibilité native avec Veeam**  
- Une **simulation fidèle d’un environnement d’entreprise**  

---

## 📌 Prochaine étape

### Intégration de Veeam

- Ajout de l’hôte **ESXi** dans Veeam  
- Création d’un **job de sauvegarde**  
- Test de **snapshot**  
- Test de **restauration**  
- Simulation de **PRA (Plan de Reprise d’Activité)**  
