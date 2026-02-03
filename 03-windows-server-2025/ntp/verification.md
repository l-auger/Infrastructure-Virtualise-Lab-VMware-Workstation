# Vérification et validation de la synchronisation NTP

Ce document décrit les commandes de vérification permettant de s’assurer
du bon fonctionnement de la synchronisation de l’heure dans
l’environnement Active Directory.

Il permet également d’identifier rapidement les causes courantes
de désynchronisation.

---

## Vérification de la configuration NTP

Sur le contrôleur de domaine principal (PDC Emulator) :

```cmd
w32tm /query /configuration
```
Résultat attendu
Type : NTP
AnnounceFlags : 5
NtpServer configuré avec des serveurs NTP externes

Ces paramètres confirment que le serveur fonctionne comme
source de temps fiable pour le domaine.

Vérification de la source de temps active
Sur le PDC Emulator, les contrôleurs de domaine secondaires
ou les postes clients :

```cmd
w32tm /query /status
```
Points de contrôle
La source de temps n’est pas Local CMOS Clock
Le Stratum est cohérent (généralement entre 2 et 5)

La source correspond :
aux serveurs NTP externes pour le PDC Emulator
au domaine Active Directory pour les autres machines

Test de connectivité vers les serveurs NTP
Sur le PDC Emulator :
w32tm /stripchart /computer:0.fr.pool.ntp.org /samples:5 /dataonly
Interprétation
Des réponses indiquent que le trafic NTP (UDP 123) est fonctionnel

Un timeout indique généralement :
un blocage firewall
un problème de résolution DNS
une absence d’accès Internet

Problèmes rencontrés dans le laboratoire :

Lors de la mise en place du service NTP, un écart de temps important
était présent sur le contrôleur de domaine principal.
Dans ce cas, le service Windows Time refuse la synchronisation automatique.
Une correction manuelle initiale de l’heure a été nécessaire afin de
ramener l’écart à un seuil acceptable.
Une fois l’heure corrigée, la synchronisation NTP fonctionne normalement.

Bonnes pratiques

Centraliser la synchronisation NTP sur le PDC Emulator
Ne jamais configurer de serveurs NTP externes sur les DC secondaires
Ne pas forcer la synchronisation NTP sur les postes clients
Désactiver la synchronisation de l’heure via VMware Tools
Vérifier régulièrement la source de temps avec w32tm
Cette approche garantit une synchronisation de l’heure stable,
fiable et conforme aux bonnes pratiques Microsoft.
---