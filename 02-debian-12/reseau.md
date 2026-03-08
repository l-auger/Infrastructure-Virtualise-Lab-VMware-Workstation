# 🌐 Architecture Réseau – Intranet

## 🎯 Objectif
Le serveur intranet est accessible uniquement depuis le réseau interne de l’entreprise afin de garantir la sécurité et éviter toute exposition directe sur Internet.

---

## 🖧 Segmentation réseau

La machine virtuelle **SVL-PS-LIN-01** est connectée au **VLAN PG-LAN**, dédié au réseau interne.

| Élément | Valeur |
|--------|--------|
| VLAN | PG-LAN |
| Réseau | 192.168.11.0 /24 |
| Passerelle | 192.168.11.1 |
| DNS | 192.168.11.2 |

---

## 🖥 Serveur Intranet

| Paramètre | Valeur |
|----------|--------|
| Nom VM | SVL-PS-LIN-01 |
| IP | 192.168.11.70 |
| Accès DNS | intranet.entreprise.local |
| Rôle | Hébergement du service intranet |

---

## 🖧 Topologie réseau ESXi

La capture ci-dessous montre le **port group PG-LAN** configuré sur **vSwitch0** ainsi que les machines virtuelles connectées au réseau interne.

![Topologie réseau PG-LAN](screenshots/05-network.png)

Les machines virtuelles présentes sur ce réseau interne sont :

- SVL-PS-FWL-01  
- SVL-PS-ADM-01  
- SVL-PS-VEEAM-01  
- SVL-APP-01  

Toutes ces VM communiquent via le **port group PG-LAN**, relié à l’interface physique **vmnic0** du serveur ESXi.

---

## 🔎 Résolution DNS

Un **enregistrement A** a été ajouté dans le serveur DNS interne :
