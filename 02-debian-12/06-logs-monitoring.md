# Supervision et journalisation — Debian 12

## Contexte

Cette section décrit la mise en place des mécanismes de **journalisation**
et de **supervision locale** du serveur Debian 12 hébergeant l’intranet Nginx.

Objectifs :

- surveiller l’état des services système
- analyser les journaux en cas d’incident
- conserver un historique exploitable
- préparer l’intégration à une supervision centralisée

---

## 1. Consultation des journaux système (journalctl)

### Affichage des derniers événements système

```bash
journalctl -xe
```
### Journaux d’un service spécifique (exemple : Nginx)
```bash
journalctl -u nginx --no-pager
```
### Suivi en temps réel
```bash
journalctl -fu nginx
```
## 2. Journaux applicatifs Nginx
### Emplacement des logs
```bash
/var/log/nginx/access.log
/var/log/nginx/error.log
```
### Consultation des dernières lignes
```bash
tail -n 50 /var/log/nginx/access.log
tail -n 50 /var/log/nginx/error.log
```
Suivi en temps réel
```bash
tail -f /var/log/nginx/access.log
```
## 3. Rotation des logs (logrotate)
### Vérification de la configuration Nginx
```bash
cat /etc/logrotate.d/nginx
```

La rotation permet :
- d’éviter la saturation disque
- d’archiver automatiquement les journaux
- de conserver un historique limité

Test manuel de rotation
```bash
sudo logrotate -f /etc/logrotate.d/nginx
```
## 4. Vérification de l’état des services
Service Nginx
```bash
systemctl status nginx --no-pager
```
Service SSH
```bash
systemctl status ssh --no-pager
```
Liste des services actifs
```bash
systemctl list-units --type=service --state=running
```
## 5. Surveillance des ressources système
### Utilisation CPU et mémoire
```bash
top
```
ou :
```bash
htop
```
(installer si nécessaire)
```bash
sudo apt -y install htop
```
### Utilisation disque
```bash
df -h
```
Inodes
```bash
df -i
```
## 6. Tests de disponibilité du service web
### Test HTTP local
```bash
curl -I http://localhost
```
### Test via FQDN interne
```bash
curl -I http://intranet.entreprise.local
```

Résultat attendu :

HTTP/1.1 200 OK

Résultat

Le serveur dispose désormais :

- d’une journalisation système exploitable
- de logs applicatifs Nginx consultables
- d’une rotation automatique des journaux
- d’outils de surveillance des ressources
- de tests simples de disponibilité du service

Cette base constitue le socle de supervision locale
avant la mise en place d’une supervision centralisée
(Zabbix, Centreon, Prometheus, etc.).