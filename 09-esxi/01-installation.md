# 🖥️ Installation de l’hyperviseur – VMware ESXi 8.x

## 🎯 Objectif

Mettre en place un hyperviseur **bare-metal** afin de :

- Se rapprocher d’une architecture d’entreprise réelle  
- Permettre l’intégration de **Veeam**  
- Centraliser la gestion des machines virtuelles  
- Remplacer **VMware Workstation** comme couche de virtualisation  

---

## 🧠 Pourquoi migrer vers ESXi ?

L’environnement sous **VMware Workstation** présentait plusieurs limites :

- Dépendance au système hôte Windows  
- Absence de vraie séparation hyperviseur / OS  
- Pas d’API VMware exploitable pour **Veeam**  
- Réseau virtuel simplifié  
- Pas d’administration centralisée de type entreprise  

👉 **ESXi permet une approche plus professionnelle et réaliste.**

---

## ⚙️ 1️⃣ Préparation matérielle

### 🖥 Machine hôte

- **CPU :** AMD Ryzen 7 7800X3D  
- **RAM :** 64 Go  
- **Stockage :** SSD dédié à ESXi  
- **Carte mère :** B650 PRO RS  
- **Mode BIOS :** UEFI  

---

### 🔧 Configuration BIOS

**Paramètres activés :**

| Paramètre     | État     |
|---------------|----------|
| SVM Mode      | Enabled  |
| IOMMU         | Enabled  |
| CSM           | Disabled |
| Secure Boot   | Disabled |
| TPM           | Enabled (optionnel) |

### 🎯 Pourquoi ces réglages ?

- **SVM** → Active la virtualisation matérielle AMD  
- **IOMMU** → Gestion avancée des périphériques  
- **CSM Disabled** → Démarrage UEFI propre  
- **Secure Boot Disabled** → Évite les conflits de pilotes ESXi  

---

## 💿 2️⃣ Installation d’ESXi

### 📥 Préparation

- ISO **VMware ESXi 8.0.2** téléchargée depuis VMware  
- Clé USB bootable créée  
- Installation prévue sur un **SSD dédié**  

---

### 🛠 Étapes réalisées

1. Boot sur la clé USB  
2. Sélection du disque SSD cible  
3. Configuration du clavier (**⚠️ QWERTY détecté**)  
4. Définition du mot de passe **root**  
5. Installation complète  
6. Redémarrage de l’hôte  

---

### 🔐 Sécurité initiale

Un **mot de passe root fort** a été défini.

**⚠️ Incident rencontré :**

Le mot de passe a été saisi en **QWERTY** lors de l’installation,  
provoquant un échec de connexion sur l’interface Web (**AZERTY côté client**).

**Résolution :**

- Vérification du layout clavier  
- Nouvelle saisie correcte du mot de passe  
- Connexion Web validée  

---

## 🌐 3️⃣ Configuration réseau initiale

Accès via la console **DCUI (F2)**.

### Configuration appliquée

- Adresse **IP statique** définie  
- **Masque réseau** configuré  
- **Passerelle par défaut** renseignée  
- **DNS** configuré  
- **Hostname :** `SVL-PS-HV-01`  

---

### 🔎 Vérification d’accès

Depuis un poste client :

```
https://IP_ESXI
```

👉 Connexion à la **Web UI ESXi réussie**.

---

## 🧪 4️⃣ Validation post-installation

### Vérifications effectuées

- Accès à l’interface Web **OK**  
- **Datastore** détecté  
- **vSwitch0** créé automatiquement  
- Carte réseau reconnue  
- Version **ESXi confirmée**  

---

## 🧠 Analyse technique

L’installation **bare-metal** permet :

- Indépendance totale du système hôte  
- Accès direct au matériel  
- Meilleure gestion des ressources  
- Exploitation des **API VMware**  
- Intégration future avec **Veeam**  

---

## 📌 Prochaine étape

Configuration de l’infrastructure virtuelle :

- Réseau virtuel  
- Port Groups  
- Plan d’adressage IP  
- Migration des VM depuis **VMware Workstation**  
