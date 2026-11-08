# Chapter 8 — Identity and Access Management (IAM)

## 1. Identity and Access Management — IAM

IAM = gestion des identités et des accès.

Permet de contrôler :

- Qui peut accéder aux systèmes
    
- Comment une personne prouve son identité
    
- Quelles ressources elle peut utiliser
    
- Quelles actions elle peut effectuer
    
- Comment ses activités sont surveillées
    

### AAA — Authentication, Authorization, Accounting

|Concept|Signification|
|---|---|
|Authentication|Vérifier qui tu es|
|Authorization|Déterminer ce que tu peux faire|
|Accounting|Enregistrer et suivre tes activités|

Exemple :

Authentication → connexion avec mot de passe.

Authorization → accès à certains fichiers.

Accounting → journalisation des connexions, du temps d'utilisation et des ressources consommées.

EXAM :

`Authentication = Who are you?`

`Authorization = What can you access?`

`Accounting = What did you do?`

⚠️ Être authentifié ne signifie pas avoir toutes les permissions.

# 2. Identity

Une identity est un ensemble d'informations permettant d'identifier :

- une personne
    
- un appareil
    
- une application
    
- un système
    
- une organisation
    

### Attributes vs Traits

|Concept|Signification|
|---|---|
|Attributes|Informations modifiables|
|Traits|Caractéristiques propres à la personne|

Exemples :

Attributes → adresse, poste, fonction.

Traits → couleur des yeux, lieu de naissance.

### Identity Claims

Différentes méthodes permettent de présenter une identité :

|Méthode|Fonction|
|---|---|
|Username|Identifiant utilisateur|
|Certificate|Certificat numérique|
|Token|Dispositif physique ou logiciel|
|SSH Key|Clé cryptographique d'authentification|
|Smartcard|Carte à puce cryptographique|

⚠️ Username ≠ Authentication

Un nom d'utilisateur indique une identité, mais ne prouve pas qu'elle t'appartient.

### SSH Keys / Smartcards

Les clés privées doivent rester secrètes.

Une clé privée publiée sur GitHub ou un autre dépôt peut permettre à un attaquant d'accéder à des systèmes.

Les smartcards peuvent générer et conserver les clés privées directement dans leur puce.

# 3. Authentication Protocols

Les principaux protocoles à connaître :

|Protocole|Utilisation|
|---|---|
|EAP|Framework d'authentification réseau|
|CHAP|Authentication par challenge-response|
|802.1X|Network Access Control|
|RADIUS|AAA pour l'accès réseau|
|TACACS+|AAA et administration réseau|
|Kerberos|Authentification par tickets|

### EAP — Extensible Authentication Protocol

Framework permettant différentes méthodes d'authentification.

Exemples :

- EAP-TLS
    
- EAP-TTLS
    
- LEAP
    

→ principalement utilisé pour l'authentification réseau, notamment Wi-Fi.

### CHAP — Challenge Handshake Authentication Protocol

Fonctionne avec un challenge-response :

1. Le serveur envoie un challenge.
    
2. Le client calcule une réponse.
    
3. Le serveur vérifie la réponse.
    

→ évite de transmettre directement le mot de passe en clair.

CHAP est plus sécurisé que PAP, un ancien protocole d'authentification.

# 4. 802.1X — Network Access Control

802.1X = contrôle d'accès au réseau.

Il permet d'authentifier les appareils avant de leur autoriser l'accès au réseau.

### Trois composants

|Composant|Rôle|
|---|---|
|Supplicant|Appareil qui demande l'accès|
|Authenticator|Switch ou point d'accès Wi-Fi|
|Authentication Server|Serveur vérifiant les identifiants|

Fonctionnement :

```
Supplicant
    ↓
Authenticator (Switch / Wi-Fi)
    ↓
RADIUS Server
    ↓
LDAP / Active Directory
```

EXAM :

`802.1X = Network Access Control`

`EAP = Authentication Framework`

`RADIUS = AAA Server`

`LDAP = Directory Service`

# 5. RADIUS vs TACACS+

Les deux sont des protocoles AAA.

