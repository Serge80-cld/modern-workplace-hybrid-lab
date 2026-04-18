\# Hybrid Azure AD Join – Configuration



\## Objectif

Configurer le Hybrid Azure AD Join pour permettre aux appareils AD On-Prem d’être enregistrés automatiquement dans Entra ID (Azure AD), afin d’activer Intune, Conditional Access et les scénarios Modern Workplace.



\---



\## 1. Pré-requis



\### Côté AD On-Prem

\- Domaine fonctionnel : Windows Server 2008 R2 minimum

\- OU des appareils synchronisée via Entra Connect

\- DNS interne fonctionnel



\### Côté Entra ID

\- Licence Azure AD P1 (ou Microsoft 365 Business Premium)

\- Entra Connect installé et configuré

\- Synchronisation des appareils activée



\---



\## 2. Activer le Hybrid Join dans Entra Connect



Dans l’assistant Entra Connect :



1\. Aller dans \*\*Configure Device Options\*\*

2\. Choisir :

&#x20;  ```

&#x20;  Configure Hybrid Azure AD Join

&#x20;  ```

3\. Sélectionner :

&#x20;  - \*\*Windows 10 or later domain-joined devices\*\*

4\. Valider



\---



\## 3. Vérifier la configuration via PowerShell



\### Vérifier la configuration du service



```powershell

dsregcmd /status

```



Les sections importantes :



\- \*\*AzureAdJoined : YES\*\*

\- \*\*DomainJoined : YES\*\*

\- \*\*DeviceId : présent\*\*

\- \*\*TenantName : sergelab.com\*\*



\---



\## 4. GPO pour activer le Device Registration



Créer une GPO :



```

Computer Configuration

→ Administrative Templates

→ Windows Components

→ Device Registration

```



Activer :



\- \*\*Register domain-joined computers as devices\*\*

\- \*\*Automatic registration\*\*



\---



\## 5. Vérifier l’enregistrement dans Entra ID



Dans le portail Entra ID :



```

Entra ID

→ Devices

→ All Devices

```



Les appareils doivent apparaître avec :



\- \*\*Join Type : Hybrid Azure AD Joined\*\*

\- \*\*MDM : Microsoft Intune\*\* (après configuration Intune)

\- \*\*Compliant : Yes\*\* (après politiques Intune)



\---



\## 6. Forcer l’enregistrement d’un poste



Sur un poste joint au domaine :



```powershell

dsregcmd /join

```



Puis :



```powershell

dsregcmd /status

```



\---



\## 7. Vérifications supplémentaires



\### Vérifier la synchro des appareils



```powershell

Start-ADSyncSyncCycle -PolicyType Delta

```



\### Vérifier les logs



```

Event Viewer

→ Applications and Services Logs

→ Microsoft

→ Windows

→ User Device Registration

```



\---



\## 8. Résultat attendu



Une fois la configuration terminée :



\- Les appareils AD On-Prem apparaissent automatiquement dans Entra ID

\- Ils sont prêts pour :

&#x20; - Intune

&#x20; - Compliance policies

&#x20; - Conditional Access

&#x20; - Autopilot (scénarios hybrides)

\- Le Modern Workplace hybride est opérationnel



