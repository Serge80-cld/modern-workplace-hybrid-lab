

\# Intune – Application Management (Win32, Store, LOB)



\## Objectif

Gérer le cycle de vie des applications dans un environnement Modern Workplace via Microsoft Intune :

\- Déploiement

\- Mise à jour

\- Désinstallation

\- Assignation ciblée

\- Automatisation



\---



\# 1. Types d’applications supportées



\## 1.1 Win32 Apps (format .intunewin)

Le format le plus utilisé pour les applications professionnelles.



Avantages :

\- Déploiement silencieux

\- Détection personnalisée

\- Scripts d’installation/désinstallation

\- Contrôle avancé



\## 1.2 Microsoft Store Apps (New Store)

\- Installation simple

\- Mises à jour automatiques

\- Idéal pour les apps modernes (Teams, PowerToys, etc.)



\## 1.3 Line-of-Business (LOB)

\- Applications internes

\- MSI classiques

\- Déploiement direct



\## 1.4 Web Apps

\- Icônes dans le menu démarrer

\- Redirection vers une URL

\- Idéal pour les apps SaaS



\---



\# 2. Win32 Apps – Processus complet



\## 2.1 Préparer l’application

Convertir un .exe ou .msi en .intunewin :



```powershell

IntuneWinAppUtil.exe

```



Paramètres :

\- Source folder

\- Setup file

\- Output folder



\## 2.2 Détection

Exemples :



\### Détection via registre

```

HKLM\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\<App>

```



\### Détection via fichier

```

C:\\Program Files\\<App>\\app.exe

```



\## 2.3 Commandes d’installation

Exemples :



\### MSI

```

msiexec /i app.msi /quiet /norestart

```



\### EXE

```

setup.exe /silent /install

```



\## 2.4 Commandes de désinstallation

```

msiexec /x {GUID} /quiet /norestart

```



\---



\# 3. Assignation des applications



\## 3.1 Groupes recommandés

\- \*\*All Windows Devices\*\*

\- \*\*Windows 11 Devices\*\*

\- \*\*App Pilots\*\*

\- \*\*VIP Devices\*\*

\- \*\*Hybrid Azure AD Joined Devices\*\*



\## 3.2 Modes d’assignation

\- \*\*Required\*\* → installation automatique

\- \*\*Available\*\* → installation via Company Portal

\- \*\*Uninstall\*\* → suppression automatique



\---



\# 4. Company Portal



Le portail utilisateur permet :

\- Installation d’applications

\- Réinstallation

\- Mise à jour

\- Accès aux ressources



Recommandation :

\- Déployer \*\*Company Portal\*\* en Required sur tous les appareils.



\---



\# 5. Mises à jour des applications



\## 5.1 Win32 Apps

\- Nouvelle version = nouveau .intunewin

\- Détection mise à jour

\- Assignation Required



\## 5.2 Store Apps

\- Mises à jour automatiques via Microsoft Store



\## 5.3 LOB Apps

\- Remplacement de la version existante



\---



\# 6. Scripts PowerShell (Intune Management Extension)



Utilisés pour :

\- Pré-requis

\- Nettoyage

\- Configuration avancée

\- Déploiement d’applications complexes



Exemple de script de vérification :



```powershell

if (Test-Path "C:\\Program Files\\App\\app.exe") {

&#x20;   Write-Output "Installed"

} else {

&#x20;   exit 1

}

```



\---



\# 7. Troubleshooting



\## 7.1 Logs IME (Intune Management Extension)

```

C:\\ProgramData\\Microsoft\\IntuneManagementExtension\\Logs

```



Fichiers importants :

\- IntuneManagementExtension.log

\- AgentExecutor.log



\## 7.2 Forcer une synchro

```powershell

Invoke-IntuneDeviceCheckin

```



\## 7.3 Vérifier l’installation

```

Intune → Devices → <device> → Managed Apps

```



\---



\# 8. Résultat attendu



Une fois la gestion des applications configurée :

\- Les applications sont déployées automatiquement

\- Les mises à jour sont contrôlées

\- Les utilisateurs disposent du Company Portal

\- Le parc logiciel est standardisé et sécurisé

\- Le poste est entièrement géré via Intune



