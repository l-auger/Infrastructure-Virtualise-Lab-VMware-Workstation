# 06 — Configuration du job de sauvegarde

## Objectif

Créer un job de sauvegarde dans Veeam pour protéger la VM **SVL-APP-01**.

---

## Étapes

### 1. Nommer le job

![Nom du job](01-nom-job.png)

Nom : `Sauvegarde applicatif - SVL-APP-01`  
Priorité haute activée.

---

### 2. Sélectionner la VM source

![Sélection de la VM](02-selection-vm.png)

VM ajoutée : **SVL-APP-01** — Taille totale : `10,2 GB`

---

### 3. Définir le stockage

![Stockage](03-mise-en-place-du-stockage.png)

| Paramètre | Valeur |
|-----------|--------|
| Référentiel | Sauvegarde de l'applicatif SVL-APP-01 |
| Espace disponible | 89,9 GB |
| Rétention | 7 jours |

---

### 4. Guest Processing

![Guest Processing](04-guest-processing.png)

Options laissées par défaut — aucun traitement applicatif activé pour ce lab.

---

### 5. Planification

![Planification](05-planification.png)

| Paramètre | Valeur |
|-----------|--------|
| Fréquence | Tous les jours |
| Heure | 14h00 |
| Tentatives en cas d'échec | 3 fois |
| Attente entre chaque tentative | 10 minutes |

---

### 6. Résumé

![Résumé du job](06-resume-job.png)

| Paramètre | Valeur |
|-----------|--------|
| Nom | Sauvegarde applicatif - SVL-APP-01 |
| Destination | F:\Sauvegardes-APP-01 |
| Type | VMware Backup |
| Source | SVL-APP-01 (192.168.56.29) |

---

## Résultat

Le job de sauvegarde est configuré et planifié. Il s'exécutera automatiquement chaque jour à **14h00** et conservera **7 points de restauration**.