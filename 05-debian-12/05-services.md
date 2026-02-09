# Services applicatifs — Debian 12

## Contexte

Le serveur Debian 12 héberge un **service web intranet Nginx**
destiné à être accessible depuis le réseau interne de l’entreprise.

Le service web n’a pas été installé dans ce projet :
il provient d’un **TP Linux précédent** et est déjà :

- installé
- configuré
- fonctionnel
- accessible via l’adresse IP du serveur

L’objectif de cette étape est donc :

- d’intégrer proprement le service dans l’infrastructure entreprise
- de permettre un accès via un **nom DNS interne**
- de masquer l’utilisation directe de l’adresse IP

---

## 1. État actuel du service Nginx

### Vérification du service

```bash
sudo systemctl status nginx --no-pager
```

## 2. Mise en place d’un enregistrement DNS interne

Objectif
Associer l’adresse IP du serveur à un nom de domaine interne :

intranet.entreprise

Permet :

- un accès utilisateur plus simple
- une meilleure intégration dans le SI
- la préparation d’un futur HTTPS
3. Création de l’enregistrement DNS (côté serveur DNS)

⚠️ Cette opération est réalisée sur le serveur DNS de l’infrastructure
(et non sur la machine Debian).

Type d’enregistrement

Type : A

Nom : intranet

Domaine : entreprise

Adresse IP : 192.168.11.51

Résultat :

intranet.entreprise → 192.168.11.51

4. Vérification de la résolution DNS

Depuis un poste du réseau :

nslookup intranet.entreprise

ou :

ping intranet.entreprise


Résultat attendu :
192.168.11.51

5. Test d’accès à l’intranet via DNS

Accès navigateur :

http://intranet.entreprise


Résultat attendu :

- affichage de la page intranet
- réponse HTTP 200 OK
- absence d’utilisation directe de l’adresse IP

Résultat final

Le service intranet est désormais :
- opérationnel sur le serveur Debian 12
- intégré au DNS interne de l’entreprise
- accessible via le nom intranet.entreprise
- conforme aux bonnes pratiques d’exploitation système