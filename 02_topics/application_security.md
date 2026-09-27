# Chapter 6 — Application Security

## 1. SDLC — Software Development Life Cycle

Le **SDLC** décrit tout le cycle de vie d'un logiciel, de sa conception jusqu'à son retrait. La sécurité doit être intégrée **à chaque étape**, pas ajoutée à la fin.

### Phases à connaître

1. **Planning** → faisabilité, coûts, solutions
    
2. **Requirements** → besoins + **security requirements**
    
3. **Design** → architecture, flux de données, intégrations
    
4. **Coding** → développement + unit testing
    
5. **Testing** → tests formels + **UAT**
    
6. **Training & Transition** → formation + déploiement
    
7. **Operations & Maintenance** → patchs, mises à jour, support
    
8. **Decommissioning** → retrait du logiciel + gestion/destruction des données
    

### Environnements

**Development → Test → Staging → Production**

- **Development** → développeurs
    
- **Test** → QA, tests sans toucher à la production
    
- **Staging** → dernière étape avant production
    
- **Production** → système réel
    

---

# 2. DevOps / DevSecOps / CI/CD

### DevOps

**Development + Operations** → optimiser et automatiser le SDLC.

### DevSecOps

**Dev + Sec + Ops**

→ la sécurité devient une responsabilité partagée pendant **tout le cycle**.

Sécurité intégrée dans :

- Design
    
- Development
    
- Testing
    
- Operations
    

### CI/CD

**CI — Continuous Integration**  
→ code régulièrement envoyé dans un repository partagé + builds/tests automatisés.

**CD — Continuous Deployment/Delivery**  
→ changements testés puis déployés automatiquement.

⚠️ Risque :  
**automatisation rapide → vulnérabilité pouvant être déployée rapidement**

Donc :  
→ automated security testing  
→ logging  
→ monitoring  
→ validation continue

---

# 3. Secure Coding

## OWASP

**OWASP** fournit des bonnes pratiques et outils pour sécuriser les applications.

À retenir :

- Security requirements
    
- Security frameworks/libraries
    
- Secure database access
    
- Encode/Escape data
    
- **Validate all inputs**
    
- MFA + secure password storage
    
- Access controls + **least privilege**
    
- Encryption
    
- Logging & monitoring
    
- Secure error handling
    

---

# 4. API Security

Une **API** permet à des applications/systèmes de communiquer.

Une API mal sécurisée peut permettre :  
→ accès non autorisé  
→ fuite de données  
→ modification de données

Protections :

**Authentication + Authorization + Data scoping + Rate limiting + Input filtering + Logging/Monitoring**

---

# 5. Security Testing

## Static vs Dynamic

|Méthode|Fonctionnement|
|---|---|
|**Static testing**|Analyse le code **sans l'exécuter**|
|**Dynamic testing**|Exécute le code avec différentes entrées|
|**Interactive testing**|Combine static + dynamic|
|**Fuzzing**|Envoie des données invalides/aléatoires|

### Fuzzing

→ cherche notamment :

- input validation issues
    
- logic issues
    
- memory leaks
    
- error handling problems
    

**EXAM :**

> Static = **code sans exécution**  
> Dynamic = **code exécuté**

---

# 6. Injection Attacks

Une injection consiste à faire entrer du **code contrôlé par l'attaquant** dans une application.

## SQL Injection — SQLi

L'attaquant injecte du SQL dans une entrée utilisateur.

**User input → Application → Database**

Si l'entrée est directement intégrée à la requête :  
→ modification de la requête SQL  
→ accès/modification de données

### Blind SQL Injection

L'attaquant ne voit pas directement les résultats.

Deux variantes :

- **Content-based** → observe les différences de réponses
    
- **Timing-based** → observe le temps de réponse
    

**Timing-based :**

`condition vraie → délai`

→ permet progressivement de déduire des informations.

### Protection

**Parameterized queries** → requête précompilée + données séparées du code SQL.

C'est une protection importante contre SQLi.

---

# 7. Autres Injection

### Code Injection

→ injection de code dans l'application.

Exemples :

- SQL injection
    
- LDAP injection
    
- XML injection
    
