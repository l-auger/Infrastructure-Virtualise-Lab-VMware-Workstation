# 🖥️ Installation de l’hyperviseur – VMware ESXi 8.0.2

## 🎯 Objectif

Cette étape consiste à mettre en place un **hyperviseur bare-metal VMware ESXi 8.0.2**  
afin de constituer la base de virtualisation de l’infrastructure du laboratoire.

L’installation d’ESXi permet :

- d’obtenir une plateforme **indépendante d’un système hôte**
- de se rapprocher d’une **architecture de production réelle**
- de centraliser l’hébergement des futures machines virtuelles :
  - **Windows Server 2025** pour les services réseau (DNS/DHCP)
  - **Debian 12** pour la couche applicative, conteneurisée et orchestrée

---

## 🧩 Environnement matériel

L’hyperviseur est déployé sur une machine physique disposant des caractéristiques suivantes :

- Processeur **AMD Ryzen 7 7800X3D**
- **64 Go de mémoire vive**
- Stockage SSD principal, dont une **portion est réservée à ESXi**
- Démarrage en mode **UEFI**

Le choix d’une installation sur **partition du SSD** correspond à un  
contexte de **laboratoire personnel réaliste**, sans disque entièrement dédié.

---

## ⚙️ Principe d’installation

L’installation d’ESXi consiste à :

1. Démarrer l’hôte sur le support d’installation ESXi.
2. Déployer l’hyperviseur sur la zone de stockage prévue.
3. Initialiser le compte administrateur local (**root**).
4. Appliquer une première configuration réseau minimale.
5. Valider l’accès à l’interface d’administration Web.

À l’issue de cette étape, l’hyperviseur constitue une  
**plateforme de virtualisation opérationnelle**.

---

## 🌐 Configuration réseau initiale

Une adresse IP statique est attribuée à l’interface de management ESXi,  
accompagnée :

- d’une passerelle par défaut
- d’un serveur DNS temporaire
- d’un nom d’hôte : `SVL-PS-HV-01`

Cette configuration garantit :

- un accès stable à l’interface d’administration
- une intégration cohérente dans le réseau local du laboratoire

---

## ✅ Validation

L’installation est considérée comme valide lorsque :

- l’interface Web ESXi est accessible
- le stockage local est détecté
- les ressources matérielles sont reconnues
- la version installée correspond à **VMware ESXi 8.0.2**

L’hyperviseur est alors prêt à être **sécurisé et configuré**.
