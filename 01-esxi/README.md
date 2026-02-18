# 🖥️ Phase ESXi – Infrastructure virtualisée minimaliste

## 🎯 Présentation

Cette phase du projet marque la transition :

- d’un laboratoire complet sous VMware Workstation  
- vers une infrastructure **bare-metal sous VMware ESXi 8.0.2**

L’objectif est de construire une base :

- plus réaliste
- plus stable
- plus proche d’un environnement de production

---

## 🧱 Composants déployés

### Hyperviseur

- VMware ESXi 8.0.2
- datastore local
- réseau virtuel structuré

### Services réseau

- Windows Server 2025  
  - DHCP  
  - DNS  

### Serveur applicatif

- Debian 12
- hébergement des services Linux

### Sauvegarde

- Veeam Backup & Replication
- stockage sur NAS local

---

## 🧪 Validation

L’infrastructure est :

- fonctionnelle
- stable
- sauvegardée
- restaurable

Elle constitue une **base technique solide** pour les évolutions futures du laboratoire.

---

## 📈 Suite du projet

Les prochaines étapes pourront inclure :

- supervision de l’infrastructure
- durcissement de la sécurité
- automatisation des déploiements
- nouveaux services applicatifs

Cette phase représente la **fondation technique** du laboratoire.
