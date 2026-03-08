# 🖥️ SVL-PS-LIN-01 – Serveur Intranet

## 🎯 Objectif
Déployer un serveur intranet accessible uniquement sur le réseau interne de l’entreprise.

## ⚙️ Infrastructure
- **Hyperviseur** : VMware ESXi 8.0  
- **VLAN** : PG-LAN (accès interne uniquement)  
- **Nom VM** : SVL-PS-LIN-01  
- **IP** : 192.168.11.70  
- **DNS** : intranet.entreprise.local  

## 🔧 Actions réalisées
- Migration de la VM depuis **VMware Workstation** vers **ESXi**
- Placement de la VM dans le **VLAN PG-LAN**
- Configuration réseau (IP, passerelle, DNS)
- Ajout d’un **enregistrement DNS A** pour `intranet.entreprise.local`
- Validation de l’accès au service intranet via le navigateur

## ✅ Résultat
- Accès à l’intranet fonctionnel via `intranet.entreprise.local`
- Service accessible uniquement depuis le réseau interne
- VM opérationnelle sur l’infrastructure ESXi