Configuration réseau — Intégration au LAN et au domaine
Objectif

Configurer la machine Debian 12 pour :

- être accessible sur le réseau local de l’entreprise
- disposer d’une connectivité LAN et Internet
- être intégrée au domaine interne
- permettre l’accès à l’intranet Nginx depuis les postes clients

Cette étape valide l’utilisation du serveur dans une infrastructure réelle d’entreprise.

1. Détection de l’interface réseau
Commande utilisée :
ip a
Résultat observé :
Interface : ens33
Adresse IP : 192.168.11.51/24
Attribution : DHCP actif
État : UP

2. Vérification du routage
ip r
Résultat :
default via 192.168.11.1 dev ens33
192.168.11.0/24 dev ens33 proto kernel scope link src 192.168.11.51
➡️ La machine est correctement reliée au réseau local entreprise.

3. Tests de connectivité
Test passerelle LAN
ping -c 4 192.168.11.1
Résultat :
0 % de perte
latence < 1 ms
➡️ Connectivité LAN valide

Test accès Internet
ping -c 4 google.com
Résultat :
résolution DNS fonctionnelle
paquets reçus sans perte
➡️ Accès Internet opérationnel

4. Intégration au domaine d’entreprise
La machine a été configurée pour rejoindre le domaine interne, permettant :
l’authentification via les comptes du domaine
l’intégration dans l’infrastructure système
la gestion centralisée des accès
Cette étape prépare l’exploitation du serveur dans un contexte professionnel réel.

5. Validation de l’accès au service intranet
Depuis la machine Debian :
curl -I http://localhost
Depuis un poste du réseau :
http://192.168.11.51
➡️ Le serveur web Nginx intranet est accessible depuis le LAN.

Résultat final
La machine Debian 12 est désormais :
connectée au LAN entreprise
intégrée au domaine interne
accessible depuis les postes clients
prête pour l’hébergement de l’intranet Nginx