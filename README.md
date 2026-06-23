# Modern Workplace – Ancien Monde → Nouveau Monde → La Transition

## 1. L’Ancien Monde (On-Prem)

L’environnement historique des entreprises, basé sur :

- **Active Directory** (identité locale)
- **Kerberos / NTLM**
- **GPO** (configuration du poste)
- **MECM / SCCM** (OSD, packaging, collections, WSUS/SUP)
- **Windows Server** (AD, DNS, DHCP, File Servers)
- **PXE / Task Sequences**
- **Scripts locaux**

 **Modèle centralisé, dépendant du réseau interne, basé sur des serveurs.**

---

## 2. Le Nouveau Monde (Cloud Modern Workplace)

Le modèle moderne, cloud-native, basé sur l’identité :

- **Entra ID** (identité cloud)
- **Conditional Access / MFA / Identity Protection**
- **Intune** (Settings Catalog, Compliance, Security Baselines)
- **Windows Autopilot** (remplace OSD)
- **Windows Update for Business** (remplace WSUS)
- **Defender for Endpoint** (EDR, TVM)
- **PowerShell + Microsoft Graph** (automatisation avancée)
- **Zero Trust**

 **Modèle distribué, indépendant du réseau interne, basé sur l’identité.**

---

## 3. Tableau de référence – Ancien Monde vs Nouveau Monde

| Concept | Ancien Monde | Nouveau Monde |
|--------|---------------|----------------|
| **Identité** | Active Directory | Entra ID |
| **Auth** | Kerberos / NTLM | OAuth2 / Modern Auth |
| **Config poste** | GPO | Intune (Settings Catalog) |
| **Provisioning** | OSD (MECM) | Autopilot |
| **Mises à jour** | WSUS / SUP | Windows Update for Business |
| **Sécurité** | Antivirus + GPO | Defender + Conditional Access |
| **Automatisation** | Scripts locaux | PowerShell + Graph API |
| **Infra** | Serveurs | Cloud 100 % |
| **Join** | Domain Join | Entra Join / Hybrid Join |
| **Transition** | MECM | Cloud Attach / Co-Management |

---

## 4. La Transition (mon expertise clé)

Ce laboratoire reproduit les scénarios de transformation Modern Workplace :

- Environnement hybride **AD + Entra ID**
- **Hybrid Join**
- **Cloud Attach / Co-Management**
- Migration progressive **MECM → Intune**
- Remplacement **OSD par Autopilot**
- Packaging Win32 industrialisé (détection, dépendances, versioning)
- Automatisations **PowerShell + Graph**
- Remédiations automatiques (Proactive Remediations)
- Dashboards **Power BI** (conformité, sécurité, inventaire)

 **Objectif : démontrer la maîtrise complète de la transition entre l’ancien monde et le nouveau monde.**

---
\ Modern Workplace Hybrid Lab – Architecture complète
\  Objectif

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



\  Architecture globale



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



\ Sécurité \& Zero Trust



Implémentation complète :

\- Conditional Access (Require MFA, Require compliant device)

\- Identity Protection (User Risk, Sign-in Risk)

\- Microsoft Defender for Endpoint (EDR, TVM, ASR)

\- Hardening Windows 10/11

\- BitLocker XTS-AES 256

\- Security Baselines



\---



\  Déploiement \& Automatisation



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



