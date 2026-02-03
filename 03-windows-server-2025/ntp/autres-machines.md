# Synchronisation NTP des autres machines du domaine

Ce document décrit la configuration de la synchronisation de l’heure
pour les machines du domaine **hors PDC Emulator**.

Dans un environnement Active Directory, seules certaines machines
nécessitent une configuration manuelle du service NTP.
Les autres utilisent automatiquement la hiérarchie du domaine.

---

## Contrôleurs de domaine secondaires

Les contrôleurs de domaine secondaires ne doivent **pas** être configurés
avec des serveurs NTP externes.

Ils se synchronisent automatiquement avec le contrôleur de domaine
détenteur du rôle **PDC Emulator** via la hiérarchie Active Directory.

### Configuration appliquée

Sur les contrôleurs de domaine secondaires (ex : `SVL-PS-DC-02`) :

```cmd
w32tm /config /syncfromflags:domhier /update
w32tm /resync
```
Cette configuration permet au serveur de récupérer l’heure
directement depuis le PDC Emulator (SRV-AD02).

Vérification
```cmd
w32tm /query /status
```
Résultat attendu
La source de temps est le domaine Active Directory

La source n’est pas Local CMOS Clock

Postes clients et serveurs membres
Les postes clients (ex : CL-TS-01) ainsi que les serveurs membres
ne nécessitent aucune configuration NTP manuelle.

Ils utilisent automatiquement la hiérarchie Active Directory
pour la synchronisation de l’heure.

Vérification
```cmd
w32tm /query /status
```
Résultat attendu
La source de temps correspond au domaine

Le contrôleur de domaine PDC Emulator est utilisé indirectement
