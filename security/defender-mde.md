\# Microsoft Defender for Endpoint (MDE) – Overview \& Configuration



\## 🎯 Objectif

Décrire l’intégration, la configuration et les capacités de \*\*Microsoft Defender for Endpoint (MDE)\*\* dans un environnement Modern Workplace hybride.  

MDE est un composant essentiel du Zero Trust, fournissant :

\- Détection avancée des menaces (EDR)

\- Protection en temps réel (AV + ASR)

\- Gestion des vulnérabilités (TVM)

\- Isolation automatique

\- Remédiation automatisée



\---



\# 1. Rôle de MDE dans le Zero Trust



MDE renforce la sécurité via :

\- \*\*Device Risk Score\*\* (Low / Medium / High)

\- \*\*Risk-based Conditional Access\*\*

\- \*\*Threat \& Vulnerability Management\*\*

\- \*\*Attack Surface Reduction\*\*

\- \*\*Endpoint Detection \& Response (EDR)\*\*



Un appareil compromis peut être :

\- isolé automatiquement  

\- bloqué via Conditional Access  

\- remédié automatiquement  



\---



\# 2. Activation de MDE



\## 2.1 Prérequis

\- Licence : Microsoft 365 E5 / E5 Security / Defender for Endpoint P2

\- Appareil Hybrid Join ou Azure AD Join

\- Intune MDM activé



\## 2.2 Activation dans le portail

```

Security → Microsoft Defender → Settings → Endpoints

```



Activer :

\- \*\*Microsoft Defender for Endpoint\*\*

\- \*\*Automated Investigation \& Response (AIR)\*\*

\- \*\*Tamper Protection\*\*



\---



\# 3. Onboarding des appareils



\## 3.1 Via Intune (recommandé)

```

Intune → Endpoint security → Endpoint detection \& response

```



Créer une policy :

\- Platform : Windows 10/11

\- Profile : Microsoft Defender for Endpoint



Activer :

\- EDR in block mode

\- Sample sharing

\- Cloud protection



\---



\## 3.2 Vérification sur un poste



\### Vérifier l’état MDE

```powershell

Get-MpComputerStatus

```



\### Vérifier l’intégration EDR

```powershell

dsregcmd /status

```



\### Vérifier la connexion au service

```

Settings → Windows Security → Virus \& threat protection

```



\---



\# 4. Attack Surface Reduction (ASR)



ASR réduit la surface d’attaque en bloquant :

\- Macros malveillantes

\- Processus suspects

\- Exécution non autorisée

\- Comportements anormaux



Exemples de règles recommandées :

\- Block Office from creating child processes

\- Block credential stealing

\- Block executable content from email/webmail



Mode recommandé :

\- \*\*Block\*\* (pas Audit)



\---



\# 5. Threat \& Vulnerability Management (TVM)



TVM fournit :

\- Inventaire logiciel

\- Détection des vulnérabilités

\- Score de risque

\- Recommandations de remédiation

\- Intégration avec Intune pour appliquer les correctifs



Exemples :

\- Applications obsolètes

\- Versions vulnérables

\- Mauvaises configurations



\---



\# 6. Automated Investigation \& Response (AIR)



AIR permet :

\- Analyse automatique des incidents

\- Remédiation automatique

\- Isolation du device

\- Suppression de fichiers malveillants

\- Restauration de paramètres compromis



AIR réduit drastiquement le temps de réponse aux incidents.



\---



\# 7. Intégration avec Conditional Access



MDE fournit un \*\*Device Risk Score\*\* utilisé par CA.



Exemple de règle :

```

If Device Risk = Medium or High → Block access

```



Cela permet :

\- d’empêcher un appareil compromis d’accéder aux données

\- d’appliquer un Zero Trust dynamique



\---



\# 8. Logs \& Troubleshooting



\## 8.1 Logs locaux

```

C:\\ProgramData\\Microsoft\\Windows Defender\\Support

```



\## 8.2 Portail MDE

```

Security → Microsoft Defender → Incidents \& Alerts

```



\## 8.3 Vérifier la connectivité

```powershell

Test-MpConnectivity

```



\---



\# 9. Résultat attendu



Une fois MDE configuré :

\- Les appareils sont protégés en temps réel

\- Les menaces sont détectées et remédiées automatiquement

\- Les vulnérabilités sont identifiées et corrigées

\- Le Device Risk Score alimente Conditional Access

\- Le Zero Trust devient \*\*proactif et dynamique\*\*



MDE devient le \*\*centre de gravité\*\* de la sécurité du poste de travail.