|RADIUS|TACACS+|
|---|---|
|Principalement accès réseau / Wi-Fi|Principalement administration des équipements|
|Client-server|Client-server|
|UDP ou TCP selon l'implémentation|TCP|
|Protection historique des mots de passe limitée|Chiffre le contenu des paquets|
|AAA|AAA|
|Moins granulaire pour les commandes|Contrôle granulaire des commandes|

### RADIUS

Remote Authentication Dial-In User Service

→ authentification, autorisation et accounting sur les réseaux.

La protection historique du mot de passe repose notamment sur un secret partagé et MD5.

⚠️ Le trafic RADIUS peut nécessiter une protection supplémentaire, par exemple IPsec.

### TACACS+

Terminal Access Controller Access Control System Plus

→ particulièrement adapté aux équipements réseau.

Permet de contrôler les commandes qu'un administrateur peut exécuter.

EXAM :

Wireless / Network AAA → RADIUS

Granular command authorization → TACACS+

# 6. Kerberos

Kerberos = authentication using tickets.

Permet aux utilisateurs de s'authentifier et d'accéder à des services sans renvoyer leur mot de passe à chaque accès.

Très utilisé dans les environnements Windows / Active Directory.

### Composants

|Terme|Fonction|
|---|---|
|KDC|Key Distribution Center|
|AS|Authentication Server|
|TGT|Ticket-Granting Ticket|
|TGS|Ticket-Granting Service|
|Realm|Domaine logique Kerberos|
|Principal|Identité Kerberos|

### Fonctionnement

```
User
  ↓
Authentication Server (AS)
  ↓
Receives TGT
  ↓
Ticket-Granting Service (TGS)
  ↓
Receives Service Ticket
  ↓
Access to Service
```

Le KDC gère la distribution des tickets.

Un principal Kerberos peut être décrit avec un nom principal, une instance et un realm.

EXAM :

`Kerberos = Tickets`

`TGT = Initial authentication ticket`

`TGS = Service ticket issuance`

`KDC = Ticket infrastructure`

# 7. Single Sign-On — SSO

SSO = une seule authentification pour accéder à plusieurs services.

Exemple :

Connexion à Google → accès à Gmail et YouTube sans se reconnecter à chaque fois.

### Avantages

- moins de mots de passe à saisir
    
- expérience utilisateur simplifiée
    
- gestion centralisée de l'authentification
    

### Inconvénients

- une session compromise peut exposer plusieurs applications
    
- concentration du risque sur le système d'identité
    
- certaines applications sensibles doivent exiger une authentification supplémentaire
    

### Technologies associées au SSO

- LDAP
    
- Kerberos
    
- SAML
    
- OpenID / OpenID Connect
    
- OAuth
    

⚠️ Toutes ces technologies n'ont pas le même rôle : certaines assurent l'authentification, d'autres l'autorisation ou l'accès aux annuaires.

# 8. LDAP

LDAP — Lightweight Directory Access Protocol

→ protocole permettant d'accéder à un annuaire d'utilisateurs et de ressources.

Souvent utilisé avec Active Directory.

### Structure LDAP

|Terme|Signification|
|---|---|
|OU|Organizational Unit|
|CN|Common Name|
|DN|Distinguished Name|

Exemple :

```
Company
   |
   +-- OU=IT
   |      |
   |      +-- CN=Alice
   |
   +-- OU=HR
          |
          +-- CN=Bob
```

LDAP permet de retrouver :

- utilisateurs
    
- groupes
    
- adresses e-mail
    
- numéros de téléphone
    
- informations organisationnelles
    

⚠️ Les annuaires contiennent des informations sensibles et doivent être protégés, particulièrement lorsqu'ils sont accessibles depuis l'extérieur.

EXAM :

`LDAP = Directory Service`

`OU = Organizational Unit`

`CN = Common Name`

`DN = Distinguished Name`

# 9. SAML vs OAuth vs OpenID

Différences importantes pour Security+.

|Technologie|Fonction principale|
|---|---|
|SAML|Échange d'assertions d'authentification et d'autorisation|
|OAuth|Autorisation déléguée|
|OpenID / OIDC|Authentification fédérée|

