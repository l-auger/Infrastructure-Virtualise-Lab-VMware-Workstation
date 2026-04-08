<div align="center">

# 🖥️ Infrastructure Lab — Virtualisation & Sauvegarde

[![Status](https://img.shields.io/badge/Status-En_cours-22c55e?style=for-the-badge)]()
[![Type](https://img.shields.io/badge/Type-Home_Lab-6366f1?style=for-the-badge)]()
[![Backup](https://img.shields.io/badge/Backup-Activé-0078D4?style=for-the-badge)]()

> Mise en place d'une infrastructure virtualisée bare-metal avec stratégie de sauvegarde,  
> reproduisant un environnement proche d'une infrastructure d'entreprise.

</div>

---

## 📌 Objectif

Ce laboratoire met en place une **infrastructure virtualisée** similaire à celles des environnements professionnels, reposant sur un **hyperviseur bare-metal** hébergeant plusieurs machines virtuelles, avec une **solution de sauvegarde** intégrée.

---

## 🎯 Objectifs principaux

| # | Objectif |
|---|----------|
| 1 | 🔍 Comprendre le fonctionnement d'un hyperviseur |
| 2 | 🚀 Déployer plusieurs machines virtuelles |
| 3 | 🗂️ Centraliser la gestion de l'infrastructure |
| 4 | 💾 Mettre en place une stratégie de sauvegarde |
| 5 | 🔄 Tester des scénarios de restauration |

---

## 🏗️ Architecture
```
┌─────────────────────────────────────────┐
│           Serveur Physique              │
│                                         │
│  ┌───────────────────────────────────┐  │
│  │      Hyperviseur Bare-Metal       │  │
│  │  ┌───────┐ ┌───────┐ ┌───────┐    │  │
│  │  │ VM APP│ │ VM ADM│ │ VM FWL│    │  │
│  │  └───────┘ └───────┘ └───────┘    │  │
│  └───────────────────────────────────┘  │
│  ┌───────────────────────────────────┐  │
│  │      Serveur de Sauvegarde VEEAM  │  │
│  └───────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

---

## 📈 Avancement

- [x] Mise en place de l'hyperviseur
- [x] Déploiement des premières VMs
- [ ] Configuration de la sauvegarde
- [ ] Tests de restauration
- [ ] Documentation finale

---

<div align="center">
<sub>🔧 Infrastructure Lab — Projet personnel</sub>
</div>