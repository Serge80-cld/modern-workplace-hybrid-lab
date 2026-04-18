\# Conditional Access – Policies \& Best Practices



\## Objectif

Configurer les règles \*\*Conditional Access (CA)\*\* pour sécuriser l’accès aux ressources cloud en appliquant les principes Zero Trust :

\- Vérification explicite

\- Accès conditionnel basé sur le risque

\- Appareils conformes uniquement

\- MFA obligatoire



Conditional Access est le \*\*cœur du Zero Trust\*\* dans Microsoft Entra ID.



\---



\# 1. Rôle du Conditional Access



CA permet de contrôler l’accès en fonction de :

\- l’identité de l’utilisateur  

\- l’état du device  

\- la localisation  

\- le risque utilisateur  

\- le risque de session  

\- l’application ciblée  

\- la conformité Intune  



CA remplace les anciens modèles basés sur le réseau (VPN, firewall périmétrique).



\---



\# 2. Règles essentielles à mettre en place



\## 2.1 Require MFA for all users

La règle la plus critique.



Paramètres recommandés :

\- Users : All users

\- Cloud apps : All apps

\- Grant : Require MFA



\---



\## 2.2 Require compliant device

Permet d’appliquer le Zero Trust complet.



Paramètres :

\- Users : All users (ou groupes pilotes)

\- Cloud apps : All apps

\- Conditions → Device state : Require compliant

\- Grant : Require device to be marked as compliant



Cela force :

\- Hybrid Join  

\- Intune MDM  

\- Compliance policies  

\- Baselines  



\---



\## 2.3 Block legacy authentication

Les protocoles hérités ne supportent pas MFA.



Paramètres :

\- Conditions → Client apps → Legacy authentication clients : Yes

\- Grant : Block access



\---



\## 2.4 Require MFA for risky sign-ins

Utilise \*\*Identity Protection\*\*.



Paramètres :

\- Conditions → Sign-in risk : Medium and above

\- Grant : Require MFA



\---



\## 2.5 Require passwordless for admins

Pour les rôles sensibles.



Paramètres :

\- Users : Privileged roles

\- Grant : Require authentication strength → Passwordless



\---



\# 3. Règles recommandées supplémentaires



\## 3.1 Block access from unsupported OS

Exemple :

\- Windows 7

\- Android rooté

\- iOS jailbreaké



\---



\## 3.2 Require compliant device for Office 365

Sécurise les apps critiques :

\- Exchange Online

\- SharePoint

\- Teams



\---



\## 3.3 Require approved app for mobile

Pour les scénarios BYOD.



Grant :

\- Require approved client app

\- Require app protection policy



\---



\# 4. Exceptions et bonnes pratiques



\## 4.1 Break-glass accounts (2 comptes max)

\- Pas de MFA

\- Pas de CA

\- Mot de passe très long

\- Monitoring renforcé



\## 4.2 Groupes pilotes

Toujours tester les règles CA avant production.



\---



\# 5. Monitoring \& Logs



\## 5.1 Sign-in logs

```

Entra ID → Monitoring → Sign-in logs

```



\## 5.2 What If Tool

Permet de simuler une règle CA avant déploiement.



```

Entra ID → Conditional Access → What If

```



\## 5.3 Insights \& Reporting

Analyse des règles appliquées.



\---



\# 6. Résultat attendu



Une fois les règles CA appliquées :

\- L’accès dépend de l’identité \*\*et\*\* de l’état du device  

\- Les appareils non conformes sont bloqués  

\- Les comptes compromis sont détectés  

\- Les protocoles non sécurisés sont éliminés  

\- Le Zero Trust devient opérationnel  



Conditional Access devient le \*\*garde du corps\*\* de ton environnement Modern Workplace.