## SAML

Security Assertion Markup Language

- utilise XML
    
- fonctionne avec un Identity Provider (IdP)
    
- transmet des assertions à un Service Provider (SP)
    
- très utilisé pour le SSO des applications web d'entreprise
    

SAML = Federation + Web SSO

## OAuth

Open Authorization

Permet à une application d'accéder à certaines ressources sans recevoir ton mot de passe.

Exemple :

Une application demande l'autorisation de consulter ton Google Calendar.

Tu acceptes les permissions demandées.

→ l'application obtient un accès limité.

⚠️ OAuth = Authorization, pas authentification à lui seul.

## OpenID / OpenID Connect

Permet l'authentification avec une identité fournie par un tiers.

Exemple :

Sign in with Google

Le site fait confiance à Google pour authentifier l'utilisateur.

OpenID Connect est la technologie moderne d'authentification construite sur OAuth 2.0.

### EXAM — Associations

`SAML = XML + Assertions + SSO`

`OAuth = Delegated Authorization`

`OpenID Connect = Authentication`

`LDAP = Directory`

# 10. Federation

Federation = plusieurs services ou organisations font confiance à un fournisseur d'identité.

L'utilisateur peut utiliser son identité sur différents systèmes sans avoir un compte indépendant dans chacun.

### Composants

|Terme|Fonction|
|---|---|
|Principal|Utilisateur|
|IdP|Identity Provider|
|SP|Service Provider|
|RP|Relying Party|
|Attestation|Confirmation de la validité d'une identité|

### Fonctionnement

```
User
  ↓
Identity Provider (IdP)
  ↓
Authentication + Attestation
  ↓
Service Provider (SP)
  ↓
Access
```

### IdP

→ gère les identités et confirme l'authentification.

### SP / RP

→ fournit le service en faisant confiance aux informations de l'IdP.

### Attestation

Attestation = vérification formelle qu'une information est vraie.

Exemple : l'IdP confirme qu'un utilisateur a été authentifié.

### Interoperability

Interoperability = différents systèmes peuvent communiquer et fonctionner ensemble.

Technologies importantes :

- SAML
    
- OAuth
    
- OpenID Connect
    

Elles facilitent notamment la fédération entre plusieurs services cloud.

### SSO vs Federation

|SSO|Federation|
|---|---|
|Une connexion pour plusieurs services|Confiance entre systèmes d'identité|
|Simplifie l'authentification|Permet le partage d'identité entre organisations|
|Peut fonctionner au sein d'une entreprise|Souvent utilisée entre plusieurs organisations|

EXAM :

`SSO = Login once`

`Federation = Trust between identity systems`

`IdP = Authenticates users`

`SP = Provides services`

# 11. Password Security

Les mots de passe sont vulnérables à plusieurs attaques :

- Brute Force → tester de nombreuses combinaisons
    
- Password Theft → vol de mot de passe
    
- Password Reuse → réutilisation d'un mot de passe
    
- Phishing → voler les identifiants en trompant l'utilisateur
    

### Password Policies

|Paramètre|Fonction|
|---|---|
|Length|Longueur minimale|
|Complexity|Exigences sur les caractères|
|Reuse|Empêcher la réutilisation d'anciens mots de passe|
|Expiration|Date d'expiration du mot de passe|
|Age|Durée minimale ou maximale d'utilisation|

### NIST Password Recommendations

Le NIST recommande notamment :

- privilégier la longueur plutôt que la complexité
    
- ne pas imposer systématiquement des caractères spéciaux
    
- autoriser les caractères ASCII et Unicode
    
- autoriser le copy/paste
    
- utiliser des password managers
    
- bloquer les mots de passe connus comme compromis
    
- supprimer les password hints
    
- utiliser le MFA
    
- limiter les tentatives abusives de connexion
    
- stocker les mots de passe avec salting + secure hashing
    
- permettre l'affichage temporaire du mot de passe pour éviter les erreurs
    

⚠️ Les changements périodiques obligatoires ne sont pas toujours recommandés. Ils dépendent de la politique de sécurité et des risques.

### LAN Manager — LM Hash

Ancien mécanisme Windows de stockage des mots de passe.

