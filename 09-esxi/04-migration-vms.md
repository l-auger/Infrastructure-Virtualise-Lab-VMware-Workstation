# 🔄 Migration des VM VMware Workstation → VMware ESXi 8.x

## 🎯 Objectif

Migrer l’infrastructure initialement déployée sous **VMware Workstation** vers **VMware ESXi 8.x** afin de :

- Centraliser la gestion des **machines virtuelles**  
- Supprimer la dépendance au **système hôte Windows**  
- Permettre l’intégration de **Veeam** via l’**API VMware**  
- Se rapprocher d’une infrastructure **entreprise** (*hyperviseur bare-metal*)  

---

## 🧠 Stratégie retenue

### ✅ Migration des VM existantes (Workstation → ESXi)

L’objectif est de **conserver les VM, leurs données et leur configuration** en les déplaçant vers ESXi.

### Méthode utilisée

- Export des VM depuis **VMware Workstation** au format **OVF / OVA**  
- Import dans **ESXi** via l’**interface Web**  

Cette approche permet une migration **fiable**, tout en limitant la **reconfiguration manuelle**.

---

## ⚠️ Pré-requis et précautions

Avant toute migration :

### 1) État des VM
- Les VM doivent être **éteintes** (*Shutdown*), jamais suspendues.  
- **Aucun snapshot actif** côté Workstation.  

### 2) Sauvegarde de sécurité (obligatoire)

Sauvegarder les dossiers Workstation des VM avant export (**copie brute**).

**Exemple (Windows) :**
```
D:\BACKUP_VM_WORKSTATION\
```

🎯 Objectif : pouvoir **revenir en arrière** en cas d’échec ou de corruption.

### 3) Réseau ESXi prêt

Sur ESXi, vérifier ou créer les **Port Groups** suivants :

- `PG-WAN`  
- `PG-LAN`  

### 4) Stockage temporaire des sauvegardes

Pendant la phase de migration, les **sauvegardes seront stockées localement** sur un :

**🟨 NAS personnel situé à domicile**

Rôle de ce NAS durant la migration :

- Servir de **cible de sauvegarde locale**  
- Conserver une **copie de sécurité** des VM migrées  
- Assurer une **protection transitoire des données** avant la mise en place d’une stratégie de sauvegarde définitive  

👉 Cette solution est **temporaire**, le temps de finaliser l’infrastructure ESXi et l’intégration complète de **Veeam**.

---

## 📋 Ordre de migration recommandé

L’ordre de migration est **critique** pour éviter les incohérences réseau ou domaine :

1️⃣ **pfSense**  
2️⃣ **DC1** — contrôleur de domaine principal  
3️⃣ **DC2** — contrôleur secondaire  
4️⃣ **Serveur Debian** (NGINX / intranet)  
5️⃣ **Client Windows 11**  
6️⃣ **Serveur Veeam**  

---

## ⚙️ Procédure de migration (par VM)

### A) Export depuis VMware Workstation

Dans **VMware Workstation** :

1. Clic droit sur la VM  
2. **Manage**  
3. **Export to OVF** (ou **OVA** selon les options disponibles)

📦 **Fichiers générés :**

- `.ovf` + `.vmdk` (+ parfois `.mf`)  
ou  
- `.ova` (*archive unique*)  

---

### B) Import dans ESXi

Dans l’**ESXi Web UI** :

1. **Virtual Machines**  
2. **Create / Register VM**  
3. **Deploy a virtual machine from an OVF or OVA file**  
4. Upload du fichier `.ova` **ou** des fichiers `.ovf` + `.vmdk`  
5. Choix du **datastore**  
6. **Network mapping** vers le bon **Port Group**  

#### 🌐 Mapping réseau recommandé

- **pfSense WAN** → `PG-WAN`  
- **pfSense LAN** → `PG-LAN`  
- **DC / Debian / Client / Veeam** → `PG-LAN`  

---

### C) Vérifications avant démarrage

Avant le premier boot :

- Vérifier les ressources **CPU / RAM**  
- Vérifier le **type de carte réseau** (E1000E ou VMXNET3)  
- Vérifier le **Port Group sélectionné**  

---

### D) Premier démarrage et tests rapides

Après démarrage :

- Vérifier l’**adresse IP**  
- Tester la **connectivité réseau**  
- Vérifier les **services critiques**  

---

## ✅ Tests de validation après migration

### 🔥 pfSense
- Interfaces **WAN / LAN** correctement détectées  
- IP LAN conforme (ex. `192.168.11.1`)  
- **NAT fonctionnel**  
- Règle **LAN → Internet** opérationnelle  
- Test : **ping Internet**  

### 🏢 DC1 / DC2
- IP **statique correcte**  
- **DNS configuré**  
- Services **Active Directory démarrés**  
- Ping **LAN OK**  
- **Réplication AD fonctionnelle**  

### 🐧 Debian (NGINX)
- IP correcte  
- **DNS interne fonctionnel**  
- **NGINX actif**  
- Accès intranet depuis le **client**  

### 🟩 Client Windows
- IP obtenue via **DHCP**  
- **Connexion au domaine** validée  
- **GPO appliquées**  
- Accès intranet **fonctionnel**  

---

## 🧯 Incidents fréquents et causes probables

### pfSense : WAN / LAN inversés
**Cause :** changement de **NIC / MAC** lors de l’import.  
➡️ **Solution :** réassocier les interfaces dans **pfSense**.

### Active Directory : erreurs liées au temps
**Cause :** décalage horaire (**NTP**).  
➡️ **Solution :** activer **NTP sur ESXi** et vérifier l’heure des **contrôleurs de domaine**.

### Windows : carte réseau non reconnue
**Cause :** type de **NIC différent**.  
➡️ **Solution :** changer le type de NIC (**E1000E / VMXNET3**) et réinstaller **VMware Tools**.

---

## 🧾 Journal de migration (à compléter)

| VM          | Export | Import ESXi | Port Group        | Résultat | Notes |
|-------------|--------|-------------|-------------------|----------|-------|
| pfSense     |        |             | PG-WAN / PG-LAN   |          |       |
| DC1         |        |             | PG-LAN            |          |       |
| DC2         |        |             | PG-LAN            |          |       |
| Debian APP  |        |             | PG-LAN            |          |       |
| Client W11  |        |             | PG-LAN            |          |       |
| Veeam       |        |             | PG-LAN            |          |       |

---

## 📌 Prochaine étape

Une fois la migration terminée :

### ✅ Intégration de Veeam

- Ajout de l’hôte **ESXi** dans **Veeam**  
- Création d’un **job de sauvegarde**  
- **Test de restauration**  
- **Simulation de PRA**  

➡️ Document associé : `05-integration-veeam.md`
