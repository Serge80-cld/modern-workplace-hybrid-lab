\# Windows Autopilot – Overview



\## 🎯 Objectif

Présenter le fonctionnement, les scénarios et les avantages de Windows Autopilot dans un environnement Modern Workplace hybride (Hybrid Azure AD Join + Intune).



Autopilot permet :

\- Le déploiement automatisé des postes Windows

\- La suppression totale des images (no more WDS/SCCM imaging)

\- L’enrôlement automatique dans Intune

\- L’application des profils, apps et policies dès le premier démarrage

\- Une expérience utilisateur moderne et simplifiée



\---



\# 1. Principe général



Autopilot repose sur trois éléments clés :



1\. \*\*L’identification du device\*\*  

&#x20;  Via le \*Hardware Hash\* (ID unique du PC)



2\. \*\*L’enregistrement du device dans Autopilot\*\*  

&#x20;  Import CSV ou script PowerShell



3\. \*\*L’application d’un Deployment Profile\*\*  

&#x20;  - User-driven  

&#x20;  - Self-deploying  

&#x20;  - Pre-provisioning (anciennement WhiteGlove)



Une fois le device enregistré, Windows sait exactement :

\- À quel tenant il appartient  

\- Quel profil appliquer  

\- Comment s’enrôler dans Intune  

\- Quelles apps/policies installer  



\---



\# 2. Scénarios Autopilot



\## 2.1 User-driven mode

Scénario le plus courant :

\- L’utilisateur allume un PC neuf

\- Il entre son email pro

\- Le PC s’enrôle automatiquement dans Intune

\- Les apps et policies s’installent



Idéal pour :

\- Télétravail

\- Onboarding simple

\- Remplacement de PC



\---



\## 2.2 Self-deploying mode

Aucun utilisateur nécessaire :

\- Le PC s’enrôle tout seul

\- Pas de login requis

\- Idéal pour bornes, salles de réunion, kiosques



\---



\## 2.3 Pre-provisioning (WhiteGlove)

Pour les équipes IT :

\- Préparation du PC avant livraison

\- Installation des apps + policies

\- L’utilisateur reçoit un PC déjà prêt



\---



\# 3. Flux Autopilot + Hybrid Join + Intune



Voici le flux complet dans un environnement hybride :



1\. Le device est joint au domaine (AD On-Prem)

2\. Entra Connect synchronise l’objet device

3\. Hybrid Azure AD Join s’active

4\. Autopilot applique le profil

5\. Intune prend le contrôle du device

6\. Les apps, policies, baselines et scripts s’installent

7\. Le poste devient \*\*100 % géré\*\* par Intune



Ce flux est aujourd’hui le standard Modern Workplace.



\---



\# 4. Avantages d’Autopilot



\### ✔️ Plus d’image à maintenir  

Plus de WDS, MDT, SCCM Task Sequences.



\### ✔️ Déploiement à distance  

L’utilisateur peut recevoir un PC neuf chez lui.



\### ✔️ Standardisation  

Tous les postes suivent le même processus.



\### ✔️ Sécurité renforcée  

BitLocker, Defender, Baselines appliqués dès le premier boot.



\### ✔️ Expérience utilisateur moderne  

Le PC se configure automatiquement.



\---



\# 5. Prérequis



\- Windows 10/11 Pro, Enterprise ou Education

\- Device enregistré dans Autopilot (Hardware Hash)

\- Intune MDM activé

\- Hybrid Join opérationnel (si environnement hybride)

\- Accès Internet au premier démarrage



\---



\# 6. Résultat attendu



Une fois Autopilot configuré :

\- Le PC démarre → se connecte au tenant → applique le profil

\- L’utilisateur n’a rien à installer

\- Le poste est sécurisé, configuré et prêt à l’emploi

\- L’IT n’a plus à gérer d’images ou de master



Autopilot devient la \*\*méthode standard\*\* de déploiement dans un environnement Modern Workplace moderne.



