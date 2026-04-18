\# Zero Trust – Overview



\## Objectif

Présenter les principes du modèle Zero Trust et son application dans un environnement Modern Workplace hybride (AD On-Prem + Entra ID + Intune + MDE).



Zero Trust repose sur un principe simple :

> \*\*Ne jamais faire confiance, toujours vérifier.\*\*



Ce modèle remplace l’approche traditionnelle basée sur le périmètre réseau.



\---



\# 1. Les 3 piliers du Zero Trust



\## 1.1 Verify Explicitly

Toujours vérifier l’identité, l’appareil, l’emplacement, le risque et la conformité avant d’autoriser l’accès.



Inclut :

\- MFA

\- Device Compliance

\- Identity Protection

\- Risk-based access



\---



\## 1.2 Least Privilege Access

Limiter les permissions au strict nécessaire.



Inclut :

\- RBAC

\- Just-In-Time (JIT)

\- Just-Enough-Access (JEA)

\- Privileged Identity Management (PIM)



\---



\## 1.3 Assume Breach

Considérer que l’environnement peut être compromis à tout moment.



Inclut :

\- Segmentation

\- Monitoring continu

\- MDE (Microsoft Defender for Endpoint)

\- Audit et logs centralisés



\---



\# 2. Architecture Zero Trust Microsoft



Microsoft structure Zero Trust autour de \*\*6 piliers\*\* :



1\. \*\*Identités\*\*  

&#x20;  Utilisateurs, comptes, rôles, MFA, Identity Protection



2\. \*\*Appareils\*\*  

&#x20;  Compliance, Intune, MDE, baselines, patching



3\. \*\*Applications\*\*  

&#x20;  SSO, Conditional Access, App Proxy, OAuth



4\. \*\*Données\*\*  

&#x20;  DLP, Sensitivity Labels, chiffrement



5\. \*\*Infrastructure\*\*  

&#x20;  Serveurs, workloads, accès privilégiés



6\. \*\*Réseau\*\*  

&#x20;  VPN, segmentation, accès conditionnel réseau



\---



\# 3. Zero Trust dans un environnement Modern Workplace hybride



\## 3.1 Identités

\- MFA obligatoire  

\- Passwordless (Windows Hello, Authenticator)  

\- Conditional Access basé sur le risque  

\- Identity Protection activé  



\## 3.2 Appareils

\- Hybrid Azure AD Join  

\- Intune MDM  

\- Compliance Policies  

\- Security Baselines  

\- MDE activé  



\## 3.3 Applications

\- SSO via Entra ID  

\- CA : “Require compliant device”  

\- App Protection Policies (MAM)  



\## 3.4 Données

\- OneDrive KFM  

\- Sensitivity Labels  

\- Chiffrement automatique (BitLocker)  



\---



\# 4. Zero Trust + Conditional Access



Le moteur principal du Zero Trust côté Microsoft est \*\*Conditional Access\*\*.



Exemples de règles essentielles :



\- Require MFA  

\- Require compliant device  

\- Block legacy authentication  

\- Require trusted location (optionnel)  

\- Require risk level = low  



\---



\# 5. Zero Trust + MDE (Microsoft Defender for Endpoint)



MDE renforce Zero Trust via :

\- Risk-based Conditional Access  

\- Device Risk Score  

\- Threat \& Vulnerability Management  

\- Isolation automatique  

\- Remédiation automatisée  



\---



\# 6. Zero Trust + Intune



Intune applique :

\- Compliance Policies  

\- Security Baselines  

\- ASR (Attack Surface Reduction)  

\- BitLocker  

\- Firewall  

\- Windows Update for Business  



Un appareil non conforme = accès bloqué via CA.



\---



\# 7. Résultat attendu



Une fois Zero Trust appliqué :

\- L’accès dépend de l’identité \*\*et\*\* de l’état du device  

\- Les comptes à privilèges sont protégés  

\- Les appareils sont sécurisés et conformes  

\- Les données sont protégées même hors du réseau  

\- Les attaques latérales sont limitées  

\- L’environnement devient résilient et moderne



Zero Trust devient le \*\*socle de sécurité\*\* du Modern Workplace.