→ sécurité faible.

Le cours explique que des politiques exigeant au moins 15 caractères permettaient d'éviter le stockage sous forme de hash LM dans certaines anciennes configurations.

EXAM :

`Long passwords > Forced complexity`

`Salt + Secure Hash = Password storage`

`MFA = Additional protection`

# 12. Password Managers

Un Password Manager permet de créer, stocker et gérer des mots de passe.

Exemples :

- Bitwarden
    
- 1Password
    
- Windows Credential Manager
    
- Apple Keychain
    

### Avantages

- génération de mots de passe longs
    
- mots de passe uniques
    
- réduction du password reuse
    
- stockage sécurisé
    
- gestion simplifiée
    

### Risque

Si le coffre est compromis, des identifiants peuvent être exposés.

Exemple du livre :

LastPass — incidents de sécurité en 2022

Des données de coffres clients et d'autres informations sensibles ont été compromises.

EXAM :

`Password Manager = Generate + Store + Manage passwords`

`Password Vault = Secure storage of credentials`

# 13. Passwordless Authentication

Passwordless = authentification sans mot de passe traditionnel.

Peut utiliser :

- Security Keys
    
- Certificates
    
- Biometrics
    
- Authentication Tokens
    

### FIDO2

Standard d'authentification utilisant la cryptographie asymétrique.

```
Security Key
    ↓
Private Key stays on device
    ↓
Public Key registered with service
    ↓
Cryptographic Authentication
    ↓
Access
```

L'utilisateur peut déverrouiller sa clé avec :

- PIN
    
- Fingerprint
    

### FIDO2 Components

|Technologie|Fonction|
|---|---|
|WebAuthn|Authentification web|
|CTAP|Communication entre client et authentificateur|

### Avantages

- réduit les risques liés aux mots de passe
    
- évite de transmettre des clés privées
    
- meilleure résistance au phishing
    

EXAM :

`Passwordless = No traditional password`

`FIDO2 = Public / Private Key Authentication`

`Private Key = Stays on device`

# 14. Multifactor Authentication — MFA

MFA = utiliser plusieurs facteurs d'authentification appartenant à des catégories différentes.

### Les 4 facteurs

|Facteur|Signification|Exemple|
|---|---|---|
|Something you know|Quelque chose que tu sais|Password, PIN|
|Something you have|Quelque chose que tu possèdes|Smartphone, Smartcard, Security Key|
|Something you are|Ce que tu es|Fingerprint, Face, Voice|
|Somewhere you are|Où tu te trouves|GPS, Network Location|

### Exemple MFA

Password + Fingerprint = MFA

Password + Security Key = MFA

⚠️ Deux mots de passe ne constituent pas du MFA.

Ils appartiennent tous les deux à la catégorie Something you know.

### Security Tokens

Deux types principaux :

Hardware Token

→ dispositif physique, comme une clé USB de sécurité.

Software Token

→ application générant des codes d'authentification.

EXAM :

`MFA = Different factor categories`

`Password = Something you know`

`Security Key = Something you have`

`Fingerprint = Something you are`

`GPS = Somewhere you are`

# 15. OTP — One-Time Password

OTP = mot de passe à usage unique.

Permet de réduire les risques liés aux mots de passe volés ou réutilisés.

### TOTP vs HOTP

|TOTP|HOTP|
|---|---|
|Time-Based OTP|HMAC-Based OTP|
|Basé sur le temps|Basé sur un compteur|
|Code change périodiquement|Code change avec un événement|
|Exemple : Google Authenticator|Exemple : token avec bouton|

### TOTP

Time-Based One-Time Password

```
Shared Secret + Current Time
             ↓
          OTP Code
```

→ le code expire après une courte période.

### HOTP

HMAC-Based One-Time Password

```
Shared Secret + Counter
             ↓
          OTP Code
```

→ le compteur évolue lorsqu'un événement se produit.

### SMS OTP

Code envoyé par SMS.

⚠️ Vulnérable à :

- SIM cloning / SIM swapping
    
- SMS interception
    
- VoIP account compromise
    
- phishing
    

### Autres méthodes