- DLL injection
    
- XSS
    

### Command Injection

L'application transmet une entrée utilisateur directement à l'OS.

**User input → Application → OS command**

→ l'attaquant peut faire exécuter des commandes système.

---

# 8. Authentication Attacks

## Password attacks

Un attaquant peut obtenir un mot de passe via :

- Social engineering
    
- Traffic non chiffré
    
- Password dumps
    
- Password reuse
    
- Brute force
    
- Default credentials
    

---

# 9. Session Hijacking / Cookie Attacks

Après authentification, le serveur donne souvent un **session cookie** au navigateur.

**Cookie = badge numérique de session**

Si l'attaquant vole le cookie :

→ il peut potentiellement **se faire passer pour l'utilisateur sans connaître son mot de passe**.

### Session Replay

**Vol du cookie → réutilisation du cookie → accès à la session**

Protection importante :

**Secure cookie**

→ cookie transmis uniquement via une connexion chiffrée.

### Pass-the-Hash

L'attaquant récupère un **NTLM hash** et tente de l'utiliser directement pour s'authentifier.

---

# 10. Unvalidated Redirect

L'application accepte une URL fournie par l'utilisateur et redirige vers celle-ci.

**Trusted website → malicious website**

Protection :

→ **validated redirects**  
→ allowlist d'URLs/domaines autorisés.

---

# 11. Authorization Attacks

## IDOR — Insecure Direct Object Reference

L'application utilise directement un identifiant fourni par l'utilisateur :

`documentID=1842`

L'attaquant change :

`1842 → 1843`

Si aucune vérification d'autorisation n'existe :

→ accès au document d'un autre utilisateur.

**IDOR = modifier une référence directe pour accéder à une ressource non autorisée.**

---

# 12. Directory Traversal

Permet de sortir du répertoire normalement autorisé.

Le symbole important :

`..`

Exemple conceptuel :

`/var/www/html/../..`

→ remonter dans l'arborescence.

Objectif possible :  
→ accéder à des fichiers sensibles.

### File Inclusion

Va plus loin :

**Directory Traversal → lire un fichier**

**File Inclusion → exécuter le contenu d'un fichier**

Deux types :

- **LFI — Local File Inclusion** → fichier local
    
- **RFI — Remote File Inclusion** → fichier distant
    

---

# 13. Privilege Escalation

**Normal user → Administrator/root**

L'attaquant exploite une vulnérabilité pour obtenir des privilèges supérieurs.

---

# 14. XSS — Cross-Site Scripting

L'attaquant injecte du **HTML/script** dans une page web.

Le navigateur d'une victime exécute ensuite ce code.

### Reflected XSS

**Attacker input → serveur → réponse → navigateur**

L'input malveillant n'est généralement pas conservé.

### Stored/Persistent XSS

Le script est **stocké sur le serveur**.

→ chaque utilisateur consultant la page peut être affecté.

### Protection

**Input validation**

→ définir exactement quel type de donnée est acceptable.

---

# 15. XSS vs CSRF vs SSRF

Très important pour l'examen :

|Attaque|Idée|
|---|---|
|**XSS**|Faire exécuter du code dans le navigateur de la victime|
|**CSRF/XSRF**|Faire exécuter une action par un utilisateur déjà authentifié|
|**SSRF**|Faire effectuer une requête par le **serveur**|

### CSRF

**Victime connectée → clique → serveur exécute une action**

Protection :  
→ anti-CSRF tokens  
→ vérification de l'origine/referer.

### SSRF

**User input → serveur → URL interne/externe**

Le serveur peut accéder à des ressources non publiques auxquelles l'attaquant n'a normalement pas accès.

---

# 16. Application Security Controls

## Input Validation

Première défense contre énormément d'attaques.

**Allow list > Deny list**

- **Allow list** → définir ce qui est autorisé
    
- **Deny list** → définir ce qui est interdit
    

⚠️ La validation **server-side** est indispensable.

La validation côté navigateur peut être contournée.

### Parameter Pollution

Envoyer plusieurs fois le même paramètre :

`account=123&account=malicious`

→ peut contourner certaines validations mal conçues.

