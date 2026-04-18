\# Modern Workplace Hybrid Lab – Runbook Opérationnel



\## Objectif

Fournir un guide opérationnel clair et structuré pour :

\- Déployer un poste via Autopilot

\- Gérer les appareils dans Intune

\- Diagnostiquer les problèmes courants

\- Assurer la conformité et la sécurité

\- Maintenir l’environnement Modern Workplace hybride



Ce runbook sert de référence pour les équipes IT, les ingénieurs et les architectes.



\---



\# 1. Cycle de vie d’un appareil



\## 1.1 Enregistrement Autopilot

1\. Récupérer le Hardware Hash :

&#x20;  ```powershell

&#x20;  md C:\\HWID

&#x20;  Set-Location C:\\HWID

&#x20;  Invoke-WebRequest -Uri https://aka.ms/getwindowsautopilotinfo -OutFile Get-WindowsAutopilotInfo.ps1

&#x20;  .\\Get-WindowsAutopilotInfo.ps1 -OutputFile AutopilotHWID.csv

&#x20;  ```

2\. Importer le CSV dans Autopilot  

3\. Vérifier l’assignation du Deployment Profile  

4\. Vérifier le Group Tag (si utilisé)



\---



\# 2. Déploiement Autopilot



\## 2.1 Étapes côté utilisateur

1\. Allumer le PC  

2\. Se connecter au Wi-Fi / Ethernet  

3\. Entrer l’email professionnel (User-driven)  

4\. Laisser l’ESP installer les apps et policies  



\## 2.2 Points de contrôle

\- ESP → Device Preparation  

\- ESP → Device Setup  

\- ESP → Account Setup  



\## 2.3 Logs ESP

```

C:\\ProgramData\\Microsoft\\IntuneManagementExtension\\Logs

```



\---



\# 3. Gestion Intune



\## 3.1 Vérifier la conformité d’un appareil

Intune → Devices → Windows → <device> → \*\*Device compliance\*\*



\## 3.2 Forcer une synchronisation

```powershell

Invoke-IntuneDeviceCheckin

```



\## 3.3 Vérifier les apps installées

Intune → Devices → <device> → \*\*Managed Apps\*\*



\## 3.4 Réinitialiser un appareil

Intune → Devices → <device> → \*\*Wipe / Fresh Start / Autopilot Reset\*\*



\---



\# 4. Packaging Win32



\## 4.1 Structure recommandée

```

C:\\Apps\\AppName\\

│

├── setup.exe / .msi

├── install.cmd

└── uninstall.cmd

```



\## 4.2 Création du .intunewin

```powershell

IntuneWinAppUtil.exe

```



\## 4.3 Points de contrôle

\- Commandes install/uninstall  

\- Règle de détection  

\- Assignation Required / Available  



\---



\# 5. Sécurité \& Zero Trust



\## 5.1 Vérifier les règles Conditional Access

Entra ID → Protection → Conditional Access



Règles critiques :

\- Require MFA  

\- Require compliant device  

\- Block legacy authentication  



\## 5.2 Vérifier Identity Protection

Entra ID → Protection → Risky Users / Risky Sign-ins



\## 5.3 Vérifier MDE

\- Portail Defender → Incidents \& Alerts  

\- `Get-MpComputerStatus`  

\- `Test-MpConnectivity`  



\---



\# 6. Troubleshooting



\## 6.1 Problèmes Autopilot

\- Vérifier l’import du Hardware Hash  

\- Vérifier l’assignation du profil  

\- Vérifier la connectivité réseau  

\- Logs ESP :  

&#x20; ```

&#x20; C:\\ProgramData\\Microsoft\\IntuneManagementExtension\\Logs

&#x20; ```



\## 6.2 Problèmes Intune

\- Vérifier IME (Intune Management Extension)  

\- Redémarrer IME :

&#x20; ```powershell

&#x20; Restart-Service IntuneManagementExtension

&#x20; ```



\## 6.3 Problèmes MDE

\- Vérifier l’onboarding  

\- Vérifier Tamper Protection  

\- Vérifier EDR in block mode  



\---



\# 7. Maintenance \& bonnes pratiques



\## 7.1 Mise à jour des apps Win32

\- Nouveau .intunewin  

\- Nouvelle règle de détection  

\- Assignation Required  



\## 7.2 Mise à jour des policies

\- Tester sur un groupe pilote  

\- Vérifier la compatibilité  

\- Déployer progressivement  



\## 7.3 Sécurité

\- Revue mensuelle des règles CA  

\- Revue des comptes à privilèges  

\- Revue des vulnérabilités TVM  



\---



\# 8. Résultat attendu



Ce runbook permet :

\- Un déploiement standardisé et reproductible  

\- Une gestion efficace du parc  

\- Une sécurité renforcée  

\- Une maintenance simplifiée  

\- Une documentation claire pour les équipes IT  



Il constitue la base opérationnelle du Modern Workplace hybride.



