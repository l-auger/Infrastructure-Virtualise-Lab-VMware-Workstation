# 💾 Intégration Veeam Backup & Replication avec ESXi

## 🎯 Objectif

Intégrer l’hyperviseur **ESXi 8.x** à **Veeam Backup & Replication** afin de :

- Sauvegarder les machines virtuelles  
- Tester la restauration  
- Simuler un **PRA (Plan de Reprise d’Activité)**  
- Se rapprocher d’un environnement d’entreprise réel  

---

## 🧠 Pourquoi Veeam ?

### Limites sous VMware Workstation

- Pas d’API VMware exploitable  
- Sauvegardes **manuelles uniquement**  
- Pas de **snapshot cohérent**  

### Avantages avec ESXi

- **API VMware native**  
- Snapshot **à chaud**  
- Sauvegarde **complète des VM**  
- **Restauration granulaire**  
- Possibilité de **tests automatisés**  

---

## 🖥️ 1️⃣ Préparation de Veeam

### Serveur dédié

**Machine virtuelle :**

- **Nom :** `SVL-PS-VEEAM-01`  
- **OS :** Windows Server  
- **Rôle :** Serveur de sauvegarde  

### Ressources recommandées

- **4 vCPU**  
- **8 à 16 Go de RAM**  
- **Stockage dédié** pour les sauvegardes  

---

## 🔗 2️⃣ Ajout de l’hyperviseur ESXi dans Veeam

### Chemin dans Veeam

```
Inventory → Add Server → VMware vSphere → VMware ESXi
```

### Informations nécessaires

- **Adresse IP** de l’hyperviseur  
- **Compte root** (ou compte dédié recommandé)  
- **Mot de passe**  

### Validation de la connexion

Connexion réussie si :

- ESXi apparaît dans **l’inventaire Veeam**  
- Les **machines virtuelles sont listées**  

---

## 🧾 3️⃣ Création d’un job de sauvegarde

### Étapes

```
Backup Job → Virtual Machine
```

### Sélection des VM

- **DC1**  
- **DC2**  
- **pfSense**  
- **APP**  

### Configuration

- Définition du **repository**  
- **Planification** (quotidienne ou manuelle)  

---

## ⚙️ Paramètres importants

- **Application-aware processing activé** (pour les contrôleurs de domaine)  
- **Compression activée**  
- **Vérification automatique** activée  
- **Retention policy** définie  

---

## ▶️ 4️⃣ Lancement du premier backup

### Résultat attendu

- Création d’un **snapshot VMware**  
- **Copie des données**  
- Suppression du snapshot  
- Statut **Backup Successful**  

---

## 🔎 Vérifications

### Dans Veeam

- Job terminé **sans erreur**  
- **Taille du backup cohérente**  
- **Temps d’exécution acceptable**  

### Dans ESXi

- Aucun **snapshot bloqué**  
- **Performances stables**  

---

## 🔄 5️⃣ Test de restauration

### Types de tests réalisés

#### 🔹 Restauration d’un fichier unique

- Restauration d’un **fichier** depuis une VM  

#### 🔹 Restauration complète d’une VM

- Restauration vers un **nouvel emplacement**  
- **Test de démarrage**  
- Vérification de l’**intégrité**  

---

## 🧪 6️⃣ Simulation PRA (Plan de Reprise d’Activité)

### Scénario

- Extinction volontaire d’une **VM**  
- **Restauration depuis Veeam**  
- Redémarrage  
- Validation des **services**  

### Objectif

Tester le **temps de reprise** et la **cohérence des données**.

---

## 🔐 Sécurité & bonnes pratiques

- Ne pas utiliser **root en production** → préférer un **compte dédié**  
- Isoler le **réseau Veeam** si possible  
- Stocker les **backups sur un datastore séparé**  
- Définir une **rotation et une rétention** adaptées  

---

## 🧠 Analyse technique

L’intégration de **Veeam** apporte :

- **Sauvegarde centralisée**  
- **Snapshots cohérents**  
- **Restauration rapide**  
- **Simulation d’incident réel**  
- Approche **professionnelle type entreprise**  

---

## 📌 Évolution future

- Mise en place d’un **repository externe**  
- Test de **réplication**  
- **Sauvegarde hors site**  
- **Durcissement de la sécurité Veeam**  
