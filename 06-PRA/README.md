# 🛡️ PCA & 🔄 PRA — Explication détaillée appliquée à mon infrastructure

---

## 📌 1. Présentation de mon infrastructure

Mon infrastructure est basée sur un environnement virtualisé avec :

* 🖥️ **VMware ESXi** : hyperviseur qui héberge toutes les machines virtuelles
* 🔐 **pfSense** : firewall et routeur principal
* 🌐 **Segmentation en VLANs** :

  * VLAN Admin (gestion)
  * VLAN Commercial (utilisateurs)
  * VLAN Web (services exposés)
* 📊 **Centreon** : supervision des équipements et services
* 💾 **Veeam Backup & Replication** : solution de sauvegarde des machines virtuelles

👉 Cette architecture reproduit une **infrastructure d’entreprise (PME)** avec des bonnes pratiques de sécurité.

---

# 🛡️ 2. PCA — Ce que je fais concrètement dans MON infra

## 🎯 Objectif

Dans mon cas, le **PCA sert à éviter qu’un problème bloque toute l’infrastructure**.

---

## 🔐 2.1 Isolation avec pfSense

pfSense est placé en frontal (WAN → LAN).

👉 Ce que je fais :

* Je configure des règles firewall entre les VLANs
* Je limite les communications inutiles
* Je protège les services exposés (VLAN Web)

👉 Résultat :

✔ Une attaque sur le serveur web ne touche pas le réseau admin
✔ Un problème est contenu dans une zone

---

## 🌐 2.2 Segmentation réseau (VLANs)

J’ai séparé mon réseau en plusieurs sous-réseaux.

👉 Pourquoi c’est important :

* Chaque zone a un rôle précis
* Les flux sont contrôlés

👉 Exemple concret :

* Si le serveur web est compromis →
  il ne peut pas accéder directement à pfSense ou aux machines admin

✔ Ça évite une compromission globale

---

## 📊 2.3 Supervision avec Centreon

Centreon me permet de surveiller :

* les machines virtuelles
* les services
* le réseau (SNMP)

👉 Ce que je fais :

* Je configure des checks
* Je surveille les états (UP / DOWN)
* Je consulte les logs

👉 Résultat :

✔ Je détecte immédiatement une panne
✔ Je peux intervenir rapidement

---

## ⚡ 2.4 Conclusion PCA dans mon infra

Même sans haute disponibilité complète :

👉 Mon PCA repose sur :

* la **sécurité (pfSense)**
* la **segmentation (VLANs)**
* la **détection rapide (Centreon)**

✔ Les incidents sont limités et maîtrisés

---

# 🔄 3. PRA — Ce que je fais concrètement avec Veeam

## 🎯 Objectif

Le PRA me permet de **restaurer rapidement mon infrastructure en cas de panne majeure**.

---

## 💾 3.1 Sauvegarde des VMs

Avec Veeam, je sauvegarde :

* pfSense (critique)
* Centreon
* serveurs web
* autres machines

👉 Pourquoi c’est important :

Toutes les machines sont des VMs →
👉 une sauvegarde = une reprise complète possible

---

## 📅 3.2 Planification

Je mets en place :

* sauvegarde **incrémentale quotidienne**
* sauvegarde **complète hebdomadaire**

👉 Résultat :

✔ Je limite la perte de données
✔ J’ai plusieurs points de restauration

---

## 🚨 3.3 Cas concrets dans MON infra

### 🔴 Cas 1 : Centreon tombe

👉 Impact :

* Plus de supervision

👉 Ce que je fais :

1. J’ouvre Veeam
2. Je lance un **Instant Recovery**
3. Je redémarre la VM

✔ Centreon est de nouveau opérationnel rapidement

---

### 🔴 Cas 2 : pfSense crash

👉 Impact :

* Plus de réseau → tout est bloqué

👉 Ce que je fais :

1. Restauration complète de la VM pfSense
2. Vérification des interfaces (WAN / LAN / VLAN)
3. Test de connectivité

✔ Toute l’infra redevient accessible

---

### 🔴 Cas 3 : serveur web compromis

👉 Impact :

* risque de sécurité

👉 Ce que je fais :

1. Suppression de la VM compromise
2. Restauration d’une sauvegarde saine
3. Vérification des accès

✔ Service restauré proprement

---

### 🔴 Cas 4 : ESXi HS

👉 Impact :

* toutes les VMs indisponibles

👉 Ce que je fais :

1. Réinstallation ESXi
2. Réinstallation Veeam (si nécessaire)
3. Restauration de toutes les VMs

✔ Infrastructure reconstruite

---

## 🧪 3.4 Tests de PRA

Je teste régulièrement :

* restauration d’une VM
* restauration d’un fichier

👉 Pourquoi :

✔ Vérifier que les sauvegardes fonctionnent vraiment

---

# ⚖️ 4. Différence dans MON infra

| Situation       | Action                        |
| --------------- | ----------------------------- |
| Problème mineur | PCA → Centreon + intervention |
| Problème majeur | PRA → restauration Veeam      |

---

# 🧠 5. Ce que ça prouve dans mon projet

Ce projet montre que :

* Je sais **sécuriser une infrastructure**
* Je sais **anticiper les pannes**
* Je sais **restaurer un système complet**
* Je comprends la différence entre **prévention (PCA)** et **réaction (PRA)**

---

# 🚀 6. Conclusion

Dans mon infrastructure :

* 🛡️ Le **PCA** permet de limiter les incidents grâce à la segmentation et la supervision
* 🔄 Le **PRA** permet de restaurer rapidement grâce à Veeam

👉 Les deux sont indispensables pour garantir la disponibilité et la sécurité du système.
