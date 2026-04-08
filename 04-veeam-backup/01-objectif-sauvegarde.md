# 🎯 01 — Objectif de sauvegarde avec Veeam Backup & Replication

---

## 📌 Contexte

Dans le cadre de ce laboratoire, l'infrastructure repose sur un hyperviseur **VMware ESXi** hébergeant plusieurs machines virtuelles.

Afin d'assurer la protection des données, la solution **Veeam Backup & Replication** est déployée pour gérer l'ensemble des sauvegardes.

---

## ❓ Pourquoi utiliser Veeam avec ESXi ?

**Veeam Backup & Replication** est une solution spécialement conçue pour les environnements virtualisés.

Elle s'intègre nativement avec **VMware ESXi** grâce aux API VMware (**VADP — vStorage APIs for Data Protection**), ce qui permet :

* 🔄 Sauvegarde **sans agent**
* ⚡ Sauvegarde **sans interruption des machines**
* 🎯 Gestion directe au niveau **hyperviseur**

---

## ✅ Avantages

* 🚀 **Aucune interruption de service**
  Les machines virtuelles restent actives grâce aux snapshots VMware

* 🧠 **Cohérence des données**
  Les données applicatives sont sécurisées avant la sauvegarde

* 🔍 **Granularité avancée**
  Restauration possible :

  * d’une VM complète
  * d’un fichier
  * d’un élément applicatif (mail, base de données…)

---

## ⚙️ Fonctionnement général

```text
┌─────────────────────────────────────────────┐
│              VMware ESXi                    │
│                                             │
│   ┌──────────┐   ┌──────────┐               │
│   │   VM 1   │   │   VM 2   │               │
│   └────┬─────┘   └────┬─────┘               │
│        │ snapshot     │ snapshot            │
└────────┼──────────────┼─────────────────────┘
         │              │
         ▼              ▼
┌─────────────────────────────────────────────┐
│       Veeam Backup & Replication            │
│                                             │
│   - Planification des jobs                  │
│   - Compression & déduplication             │
│   - Envoi vers le stockage                  │
└─────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────┐
│         Référentiel de sauvegarde           │
│       (disque local, NAS, etc.)             │
└─────────────────────────────────────────────┘
```

---

## 🎯 Objectifs visés

| Objectif                     | Description                             |
| ---------------------------- | --------------------------------------- |
| 💾 Sauvegarde des VMs        | Protéger toutes les machines virtuelles |
| ⏱️ Planification automatique | Mettre en place des backups réguliers   |
| 🗜️ Optimisation du stockage | Compression et déduplication            |
| 🔄 Restauration rapide       | Restaurer rapidement en cas d’incident  |
| ✅ Validation des backups     | Vérifier l’intégrité (SureBackup)       |

---

## 🧪 Compétences mises en pratique

* Installer et configurer **Veeam Backup & Replication**
* Connecter Veeam à un hôte **ESXi**
* Créer et planifier des jobs de sauvegarde
* Réaliser une restauration complète de VM
* Effectuer une restauration granulaire (fichier)

---

## 🧠 Conclusion

Ce laboratoire permet de comprendre concrètement comment sécuriser une infrastructure virtualisée en mettant en place une stratégie de sauvegarde fiable, automatisée et testée.
