# Infrastructure virtualisée – Laboratoire VMware ESXi

---

# 1. Présentation du laboratoire

Ce laboratoire a pour objectif de concevoir et exploiter une infrastructure virtualisée réaliste, hébergée sur l’hyperviseur **VMware ESXi**, afin de reproduire un environnement proche de celui d’une petite ou moyenne entreprise.

Le projet vise à mettre en pratique plusieurs compétences fondamentales de l’administration systèmes et réseaux :

- administration de systèmes **Windows et Linux**
- gestion de **services réseau essentiels**
- exploitation d’un **serveur Linux**
- mise en œuvre d’une **solution de supervision**
- déploiement d’une **stratégie de sauvegarde et de reprise d’activité**

L’approche adoptée privilégie une architecture **simple, cohérente et exploitable**, permettant d’analyser concrètement les interactions entre les différents composants de l’infrastructure.

---

# 2. Phase 3 – Mise en place de la supervision

La troisième phase du laboratoire introduit une **solution de supervision centralisée** afin d’améliorer la visibilité opérationnelle de l’infrastructure.

Dans un environnement professionnel, la supervision constitue un élément essentiel permettant :

- de surveiller la **disponibilité des systèmes**
- d’identifier rapidement les **incidents**
- d’analyser l’état des **services critiques**
- de valider la **reprise de service après incident**

La solution retenue pour ce laboratoire est **Centreon**.

Cette approche permet de simplifier le déploiement de la plateforme de supervision tout en conservant une **architecture modulaire**.

---

# 3. Architecture de l’infrastructure

L’infrastructure est constituée de **plusieurs machines virtuelles hébergées sur VMware ESXi**.

Chaque machine virtuelle remplit un **rôle spécifique** au sein de l’environnement.

---

## 3.1 Serveur Windows – Services réseau

Une machine virtuelle exécutant **Windows Server** assure les services d’infrastructure réseau essentiels.

Les services configurés sont les suivants :

### DHCP (Dynamic Host Configuration Protocol)

Attribution automatique des adresses IP aux machines du réseau.

### DNS (Domain Name System)

Résolution de noms interne permettant aux machines de communiquer via des noms plutôt que des adresses IP.

L’objectif est de reproduire un **socle réseau minimal** permettant d’assurer la communication entre les différents systèmes de l’infrastructure.

---

## 3.2 Serveur Debian – Services Linux et supervision

Une machine virtuelle exécutant **Debian** joue le rôle de serveur Linux principal.

Elle remplit deux fonctions :

- hébergement d’un **intranet local**
---

### 3.2.1 Hébergement d’un intranet interne

Le serveur Debian héberge un **intranet interne accessible uniquement depuis le réseau local**.

Le service web est assuré par **NGINX**.

Cet intranet permet notamment :

- de valider le fonctionnement du **serveur web**
- de tester la **résolution DNS interne**
- de vérifier la **connectivité réseau**
- de disposer d’un **service applicatif simple à superviser**

Cette approche permet de reproduire un **service interne typiquement présent dans une infrastructure d’entreprise**.

---

### 3.2.2 Supervision de l’infrastructure

La supervision de l’environnement est assurée par **Centreon**.

La plateforme de supervision permet de surveiller :

- la **disponibilité des machines virtuelles**
- l’**accessibilité réseau des systèmes**
- l’état des **services applicatifs**
- le fonctionnement du **serveur web NGINX**

Les mécanismes de supervision reposent principalement sur :

- des **vérifications ICMP**
- des **contrôles de services réseau**
- des **tests d’accessibilité applicative**

La supervision permet ainsi de reproduire le fonctionnement d’un **outil de supervision utilisé dans les centres d’exploitation informatique (NOC)**.

---

# 4. Architecture réseau

L’infrastructure réseau repose sur les éléments suivants :

- **Hyperviseur :** VMware ESXi  
- **Pare-feu :** pfSense  
- **Réseau :** LAN virtualisé

Le pare-feu **pfSense** assure plusieurs fonctions :

- séparation entre les réseaux **WAN et LAN**
- **contrôle des flux réseau**
- application de **règles de filtrage**

Le fonctionnement global du réseau repose sur :

1. attribution des adresses IP par le **serveur DHCP Windows**
2. résolution des noms via le **serveur DNS interne**
3. filtrage et contrôle des communications par **pfSense**

Cette architecture reproduit une **topologie réseau simplifiée mais représentative d’une infrastructure professionnelle**.

---

# 5. Sauvegarde et reprise d’activité

La stratégie de sauvegarde de l’environnement repose sur **Veeam Backup & Replication**.

Les objectifs principaux sont :

- protéger les **machines virtuelles critiques**
- permettre une **restauration rapide en cas d’incident**
- vérifier l’**intégrité des services après restauration**

Plusieurs scénarios de test ont été réalisés :

- suppression simulée d’une **machine virtuelle**
- restauration complète à partir de la **sauvegarde**
- vérification du **redémarrage des services**
- validation de la **connectivité réseau**

La supervision via **Centreon** permet également de confirmer le **retour à un état opérationnel après restauration**.

---

# 6. Compétences développées

La mise en œuvre de ce laboratoire permet de développer plusieurs compétences techniques :

- administration **Windows Server**
- configuration **DHCP / DNS**
- exploitation d’un **serveur Linux Debian**
- déploiement d’un **serveur web NGINX**
- mise en place d’une **solution de supervision**
- gestion des **sauvegardes et restaurations**
- rédaction de **documentation technique**

---

# 7. Positionnement dans le projet global

| Phase   | Description                              | Statut        |
|---------|------------------------------------------|---------------|
| Phase 1 | Infrastructure sous VMware Workstation   | ✅ Terminée    |
| Phase 2 | Migration vers VMware ESXi 8.x           | ✅ Terminée   |
| Phase 3 | Intégration Veeam & PRA                  | ✅ Terminée  |

---

# 8. Conclusion

Ce laboratoire a pour objectif de reproduire une **infrastructure virtualisée cohérente et exploitable**, représentative d’un environnement professionnel de petite taille.

L’ajout d’une solution de supervision permet d’améliorer la **gestion opérationnelle de l’infrastructure** en offrant une visibilité sur l’état des systèmes et des services.

L’ensemble du projet s’inscrit dans une démarche progressive visant à maîtriser les différentes étapes du **cycle de vie d’une infrastructure** :

- déploiement
- configuration
- supervision
- sauvegarde
- restauration après incident
