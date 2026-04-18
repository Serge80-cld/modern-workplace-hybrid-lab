\# Modern Workplace Hybrid Lab – Architecture complète



\##  Objectif

Ce projet démontre la mise en place d’un environnement \*\*Modern Workplace hybride\*\* complet, incluant :



\- Identité hybride (AD On-Prem + Entra ID)

\- Hybrid Azure AD Join

\- Intune MDM \& Configuration Profiles

\- Windows Autopilot (User-driven, Self-deploying)

\- Packaging Win32 (.intunewin)

\- Security Baselines \& Compliance

\- Zero Trust (Conditional Access, Identity Protection)

\- Microsoft Defender for Endpoint (EDR, TVM, ASR)

\- Automatisation \& standardisation du poste de travail



Ce lab reflète les bonnes pratiques Microsoft pour les environnements d’entreprise.



\---



\#  Architecture globale



L’environnement repose sur :



\- \*\*AD On-Prem\*\* pour l’identité locale  

\- \*\*Entra Connect\*\* pour la synchronisation  

\- \*\*Entra ID\*\* comme autorité d’identité cloud  

\- \*\*Hybrid Azure AD Join\*\* pour les appareils  

\- \*\*Intune\*\* pour la gestion du poste de travail  

\- \*\*Autopilot\*\* pour le déploiement automatisé  

\- \*\*MDE\*\* pour la sécurité avancée  

\- \*\*Zero Trust\*\* comme modèle de sécurité global  



Diagrammes disponibles dans :  

 `docs/diagrams/`



\---



\#  Documentation



La documentation complète est disponible dans :



```

docs/

├── architecture-overview.md

├── runbook.md

├── portfolio-summary.md

└── diagrams/

```



\---



\#  Sécurité \& Zero Trust



Implémentation complète :

\- Conditional Access (Require MFA, Require compliant device)

\- Identity Protection (User Risk, Sign-in Risk)

\- Microsoft Defender for Endpoint (EDR, TVM, ASR)

\- Hardening Windows 10/11

\- BitLocker XTS-AES 256

\- Security Baselines



\---



\#  Déploiement \& Automatisation



\- Windows Autopilot (end-to-end)

\- ESP (Enrollment Status Page)

\- Win32 Packaging (.intunewin)

\- Scripts PowerShell IME

\- Compliance Policies

\- Configuration Profiles



\---



\#  Objectifs pédagogiques



Ce projet démontre :

\- Une architecture Modern Workplace complète

\- Une approche cloud-first sécurisée

\- Une automatisation du cycle de vie du poste de travail

\- Une implémentation Zero Trust opérationnelle

\- Une expertise Intune + Autopilot + MDE



\---



\#  Auteur



\*\*Serge — Cloud Engineer / Cloud Architect Modern Workplace\*\*  

Spécialisé en environnements hybrides, Intune, Autopilot, Zero Trust et sécurité Microsoft 365.



