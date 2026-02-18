# 🏗️ Architecture finale – Phase ESXi

## 🎯 Objectif

Présenter une vue synthétique de l’infrastructure déployée  
après la migration vers VMware ESXi.

---

## 🖥️ Hyperviseur

- **VMware ESXi 8.0.2**
- installation sur **partition dédiée du SSD**
- accès Web sécurisé
- datastore local pour les VM

---

## 🪟 Services Windows

Une machine virtuelle **Windows Server 2025** assure :

- **DHCP** → attribution automatique des adresses IP
- **DNS** → résolution de noms interne

Cette VM représente le **socle réseau minimal** du laboratoire.

---

## 🐧 Couche Linux applicative

Une VM **Debian 12** héberge :

- les services applicatifs
- les futurs outils de supervision ou d’automatisation
- les tests d’exploitation Linux

Elle constitue le **cœur technique du lab**.

---

## 💾 Sauvegarde

La protection des services repose sur :

- **Veeam Backup & Replication**
- sauvegarde des VM critiques
- stockage sur **NAS personnel local**

Objectif :

> simuler une stratégie de sauvegarde réaliste en environnement réduit.

---

## 🧠 Vision globale

L’architecture finale est volontairement :

- **simple**
- **cohérente**
- **représentative d’un environnement réel minimal**

Elle sert de base pour :

- la supervision
- la sécurisation
- l’automatisation
- les futurs projets d’infrastructure.
