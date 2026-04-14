\# Intune – Compliance Policies



\## 🎯 Objectif

Définir les règles de conformité Intune pour garantir que les appareils respectent les exigences de sécurité de l’entreprise.  

La conformité est essentielle pour :

\- Conditional Access

\- Zero Trust

\- Sécurité du poste de travail

\- Gestion du risque utilisateur/appareil



\---



\# 1. Rôle des policies de conformité



Les policies de conformité permettent de :

\- Vérifier l’état de sécurité d’un appareil

\- Bloquer l’accès aux ressources si l’appareil n’est pas conforme

\- Déclencher des actions automatiques (remédiation, alertes)

\- Alimenter le moteur de risque d’Entra ID



\---



\# 2. Paramètres recommandés pour Windows 10/11



\## 2.1 Sécurité du système

\- \*\*Require BitLocker\*\* : Yes  

\- \*\*Require Secure Boot\*\* : Yes  

\- \*\*Require TPM\*\* : Yes  

\- \*\*Require code integrity\*\* : Enabled  



\## 2.2 Antivirus / Defender

\- \*\*Real-time protection\*\* : Required  

\- \*\*Cloud-delivered protection\*\* : Required  

\- \*\*Automatic sample submission\*\* : Required  



\## 2.3 OS \& Updates

\- \*\*Minimum OS version\*\* : définir selon politique interne  

\- \*\*Block devices with jailbroken/rooted status\*\* : Yes  



\## 2.4 Password / Authentication

\- \*\*Require password to unlock device\*\* : Yes  

\- \*\*Minimum password length\*\* : 6+  

\- \*\*Password expiration\*\* : Optional (modern security = no expiration)  



\---



\# 3. Actions for non-compliance



Recommandation Modern Workplace :



\- \*\*Mark device non-compliant after 1 day\*\*

\- \*\*Send email to user\*\*

\- \*\*Send email to admin\*\*

\- \*\*Block access via Conditional Access\*\*



\---



\# 4. Compliance + Conditional Access



La conformité seule ne bloque rien.  

Elle doit être combinée avec une règle CA :



```

Conditional Access

→ Require device to be marked as compliant

```



Cela permet :

\- d’empêcher un appareil non sécurisé d’accéder aux ressources

\- d’appliquer Zero Trust

\- de protéger les données sensibles



\---



\# 5. Vérification sur un appareil



Sur un poste Windows :



\### Vérifier l’état MDM

```powershell

dsregcmd /status

```



\### Vérifier la conformité

Paramètres Windows :

```

Settings → Accounts → Access work or school → Info

```



\### Vérifier dans Intune

```

Devices → All Devices → <device> → Device compliance

```



\---



\# 6. Logs et troubleshooting



\### Logs Windows

```

Event Viewer

→ Applications and Services Logs

→ Microsoft

→ Windows

→ DeviceManagement-Enterprise-Diagnostics-Provider

```



\### Forcer une synchro

```powershell

Invoke-IntuneDeviceCheckin

```



\---



\# 7. Résultat attendu



Une fois les policies appliquées :

\- L’appareil est marqué \*\*Compliant : Yes\*\*

\- Les règles Conditional Access autorisent l’accès

\- Les risques sont réduits

\- Le poste est sécurisé selon les standards Modern Workplace



