\# Modern Workplace Hybrid Lab – Diagrammes d’Architecture



\## 🎯 Objectif

Fournir les instructions pour créer les diagrammes d’architecture du lab Modern Workplace hybride.  

Ces diagrammes servent à :

\- illustrer l’architecture globale

\- clarifier les flux techniques

\- renforcer le portfolio GitHub

\- préparer les entretiens architecte

\- communiquer avec les équipes IT / DSI



Les diagrammes peuvent être réalisés avec :

\- draw.io / diagrams.net (recommandé)

\- Excalidraw

\- Visio

\- Whimsical



\---



\# 1. Structure recommandée



```

docs/

└── diagrams/

&#x20;   ├── architecture-global.png

&#x20;   ├── hybrid-join-flow.png

&#x20;   ├── autopilot-flow.png

&#x20;   ├── zero-trust-architecture.png

&#x20;   ├── mde-integration.png

&#x20;   └── README.md

```



\---



\# 2. Diagramme 1 – Architecture globale Modern Workplace



Nom du fichier :

```

architecture-global.png

```



Éléments à représenter :

\- AD On-Prem  

\- Entra Connect  

\- Entra ID  

\- Hybrid Azure AD Join  

\- Intune  

\- Autopilot  

\- Microsoft Defender for Endpoint  

\- Conditional Access  

\- Identity Protection  



Flux à dessiner :

\- Sync AD → Entra ID  

\- Device Hybrid Join  

\- Enrollment Intune  

\- Autopilot provisioning  

\- MDE onboarding  

\- CA + Identity Protection  



\---



\# 3. Diagramme 2 – Flux Hybrid Azure AD Join



Nom du fichier :

```

hybrid-join-flow.png

```



Étapes à représenter :

1\. PC rejoint au domaine On-Prem  

2\. Entra Connect synchronise l’objet device  

3\. Le PC contacte Entra ID  

4\. Device Registration  

5\. Hybrid Join finalisé  

6\. Device visible dans Intune (si MDM auto-enroll)  



\---



\# 4. Diagramme 3 – Flux Autopilot (User-driven)



Nom du fichier :

```

autopilot-flow.png

```



Étapes à représenter :

1\. Import Hardware Hash  

2\. Assignation Deployment Profile  

3\. Premier boot du PC  

4\. OOBE simplifié  

5\. ESP (Device Preparation → Device Setup → Account Setup)  

6\. Installation apps Required  

7\. Application des baselines  

8\. Device opérationnel  



\---



\# 5. Diagramme 4 – Architecture Zero Trust



Nom du fichier :

```

zero-trust-architecture.png

```



Piliers à représenter :

\- Identité  

\- Appareils  

\- Applications  

\- Données  

\- Réseau  

\- Infrastructure  



Flux à inclure :

\- CA : Require MFA  

\- CA : Require compliant device  

\- Identity Protection  

\- Device Risk Score (MDE)  

\- DLP / Sensitivity Labels  



\---



\# 6. Diagramme 5 – Intégration MDE + Conditional Access



Nom du fichier :

```

mde-integration.png

```



Éléments à représenter :

\- Device  

\- MDE (EDR, TVM, ASR)  

\- Device Risk Score  

\- Entra ID  

\- Conditional Access  

\- Blocage ou autorisation  



Flux :

1\. MDE détecte une menace  

2\. Device Risk = Medium/High  

3\. CA applique : Block access  

4\. Remédiation automatique (AIR)  



\---



\# 7. Conventions graphiques recommandées



\- \*\*Bleu\*\* : Identité / Entra ID  

\- \*\*Vert\*\* : Appareils / Intune  

\- \*\*Orange\*\* : Sécurité / MDE  

\- \*\*Violet\*\* : Zero Trust / CA  

\- \*\*Gris\*\* : On-Prem  



Flèches :

\- → Flux principal  

\- ⇄ Synchronisation  

\- ⤴ Escalade / remontée d’alerte  



\---



\# 8. Résultat attendu



Une fois les diagrammes créés :

\- Le repo devient visuel et professionnel  

\- L’architecture est immédiatement compréhensible  

\- Le portfolio est au niveau d’un architecte Modern Workplace  

\- Les recruteurs voient instantanément la maîtrise du sujet  



Ces diagrammes complètent la documentation et renforcent la valeur du projet.



