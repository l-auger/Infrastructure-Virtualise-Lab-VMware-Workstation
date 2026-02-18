# 🌐 Vue globale de l’infrastructure

## 🎯 Objectif

Fournir une représentation synthétique de l’architecture du laboratoire,
afin de comprendre rapidement :

- les composants principaux
- leurs interactions
- leur rôle fonctionnel

---

## 🧱 Hyperviseur

L’infrastructure repose sur :

- **VMware ESXi 8.0.2**
- stockage local
- réseau virtuel segmenté

Cet hyperviseur héberge l’ensemble des machines virtuelles du laboratoire.

---

## 🪟 Services d’infrastructure

Une machine virtuelle **Windows Server 2025** assure :

- **DHCP** : attribution automatique des adresses IP
- **DNS** : résolution de noms interne

Elle constitue le **socle réseau minimal**.

---

## 🐧 Couche applicative Linux

Une machine virtuelle **Debian 12** héberge :

- les services applicatifs
- les futurs outils de supervision ou d’automatisation
- les expérimentations système Linux

Elle représente le **cœur fonctionnel** de l’environnement.

---

## 💾 Sauvegarde

La protection de l’infrastructure repose sur :

- **Veeam Backup & Replication**
- sauvegarde des VM critiques
- stockage sur **NAS personnel local**

---

## 🧠 Vision

L’architecture est volontairement :

- **simple**
- **réaliste**
- **évolutive**

afin de servir de base à des expérimentations
en administration systèmes et réseaux.
