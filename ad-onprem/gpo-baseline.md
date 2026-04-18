\# GPO Baseline – Modern Workplace Hybride



\## Objectif

Définir une baseline GPO propre avant migration vers Intune.



\---



\## 1. GPO de base (Baseline)



\### Password Policy

\- Minimum length : 12

\- Complexity : Enabled

\- Lockout threshold : 5



\### Audit Policy

\- Logon events

\- Account management

\- Policy changes



\### Windows Defender

\- Real-time protection

\- Cloud-delivered protection

\- Sample submission



\### Firewall

\- Domain profile : Enabled

\- Private profile : Enabled

\- Public profile : Enabled



\---



\## 2. GPO à migrer vers Intune



\### Paramètres compatibles

\- Windows Update

\- Defender

\- Firewall

\- BitLocker

\- Security Baseline

\- Password policy



\### Paramètres non compatibles

\- Scripts de logon/logoff

\- Paramètres legacy (IE, SMBv1…)

\- Group Policy Preferences (GPP)



\---



\## 3. Export des GPO



```powershell

Backup-GPO -All -Path "C:\\GPO-Backup"

```



\---



\## 4. Objectif final

Migrer progressivement les GPO vers :

\- Intune Configuration Profiles

\- Intune Security Baselines

\- Scripts de remédiation



