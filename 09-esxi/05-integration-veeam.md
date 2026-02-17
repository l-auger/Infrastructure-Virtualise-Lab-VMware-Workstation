# 💾 Intégration Veeam Backup & Replication avec ESXi

## 🎯 Objectif

Intégrer l’hyperviseur **VMware ESXi 8.x** à **Veeam Backup & Replication** afin de :

- Mettre en place une **stratégie de sauvegarde réelle**  
- Tester les mécanismes de **restauration**  
- Simuler un **PRA (Plan de Reprise d’Activité)**  
- Se rapprocher d’un **environnement de production minimaliste**  

Dans la **phase 2 du projet**, la sauvegarde ne concerne plus une infrastructure complète,  
mais une **architecture simplifiée centrée sur les services réellement exploités**.

---

## 🧠 Pourquoi Veeam ?

### Limites sous VMware Workstation

- Absence d’**API VMware exploitable**  
- Sauvegardes **manuelles uniquement**  
- Pas de **snapshot cohérent à chaud**  

### Apports avec ESXi

- **API VMware native** compatible Veeam  
- **Snapshots à chaud** sans interruption de service  
- Sauvegarde **complète des VM**  
- **Restauration granulaire** (fichiers ou VM entière)  
- Possibilité de **tests automatisés de reprise**  

👉 Veeam devient ainsi la **brique centrale de continuité d’activité** du laboratoire.

---

## 🖥️ 1️⃣ Préparation de Veeam

### Machine virtuelle dédiée

- **Nom :** `SVL-PS-VEEAM-01`  
- **OS :** Windows Server  
- **Rôle :** serveur de sauvegarde  

### Ressources recommandées

- **4 vCPU**  
- **8 à 16 Go de RAM**  
- **Stockage dédié** aux fichiers de sauvegarde  

---

## 🔗 2️⃣ Ajout de l’hyperviseur ESXi dans Veeam

### Chemin de configuration

```
Inventory → Add Server → VMware vSphere → VMware ESXi
```

### Informations nécessaires

- **Adresse IP** de l’hyperviseur  
- **Compte administrateur ESXi** (compte dédié recommandé)  
- **Mot de passe** associé  

### Validation

La connexion est valide lorsque :

- l’hôte **ESXi apparaît dans l’inventaire Veeam**  
- les **machines virtuelles sont détectées**  

---

## 🧾 3️⃣ Création d’un job de sauvegarde

### Cible de sauvegarde (phase 2)

Contrairement à la phase 1, la sauvegarde porte désormais sur :

- **SVL-PS-APP-01** — serveur Debian 12 applicatif  
- (éventuellement) futures **VM Linux / Kubernetes**  

👉 L’objectif est une **sauvegarde ciblée mais réaliste**.

### Étapes

```
Backup Job → Virtual Machine
```

### Configuration principale

- Sélection des **VM critiques uniquement**  
- Définition du **repository de sauvegarde**  
- **Planification automatique** (quotidienne recommandée)  

---

## 💾 Repository de sauvegarde

### Stockage principal

Les sauvegardes sont stockées sur :

- **NAS personnel local**  
- accessible via **partage réseau sécurisé**  

Objectifs :

- isoler les sauvegardes de l’hyperviseur  
- simuler une **stratégie de sauvegarde réelle**  
- préparer une logique **3-2-1** à terme  

---

## ⚙️ Paramètres importants

- **Compression activée**  
- **Vérification automatique** après sauvegarde  
- **Retention policy définie**  
- **Application-aware processing** activé uniquement si nécessaire  

---

## ▶️ 4️⃣ Lancement du premier backup

### Résultat attendu

- Création d’un **snapshot VMware**  
- **Copie des données vers le NAS**  
- Suppression automatique du snapshot  
- Statut **Backup Successful**  

---

## 🔎 Vérifications

### Côté Veeam

- Job terminé **sans erreur**  
- **Taille cohérente** du backup  
- **Durée d’exécution acceptable**  

### Côté ESXi

- Aucun **snapshot résiduel**  
- **Performances stables** des VM  

---

## 🔄 5️⃣ Tests de restauration

### Restauration fichier

- Extraction d’un **fichier individuel** depuis la sauvegarde  

### Restauration complète

- Restauration d’une **VM entière**  
- **Test de démarrage**  
- Vérification de l’**intégrité applicative**  

👉 Étape essentielle pour valider le **PRA réel**.

---

## 🧪 6️⃣ Simulation de PRA

### Scénario

- Arrêt volontaire d’une **VM critique**  
- **Restauration via Veeam**  
- Redémarrage et validation des services  

### Objectif

Mesurer :

- le **temps de reprise**  
- la **cohérence des données restaurées**  

---

## 🔐 Sécurité & bonnes pratiques

- Utiliser un **compte dédié Veeam** (éviter root)  
- Restreindre l’accès réseau au **serveur de sauvegarde**  
- Stocker les sauvegardes **hors ESXi** (NAS)  
- Mettre en place une **rétention adaptée**  

---

## 🧠 Analyse technique

Dans la phase 2, Veeam apporte :

- une **continuité d’activité réaliste**  
- une **sauvegarde centralisée mais ciblée**  
- des **tests de restauration concrets**  
- une approche alignée avec une **production légère moderne**  

---

## 📌 Évolutions futures

- Ajout de sauvegardes pour les **nœuds Kubernetes**  
- Mise en place d’une **réplication ou copie hors site**  
- Intégration d’une **supervision des sauvegardes**  
- Renforcement de la **sécurité Veeam**  
