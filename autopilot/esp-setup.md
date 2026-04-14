\# Windows Autopilot – Enrollment Status Page (ESP)



\## 🎯 Objectif

Configurer l’Enrollment Status Page (ESP) pour contrôler l’installation des applications et des politiques lors du déploiement Autopilot.  

L’ESP garantit que le poste est \*\*sécurisé, configuré et opérationnel\*\* avant que l’utilisateur accède au bureau.



\---



\# 1. Rôle de l’ESP



L’ESP permet de :

\- Bloquer l’accès au bureau tant que les apps critiques ne sont pas installées

\- Garantir l’application des Security Baselines

\- Assurer la conformité dès le premier démarrage

\- Améliorer l’expérience utilisateur (progression visible)

\- Éviter les postes “semi-configurés”



\---



\# 2. Activation de l’ESP



Portail Intune :

```

Devices → Windows → Windows enrollment → Enrollment Status Page

```



Créer un profil ou modifier le profil par défaut.



\---



\# 3. Paramètres recommandés



\## 3.1 Mode d’application

\- \*\*Enable ESP : Yes\*\*

\- \*\*Show ESP for all users and all devices : Yes\*\*



\## 3.2 Blocking behavior

\- \*\*Block device use until required apps are installed : Yes\*\*

\- \*\*Allow users to reset device if installation fails : Yes\*\*

\- \*\*Allow users to collect logs : Yes\*\*



\## 3.3 Timeout

\- \*\*Timeout : 60 minutes\*\*

\- \*\*Retry count : 2\*\*



\---



\# 4. Applications Required dans l’ESP



Il est essentiel de définir les applications qui doivent absolument être installées avant l’accès au bureau.



Recommandation Modern Workplace :



\### Apps critiques à inclure :

\- Microsoft Edge

\- Company Portal

\- OneDrive

\- Microsoft Defender (si Win32)

\- Agent MDE (si utilisé)

\- VPN / Agent réseau (si nécessaire)

\- Scripts de configuration essentiels



\### Apps à éviter dans l’ESP :

\- Applications lourdes (Office, Adobe, etc.)

\- Applications non critiques

\- Applications Win32 complexes



\---



\# 5. Phases de l’ESP



L’ESP se déroule en trois étapes :



\## 5.1 Device Preparation

\- Join Azure AD / Hybrid Join

\- Installation de l’Intune Management Extension

\- Configuration initiale



\## 5.2 Device Setup

\- Installation des apps Required

\- Application des policies

\- Application des Security Baselines



\## 5.3 Account Setup (User-driven)

\- Configuration du profil utilisateur

\- Installation des apps utilisateur



\---



\# 6. Troubleshooting ESP



\## 6.1 Logs locaux

```

C:\\ProgramData\\Microsoft\\IntuneManagementExtension\\Logs

```



Fichiers importants :

\- IntuneManagementExtension.log

\- AgentExecutor.log



\## 6.2 Forcer une synchro

```powershell

Invoke-IntuneDeviceCheckin

```



\## 6.3 Redémarrer l’ESP

```

Shift + F10 → powershell → Restart-Computer

```



\---



\# 7. Résultat attendu



Une fois l’ESP configurée :

\- Le poste est entièrement configuré avant l’accès utilisateur

\- Les apps critiques sont installées

\- Les policies de sécurité sont appliquées

\- L’expérience utilisateur est fluide et contrôlée

\- Le déploiement Autopilot devient fiable et reproductible



