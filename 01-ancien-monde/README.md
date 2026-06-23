# 01 – Ancien Monde (On-Prem)

Ce dossier présente les fondations de l’environnement traditionnel On-Premise, encore présent dans la majorité des entreprises.  
Il constitue le socle historique du poste de travail avant la transition vers le Modern Workplace cloud.

---

## 🔹 1. Active Directory (AD DS)

L’élément central de l’identité On-Prem :

- Référentiel d’identité local
- Authentification **Kerberos / NTLM**
- Structure **OU** pour organiser les objets
- Gestion des comptes, groupes, permissions
- Dépend fortement du **DNS interne**

 Sans AD, aucune authentification locale, aucune GPO, aucun Domain Join.

---

## 🔹 2. DNS (Domain Name System)

Le service critique souvent sous-estimé :

- Résolution interne indispensable
- Zones AD-intégrées
- Dépendance directe avec Kerberos
- Nécessaire pour MECM, GPO, Hybrid Join

 Si DNS tombe, tout tombe.

---

## 🔹 3. DHCP

Service d’attribution d’adresses IP :

- Scopes, réservations
- Options 066/067 pour **PXE**
- Indispensable pour OSD MECM

👉 Le DHCP est la porte d’entrée du poste sur le réseau.

---

## 🔹 4. GPO (Group Policy Objects)

Le mécanisme historique de configuration du poste :

- Paramètres Windows
- Sécurité
- Scripts de démarrage
- Mappage lecteurs, imprimantes
- Hardening

👉 Les GPO sont remplacées progressivement par **Intune Settings Catalog**.

---

## 🔹 5. MECM / SCCM

La solution de gestion On-Prem la plus répandue :

- **OSD (Operating System Deployment)**  
  → Task Sequences, Boot Images, PXE, WIM
- **Packaging** (Applications, Packages)
- **Collections** (ciblage dynamique)
- **SUP / WSUS** (mises à jour)
- **Inventaire matériel / logiciel**

 MECM reste présent dans 80 % des grands comptes.

---

## 🔹 6. Domain Join

Le modèle d’appartenance historique :

- Appareil joint au domaine AD
- Authentification Kerberos
- Dépendance réseau interne
- Dépendance aux contrôleurs de domaine

 Ce modèle est remplacé par **Entra Join** dans le cloud.

---

## 🔹 7. Schéma ASCII – Architecture On-Prem

----------------------+
|   Active Directory   |
|  (Identité locale)   |
+----------+-----------+
|
| Kerberos / NTLM
|
+------------------+------------------+
|                                     |
+-------+-------+                     +--------+--------+
|     DNS       |                     |       GPO       |
| (Résolution)  |                     | (Config poste)  |
+---------------+                     +------------------+
|
|
+-------+-------+
|     MECM      |
|  (OSD, Apps)  |
+---------------+
|
|
+-------+-------+
|     DHCP      |
|   (PXE Boot)  |
+---------------+

---

## 🔹 8. Ce qu’il faut retenir absolument

- AD = identité locale  
- DNS = cœur du fonctionnement  
- DHCP = réseau + PXE  
- GPO = configuration On-Prem  
- MECM = OSD + packaging + collections  
- Domain Join = modèle historique  
- Tout dépend du réseau interne et des serveurs

 **C’est le monde d’hier, mais encore présent partout.**

---

## 🔹 9. Lien avec la transition

Ce dossier prépare la compréhension de :

- Hybrid Join  
- Cloud Attach  
- Migration MECM → Intune  
- Remplacement OSD → Autopilot  
- Zero Trust  
- Modern Auth

 **Sans comprendre l’ancien monde, on ne peut pas réussir la transition vers le nouveau.**

