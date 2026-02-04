# Limites et choix techniques

Cette section présente les choix techniques réalisés
ainsi que les limites liées à un environnement de lab local.

---

## Choix techniques

Les choix suivants ont été faits volontairement :

- Utilisation d’un **LAN Segment VMware**
- Réseau interne totalement isolé
- Haute disponibilité assurée uniquement par les services (DNS, DHCP)

Ces choix favorisent :
- La compréhension des mécanismes réseau
- La stabilité du lab
- Une mise en œuvre réaliste sur poste personnel

---

## Limites identifiées

Le lab présente certaines limites :

- Pas de redondance matérielle
- Dépendance aux ressources de la machine hôte
- Pas de routage complexe entre plusieurs segments

Ces limites sont acceptables dans un contexte pédagogique.

---

## Objectif pédagogique

L’objectif principal est :

- Comprendre le fonctionnement des services réseau
- Savoir les déployer proprement
- Être capable de documenter une infrastructure claire

La complexité est volontairement progressive.
