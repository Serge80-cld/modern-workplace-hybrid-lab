\# Configuration d’Entra Connect (Azure AD Connect)



\## 🎯 Objectif

Configurer Entra Connect après l’installation pour garantir une synchronisation fiable, sécurisée et compatible avec un environnement Modern Workplace hybride.



\---



\## 1. Mode de synchronisation



Le mode recommandé pour 99 % des entreprises :



```

Password Hash Synchronization (PHS)

```



\### Avantages

\- Haute disponibilité native

\- Pas de dépendance au domaine On-Prem pour l’authentification

\- Compatible MFA / Conditional Access

\- Maintenance minimale



\---



\## 2. Scheduler (planification de la synchro)



\### Vérifier la configuration actuelle



```powershell

Get-ADSyncScheduler

```



\### Activer la synchronisation automatique (si désactivée)



```powershell

Set-ADSyncScheduler -SyncCycleEnabled $true

```



\### Forcer une synchro delta



```powershell

Start-ADSyncSyncCycle -PolicyType Delta

```



\---



\## 3. Filtrage OU (Organizational Units)



\### OU à synchroniser



```

\_Users

\_Devices

\_Groups

\_ServiceAccounts

```



\### OU à exclure



\- Domain Controllers  

\- Builtin  

\- Computers (racine)  

\- Users (racine)  

\- Tout ce qui n’est pas utilisé dans le Modern Workplace  



\---



\## 4. Filtrage par attribut (optionnel)



Pour synchroniser uniquement les comptes marqués :



\### Exemple : filtrer sur `extensionAttribute1`



```powershell

Set-ADSyncAADCompanyFeature -EnableDirSyncProvisioning $true

```



Puis dans l’interface graphique, définir :



```

extensionAttribute1 = "SyncToCloud"

```



\---



\## 5. Comptes de service



\### Compte AD On-Prem utilisé par Entra Connect



```

SVC\_AADConnect

```



Droits nécessaires :

\- Lecture sur l’annuaire

\- Lecture sur les OU synchronisées



\### Compte Entra ID utilisé lors de l’installation

\- Global Administrator (temporaire)

\- Peut être retiré après installation



\---



\## 6. Logs et supervision



\### Vérifier les erreurs de synchronisation



```powershell

Get-ADSyncConnectorRunStatus

```



\### Vérifier les événements dans Windows Event Viewer



```

Applications and Services Logs

→ Directory Synchronization

```



\---



\## 7. Bonnes pratiques



\- Ne jamais installer Entra Connect sur un DC  

\- Ne jamais synchroniser les OU système  

\- Toujours documenter les OU synchronisées  

\- Activer l’auto-upgrade  

\- Utiliser PHS sauf cas très spécifiques  



