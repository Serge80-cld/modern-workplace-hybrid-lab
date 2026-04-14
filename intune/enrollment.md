\# Intune – Enrollment (MDM/MAM)



\## 🎯 Objectif

Configurer les méthodes d’enrôlement des appareils dans Microsoft Intune pour un environnement Modern Workplace hybride (Hybrid Azure AD Join + Intune MDM).



\---



\# 1. Types d’enrôlement



\## 1.1 MDM (Mobile Device Management)

Gestion complète de l’appareil :

\- Configuration

\- Sécurité

\- Compliance

\- Applications

\- Scripts

\- Windows Update



Recommandé pour :

\- Postes Windows 10/11

\- Appareils professionnels



\## 1.2 MAM (Mobile Application Management)

Gestion des applications uniquement (sans enrôler l’appareil).



Recommandé pour :

\- BYOD

\- Smartphones personnels

\- Scénarios légers



\---



\# 2. Plateformes supportées



\- Windows 10/11

\- iOS / iPadOS

\- Android

\- macOS



\---



\# 3. Configuration de l’enrôlement Windows



\## 3.1 Activer MDM dans Entra ID



Portail Entra ID :

```

Entra ID

→ Mobility (MDM and MAM)

→ Microsoft Intune

```



Définir :

\- \*\*MDM user scope : All\*\*

\- \*\*MAM user scope : None\*\* (sauf BYOD)



\---



\# 4. Enrôlement automatique (Auto-enrollment)



\## 4.1 Pour les appareils Hybrid Azure AD Join



Déjà activé via :

\- Entra Connect

\- GPO Device Registration



Vérification sur un poste :



```powershell

dsregcmd /status

```



Doit afficher :

\- AzureAdJoined : YES

\- DomainJoined : YES

\- MDMUrl : présent



\---



\# 5. GPO pour activer l’auto-enrollment



Créer une GPO :



```

Computer Configuration

→ Administrative Templates

→ Windows Components

→ MDM

```



Activer :

\- \*\*Enable automatic MDM enrollment using default Azure AD credentials\*\*

\- Mode : \*\*User Credential\*\*



\---



\# 6. Vérifier l’enrôlement dans Intune



Portail Intune :

```

Devices → All Devices

```



Un appareil enrôlé doit afficher :

\- \*\*Join Type : Hybrid Azure AD Joined\*\*

\- \*\*MDM : Microsoft Intune\*\*

\- \*\*Compliance : Yes\*\* (après policies)

\- \*\*Last check-in : récent\*\*



\---



\# 7. Troubleshooting



\## 7.1 Forcer l’enrôlement



```powershell

dsregcmd /join

```



\## 7.2 Forcer la synchro MDM



```powershell

Invoke-IntuneDeviceCheckin

```



\## 7.3 Vérifier les logs



```

Event Viewer

→ Applications and Services Logs

→ Microsoft

→ Windows

→ DeviceManagement-Enterprise-Diagnostics-Provider

```



\---



\# 8. Résultat attendu



Une fois l’enrôlement configuré :

\- Les appareils Hybrid Join s’enregistrent automatiquement dans Intune

\- Les policies de sécurité et de configuration peuvent s’appliquer

\- Les applications Win32/Store peuvent être déployées

\- L’appareil devient gérable de bout en bout via Intune





