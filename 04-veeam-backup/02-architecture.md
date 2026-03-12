# 02 — Architecture de l'infrastructure

## Hyperviseur

**VMware ESXi** — héberge l'ensemble des machines virtuelles du lab.

---

## Machines virtuelles

| VM | Rôle |
|----|------|
| SVL-APP-01 | Serveur applicatif |
| SVL-PS-VEEAM-01 | Serveur de sauvegarde Veeam |
| SVL-PS-ADM-01 | Serveur d'administration |
| SVL-PS-FWL-01 | Pare-feu / Firewall |

---

## Stockage

| Datastore | Type | Capacité |
|-----------|------|----------|
| datastore1 | SSD — VMFS6 | 13,75 Go |
| DS-LOCAL-01 | SSD — VMFS6 | 221,5 Go |

---

## Réseau

| Groupe de ports | Usage |
|-----------------|-------|
| PG-LAN | Réseau interne |
| PG-WAN | Réseau externe |