# 💾 Intégration de Veeam – Sauvegarde de la phase 2

## 🎯 Objectif

Mettre en place une stratégie de sauvegarde :

- simple
- fiable
- réaliste

adaptée à une infrastructure minimaliste.

---

## 🧱 Périmètre de sauvegarde

Les sauvegardes concernent uniquement :

- la VM **Windows DNS/DHCP**
- la VM **Debian applicative**

---

## 🗄 Stockage des sauvegardes

Les données sont conservées sur un  
**NAS personnel local**, permettant :

- d’isoler les sauvegardes de l’hyperviseur
- de simuler une stratégie proche du **3-2-1**
- de préparer une évolution vers un stockage externe

---

## 🔄 Tests de restauration

Des restaurations complètes et partielles sont réalisées afin de :

- vérifier l’intégrité des sauvegardes
- mesurer le temps de reprise
- valider le scénario de PRA

---

## 🧠 Résultat

L’infrastructure dispose désormais :

- d’une **continuité d’activité fonctionnelle**
- d’une base compatible avec une exploitation réelle
