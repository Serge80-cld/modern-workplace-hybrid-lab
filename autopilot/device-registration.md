\# Windows Autopilot – Device Registration



\## 🎯 Objectif

Enregistrer les appareils Windows dans Autopilot afin qu’ils puissent recevoir automatiquement un Deployment Profile lors du premier démarrage.



L’enregistrement peut se faire :

\- via un fichier CSV

\- via un script PowerShell

\- via un fournisseur (OEM)

\- via Intune directement (si déjà géré)



\---



\# 1. Récupération du Hardware Hash



Le Hardware Hash est l’identifiant unique du PC utilisé par Autopilot.



\## 1.1 Script PowerShell officiel



Exécuter sur le poste :



```powershell

md c:\\HWID

Set-Location c:\\HWID

Invoke-WebRequest -Uri https://aka.ms/getwindowsautopilotinfo -OutFile Get-WindowsAutopilotInfo.ps1

.\\Get-WindowsAutopilotInfo.ps1 -OutputFile AutopilotHWID.csv

```



Résultat :

\- Un fichier \*\*AutopilotHWID.csv\*\*

\- Contient le Hardware Hash du device



\---



\# 2. Import manuel dans Autopilot



Portail Intune :

```

Devices → Windows → Windows enrollment → Devices → Import

```



Importer :

\- Le fichier \*\*AutopilotHWID.csv\*\*

\- Ou un fichier CSV contenant plusieurs appareils



Après import :

\- Le device apparaît dans la liste Autopilot

\- Il peut recevoir un Deployment Profile



\---



\# 3. Format du fichier CSV Autopilot



Exemple :



```

Device Serial Number,Windows Product ID,Hardware Hash

1234567890,,MIIKvgYJKoZIhvcNAQcCoIIKr...

```



Seule la colonne \*\*Hardware Hash\*\* est obligatoire.



\---



\# 4. Enregistrement automatique via OEM



Les constructeurs peuvent enregistrer les appareils directement dans ton tenant :

\- Dell

\- HP

\- Lenovo

\- Surface



Avantages :

\- Aucun script à exécuter

\- Le PC arrive déjà prêt pour Autopilot

\- Idéal pour les déploiements à grande échelle



\---



\# 5. Enregistrement via Intune (si device déjà géré)



Si un appareil est déjà dans Intune :



```

Devices → Windows → <device> → Convert to Autopilot

```



Cela génère automatiquement le Hardware Hash.



\---



\# 6. Vérifications après import



Dans Intune :

```

Devices → Windows → Windows enrollment → Devices

```



Vérifier :

\- \*\*Profile status : Assigned\*\*

\- \*\*Enrollment state : Enrolled / Not enrolled\*\*

\- \*\*Group tag : présent si utilisé\*\*

\- \*\*Serial number : correct\*\*



\---



\# 7. Group Tags (optionnel mais recommandé)



Les Group Tags permettent :

\- d’assigner automatiquement un Deployment Profile

\- de cibler des groupes dynamiques



Exemples :

\- `W11-Standard`

\- `VIP`

\- `Kiosk`

\- `Pilot`



\---



\# 8. Résultat attendu



Une fois l’enregistrement terminé :

\- Le device est visible dans Autopilot

\- Il reçoit automatiquement un Deployment Profile

\- Il peut être déployé sans image

\- Le flux Autopilot → Hybrid Join → Intune fonctionne de bout en bout



