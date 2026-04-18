\# Structure d’OU – Modern Workplace Hybride



\## Objectif

Créer une structure d’OU propre, lisible, et compatible avec Azure AD Connect + Intune.



\---



\## Structure recommandée



SERGELAB.local

│

├── \_Admins

│

├── \_Groups

│

├── \_Users

│   ├── Production

│   ├── VIP

│   └── Test

│

├── \_Devices

│   ├── Workstations

│   │   ├── Production

│   │   ├── VIP

│   │   └── Test

│   └── Servers

│

└── \_ServiceAccounts



\---



\## Commandes PowerShell pour créer les OU



```powershell

New-ADOrganizationalUnit -Name "\_Users" -Path "DC=sergelab,DC=local"

New-ADOrganizationalUnit -Name "Production" -Path "OU=\_Users,DC=sergelab,DC=local"

New-ADOrganizationalUnit -Name "Test" -Path "OU=\_Users,DC=sergelab,DC=local"

New-ADOrganizationalUnit -Name "VIP" -Path "OU=\_Users,DC=sergelab,DC=local"



New-ADOrganizationalUnit -Name "\_Devices" -Path "DC=sergelab,DC=local"

New-ADOrganizationalUnit -Name "Workstations" -Path "OU=\_Devices,DC=sergelab,DC=local"

New-ADOrganizationalUnit -Name "Servers" -Path "OU=\_Devices,DC=sergelab,DC=local"

```



\---



\## Notes

\- Les OU commençant par `\_` sont des conteneurs techniques.

\- Cette structure est compatible avec :

&#x20; - Azure AD Connect (filtrage OU)

&#x20; - Hybrid Join

&#x20; - Intune (groupes dynamiques)