---

## WAF — Web Application Firewall

Firewall spécialisé pour les applications web.

**Internet → WAF → Web Server**

Il inspecte les requêtes et peut bloquer les entrées malveillantes.

---

## Parameterized Queries

Sépare :

**SQL code ≠ User input**

→ protection contre SQL Injection.

---

## Sandboxing

Exécuter une application dans un environnement **isolé et restreint**.

→ permissions limitées  
→ accès fichiers limité  
→ accès OS limité  
→ communication limitée

Utile pour tester du logiciel **nouveau ou non fiable**.

---

# 17. Code Signing

Le développeur signe le code avec sa **private key**.

Le système utilise la **public key** pour vérifier :

→ authenticité  
→ intégrité

### Protection contre :

**Malicious Update**

Exemple :

`Fake update → signature invalide → rejet`

---

# 18. Code Reuse & Software Diversity

### Code Reuse

Utilisation de :

- Libraries
    
- SDKs
    
- Third-party code
    

Avantage :  
→ développement plus rapide.

Risque :  
→ vulnérabilité dans une dépendance = vulnérabilité potentielle dans ton application.

Donc :

**Package monitoring → dépendances à jour + sources fiables.**

### Software Diversity

Éviter de dépendre d'un **unique composant/code/compiler**.

→ réduit les single points of failure.

---

# 19. Code Repository & Integrity

### Code Repository

Centralise :

- source code
    
- version control
    
- changements
    
- rollback
    
- audit/logging
    

### Code Integrity Measurement

On calcule un **cryptographic hash** du code approuvé.

Puis :

`Hash approuvé ≠ Hash actuel`

→ code modifié → investigation nécessaire.

---

# 20. Secure Coding — erreurs classiques

### Source Code Comments

Les commentaires peuvent révéler des informations sensibles.

→ éviter de laisser des commentaires sensibles accessibles en production.

### Error Handling

Les erreurs doivent être gérées proprement.

⚠️ Trop d'informations dans une erreur :

`SQL error → structure DB révélée`

→ facilite l'attaque.

### Hard-Coded Credentials

Credentials directement dans le code.

Exemples :

- backdoor account
    
- API key
    
- password
    

⚠️ particulièrement dangereux si le repository devient public.

### Package Monitoring

→ surveiller les dépendances tierces  
→ détecter les versions vulnérables  
→ appliquer les updates  
→ utiliser des repositories fiables.

---

# 21. Memory Management

## Resource Exhaustion

Un système consomme toute une ressource :

- RAM
    
- Storage
    
- CPU
    
- Processing time
    

→ système ralenti/crash.

### Memory Leak

L'application réserve de la mémoire mais ne la libère pas.

**Memory leak → RAM progressivement consommée → crash**

### Null Pointer Exception

L'application tente de dereference un **null pointer**.

→ crash possible  
→ informations de debugging potentiellement révélées  
→ dans certains cas, contournement de contrôles.

---

# 22. Buffer Overflow

L'application écrit **plus de données que l'espace mémoire prévu**.

**Too much data → overwrite memory → memory injection**

L'objectif peut être de placer des instructions dans une zone mémoire sensible.

### Integer Overflow

Une valeur numérique devient trop grande pour l'espace prévu.

**Buffer Overflow = dépassement mémoire**

**Memory Injection = contenu malveillant placé en mémoire**

---

# 23. Race Conditions

La sécurité dépend de **l'ordre des événements**.

### TOC — Time-of-Check

Moment où le système vérifie une permission.

### TOU — Time-of-Use

Moment où la ressource est réellement utilisée.

### TOCTTOU / TOC/TOU

**Check → changement → Use**

Le contrôle est effectué trop tôt.

Solution :  
→ vérifier les permissions **au moment de chaque requête**, plutôt que conserver une ancienne liste.

### TOE — Target of Evaluation

Composant/mécanisme évalué pendant le test.

---

# 24. Unprotected APIs

Une API non protégée peut permettre à n'importe qui d'appeler certaines fonctions.

Protection :

**Authentication + API key + Encryption**

---

# 25. Automation & Orchestration

## SOAR

