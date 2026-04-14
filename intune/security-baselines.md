\# Intune – Security Baselines



\## 🎯 Objectif

Appliquer les Security Baselines Microsoft pour renforcer la sécurité des appareils Windows 10/11 dans un environnement Modern Workplace.  

Les baselines fournissent une configuration de sécurité recommandée par Microsoft, prête à l’emploi.



\---



\# 1. Types de Security Baselines



\## 1.1 Microsoft Defender for Endpoint Baseline

Inclut :

\- Antivirus

\- ASR (Attack Surface Reduction)

\- Exploit Guard

\- Network Protection

\- Tamper Protection



\## 1.2 Windows 10/11 Security Baseline

Inclut :

\- BitLocker

\- Credential Guard

\- Local Policies

\- Firewall

\- SmartScreen

\- Windows Update



\## 1.3 Microsoft Edge Baseline

Inclut :

\- SmartScreen

\- Password Manager

\- Extensions

\- Tracking Prevention



\---



\# 2. Pourquoi utiliser les baselines ?



\- Configuration standardisée

\- Alignement sur les recommandations Microsoft

\- Réduction des risques

\- Remplacement progressif des GPO

\- Compatible Zero Trust



Les baselines sont un \*\*excellent point de départ\*\*, puis on ajoute des profils Settings Catalog pour affiner.



\---



\# 3. Déploiement recommandé



\## 3.1 Ordre de déploiement

1\. \*\*Windows 10/11 Security Baseline\*\*

2\. \*\*Microsoft Defender Baseline\*\*

3\. \*\*Microsoft Edge Baseline\*\*



\## 3.2 Ciblage

\- Groupes dynamiques d’appareils

\- Groupes pilotes avant production

\- Appareils Hybrid Azure AD Join



\---



\# 4. Paramètres critiques à vérifier



\## 4.1 BitLocker

\- XTS-AES 256

\- TPM obligatoire

\- Sauvegarde des clés dans Entra ID



\## 4.2 Credential Guard

\- Enabled

\- Virtualization-based security (VBS)



\## 4.3 Defender

\- Real-time protection : Enabled

\- Cloud protection : Enabled

\- Tamper Protection : Enabled

\- ASR rules : Block



\## 4.4 Firewall

\- Domain / Private / Public : Enabled

\- Block inbound connections



\## 4.5 SmartScreen

\- Enabled

\- Block untrusted apps



\---



\# 5. Vérification sur un appareil



\## 5.1 Dans Intune

```

Devices → <device> → Device configuration → Baselines

```



\## 5.2 Forcer une synchro

```powershell

Invoke-IntuneDeviceCheckin

```



\## 5.3 Logs Windows

```

Event Viewer

→ Applications and Services Logs

→ Microsoft

→ Windows

→ DeviceManagement-Enterprise-Diagnostics-Provider

```



\---



\# 6. Résultat attendu



Une fois les baselines appliquées :

\- Le poste respecte les standards Microsoft

\- La surface d’attaque est réduite

\- Les GPO historiques deviennent inutiles

\- Le poste est prêt pour Zero Trust

\- La conformité est plus facile à atteindre





