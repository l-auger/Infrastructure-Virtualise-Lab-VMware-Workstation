# Rôles – DC1

Le serveur **DC1** est le contrôleur de domaine principal du domaine `entreprise.local`.
Il héberge les services essentiels de l’infrastructure Active Directory.

---

## Active Directory (AD DS)

- Centralise les comptes utilisateurs, ordinateurs et groupes
- Assure l’authentification au domaine
- Réplication automatique avec DC2 pour la redondance

---

## DNS

- DNS intégré à Active Directory
- Zones DNS répliquées automatiquement vers DC2
- Permet la résolution des noms et le fonctionnement des services AD  
- Redondance assurée par la présence de plusieurs serveurs DNS (pas de HA actif/passif)

---

## DHCP

- Attribution automatique des adresses IP aux clients
- Distribution des options réseau (passerelle, DNS, domaine)
- Configuration en haute disponibilité avec DC2
- Mode : **équilibrage de charge (50/50)**

---

## Résumé

DC1 assure :
- l’authentification du domaine
- la résolution DNS
- la distribution des adresses IP

La redondance avec DC2 garantit la continuité des services critiques.