Phone Call Authentication

→ validation par appel téléphonique.

Limites : lenteur, coûts, détournement potentiel des appels.

Static Recovery Codes

→ codes pré-générés, stockés ou imprimés.

Ils peuvent permettre une récupération d'accès sans connexion ou dispositif supplémentaire.

⚠️ Ils doivent être protégés contre le vol.

### MFA Attacks

- OTP Phishing → voler et utiliser immédiatement un code.
    
- SIM Swapping → détourner les codes SMS.
    
- MFA Fatigue → multiplier les demandes de validation jusqu'à ce que l'utilisateur accepte.
    
- Device Compromise → voler les codes directement sur l'appareil.
    

EXAM :

`TOTP = Time`

`HOTP = Counter`

`SMS OTP = SIM Swapping Risk`

`MFA Fatigue = Repeated Authentication Requests`

# 16. Biometrics

Biometrics = authentication based on physical or behavioral characteristics.

### Types

|Technologie|Fonction|
|---|---|
|Fingerprint|Empreintes digitales|
|Retina Scan|Vaisseaux sanguins de la rétine|
|Iris Recognition|Motifs de l'iris|
|Facial Recognition|Caractéristiques du visage|
|Voice Recognition|Caractéristiques de la voix|
|Vein Recognition|Réseau des veines|
|Gait Analysis|Façon de marcher|

Les empreintes peuvent être analysées avec des capteurs optiques, ultrasoniques ou capacitifs.

L'iris peut être reconnu à plus grande distance que la rétine.

### FAR vs FRR

Très important pour Security+.

|Métrique|Signification|
|---|---|
|FAR — False Acceptance Rate|Un imposteur est accepté|
|FRR — False Rejection Rate|Un utilisateur légitime est refusé|

### FAR

```
Unauthorized User
       ↓
System ACCEPTS
       ↓
False Acceptance
```

→ problème de sécurité.

### FRR

```
Legitimate User
       ↓
System REJECTS
       ↓
False Rejection
```

→ problème d'accessibilité et d'utilisation.

### ROC

Receiver Operating Characteristic

→ permet d'évaluer le compromis entre faux rejets et fausses acceptations.

En général :

Moins de FRR → risque de davantage de FAR

### IAPMR

Imposter Attack Presentation Match Rate

→ mesure la fréquence à laquelle une tentative d'attaque biométrique réussit.

### Seuils cités dans le livre

FIDO BioLevel1 :

- FRR = 3 %
    
- FAR = 0,01 %
    

### Limites

- erreurs de reconnaissance
    
- caractéristiques physiques difficiles à scanner
    
- acceptation variable par les utilisateurs
    
- nécessité d'une méthode de secours
    

EXAM :

`FAR = False person Accepted`

`FRR = Real person Rejected`

`ROC = FAR / FRR Trade-off`

`IAPMR = Biometric Attack Success`

# 17. Account Types

Différents comptes existent dans une organisation.

|Type|Fonction|
|---|---|
|User Account|Utilisateur standard|
|Privileged Account|Administrateur|
|Shared / Generic Account|Compte utilisé par plusieurs personnes|
|Guest Account|Accès invité et limité|
|Service Account|Compte pour applications ou services|

### User Account

→ compte standard avec permissions limitées.

Exemple : Windows Standard User.

Les actions administratives peuvent nécessiter une élévation de privilèges via UAC.

### Privileged Account

→ possède des droits élevés.

Exemples :

- Windows Administrator
    
- Linux root
    
- membres du groupe wheel
    

⚠️ Ces comptes nécessitent une protection et une surveillance renforcées.

### Shared Account

→ plusieurs utilisateurs partagent un compte.

Problème :

Difficulté à identifier qui a effectué une action.

→ risque pour l'accounting et l'audit.

### Guest Account

→ accès temporaire et permissions très limitées.

### Service Account

→ utilisé par les services et applications.

⚠️ Ne doit normalement pas permettre une connexion interactive.

# 18. Account Lifecycle

Le cycle de vie d'un compte comprend notamment sa création, sa gestion et sa suppression.

### Provisioning

Provisioning = création et configuration d'un compte.

