\# Windows Autopilot – Deployment Profiles



\## 🎯 Objectif

Configurer les Deployment Profiles Autopilot pour définir le comportement du poste lors du premier démarrage :

\- Mode d’enrôlement

\- Expérience utilisateur

\- Paramètres de sécurité

\- Hybrid Join ou Azure AD Join



\---



\# 1. Types de Deployment Profiles



\## 1.1 User-driven mode (le plus utilisé)

L’utilisateur configure son PC :

\- Il entre son email professionnel

\- Le PC s’enrôle automatiquement dans Intune

\- Les apps et policies s’installent



Idéal pour :

\- Télétravail

\- Onboarding simple

\- Remplacement de PC



\---



\## 1.2 Self-deploying mode

Aucun utilisateur nécessaire :

\- Le PC s’enrôle tout seul

\- Pas de login requis

\- Idéal pour :

&#x20; - Bornes

&#x20; - Salles de réunion

&#x20; - Kiosques



\---



\## 1.3 Pre-provisioning (anciennement WhiteGlove)

Pour les équipes IT :

\- Préparation du PC avant livraison

\- Installation des apps + policies

\- L’utilisateur reçoit un PC déjà prêt



Idéal pour :

\- Déploiements en masse

\- Environnements avec beaucoup d’applications



\---



\# 2. Création d’un Deployment Profile



Portail Intune :

```

Devices → Windows → Windows enrollment → Deployment Profiles → Create profile

```



Choisir :

\- \*\*Windows PC\*\*

\- \*\*User-driven\*\* (recommandé)

\- \*\*Azure AD Join\*\* ou \*\*Hybrid Azure AD Join\*\* selon l’environnement



\---



\# 3. Paramètres recommandés



\## 3.1 User-driven profile



\### Join type

\- \*\*Azure AD Join\*\* (cloud natif)

\- \*\*Hybrid Azure AD Join\*\* (environnement hybride)



\### OOBE (Out-of-box experience)

\- Skip privacy settings : Yes

\- Skip EULA : Yes

\- Skip keyboard selection : Yes

\- Skip region selection : No (Windows impose ce choix)

\- Allow pre-provisioning : Yes



\### User account type

\- Standard user (recommandé)

\- Administrator (à éviter)



\---



\## 3.2 Self-deploying profile



Paramètres clés :

\- Join type : Azure AD Join

\- Userless : Enabled

\- Language/Region : automatique

\- Skip all OOBE steps : Yes



\---



\## 3.3 Pre-provisioning (WhiteGlove)



Activer :

\- \*\*Allow pre-provisioning\*\*

\- \*\*Show pre-provisioning landing page\*\*



Avantages :

\- Les apps Required s’installent avant la livraison

\- L’utilisateur gagne du temps

\- L’IT valide le PC avant envoi



\---



\# 4. Assignation des profils



Les profils peuvent être assignés à :

\- Groupes dynamiques Autopilot

\- Groupes basés sur Group Tag

\- Tous les appareils Autopilot



Exemple de groupe dynamique basé sur Group Tag :



```

(device.devicePhysicalIds -any (\_ -eq "\[OrderID]:W11-Standard"))

```



\---



\# 5. Vérifications après assignation



Dans Intune :

```

Devices → Windows → Windows enrollment → Deployment Profiles

```



Vérifier :

\- \*\*Profile status : Assigned\*\*

\- \*\*Devices assigned : > 0\*\*

\- \*\*Last sync : récent\*\*



\---



\# 6. Résultat attendu



Une fois le Deployment Profile appliqué :

\- Le PC démarre → se connecte au tenant

\- Le profil Autopilot s’applique automatiquement

\- L’utilisateur suit un OOBE simplifié

\- Le PC s’enrôle dans Intune

\- Les apps, policies et baselines s’installent



Autopilot devient la méthode standard de déploiement du poste de travail.



