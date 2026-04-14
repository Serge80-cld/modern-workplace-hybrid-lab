\# Intune – Configuration Profiles (Settings Catalog)



\## 🎯 Objectif

Déployer et gérer la configuration des appareils Windows 10/11 via Intune en utilisant les profils de configuration modernes (Settings Catalog).



Les profils remplacent progressivement :

\- Les GPO classiques

\- Les scripts de configuration

\- Les baselines héritées



\---



\# 1. Types de profils de configuration



\## 1.1 Settings Catalog (recommandé)

\- Le plus complet

\- Recherche par mot-clé

\- Compatible avec toutes les nouvelles fonctionnalités Windows

\- Remplace 90 % des GPO



\## 1.2 Templates

\- Modèles préconfigurés

\- Moins flexibles

\- Utiles pour des besoins simples



\## 1.3 Custom (OMA-URI)

\- Pour les paramètres avancés

\- Pour les fonctionnalités non encore disponibles dans Settings Catalog



\---



\# 2. Profils essentiels pour un environnement Modern Workplace



\## 2.1 Windows Update for Business

\- Définir les anneaux de mise à jour

\- Reporter les mises à jour

\- Gérer les redémarrages



Paramètres recommandés :

\- Automatic Updates : Enabled

\- Active Hours : 8h–20h

\- Deadline for quality updates : 7 jours

\- Deadline for feature updates : 30 jours



\---



\## 2.2 BitLocker

\- Activer le chiffrement automatique

\- Exiger TPM

\- Sauvegarder les clés dans Entra ID



Paramètres recommandés :

\- Require BitLocker : Yes

\- Encryption method : XTS-AES 256

\- Store recovery key in Azure AD : Yes



\---



\## 2.3 Microsoft Defender

\- Real-time protection

\- Cloud-delivered protection

\- Tamper Protection

\- Attack Surface Reduction (ASR)



Paramètres recommandés :

\- Real-time protection : Enabled

\- Cloud protection : Enabled

\- Tamper Protection : Enabled

\- ASR rules : Block mode



\---



\## 2.4 Firewall

\- Domain / Private / Public profiles : Enabled

\- Block inbound connections

\- Autoriser les applications approuvées uniquement



\---



\## 2.5 OneDrive Known Folder Move (KFM)

\- Rediriger automatiquement :

&#x20; - Desktop

&#x20; - Documents

&#x20; - Pictures



Paramètres recommandés :

\- Silently move Windows known folders to OneDrive : Enabled

\- Prevent users from redirecting : Enabled



\---



\## 2.6 Configuration du navigateur Edge

\- Sync

\- Favorites

\- Password manager

\- SmartScreen

\- Extensions autorisées



\---



\# 3. Groupes dynamiques pour cibler les profils



\## 3.1 Appareils Hybrid Join



```

(device.devicePhysicalIds -any (\_ -contains "Hybrid"))

```



\## 3.2 Appareils Windows 11



```

(device.deviceOSType -eq "Windows") -and (device.deviceOSVersion -startsWith "10.0.2")

```



\## 3.3 Appareils Intune + Compliant



```

(device.managementType -eq "MDM") -and (device.complianceState -eq "compliant")

```



\---



\# 4. Déploiement des profils



\## 4.1 Assignation

\- All devices

\- Groupes dynamiques

\- Groupes pilotes



\## 4.2 Ordre de déploiement recommandé

1\. BitLocker  

2\. Defender  

3\. Firewall  

4\. Windows Update  

5\. OneDrive KFM  

6\. Edge  

7\. Paramètres spécifiques entreprise  



\---



\# 5. Troubleshooting



\## 5.1 Vérifier l’état du profil



```

Intune → Devices → <device> → Device configuration

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



Une fois les profils appliqués :

\- Le poste est configuré automatiquement

\- Les GPO sont remplacées par des policies modernes

\- La sécurité est renforcée

\- L’expérience utilisateur est cohérente et standardisée



