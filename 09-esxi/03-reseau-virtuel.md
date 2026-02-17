# 🌐 Mise en place du réseau virtuel ESXi – Phase 2

## 🎯 Objectif

Concevoir une architecture réseau virtuelle :

- simple
- lisible
- réaliste

permettant d’héberger :

- une VM **Windows Server 2025** (DNS/DHCP)
- plusieurs VM **Linux** destinées à Docker, Kubernetes et Ansible

---

## 🏗 Principe d’architecture

L’organisation réseau repose sur une séparation logique entre :

- le **réseau de management ESXi**
- le **réseau interne des machines virtuelles**

Cette séparation permet :

- de protéger l’hyperviseur
- de structurer les flux applicatifs
- de se rapprocher d’une architecture d’entreprise minimale

---

## 🔵 Réseau de management

Ce réseau est exclusivement dédié :

- à l’administration d’ESXi
- à l’accès à l’interface Web
- aux opérations de maintenance

Aucune machine virtuelle applicative n’y est connectée.

---

## 🟢 Réseau interne des VM

Ce réseau héberge :

- les services réseau Windows (DNS/DHCP)
- les serveurs Linux applicatifs
- les futurs nœuds Kubernetes

Il constitue le **cœur fonctionnel du laboratoire**.

---

## 🧪 Validation

La configuration est validée lorsque :

- les machines virtuelles communiquent entre elles
- l’attribution d’adresses IP fonctionne
- la résolution DNS interne est opérationnelle
- l’accès Internet est disponible

Le réseau virtuel est alors prêt pour le  
**déploiement des machines virtuelles**.
