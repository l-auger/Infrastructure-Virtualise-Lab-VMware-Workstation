# Hardening sécurité — Debian 12

## Contexte

Ce document décrit la mise en place du **durcissement de sécurité**
du serveur Debian 12 hébergeant l’intranet Nginx dans le réseau entreprise.

Le hardening est appliqué **après** :

- configuration réseau fonctionnelle
- intégration au LAN
- mise en place d’un accès SSH par clé
- création d’un utilisateur administrateur dédié

Objectif :

- sécuriser l’accès distant
- limiter la surface d’attaque
- protéger le serveur contre les attaques courantes
- rendre l’environnement exploitable en entreprise

---

# 1. Sécurisation du service SSH

## Édition de la configuration SSH

```bash
sudo nano /etc/ssh/sshd_config
```
## Configuration appliquée
```bash
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
AllowUsers adminsrv
```
Explications :

- PermitRootLogin no → interdit la connexion root
- PasswordAuthentication no → interdit les connexions par mot de passe
- PubkeyAuthentication yes → autorise uniquement les clés SSH
- AllowUsers adminsrv → limite l’accès SSH à l’utilisateur administrateur

## 2. Activation des mises à jour automatiques
```bash
sudo apt -y install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```
Objectif : Appliquer les correctifs de sécurité critiques

## 3. Mise en place du firewall UFW
Installation
```bash
sudo apt -y install ufw
```
Politique de filtrage par défaut
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Autorisation des services nécessaires
```bash
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

Services autorisés :
22/tcp → accès SSH administrateur
80/tcp → accès HTTP intranet
443/tcp → accès HTTPS futur

Activation du firewall
```bash
sudo ufw enable
sudo ufw status verbose
```

## 4. Protection contre les attaques brute-force (Fail2ban)
Installation
```bash
sudo apt -y install fail2ban
```

Activation du service
```bash
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
sudo systemctl status fail2ban --no-pager
```

Objectif :

- bloquer automatiquement les tentatives de connexion SSH répétées
- limiter les attaques par force brute
- Résultat final du hardening

Le serveur Debian 12 est désormais :

- accessible uniquement via SSH sécurisé par clé
- protégé contre les connexions root
- filtré par un firewall actif
- surveillé contre les attaques brute-force
- maintenu à jour automatiquement

Cette configuration constitue la base de sécurité minimale
avant toute mise en production de l’intranet.