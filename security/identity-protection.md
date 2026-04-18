\# Microsoft Entra ID – Identity Protection



\## Objectif

Décrire le rôle d’\*\*Identity Protection\*\* dans la détection et la remédiation des risques liés aux identités.  

Identity Protection analyse en continu :

\- les connexions suspectes  

\- les comportements anormaux  

\- les comptes compromis  

\- les risques utilisateurs et sessions  



C’est un composant essentiel du Zero Trust.



\---



\# 1. Types de risques détectés



Identity Protection identifie deux catégories principales :



\## 1.1 User Risk

Probabilité qu’un \*\*compte utilisateur\*\* soit compromis.



Exemples :

\- Credentials volés  

\- Activité impossible (Impossible Travel)  

\- Connexion depuis un botnet  

\- Fuite de mot de passe  

\- MFA contourné  



Niveaux :

\- Low  

\- Medium  

\- High  



\---



\## 1.2 Sign-in Risk

Probabilité qu’une \*\*connexion\*\* soit malveillante.



Exemples :

\- Adresse IP anormale  

\- Device inconnu  

\- Session anormale  

\- Tor / anonymizer  

\- Patterns de brute force  



Niveaux :

\- Low  

\- Medium  

\- High  



\---



\# 2. Policies Identity Protection



Identity Protection fournit \*\*deux policies automatiques\*\*.



\## 2.1 User Risk Policy

Action recommandée :

\- \*\*Require password change\*\*  

\- \*\*Block access\*\* si risque élevé  



Cible :

\- All users  

\- Exclure comptes break-glass  



\---



\## 2.2 Sign-in Risk Policy

Action recommandée :

\- \*\*Require MFA\*\* pour risque Medium+  

\- \*\*Block access\*\* pour risque High  



Cible :

\- All users  

\- Groupes pilotes au début  



\---



\# 3. Intégration avec Conditional Access



Identity Protection alimente CA avec :

\- User Risk  

\- Sign-in Risk  



Exemple de règle Zero Trust :

```

If Sign-in Risk = Medium or High → Require MFA

If User Risk = High → Block access

```



Cela permet :

\- de bloquer les comptes compromis  

\- de forcer une remédiation immédiate  

\- d’empêcher l’accès depuis des sessions suspectes  



\---



\# 4. Identity Protection + MFA + Passwordless



Identity Protection fonctionne encore mieux avec :

\- MFA obligatoire  

\- Windows Hello for Business  

\- Authenticator App  

\- FIDO2 Security Keys  



Objectif :

> Réduire la dépendance au mot de passe, principal vecteur de compromission.



\---



\# 5. Identity Protection + Risk-based Conditional Access



Scénario Zero Trust complet :

1\. Un utilisateur se connecte depuis un pays inhabituel  

2\. Identity Protection détecte un risque Medium  

3\. Conditional Access applique : \*\*Require MFA\*\*  

4\. Si le risque devient High → \*\*Block access\*\*  

5\. L’utilisateur doit réinitialiser son mot de passe  



C’est un modèle dynamique et automatique.



\---



\# 6. Monitoring \& Investigation



\## 6.1 Risky Users

```

Entra ID → Protection → Risky Users

```



\## 6.2 Risky Sign-ins

```

Entra ID → Protection → Risky Sign-ins

```



\## 6.3 Risk Detections

```

Entra ID → Protection → Risk Detections

```



\---



\# 7. Remédiation automatique



Identity Protection peut :

\- forcer un reset de mot de passe  

\- bloquer l’accès  

\- exiger MFA  

\- isoler les sessions suspectes  



Combiné avec MDE + CA, cela crée un \*\*Zero Trust dynamique\*\*.



\---



\# 8. Résultat attendu



Une fois Identity Protection activé :

\- Les comptes compromis sont détectés automatiquement  

\- Les connexions suspectes sont bloquées  

\- Le risque utilisateur influence l’accès  

\- Le Zero Trust devient intelligent et adaptatif  

\- L’environnement est protégé contre les attaques d’identité  