Comprend :

- création du compte
    
- attribution des permissions
    
- attribution des groupes et rôles
    
- accès aux ressources nécessaires
    

### Identity Proofing

Identity Proofing = vérifier la véritable identité d'une personne.

Exemple :

Vérification d'une pièce d'identité avant la création d'un compte bancaire.

### Onboarding

Arrivée d'un employé :

→ création des comptes

→ attribution des droits

→ formation

### Permission Creep

Permission Creep = accumulation progressive de permissions inutiles.

Exemple :

Un employé change de poste, mais conserve ses anciens droits.

Résultat :

→ privilèges excessifs.

### Deprovisioning

Deprovisioning = suppression des accès qui ne sont plus nécessaires.

Comprend :

- retrait des permissions
    
- suppression ou désactivation appropriée des comptes
    
- traitement des données et ressources associées
    

Objectif :

→ empêcher qu'un ancien compte soit utilisé par un attaquant.

Le livre privilégie la suppression des comptes devenus inutiles, lorsque les procédures le permettent.

### Least Privilege

Least Privilege = minimum permissions necessary.

Un utilisateur doit disposer uniquement des droits nécessaires à son travail.

EXAM :

`Provisioning = Create account`

`Identity Proofing = Verify identity`

`Permission Creep = Excessive accumulated permissions`

`Deprovisioning = Remove account/access`

`Least Privilege = Minimum required permissions`

# 19. Privileged Access Management — PAM

PAM = contrôler et sécuriser les comptes privilégiés.

Objectifs :

- limiter les privilèges administratifs
    
- surveiller les comptes sensibles
    
- enregistrer les actions
    
- réduire les accès permanents inutiles
    

### Trois technologies importantes

|Technologie|Fonction|
|---|---|
|JIT Permissions|Permissions temporaires|
|Password Vaulting|Coffre-fort d'identifiants privilégiés|
|Ephemeral Accounts / Credentials|Comptes ou identifiants de courte durée|

### JIT — Just-in-Time

Les permissions sont accordées uniquement lorsqu'elles sont nécessaires.

Exemple :

```
Admin needs access
        ↓
JIT grants privileges
        ↓
Admin performs task
        ↓
Privileges removed
```

→ limite les privilèges permanents et le permission creep.

### Password Vaulting

Les identifiants privilégiés sont stockés dans un coffre sécurisé.

Permet :

- contrôle des accès aux identifiants
    
- journalisation
    
- audit
    
- récupération des identifiants en cas d'urgence
    

### Ephemeral Accounts

Ephemeral = temporary / short-lived.

Compte créé pour une durée limitée.

Exemple :

Un intervenant dispose d'un compte temporaire pour effectuer une opération.

→ le compte est supprimé après utilisation.

EXAM :

`PAM = Privileged Accounts`

`JIT = Temporary Privileges`

`Password Vaulting = Secure Credential Storage`

`Ephemeral = Short-lived Account`

# 20. Access Control Models

Les modèles de contrôle d'accès déterminent qui peut accéder aux ressources.

### Les modèles à connaître

|Modèle|Fonction|
|---|---|
|MAC|Contrôle imposé centralement|
|DAC|Contrôle par le propriétaire|
|RBAC|Contrôle par rôle|
|Rule-Based|Contrôle par règles|
|ABAC|Contrôle par attributs|

## MAC — Mandatory Access Control

Les permissions sont définies par une politique de sécurité centrale.

Les utilisateurs ne peuvent pas les modifier librement.

Exemples :

- environnements militaires
    
- SELinux
    
- Windows Mandatory Integrity Control
    

MAC = Central authority controls access

## DAC — Discretionary Access Control

Le propriétaire d'un fichier décide qui peut y accéder.

Exemple :

Un propriétaire Linux attribue des droits de lecture et d'écriture.

DAC = Owner controls access

## RBAC — Role-Based Access Control

Les permissions dépendent du rôle de l'utilisateur.

Exemple :

|Rôle|Permissions|
|---|---|
|HR|Employee Records|
|Accountant|Financial Data|
|Administrator|System Administration|

### Trois règles RBAC

