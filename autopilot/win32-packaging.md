\# Intune – Win32 App Packaging (IntuneWin)



\## 🎯 Objectif

Créer, packager et déployer des applications Win32 dans Intune en utilisant le format `.intunewin`.  

Ce format permet :

\- des installations silencieuses

\- des règles de détection avancées

\- des scripts personnalisés

\- un contrôle complet du cycle de vie applicatif



\---



\# 1. Préparation du packaging



\## 1.1 Télécharger l’outil officiel

Télécharger \*\*IntuneWinAppUtil.exe\*\* depuis Microsoft :



```

https://github.com/Microsoft/Microsoft-Win32-Content-Prep-Tool

```



Placer l’outil dans un dossier, par exemple :



```

C:\\IntuneWin\\

```



\---



\# 2. Structure recommandée du dossier source



Créer un dossier contenant :

\- le fichier d’installation (`.exe` ou `.msi`)

\- les scripts nécessaires (install / uninstall)

\- les fichiers de configuration



Exemple :



```

C:\\Apps\\7zip\\

│

├── 7z1900-x64.msi

├── install.cmd

└── uninstall.cmd

```



\---



\# 3. Commandes d’installation et de désinstallation



\## 3.1 Exemple MSI

\*\*install.cmd\*\*

```

msiexec /i 7z1900-x64.msi /quiet /norestart

```



\*\*uninstall.cmd\*\*

```

msiexec /x {GUID} /quiet /norestart

```



\## 3.2 Exemple EXE

\*\*install.cmd\*\*

```

setup.exe /silent /install

```



\*\*uninstall.cmd\*\*

```

setup.exe /silent /uninstall

```



\---



\# 4. Création du fichier .intunewin



Exécuter :



```powershell

IntuneWinAppUtil.exe

```



Paramètres :

\- Source folder : `C:\\Apps\\7zip`

\- Setup file : `install.cmd`

\- Output folder : `C:\\Apps\\Output`



Résultat :

\- Un fichier \*\*7zip.intunewin\*\*



\---



\# 5. Import dans Intune



Portail Intune :

```

Apps → Windows → Add → Win32 App

```



Téléverser le fichier `.intunewin`.



\---



\# 6. Configuration de l’application



\## 6.1 Program

\- Install command : `install.cmd`

\- Uninstall command : `uninstall.cmd`

\- Install behavior : System



\## 6.2 Requirements

\- OS : Windows 10/11

\- Architecture : x64



\## 6.3 Detection rules



\### Détection via registre

```

HKLM\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\7-Zip

```



\### Détection via fichier

```

C:\\Program Files\\7-Zip\\7z.exe

```



\---



\# 7. Assignation



Modes :

\- \*\*Required\*\* → installation automatique

\- \*\*Available\*\* → via Company Portal

\- \*\*Uninstall\*\* → suppression automatique



Groupes recommandés :

\- Windows 11 Devices

\- Hybrid Azure AD Joined Devices

\- App Pilots



\---



\# 8. Mise à jour d’une application Win32



Pour mettre à jour :

1\. Créer un nouveau `.intunewin`

2\. Modifier la règle de détection (nouvelle version)

3\. Déployer en \*\*Required\*\*



Intune gère automatiquement :

\- la mise à jour

\- la réinstallation si nécessaire



\---



\# 9. Troubleshooting



\## 9.1 Logs IME (Intune Management Extension)

```

C:\\ProgramData\\Microsoft\\IntuneManagementExtension\\Logs

```



Fichiers importants :

\- IntuneManagementExtension.log

\- AgentExecutor.log



\## 9.2 Forcer une synchro

```powershell

Invoke-IntuneDeviceCheckin

```



\## 9.3 Vérifier l’installation

```

Intune → Devices → <device> → Managed Apps

```



\---



\# 10. Résultat attendu



Une fois le packaging Win32 maîtrisé :

\- Les applications sont déployées silencieusement

\- Les mises à jour sont contrôlées

\- Les désinstallations sont automatisées

\- Le parc logiciel est standardisé

\- Le poste est entièrement géré via Intune + Autopilot



Le packaging Win32 devient un pilier de ton Modern Workplace.



