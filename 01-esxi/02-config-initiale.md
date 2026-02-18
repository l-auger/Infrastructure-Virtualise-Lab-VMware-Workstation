# ⚙️ Configuration initiale et sécurisation d’ESXi

## 🎯 Objectif

Cette phase vise à :

- sécuriser l’accès à l’hyperviseur
- stabiliser l’environnement de virtualisation
- préparer l’hébergement des machines virtuelles critiques

---

## 🔐 Sécurisation des accès

Plusieurs mesures sont appliquées :

- définition d’un **mot de passe administrateur robuste**
- limitation de l’accès à l’interface d’administration au **réseau local**
- désactivation des services distants non nécessaires hors maintenance
- sauvegarde de la **configuration ESXi**

Ces actions réduisent la **surface d’exposition** de l’hyperviseur.

---

## ⏱ Synchronisation temporelle

Une source de temps fiable est configurée afin de garantir :

- la cohérence des journaux système
- la validité des certificats
- le bon fonctionnement des sauvegardes et restaurations

La synchronisation horaire constitue un prérequis essentiel  
dans tout environnement virtualisé.

---

## 💾 Vérification du stockage

Le datastore local est contrôlé afin de valider :

- sa détection correcte par ESXi
- l’espace disponible pour les futures machines virtuelles
- l’absence d’erreurs matérielles

---

## 🧪 Validation globale

L’environnement est considéré comme prêt lorsque :

- l’accès à l’interface Web est stable
- aucune alerte critique n’est présente
- les ressources CPU, mémoire et stockage sont opérationnelles

Cette étape marque la transition vers la **mise en place du réseau virtuel**.
