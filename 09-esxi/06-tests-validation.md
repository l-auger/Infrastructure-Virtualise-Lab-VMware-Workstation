# 🧪 Tests et validation globale – Infrastructure ESXi

## 🎯 Objectif

Vérifier que l’infrastructure déployée sous ESXi :

- fonctionne correctement
- est stable dans le temps
- peut être restaurée en cas d’incident

Cette étape permet de valider la **cohérence technique globale** du laboratoire.

---

## 🔍 Validation de l’hyperviseur

Les points suivants sont contrôlés :

- accès à l’interface Web ESXi opérationnel
- ressources CPU et mémoire correctement détectées
- datastore fonctionnel et accessible
- absence d’erreurs critiques dans les logs système

Résultat :

> Hyperviseur stable et prêt pour l’exploitation.

---

## 🌐 Validation réseau

Les tests réseau vérifient :

- attribution d’adresse IP via **DHCP Windows**
- résolution de noms via **DNS interne**
- communication entre les machines virtuelles
- accès Internet depuis les VM Linux

Résultat :

> Connectivité interne et externe fonctionnelle.

---

## 🐧 Validation du serveur Debian applicatif

Les contrôles effectués :

- accès SSH fonctionnel
- services applicatifs démarrés
- stabilité du système Linux
- connectivité réseau complète

Résultat :

> Serveur applicatif opérationnel.

---

## 💾 Validation des sauvegardes Veeam

Tests réalisés :

- exécution d’un job de sauvegarde complet
- vérification de l’intégrité des fichiers sauvegardés
- restauration d’une VM de test
- validation du redémarrage après restauration

Résultat :

> Sauvegarde et restauration pleinement fonctionnelles.

---

## 🏁 Conclusion

L’infrastructure ESXi est :

- stable
- cohérente
- sauvegardée
- restaurable

