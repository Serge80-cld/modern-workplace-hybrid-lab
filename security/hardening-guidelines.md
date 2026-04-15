\# Windows \& Modern Workplace – Hardening Guidelines



\## 🎯 Objectif

Fournir un ensemble de bonnes pratiques de \*\*hardening\*\* pour sécuriser un environnement Modern Workplace hybride :

\- Windows 10/11  

\- Intune  

\- Entra ID  

\- MDE  

\- Applications  

\- Réseau  



Ces recommandations complètent les baselines, les policies Intune et le modèle Zero Trust.



\---



\# 1. Hardening Windows 10/11



\## 1.1 Sécurité du système

\- Activer \*\*Secure Boot\*\*

\- Activer \*\*TPM 2.0\*\*

\- Activer \*\*Virtualization-Based Security (VBS)\*\*

\- Activer \*\*Credential Guard\*\*

\- Activer \*\*Memory Integrity\*\*



\## 1.2 BitLocker

\- Chiffrement XTS-AES 256

\- Sauvegarde automatique des clés dans Entra ID

\- Interdiction de suspendre BitLocker sans justification



\## 1.3 Windows Update

\- Windows Update for Business

\- Deadlines configurées

\- Redémarrages contrôlés



\---



\# 2. Hardening Microsoft Defender (AV + EDR)



\## 2.1 Antivirus

\- Real-time protection : Enabled

\- Cloud-delivered protection : Enabled

\- Automatic sample submission : Enabled



\## 2.2 Attack Surface Reduction (ASR)

Règles recommandées :

\- Block Office from creating child processes

\- Block credential stealing

\- Block executable content from email/webmail

\- Block untrusted USB devices



\## 2.3 EDR

\- EDR in block mode : Enabled

\- Tamper Protection : Enabled



\---



\# 3. Hardening via Intune



\## 3.1 Compliance Policies

\- Require BitLocker

\- Require Secure Boot

\- Require TPM

\- Require password

\- Block rooted/jailbroken devices



\## 3.2 Security Baselines

\- Windows 10/11 Baseline

\- Defender Baseline

\- Edge Baseline



\## 3.3 Configuration Profiles

\- Firewall activé sur les 3 profils

\- SmartScreen activé

\- OneDrive KFM activé

\- Désactivation des protocoles hérités (SMBv1, TLS 1.0/1.1)



\---



\# 4. Hardening Entra ID (Azure AD)



\## 4.1 MFA obligatoire

\- Pour tous les utilisateurs

\- Authenticator App recommandée



\## 4.2 Passwordless

\- Windows Hello for Business

\- FIDO2 Security Keys



\## 4.3 Conditional Access

\- Block legacy authentication

\- Require compliant device

\- Require MFA

\- Require passwordless for admins



\## 4.4 Identity Protection

\- User Risk Policy

\- Sign-in Risk Policy



\---



\# 5. Hardening des comptes \& rôles



\## 5.1 Comptes break-glass

\- 2 comptes maximum

\- Pas de MFA

\- Pas de CA

\- Mot de passe très long

\- Monitoring renforcé



\## 5.2 Comptes administrateurs

\- PIM (Privileged Identity Management)

\- JIT (Just-In-Time)

\- JEA (Just Enough Access)

\- Pas d’administrateurs locaux permanents



\---



\# 6. Hardening réseau



\## 6.1 VPN moderne

\- Always On VPN

\- Tunnel device-based

\- Certificats ou Entra ID



\## 6.2 Filtrage DNS

\- Microsoft Defender for DNS

\- Bloquer les domaines malveillants



\## 6.3 Segmentation

\- Séparer les environnements sensibles

\- Limiter les mouvements latéraux



\---



\# 7. Hardening des applications



\## 7.1 Office

\- Macros signées uniquement

\- Protected View activé

\- Safe Links / Safe Attachments



\## 7.2 Edge

\- SmartScreen activé

\- Password Manager activé

\- Extensions contrôlées



\## 7.3 Win32 Apps

\- Packaging propre

\- Détection fiable

\- Désinstallation automatisée



\---



\# 8. Résultat attendu



Une fois le hardening appliqué :

\- Le poste de travail est sécurisé de bout en bout  

\- Les identités sont protégées  

\- Les appareils sont conformes et contrôlés  

\- Les attaques latérales sont limitées  

\- Le Zero Trust devient opérationnel et robuste  

\- L’environnement est aligné avec les standards Microsoft et les bonnes pratiques du marché  



Ces guidelines complètent l’ensemble de ton architecture Modern Workplace hybride.



