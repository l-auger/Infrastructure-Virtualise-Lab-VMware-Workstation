# Accès distant sécurisé — SSH Debian 12

## Objectif

Mettre en place un **accès distant sécurisé** au serveur Debian 12
hébergeant l’intranet Nginx dans le réseau entreprise.

Cette configuration vise à :

- interdire l’accès direct au compte **root**
- utiliser un **compte administrateur dédié**
- sécuriser l’authentification par **clé SSH**
- désactiver l’authentification par **mot de passe**
- respecter les **bonnes pratiques d’administration système en entreprise**

---

# 1. Installation du service SSH

## Installation du serveur OpenSSH

```bash
sudo apt update
sudo apt -y install openssh-server
```