# 03 — Installation de Veeam Backup & Replication

## Prérequis

| Élément | Valeur |
|---------|--------|
| VM | SVL-PS-VEEAM-01 |
| OS | Windows Server 2025 (64 bits) |
| CPU | 2 vCPU |
| RAM | 4 Go |
| ISO | Veeam Backup and Replication |

---

## Étapes d'installation

### 1. Monter l'ISO
Monter l'ISO de Veeam sur le lecteur DVD de la VM depuis l'interface ESXi.

### 2. Lancer le Setup

![Installation Veeam](01-install-veeam.png)

Ouvrir le lecteur DVD `(E:)` et exécuter `Setup.exe`.

### 3. Sélectionner le produit
Choisir **Veeam Backup & Replication** dans le menu d'installation.

### 4. Accepter la licence
Accepter le contrat de licence (EULA).

### 5. Choisir les composants
Laisser les composants par défaut :
- Veeam Backup & Replication
- Veeam Backup Catalog
- Veeam Enterprise Manager *(optionnel)*

### 6. Vérifier les prérequis
Veeam vérifie automatiquement les dépendances (.NET, SQL, etc.)
et les installe si nécessaire.

### 7. Configurer le chemin d'installation
Laisser le chemin par défaut ou personnaliser.

### 8. Configurer la base de données
Utiliser l'instance **SQL Server Express** installée automatiquement
par Veeam si aucune instance SQL n'existe déjà.

### 9. Finaliser
Lancer l'installation et attendre la fin du processus.

---

## Résultat

Veeam Backup & Replication est installé et accessible depuis le bureau de la VM **SVL-PS-VEEAM-01**.