# Filtrage réseau avec pfSense

La sécurité réseau repose principalement sur le pare-feu pfSense, positionné en frontal de l’infrastructure.

---

## Principe de filtrage

- Filtrage appliqué sur l’interface LAN
- Autorisation explicite des flux sortants
- Aucun flux entrant autorisé depuis Internet
- NAT automatique pour l’accès Internet

---

## Choix de conception

Les règles de filtrage ont été volontairement limitées afin de :
- faciliter la compréhension
- éviter les erreurs de configuration
- garantir la stabilité du lab

Cette approche correspond à un environnement de type PME sans exposition publique.
