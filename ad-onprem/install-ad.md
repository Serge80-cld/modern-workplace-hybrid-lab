\# Installation et Configuration d’Active Directory Domain Services (AD DS)



\## Objectif

Déployer un contrôleur de domaine Windows Server pour simuler l’environnement On‑Prem d’une entreprise hybride Modern Workplace.



\---



\## 1. Préparation du serveur



\### Configuration réseau

\- Adresse IP fixe

\- DNS pointant vers lui-même

\- Nom du serveur :

&#x20; ```

&#x20; DC01

&#x20; ```



\### Installation du rôle AD DS



```powershell

Install-WindowsFeature AD-Domain-Services -IncludeManagementTools

```



\---



\## 2. Promotion en contrôleur de domaine



\### Création d’une nouvelle forêt



```powershell

Install-ADDSForest `

&#x20; -DomainName "sergelab.local" `

&#x20; -DomainNetbiosName "SERGELAB" `

&#x20; -InstallDNS `

&#x20; -Force

```



Le serveur redémarre automatiquement.



\---



\## 3. Vérifications post-installation



\### Vérifier le domaine



```powershell

Get-ADDomain

```



\### Vérifier le contrôleur de domaine



```powershell

Get-ADDomainController

```



\### Vérifier DNS



```powershell

Get-DnsServerZone

```



\---



\## 4. Comptes de test



Créer un utilisateur de test :



```powershell

New-ADUser -Name "Test User" -GivenName "Test" -Surname "User" -SamAccountName tuser -AccountPassword (Read-Host -AsSecureString "Password") -Enabled $true

```



\---



\## 5. Préparation pour Azure AD Connect



\### Ajouter un suffixe UPN compatible cloud



```powershell

Get-ADForest | Set-ADForest -UPNSuffixes @{Add="sergelab.com"}

```



Ce suffixe sera utilisé pour la synchronisation Entra ID.



