# 🧾 Plan d’adressage

## Réseaux 
- LAN : 192.168.11.0/24 (passerelle: 192.168.11.1)
- WAN : 192.168.56.0/24

## Équipements principaux
- pfSense LAN : 192.168.11.1/24
- pfSense WAN : 192.168.56.22/24
- DC1 : 192.168.11.2 
- DC2 : 192.168.11.3
- Win11 : DHCP

## DNS/DHCP
- DNS primaire : DC1
- DNS secondaire : DC2
- DHCP : failover DC1/DC2
