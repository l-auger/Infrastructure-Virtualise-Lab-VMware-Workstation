# 01 — Objectif de sauvegarde avec Veeam

## Contexte

L'infrastructure tourne sur un hyperviseur **VMware ESXi**. Pour protéger les machines virtuelles, on utilise **Veeam Backup & Replication** comme solution de sauvegarde.

---

## Pourquoi Veeam ?

Veeam s'intègre directement avec ESXi sans avoir besoin d'installer un agent dans chaque VM. Il utilise les snapshots VMware pour sauvegarder les machines **sans les éteindre**.

---

## Objectifs

- Sauvegarder les VMs hébergées sur ESXi
- Planifier des jobs de backup automatiques
- Être capable de restaurer une VM complète en cas d'incident
- Tester une restauration granulaire (fichier unique)

---

## Ce que ce lab met en pratique

- Installer et configurer Veeam Backup & Replication
- Connecter Veeam à l'hôte ESXi
- Créer un job de sauvegarde
- Réaliser une restauration complète