1. Role Assignment → le rôle doit être attribué.
    
2. Role Authorization → le rôle actif doit être autorisé.
    
3. Permission Authorization → seules les permissions du rôle actif sont utilisables.
    

Un utilisateur peut posséder plusieurs rôles.

Exemple : `sudo` sous Linux permet d'exécuter certaines actions avec des privilèges élevés.

RBAC = Role determines access

## Rule-Based Access Control

Les accès sont déterminés par des règles.

Exemple :

```
IF traffic matches rule
         ↓
Allow or Deny
```

Cas typique : règles de pare-feu.

### ACL — Access Control List

Liste de règles définissant les accès autorisés ou refusés.

⚠️ Rule-Based est parfois appelé RuBAC afin de le différencier de Role-Based RBAC.

Rule-Based = Rules determine access

## ABAC — Attribute-Based Access Control

Les permissions dépendent des attributs associés à l'utilisateur et au contexte.

Exemple :

```
Department = Finance
        +
Role = Manager
        +
Access Conditions
        ↓
Access Granted
```

Utilisé notamment dans :

- applications d'entreprise
    
- bases de données
    
- API
    
- microservices
    
- systèmes de gestion de contenu
    

### Avantage

→ flexible et très précis.

### Inconvénient

→ politiques parfois complexes à gérer.

ABAC = Attributes determine access

# 21. Additional Access Controls

### Time-of-Day Restrictions

Restreindre l'accès selon l'heure.

Exemple :

```
Allowed Login:
08:00 → 18:00
```

Peut être configuré dans Active Directory.

### Least Privilege

Donner uniquement les permissions nécessaires.

→ réduit les conséquences d'une compromission.

### EXAM — Access Control

|Situation|Réponse|
|---|---|
|Administrateur central impose les règles|MAC|
|Propriétaire décide des permissions|DAC|
|Accès basé sur le poste|RBAC|
|Accès basé sur des règles|Rule-Based|
|Accès basé sur les caractéristiques|ABAC|
|Accès autorisé uniquement à certaines heures|Time-of-Day|
|Minimum de permissions|Least Privilege|

# 22. Linux File Permissions

Linux utilise trois catégories d'utilisateurs :

- User (u) → propriétaire
    
- Group (g) → groupe
    
- Others (o) → autres utilisateurs
    

### Permissions

|Permission|Lettre|Valeur|
|---|---|---|
|Read|`r`|4|
|Write|`w`|2|
|Execute|`x`|1|

### Calcul des permissions

|Permissions|Valeur|
|---|---|
|`rwx`|7|
|`rw-`|6|
|`r-x`|5|
|`r--`|4|
|`-wx`|3|
|`-w-`|2|
|`--x`|1|
|`---`|0|

### Exemple

```
-rwxr-xr--
```

Décomposition :

```
-    rwx    r-x    r--
|     |      |      |
Type  User  Group  Others
       7      5      4
```

→ permissions 754.

### chmod

Commande permettant de modifier les permissions.

```
chmod 754 file.txt
```

Résultat :

- User → Read + Write + Execute
    
- Group → Read + Execute
    
- Others → Read
    

### Autre exemple

```
chmod 700 file.txt
```

Résultat :

- User → RWX
    
- Group → aucun accès
    
- Others → aucun accès
    

⚠️ Le premier caractère indique le type :

`- = regular file`

`d = directory`

EXAM :

`Read = 4`

`Write = 2`

`Execute = 1`

`rwx = 7`

`rw- = 6`

`r-x = 5`

# 23. Windows File Permissions

Windows utilise également des permissions pour contrôler l'accès aux fichiers et dossiers.

|Permission|Fonction|
|---|---|
|Full Control|Contrôle complet|
|Modify|Lire et modifier|
|Read & Execute|Lire et exécuter|
|Read|Lecture|
|Write|Écriture|

### Full Control

Permet notamment de :

- lire
    
- écrire
    
- exécuter
    
- modifier
    
- gérer les permissions
    

### Modify

→ permet de modifier les fichiers et dossiers.

### Read & Execute

→ lecture et exécution, sans modification.

### Sécurité

