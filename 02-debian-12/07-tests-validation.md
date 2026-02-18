# Tests de validation — Infrastructure Debian 12

## Contexte

Ce document présente les **tests fonctionnels et techniques**
permettant de valider le bon fonctionnement du serveur Debian 12
hébergeant l’intranet Nginx au sein de l’infrastructure entreprise.

Objectifs :

- vérifier la connectivité réseau
- valider la résolution DNS interne
- confirmer la disponibilité du service web
- contrôler la sécurité et l’état des services

---

## 1. Validation réseau

### Vérification de l’adresse IP

```bash
ip a
```

Adresse attendue :

192.168.11.51/24

Test de la passerelle
```bash
ping -c 4 192.168.11.1
```
Résultat attendu :

- 0 % de perte de paquets
- latence stable

Test d’accès Internet
```bash
ping -c 4 8.8.8.8
ping -c 4 google.com
```

Permet de valider :

- la connectivité externe
- la résolution DNS publique

## 2. Validation DNS interne
### Résolution du FQDN intranet
```bash
nslookup intranet.entreprise.local
```

Résultat attendu :

Address: 192.168.11.51

## 3. Validation du service web Nginx
### Vérification du service
systemctl status nginx --no-pager


État attendu :

active (running)

Test HTTP local
```bash
curl -I http://localhost
```
Test HTTP via DNS interne
```bash
curl -I http://intranet.entreprise.local
```

Résultat attendu :
HTTP/1.1 200 OK

Accès navigateur depuis un poste client
http://intranet.entreprise.local


La page intranet doit s’afficher correctement.

## 4. Validation de la sécurité SSH
### Test de connexion SSH

Depuis un poste client :
```bash
ssh adminsrv@192.168.11.51
```

Résultat attendu :

- authentification par clé SSH uniquement

- aucune demande de mot de passe

- accès root impossible

## 5. Validation du firewall
### Vérification de l’état UFW
```bash
sudo ufw status verbose
```
Doivent apparaître :

- ports 22, 80, 443 autorisés
- politique deny incoming

## 6. Validation de la supervision locale
### Consultation des logs Nginx
```bash
tail -n 20 /var/log/nginx/access.log
tail -n 20 /var/log/nginx/error.log
```
Vérification des services actifs
```bash
systemctl list-units --type=service --state=running
```
Utilisation disque
```bash
df -h
```
Résultat global

L’ensemble des tests confirme que :

- le serveur est correctement connecté au réseau
- la résolution DNS interne est fonctionnelle
- le service Nginx est disponible via le FQDN
- l’accès SSH est sécurisé
- le firewall est actif
- la journalisation et la supervision locale sont opérationnelles

L’infrastructure Debian 12 est donc fonctionnelle, sécurisée et exploitable
dans un contexte professionnel.