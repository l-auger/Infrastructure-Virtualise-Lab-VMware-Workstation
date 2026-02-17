# 🖥️ Déploiement des machines virtuelles – Phase 2

## 🎯 Objectif

Mettre en place uniquement les services réellement utiles  
dans une logique d’infrastructure **minimaliste mais réaliste**.

---

## 🧠 Nouvelle orientation

Contrairement à la phase 1 du projet,  
l’architecture ne repose plus sur une PME complète simulée.

Seuls sont conservés :

- **Windows Server 2025** pour les services réseau essentiels (DNS/DHCP)
- **Debian 12** pour la couche applicative moderne

Cette simplification permet de :

- réduire la complexité
- se concentrer sur les technologies actuelles
- construire un laboratoire exploitable sur la durée

---

## 🏗 Déploiement des rôles

### Windows Server 2025

Rôle :

- attribution automatique des adresses IP (DHCP)
- résolution de noms interne (DNS)

Il constitue le **socle réseau minimal**.

---

### Debian 12

Rôle :

- hébergement applicatif
- conteneurisation Docker
- orchestration Kubernetes
- automatisation Ansible

Cette machine devient le **cœur technique du laboratoire**.

---

## 🧪 Validation

Le déploiement est validé lorsque :

- les services DHCP et DNS fonctionnent
- la machine Debian est accessible
- la connectivité réseau globale est stable

L’infrastructure est alors prête pour la  
**mise en place des sauvegardes**.
