# 🌐 Configuration du réseau virtuel – VMware ESXi 8.x

## 🎯 Objectif

Mettre en place une architecture réseau virtuelle cohérente et structurée afin de :

- Segmenter correctement les flux  
- Isoler les environnements (LAN / WAN / Management)  
- Préparer l’intégration de pfSense  
- Se rapprocher d’une architecture d’entreprise  

---

## 🧠 Contexte

Lors de l’installation d’ESXi, un vSwitch par défaut est créé automatiquement :

- **vSwitch0**
- **Port Group par défaut :** VM Network  
- **Interface de management associée**

Ce réseau unique est fonctionnel, mais **non structuré pour une architecture multi-segments**.

👉 Une organisation propre est donc nécessaire.

---

## 🏗 1️⃣ Architecture cible

L’objectif est de séparer :

```
                INTERNET
                    |
                 [ WAN ]
                    |
               pfSense (VM)
                    |
                 [ LAN ]
                    |
      ---------------------------------
      |        |        |        |
     DC1      DC2      APP     CLIENT
```

---

## ⚙️ 2️⃣ Configuration du vSwitch

### vSwitch0

**Utilisé pour :**

- Interface de management ESXi  
- Port Group LAN interne  

**Caractéristiques :**

- Connecté à la carte réseau physique  
- Uplink actif  
- Pas de VLAN (lab simple)  

---

## 🧩 3️⃣ Création des Port Groups

Deux Port Groups principaux ont été définis :

### 🔵 Management Network (par défaut)

Utilisé pour :

- Administration ESXi  
- Accès Web UI  
- Accès SSH (si activé)  

---

### 🟢 LAN

Réseau interne des machines virtuelles.

**Héberge :**

- DC1  
- DC2  
- APP  
- CLIENT  

Connecté à l’interface **LAN de pfSense**.

---

### 🔴 WAN

Port Group dédié à l’interface **WAN de pfSense**.

- Connecté à la carte réseau physique vers l’extérieur  

---

## 🧠 Pourquoi cette séparation ?

### 🔐 Sécurité

- Séparation claire des flux  
- pfSense devient le **point de contrôle unique**  
- Isolation logique entre hyperviseur et réseau interne  

### 🏢 Approche entreprise

En production :

- Management réseau isolé  
- VLAN dédiés  
- Segmentation forte  

---

## 🔎 4️⃣ Vérifications effectuées

- vSwitch0 visible et actif  
- Uplink physique opérationnel  
- Port Groups créés sans erreur  
- Management accessible  
- Aucune perte d’accès après configuration  

---

## 🧪 5️⃣ Tests réseau

**Tests réalisés :**

- Ping ESXi depuis le LAN  
- Ping entre VM sur le même Port Group  
- Vérification de la connectivité WAN de pfSense  
- Accès Web UI stable  

---

## 🧠 Analyse technique

La configuration réseau virtuelle permet :

- Un **contrôle centralisé des flux**  
- La **simulation d’une topologie d’entreprise**  
- La **préparation à l’intégration Veeam**  
- Une **meilleure lisibilité de l’architecture**  

---

## 📌 Prochaine étape

Migration des machines virtuelles :

- Export OVA ou recréation propre  
- Import dans ESXi  
- Attribution aux bons Port Groups  
- Validation AD / DNS / DHCP  
- Test complet des flux réseau  
