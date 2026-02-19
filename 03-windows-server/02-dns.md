# DNS Server

## Installation

- Rôle DNS installé via Server Manager

## Configuration

- Création zone directe : entreprise.local
- Ajout enregistrement A :
  - debian.entreprise.local → 192.168.11.2

## Tests

```bash
nslookup debian.entreprise.local
```
```bash
ping debian.entreprise.local
```