# 🪟 Windows Server – Infrastructure principale

## 🎯 Objectif

Cette machine virtuelle assure les services critiques de l’infrastructure :

- Active Directory
- DNS
- DHCP

Elle constitue le contrôleur de domaine principal du laboratoire.

---

## 🖥 Informations VM

- Hyperviseur : VMware ESXi
- OS : Windows Server 2022
- IP : 192.168.11.2
- Masque : 255.255.255.0
- Passerelle : 192.168.11.1
- DNS : 192.168.11.2
- Domaine : entreprise.local

---

## 🔧 Rôles installés

- Active Directory Domain Services
- DNS Server
- DHCP Server

---

## 🧪 Validation globale

- Résolution DNS interne et externe fonctionnelle
- Attribution IP automatique via DHCP
- Intégration client au domaine validée
- Connectivité Internet validée
