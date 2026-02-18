# Bonnes pratiques de sécurité

Les bonnes pratiques suivantes ont été appliquées dans l’infrastructure.

---

## Systèmes

- Utilisation d’adresses IP fixes pour les serveurs
- Mise à jour des systèmes
- Rôles clairement séparés
- Services inutiles non installés

---

## Active Directory

- Deux contrôleurs de domaine (redondance)
- DNS intégré à Active Directory
- DHCP sécurisé et centralisé
- GPO utilisées pour appliquer des règles communes

## Postes clients

Les postes clients intégrés au domaine sont volontairement restreints via des stratégies de groupe (GPO).

### Restrictions appliquées

- Accès aux paramètres système bloqué pour les utilisateurs standards
- Empêchement des modifications réseau locales
- Réduction des risques de mauvaise manipulation
- Renforcement de la sécurité côté poste utilisateur

### Objectif

Ces restrictions permettent :
- de conserver un environnement stable
- de centraliser l’administration via Active Directory
- de limiter les droits utilisateurs conformément aux bonnes pratiques PME

---

## Réseau

- Pare-feu en frontal (pfSense)
- NAT sortant uniquement
- Aucune ouverture entrante non justifiée
- Règles simples et lisibles
