# pfSense – Pare-feu et routage

Ce dossier décrit la mise en place du pare-feu **pfSense**, utilisé comme point central de sécurité et de routage de l’infrastructure virtualisée du laboratoire.

pfSense assure la séparation des flux réseau, la sortie Internet et le contrôle du trafic entre le réseau interne et l’extérieur.

---

## Rôle dans l’architecture globale

pfSense constitue la **passerelle principale** de l’infrastructure et représente la première ligne de défense du système d’information.

Il est positionné en frontal du réseau interne et centralise l’ensemble des flux entrants et sortants.

---

## Rôles principaux

- Pare-feu principal de l’infrastructure
- Routeur entre le réseau interne et Internet
- Passerelle par défaut des machines internes
- Point central de filtrage et de contrôle des flux réseau

---

## Fonctions mises en place

- Interface **WAN** pour l’accès Internet
- Interface **LAN** pour le réseau interne
- Règles de pare-feu appliquées sur le LAN
- NAT sortant pour l’accès Internet
- Configuration volontairement simple et lisible

Cette approche est adaptée à un **environnement de type PME** et à un **lab pédagogique**, tout en respectant les principes de base de sécurité réseau.

---

## Contenu du dossier

- `interfaces.md` : configuration des interfaces réseau
- `nat.md` : configuration de la traduction d’adresses (NAT)
- `firewall-rules.md` : règles de pare-feu appliquées
- `screenshots/` : captures de configuration pfSense
