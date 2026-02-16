# 🧪 Tests & validation globale de l’infrastructure

## 🎯 Objectif

Vérifier que l’ensemble de l’infrastructure fonctionne correctement après :

- Installation d’**ESXi**  
- Configuration **réseau**  
- Migration des **machines virtuelles**  
- Intégration de **Veeam**  

Cette phase permet de valider :

- La **cohérence technique**  
- La **stabilité**  
- La **résilience**  
- La **capacité de reprise**  

---

## 🖥️ 1️⃣ Validation de l’hyperviseur ESXi

### Vérifications réalisées

- Accès **Web UI** opérationnel  
- **Version ESXi** confirmée  
- **Datastore** accessible  
- **vSwitch** actif  
- Ressources **CPU / RAM** correctement détectées  

### Résultat

👉 **Hyperviseur stable et fonctionnel.**

---

## 🌐 2️⃣ Validation du réseau interne

### Tests effectués

- Ping entre **DC1** et **DC2**  
- Ping **DC → pfSense**  
- Ping **Client → DC**  
- Ping **Client → Internet**  
- **Résolution DNS interne**  
- **Résolution DNS externe**  

### Résultat

- **Connectivité LAN** opérationnelle  
- **Passerelle** fonctionnelle  
- **DNS interne prioritaire**  
- Accès Internet **contrôlé par pfSense**  

---

## 🗄️ 3️⃣ Validation Active Directory

### Tests réalisés

- **Réplication AD** entre DC1 et DC2  
- **Authentification utilisateur**  
- Application des **GPO**  
- Attribution **DHCP** correcte  
- Résolution **DNS du domaine**  

### Résultat

👉 **Domaine fonctionnel et redondant.**

---

## 🌍 4️⃣ Validation du serveur applicatif (NGINX)

### Tests effectués

- Accès **intranet** depuis le client  
- Résolution **DNS vers le serveur APP**  
- Vérification des **ports 80 / 443**  
- Analyse des **logs**  

### Résultat

👉 **Service web interne accessible et stable.**

---

## 🔥 5️⃣ Validation pfSense

### Vérifications

- **NAT** opérationnel  
- **Règles firewall** actives  
- **Journal firewall** cohérent  
- Absence de **trafic non autorisé**  

### Résultat

👉 **Pare-feu fonctionnel et centralisé.**

---

## 💾 6️⃣ Validation Veeam Backup

### Tests réalisés

- **Job de sauvegarde complet**  
- **Snapshot VMware automatique**  
- Suppression du snapshot après sauvegarde  
- Vérification du **repository**  
- **Restauration d’un fichier unique**  
- **Restauration complète d’une VM**  
- **Simulation de PRA**  

### Résultat

- **Sauvegardes cohérentes**  
- **Restauration fonctionnelle**  
- Infrastructure **récupérable**  

---

## 🚨 7️⃣ Simulation d’incident

### Scénarios testés

- Extinction d’un **contrôleur de domaine**  
- **Restauration depuis sauvegarde**  
- Vérification de la **cohérence AD**  
- Redémarrage des **services**  

### Objectif

Valider la **capacité de reprise après incident**.

---

## 📊 8️⃣ Résumé de validation

| Composant   | Statut        |
|-------------|---------------|
| ESXi        | ✅ Stable      |
| Réseau      | ✅ Fonctionnel |
| AD          | ✅ Redondant   |
| DNS         | ✅ Opérationnel|
| DHCP        | ✅ Opérationnel|
| pfSense     | ✅ Actif       |
| Intranet    | ✅ Accessible  |
| Sauvegarde  | ✅ Validée     |
| Restauration| ✅ Testée      |

---

## 🧠 Analyse globale

L’infrastructure :

- Est **stable**  
- Est **segmentée**  
- Est **redondante**  
- Est **sauvegardée**  
- Peut être **restaurée**  

👉 Elle simule une **architecture PME réaliste**.

---

## 📌 Conclusion technique

La migration vers **ESXi** a permis :

- Une meilleure **isolation des ressources**  
- Une **gestion centralisée**  
- Une **compatibilité avec Veeam**  
- Une approche **production-like**  

### Ce lab démontre

- La **compréhension de la virtualisation**  
- La gestion d’un **Active Directory redondé**  
- La **configuration d’un pare-feu**  
- L’**intégration d’une solution de sauvegarde**  
- La **capacité de diagnostic**  
- La **simulation d’un PRA**  