Des permissions incorrectes peuvent faciliter :

- le vol de données
    
- les modifications non autorisées
    
- l'exécution de fichiers malveillants
    
- certaines attaques de Directory Traversal
    

EXAM :

`Linux = rwx / chmod`

`Windows = NTFS-style File Permissions`

`Incorrect Permissions = Unauthorized Access Risk`

# À RETENIR

|Concept|Association|
|---|---|
|IAM|Identity and Access Management|
|AAA|Authentication + Authorization + Accounting|
|Authentication|Verify identity|
|Authorization|Determine permissions|
|Accounting|Track activities|
|Username|Identity claim, not authentication|
|EAP|Authentication Framework|
|CHAP|Challenge-Response|
|802.1X|Network Access Control|
|RADIUS|Network AAA|
|TACACS+|AAA + Granular Command Control|
|Kerberos|Ticket-Based Authentication|
|KDC|Distributes Kerberos Tickets|
|TGT|Initial Authentication Ticket|
|SSO|Login once, multiple services|
|LDAP|Directory Service|
|SAML|XML + SSO + Assertions|
|OAuth|Delegated Authorization|
|OpenID Connect|Authentication|
|Federation|Trust between Identity Systems|
|IdP|Identity Provider|
|SP|Service Provider|
|Attestation|Identity Validation|
|Password Manager|Store + Generate Passwords|
|Passwordless|Authentication without Password|
|FIDO2|Public / Private Key Authentication|
|MFA|Multiple Different Factors|
|TOTP|Time-Based OTP|
|HOTP|Counter-Based OTP|
|FAR|False Acceptance|
|FRR|False Rejection|
|ROC|Biometric Error Trade-off|
|Provisioning|Create Account|
|Deprovisioning|Remove Account/Access|
|Permission Creep|Accumulated Excessive Permissions|
|PAM|Privileged Access Management|
|JIT|Temporary Privileges|
|Password Vaulting|Secure Credential Storage|
|Ephemeral Account|Temporary Account|
|MAC|Central Policy Control|
|DAC|Owner Controls Access|
|RBAC|Role-Based Permissions|
|Rule-Based|Rule-Based Permissions|
|ABAC|Attribute-Based Permissions|
|ACL|Access Control List|
|Least Privilege|Minimum Necessary Permissions|
|chmod|Modify Linux Permissions|

## EXAM — ASSOCIATIONS À CONNAÎTRE

Vérifier l'identité → Authentication

Déterminer les permissions → Authorization

Enregistrer les activités → Accounting

Authentification Wi-Fi / réseau → 802.1X + EAP + RADIUS

Contrôle granulaire des commandes réseau → TACACS+

Authentification avec tickets → Kerberos

Ticket initial Kerberos → TGT

Une connexion pour plusieurs applications → SSO

Accéder à un annuaire d'utilisateurs → LDAP

SSO web avec assertions XML → SAML

Autorisation déléguée → OAuth

Connexion avec une identité externe → OpenID Connect

Confiance entre plusieurs systèmes d'identité → Federation

Fournisseur d'identité → IdP

Vérification formelle d'identité → Attestation

Mot de passe + empreinte digitale → MFA

Authentification cryptographique sans mot de passe → FIDO2

Code OTP basé sur le temps → TOTP

Code OTP basé sur un compteur → HOTP

Utilisateur légitime refusé → FRR

Imposteur accepté → FAR

Création d'un compte → Provisioning

Suppression des accès → Deprovisioning

Accumulation de droits inutiles → Permission Creep

Gestion des comptes administrateurs → PAM

Privilèges uniquement lorsque nécessaires → JIT

Identifiants privilégiés stockés dans un coffre → Password Vaulting

Compte temporaire → Ephemeral Account

Contrôle central imposé → MAC

Propriétaire décide des permissions → DAC

Permissions selon le rôle → RBAC

Permissions selon les règles → Rule-Based

Permissions selon les attributs → ABAC

Permissions minimales nécessaires → Least Privilege

Linux permissions → Read = 4 / Write = 2 / Execute = 1

`rwxr-xr--` → 754

Modifier les permissions Linux → chmod
