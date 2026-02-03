# Configuration NTP du PDC Emulator (SRV-AD02)

## Objectif

Configurer le contrôleur de domaine principal (PDC Emulator) comme source de temps fiable pour l’ensemble du domaine.

---

## Prérequis

- Le serveur détient le rôle FSMO PDC Emulator
- Accès Internet fonctionnel
- Résolution DNS externe opérationnelle
- Synchronisation VMware Tools désactivée

---

## Étape 1 – Vérification du rôle FSMO

```bash
netdom query fsmo
```
Le serveur SRV-AD02 doit apparaître comme Contrôleur de domaine principal (PDC).

Étape 2 – Désactivation de la synchronisation VMware

Dans VMware Workstation :

VMware Tools
Désactiver Synchronize guest time with host
Cette option peut provoquer des dérives de temps et doit être désactivée sur les contrôleurs de domaine.

Étape 3 – Configuration NTP manuelle
```bash
w32tm /config /manualpeerlist:"0.fr.pool.ntp.org,0x8 1.fr.pool.ntp.org,0x8" /syncfromflags:manual /reliable:yes /update
```
Explication :
manualpeerlist : serveurs NTP externes
0x8 : client NTP fiable
syncfromflags:manual : source manuelle
reliable:yes : annonce le serveur comme source fiable AD

Étape 4 – Redémarrage du service de temps
```bash
net stop w32time
net start w32time
```
Étape 5 – Synchronisation et redécouverte
```bash
w32tm /resync /rediscover
```
Cette commande force la redécouverte des serveurs NTP configurés.

Étape 6 – Vérification
```bash
w32tm /query /configuration
```

Résultat attendu :
Type : NTP
NtpServer : 0.fr.pool.ntp.org,0x8 1.fr.pool.ntp.org,0x8
AnnounceFlags : 5


---