**Security Orchestration, Automation and Response**

Permet d'automatiser des actions de sécurité entre plusieurs systèmes.

Un processus est particulièrement adapté à l'automatisation s'il est :

**Repeatable + sans interaction humaine nécessaire**

Exemples :

- User provisioning
    
- Resource provisioning
    
- Guard rails
    
- Security groups
    
- Ticket creation
    
- Escalation
    
- Enable/disable services
    
- CI/testing
    
- API integrations
    

### Scripting

Langages typiques :

**Python / Bash / PowerShell**

→ automatiser logs, scans, alertes, réponses, etc.

---

# 26. Benefits vs Risks — Automation

### Benefits

|Benefit|Idée|
|---|---|
|Efficiency/time saving|moins de travail manuel|
|Enforcing baselines|configurations cohérentes|
|Standard infrastructure|mêmes configurations|
|Secure scaling|scaling sécurisé|
|Employee retention|moins de tâches répétitives|
|Reaction time|réponse plus rapide|
|Workforce multiplier|augmente la capacité de l'équipe|

### Risks

|Risk|Idée|
|---|---|
|Complexity|automatisation difficile à maintenir|
|Cost|outils + formation|
|Single point of failure|un script défectueux peut tout affecter|
|Technical debt|scripts vieillissants|
|Supportability|maintenance continue|

Le livre indique explicitement que ces listes sont directement liées aux objectifs Security+ et constituent donc du **contenu à mémoriser**.

---

# À RETENIR

|Concept|Association|
|---|---|
|**SDLC**|Cycle de vie du logiciel|
|**DevSecOps**|Security intégrée à DevOps|
|**CI/CD**|Build/test/deployment automatisés|
|**Static testing**|Code non exécuté|
|**Dynamic testing**|Code exécuté|
|**Fuzzing**|Entrées aléatoires/invalides|
|**SQLi**|Injection SQL|
|**Command injection**|Injection de commandes OS|
|**Session hijacking**|Vol d'une session existante|
|**Session replay**|Réutilisation d'un cookie volé|
|**IDOR**|Accès à une ressource via référence modifiée|
|**Directory traversal**|`..` → sortir du répertoire|
|**LFI**|Inclusion fichier local|
|**RFI**|Inclusion fichier distant|
|**Privilege escalation**|User → Admin/root|
|**XSS**|Script exécuté dans le navigateur|
|**CSRF**|Faire agir une victime authentifiée|
|**SSRF**|Faire agir le serveur|
|**Input validation**|Contrôler les entrées|
|**WAF**|Protection applicative web|
|**Parameterized query**|Protection SQLi|
|**Sandbox**|Isolation|
|**Code signing**|Authenticité + intégrité|
|**Buffer overflow**|Trop de données → mémoire|
|**Race condition**|Sécurité dépendante de l'ordre|
|**TOC**|Time-of-Check|
|**TOU**|Time-of-Use|
|**TOCTTOU**|Check trop tôt → Use plus tard|
|**Memory leak**|Mémoire non libérée|
|**SOAR**|Orchestration + automation + response|

## EXAM — ASSOCIATIONS À CONNAÎTRE

**SQL injection** → malicious SQL dans une entrée  
**XSS** → script injecté exécuté par le navigateur  
**CSRF** → utilisateur authentifié trompé pour effectuer une action  
**SSRF** → serveur trompé pour effectuer une requête  
**IDOR** → modification d'un ID pour accéder à une autre ressource  
**Directory traversal** → `..`  
**LFI/RFI** → exécution d'un fichier local/distant  
**Buffer overflow** → trop de données dans une zone mémoire  
**Race condition** → dépend de l'ordre des événements  
**TOC** → vérification  
**TOU** → utilisation  
**Sandbox** → environnement isolé  
**Code signing** → private key signe / public key vérifie  
**Static** → ne lance pas le code  
**Dynamic** → lance le code  
**Fuzzing** → données invalides/aléatoires  
**Parameterized query** → protection contre SQLi  
**WAF** → filtre les requêtes web  
**DevSecOps** → sécurité intégrée au DevOps  
**SOAR** → automatisation/orchestration de la sécurité