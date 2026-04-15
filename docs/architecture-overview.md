\# Modern Workplace Hybrid Lab – Architecture Overview



\## 🎯 Objectif

Présenter l’architecture globale du lab Modern Workplace hybride, incluant :

\- Identité (AD On-Prem + Entra ID)

\- Hybrid Join

\- Intune MDM

\- Autopilot

\- Sécurité Zero Trust

\- Microsoft Defender for Endpoint

\- Packaging \& automatisation



Ce document sert de \*\*vue d’ensemble\*\* pour les recruteurs, les architectes et les équipes techniques.



\---



\# 1. Architecture globale



Le lab repose sur une architecture hybride moderne :



\- \*\*AD On-Prem\*\* pour l’identité locale  

\- \*\*Entra Connect\*\* pour la synchronisation  

\- \*\*Entra ID\*\* comme autorité d’identité principale  

\- \*\*Hybrid Azure AD Join\*\* pour les appareils  

\- \*\*Intune\*\* pour la gestion du poste de travail  

\- \*\*Autopilot\*\* pour le déploiement automatisé  

\- \*\*MDE\*\* pour la sécurité avancée  

\- \*\*Conditional Access\*\* pour le Zero Trust  



L’objectif : un environnement \*\*cloud-first\*\*, sécurisé, automatisé et standardisé.



\---



\# 2. Flux d’identité



\## 2.1 AD On-Prem → Entra ID

\- Synchronisation via Entra Connect  

\- Password Hash Sync  

\- Device Writeback (si nécessaire)  



\## 2.2 Authentification

\- MFA obligatoire  

\- Passwordless (Windows Hello / Authenticator)  

\- Conditional Access basé sur le risque  



\---



\# 3. Flux appareil (Device Lifecycle)



\## 3.1 Enregistrement Autopilot

\- Hardware Hash → Autopilot  

\- Group Tags → Groupes dynamiques  

\- Assignation automatique du Deployment Profile  



\## 3.2 Déploiement Autopilot

\- User-driven ou Self-deploying  

\- ESP (Enrollment Status Page)  

\- Installation des apps Required  

\- Application des baselines et policies  



\## 3.3 Gestion Intune

\- Compliance Policies  

\- Configuration Profiles  

\- Security Baselines  

\- Win32 Apps (packaging .intunewin)  

\- Scripts PowerShell IME  



\---



\# 4. Sécurité Zero Trust



Le modèle Zero Trust repose sur :



\### Identité

\- MFA obligatoire  

\- Identity Protection  

\- CA : Require compliant device  

\- CA : Block legacy authentication  



\### Appareils

\- Compliance obligatoire  

\- BitLocker XTS-AES 256  

\- Firewall activé  

\- SmartScreen activé  

\- ASR rules en mode Block  



\### Applications

\- SSO Entra ID  

\- App Protection Policies (MAM)  



\### Données

\- OneDrive KFM  

\- Sensitivity Labels  

\- Chiffrement automatique  



\---



\# 5. Microsoft Defender for Endpoint (MDE)



MDE apporte :

\- EDR (Endpoint Detection \& Response)  

\- TVM (Threat \& Vulnerability Management)  

\- ASR (Attack Surface Reduction)  

\- Device Risk Score  

\- Remédiation automatique (AIR)  



Intégration avec Conditional Access :

```

If Device Risk = Medium or High → Block access

```



\---



\# 6. Packaging \& Automatisation



\## 6.1 Win32 Apps

\- Packaging via IntuneWinAppUtil  

\- Scripts install/uninstall  

\- Détection via registre ou fichier  

\- Assignation Required / Available  



\## 6.2 Scripts PowerShell IME

\- Pré-requis  

\- Nettoyage  

\- Configuration avancée  



\---



\# 7. Diagrammes (à ajouter dans /docs/diagrams)



Diagrammes recommandés :

\- Architecture globale Modern Workplace  

\- Flux Hybrid Join  

\- Flux Autopilot  

\- Flux Zero Trust + Conditional Access  

\- Flux MDE + Risk-based Access  



Ces diagrammes renforcent la compréhension de l’architecture.



\---



\# 8. Résultat attendu



Ce lab démontre :

\- Une maîtrise complète du Modern Workplace hybride  

\- Une architecture cloud-first sécurisée  

\- Une automatisation du cycle de vie du poste de travail  

\- Une implémentation Zero Trust opérationnelle  

\- Une expertise Intune + Autopilot + MDE  



Ce document sert de \*\*vue d’ensemble professionnelle\*\* pour ton portfolio, LinkedIn et tes entretiens.



