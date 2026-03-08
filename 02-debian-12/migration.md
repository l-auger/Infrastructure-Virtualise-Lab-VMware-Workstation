🖥️ SVL-PS-LIN-01 – Serveur Intranet
🎯 Objectif
Cette machine virtuelle héberge le service intranet de l’entreprise et permet l’accès interne aux ressources et informations partagées.

🖥 Informations VM
- Hyperviseur : VMware ESXi 8.0
- Stockage : DS-LOCAL-01
- Nom VM : SVL-PS-LIN-01
- Accès : intranet.entreprise.local (DNS IPv4)
- IP : 192.168.11.70
- Masque : 255.255.255.0
- Passerelle : 192.168.11.1
- DNS : 192.168.11.2

🔧 Actions réalisées
- Migration de la VM depuis VMware Workstation vers ESXi.
![Import-Vers-ESXi](screenshots/01-Migration-DEBIAN-APP.png)
- Import sur DS-LOCAL-01 et démarrage de la VM.
![Ouverture-Vers-ESXi](screenshots/02-Migration-FAIT.png)
- Ajout d’un enregistrement DNS A pointant intranet.entreprise.local vers l’IP de la VM.
![MAJ-DNS-intranet](screenshots/03-DNS-MAJ-INTRANET.png)
- Vérification de l’accès au service via le nom DNS.
![Validation-Migration](screenshots/04-validation-migration.png)
🧪 Validation globale
- Résolution DNS par nom fonctionnelle (intranet.entreprise.local → 192.168.11.10)

- Page d’accueil de l’intranet accessible depuis le réseau interne

- VM démarrée et service intranet opérationnel

- Captures d’écran ajoutées pour traçabilité (import, VM en fonctionnement, enregistrement DNS, accès web)

