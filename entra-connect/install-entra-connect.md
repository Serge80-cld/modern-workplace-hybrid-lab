\# Installation d’Entra Connect (Azure AD Connect)



\## Objectif

Installer Entra Connect pour synchroniser les identités AD On-Prem vers Entra ID (Azure AD) dans un environnement hybride Modern Workplace.



\---



\## 1. Pré-requis



\### Serveur dédié

\- Windows Server 2019 ou 2022

\- Membre du domaine On-Prem

\- Ne pas installer sur un contrôleur de domaine

\- IP fixe



\### Comptes nécessaires

\- Compte AD On-Prem avec droits de lecture :

&#x20; ```

&#x20; SVC\_AADConnect

&#x20; ```

\- Compte Global Administrator Entra ID (uniquement pour l’installation)



\---



\## 2. Téléchargement



Télécharger Entra Connect depuis Microsoft :

https://www.microsoft.com/en-us/download/details.aspx?id=47594



\---



\## 3. Installation



Lancer l’installeur et choisir :



\### Mode d’installation

\- \*\*Customize\*\* (jamais Express)

\- Mode de synchronisation :

&#x20; ```

&#x20; Password Hash Synchronization (PHS)

&#x20; ```

\- Activer :

&#x20; - Auto-upgrade

&#x20; - Staging mode (optionnel)



\---



\## 4. Connexion aux environnements



\### Connexion à Entra ID

Utiliser un compte Global Admin (temporairement).



\### Connexion à AD On-Prem

Utiliser :

```

SVC\_AADConnect

```



\---



\## 5. Filtrage OU



Sélectionner uniquement les OU suivantes :



```

\_Users

\_Devices

\_Groups

\_ServiceAccounts

```



Ne jamais synchroniser :

\- Domain Controllers

\- Builtin

\- Computers (racine)

\- Users (racine)



\---



\## 6. Lancer la première synchronisation



```powershell

Start-ADSyncSyncCycle -PolicyType Initial

```



\---



\## 7. Vérifications



\### Vérifier le statut du scheduler



```powershell

Get-ADSyncScheduler

```



\### Vérifier la dernière synchronisation



```powershell

Get-ADSyncConnectorRunStatus

```



\### Vérifier dans Entra ID

\- Users → comptes synchronisés

\- Devices → Hybrid Join (après configuration)



