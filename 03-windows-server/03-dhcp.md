# DHCP Server

## Installation

- Rôle DHCP installé
- Autorisation dans l’AD (si nécessaire)

## Configuration Scope

- Plage IP : 192.168.11.50 → 192.168.11.150
- Exclusions : 192.168.11.1-20
- Passerelle : 192.168.11.1
- DNS : 192.168.11.2
- Domaine : entreprise.local

## Tests

Sur client :

```bash
ipconfig /release
ipconfig /renew
```
Vérification IP obtenue.
