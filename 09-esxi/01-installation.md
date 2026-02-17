# 🖥️ Installation de l’hyperviseur – VMware ESXi 8.x

## 🎯 Objectif

Mettre en place un **hyperviseur bare-metal** afin de :

- Se rapprocher d’une **architecture d’entreprise réelle**  
- Centraliser la **gestion des machines virtuelles**  
- Préparer l’**intégration future de Veeam**  
- Remplacer **VMware Workstation** comme couche de virtualisation  

---

## 🧠 Pourquoi migrer vers ESXi ?

L’environnement sous **VMware Workstation** présentait plusieurs limites :

- Dépendance au **système hôte Windows**  
- Absence de réelle séparation **hyperviseur / OS**  
- Pas d’**API VMware exploitable** pour des sauvegardes professionnelles  
- Réseau virtuel **simplifié**  
- Absence d’**administration centralisée** de type entreprise  

👉 **ESXi** permet une approche plus **professionnelle, isolée et réaliste**.

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

| Paramètre   | État     |
|------------|----------|
| SVM Mode   | Enabled  |
| IOMMU      | Enabled  |
| CSM        | Disabled |
| Secure Boot| Disabled |
| TPM        | Enabled (optionnel) |

### 🎯 Pourquoi ces réglages ?

- **SVM** → active la virtualisation matérielle AMD  
- **IOMMU** → permet une gestion avancée des périphériques  
- **CSM Disabled** → garantit un démarrage **UEFI natif**  
- **Secure Boot Disabled** → évite les conflits de signature de pilotes ESXi  

Ces paramètres assurent une **compatibilité complète avec ESXi 8.x**.

---

## 💿 2️⃣ Installation d’ESXi

### 📥 Préparation

- ISO **VMware ESXi 8.0.2** téléchargée depuis VMware  
- **Clé USB bootable** créée  
- Installation prévue sur un **SSD dédié**  

---

### 🛠 Étapes d’installation

1. Boot sur la **clé USB**  
2. Sélection du **disque SSD cible**  
3. Configuration du **clavier** (⚠️ QWERTY détecté)  
4. Définition du **mot de passe root**  
5. **Installation complète**  
6. **Redémarrage** de l’hôte  

---

### 🔐 Sécurité initiale

Un **mot de passe root fort** a été défini.

#### ⚠️ Incident rencontré

Le mot de passe a été saisi en **QWERTY** lors de l’installation,  
provoquant un **échec de connexion à l’interface Web** (poste client en AZERTY).

#### ✅ Résolution

- Vérification du **layout clavier**  
- Nouvelle saisie correcte du **mot de passe**  
- **Connexion Web validée**  

---

## 🌐 3️⃣ Configuration réseau initiale

Configuration réalisée via la **console DCUI (F2)**.

### Paramètres appliqués

- **Adresse IP statique** définie  
- **Masque réseau** configuré  
- **Passerelle par défaut** renseignée  
- **DNS temporaire** configuré  
- **Hostname :** `SVL-PS-HV-01`  

⚠️ À ce stade, le **réseau de management** reste **indépendant** des futures machines virtuelles.

---

### 🔎 Vérification d’accès

Depuis un poste client :

```
https://IP_ESXI
```

👉 **Connexion à la Web UI ESXi validée.**

---

## 🧪 4️⃣ Validation post-installation

### Vérifications effectuées

- Accès à l’**interface Web fonctionnel**  
- **Datastore local détecté**  
- **vSwitch0 créé automatiquement**  
- **Carte réseau reconnue**  
- **Version ESXi confirmée**  
- **Redémarrage test validé**  

---

## 🧠 Analyse technique

L’installation **bare-metal** apporte :

- Une **indépendance totale** vis-à-vis du système hôte  
- Un **accès direct au matériel**  
- Une **stabilité accrue**  
- Une **meilleure gestion des ressources**  
- Une **base saine** pour l’architecture virtuelle  

👉 L’hyperviseur est désormais **prêt pour la configuration avancée**.

---

## 📌 Étape suivante dans la documentation

Le document suivant :

```
02_configuration_initiale_esxi.md
```

Traite de :

- La **sécurisation du réseau de management**  
- La **sauvegarde de la configuration ESXi**  
- La **vérification des services**  
- La **préparation du réseau virtuel**  
- La création des **premiers vSwitch et Port Groups**  
