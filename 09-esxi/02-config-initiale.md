# ⚙️ Configuration initiale – VMware ESXi 8.x

## 🎯 Objectif

Sécuriser et préparer l’hyperviseur après installation afin de :

- Réduire la surface d’attaque  
- Stabiliser l’environnement  
- Préparer la production des VM  
- Garantir une gestion propre et maintenable  

---

## 🔐 1️⃣ Sécurisation de l’accès root

### Configuration réalisée

- Mot de passe **root fort**  
- Accès Web uniquement via **HTTPS**  
- Accès limité au **LAN**  
- **Aucune exposition WAN**  

### 🔎 Vérifications

- Connexion Web fonctionnelle  
- Aucune tentative d’accès externe détectée  
- Adresse IP ESXi **non exposée sur le WAN**  

---

## 🛠 2️⃣ Désactivation des services inutiles

Par défaut, certains services peuvent être actifs.

### Service SSH

- Activé **temporairement** si nécessaire  
- Désactivé après configuration  

👉 En production, **SSH ne doit pas rester actif**.

### Shell ESXi

- Utilisé uniquement pour le **diagnostic**  
- Désactivé hors période de maintenance  

---

## ⏱ 3️⃣ Configuration NTP (synchronisation horaire)

### Pourquoi ?

- **Active Directory** dépend fortement de l’heure  
- Les certificats **HTTPS** utilisent le temps système  
- Les **logs** doivent être cohérents  

### Action réalisée

- Configuration d’un **serveur NTP**  
- Synchronisation automatique activée  
- Vérification de l’**heure système**  

---

## 🗂 4️⃣ Vérification du Datastore

### Points validés

- Datastore local détecté  
- **Espace disque suffisant**  
- Aucun problème **SMART**  
- Support **SSD reconnu correctement**  

---

## 🌐 5️⃣ Vérification du réseau Management

### Vérifications effectuées

- **IP statique** fonctionnelle  
- **Passerelle** correcte  
- **DNS** opérationnel  
- Ping vers la **passerelle OK**  
- Ping vers le **DNS OK**  

---

## 👤 6️⃣ Gestion des accès 

### Bonne pratique en entreprise

- Ne pas utiliser **root** pour toutes les opérations  
- Créer un **utilisateur administrateur dédié**  
- Attribuer un **rôle adapté**  

Même si l’utilisation de root est acceptable en **lab**,  
la logique **entreprise** est documentée.

---

## 💾 7️⃣ Sauvegarde de la configuration ESXi

### Bonne pratique

- Sauvegarde de la **configuration de l’hyperviseur**  
- Conservation **hors hyperviseur**  

### Pourquoi ?

En cas de panne :

- Réinstallation rapide  
- Restauration immédiate de la configuration  
- **Gain de temps critique**  

---

## 🧪 8️⃣ Vérification des ressources matérielles

- **CPU reconnu correctement**  
- Nombre de **cœurs validé**  
- **RAM totale détectée**  
- **Carte réseau identifiée**  
- Aucune erreur **hardware**  

---

## 🔎 9️⃣ Vérification des logs système

### Objectif

- S’assurer qu’aucune **erreur critique** n’est présente  
- Vérifier l’absence de **warning matériel**  

---

## 🧠 Analyse technique

Cette phase permet :

- De **sécuriser l’hyperviseur**  
- D’éviter les **erreurs futures**  
- De garantir la **stabilité des VM**  
- D’adopter des **pratiques professionnelles**  

---

## 📌 Prochaine étape

- Configuration du **réseau virtuel**  
- Création des **Port Groups**  
- Déploiement de **pfSense**  
- Début de la **migration des VM**  
