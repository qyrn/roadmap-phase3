# Security Assessment & Testing

## Vulnerability Management

**Vulnerability Management** → processus permettant d'**identifier, prioriser et remédier** aux vulnérabilités.

### Identifier les systèmes à scanner

On regarde notamment :

- **Data classification**
    
- Internet/public exposure
    
- Services proposés
    
- Production / Test / Development
    

→ L'**asset inventory** + la **criticality** déterminent la fréquence et la priorité des scans.

---

# Vulnerability Scanning

**Vulnerability Scan** → recherche automatisée de vulnérabilités connues.

### Fréquence

Dépend de :

- **Risk appetite**
    
- Regulatory requirements
    
- Technical constraints
    
- Business constraints
    
- Licensing
    

→ Un environnement très risk-averse peut scanner plus fréquemment.

### Scan sensitivity

Détermine la profondeur des vérifications.

⚠️ Certains **intrusive plugins** peuvent perturber ou endommager un système de production.

→ Tester d'abord sur un **test environment** lorsque possible.

---

# Credentialed vs Noncredentialed Scan

### Noncredentialed

Scanner voit le système **de l'extérieur**.

→ Peut détecter une vulnérabilité sans pouvoir la confirmer précisément.

### Credentialed

Le scanner possède des credentials et peut consulter la configuration du système.

→ **Plus précis**  
→ Peut vérifier si un patch est réellement installé.

⚠️ Utiliser idéalement un compte **read-only / least privilege**.

### Agent-based

Un **agent** est installé directement sur le serveur.

→ Scan **inside-out**  
→ Analyse la configuration locale  
→ Envoie les résultats à la plateforme de vulnerability management.

---

# Scan Perspectives

### External Scan

→ Depuis Internet  
→ Vision d'un attaquant externe

### Internal Scan

→ Depuis le réseau interne  
→ Vision potentielle d'un insider

### Agent / Datacenter Scan

→ Vue plus proche de l'état réel du système.

Les résultats peuvent être influencés par :

- Firewall
    
- Network segmentation
    
- IDS
    
- IPS
    

---

# Scanner Maintenance

Un scanner doit lui-même être sécurisé.

→ Mettre à jour le **scanner software**  
→ Mettre à jour les **vulnerability feeds / plugins**

Les nouveaux plugins permettent de détecter les nouvelles vulnérabilités.

---

# SCAP

**SCAP = Security Content Automation Protocol**

→ Standardisation des informations de sécurité pour automatiser les interactions entre outils de sécurité.

### À connaître

|Acronyme|Signification|Rôle|
|---|---|---|
|**CCE**|Common Configuration Enumeration|Configuration issues|
|**CPE**|Common Platform Enumeration|Product names / versions|
|**CVE**|Common Vulnerabilities and Exposures|Identifie les vulnérabilités|
|**CVSS**|Common Vulnerability Scoring System|Score la sévérité|
|**XCCDF**|Extensible Configuration Checklist Description Format|Checklists|
|**OVAL**|Open Vulnerability and Assessment Language|Tests techniques|

### ⚠️ EXAM

**CVE = identifier/naming d'une vulnérabilité**

**CVSS = score de sévérité**

Ne pas les confondre.

---

# Vulnerability Scanners

### Infrastructure

- **Nessus**
    
- **Qualys**
    
- **Nexpose / Rapid7**
    
- **OpenVAS**
    

→ Détectent des vulnérabilités connues sur les systèmes réseau.

### Application Testing

**SAST — Static**  
→ Analyse le code **sans l'exécuter**.

**DAST — Dynamic**  
→ Exécute l'application et teste ses interfaces.

**IAST — Interactive**  
→ Combine analyse du code + interaction avec l'application.

### Web Application Scanning

Recherche notamment :

- SQL Injection
    
- XSS
    
- CSRF
    

Techniques :  
→ Malicious input  
→ Fuzzing

Outils cités :

- Nikto
    
- Arachni
    
- Nessus
    
- Qualys
    
- Nexpose
    

---

# Scan Results — False Positive / False Negative

### True Positive

→ Vulnérabilité détectée **et réellement présente**.

### False Positive

→ Scanner dit **vulnérable**, mais la vulnérabilité n'existe pas.

### True Negative

→ Scanner dit **pas vulnérable**, et c'est vrai.

### False Negative

→ Scanner dit **pas vulnérable**, alors qu'elle existe.

### EXAM

**False Positive**  
`Scanner: vulnérable ❌`  
`Reality: safe ✅`

**False Negative**  
`Scanner: safe ❌`  
`Reality: vulnerable ✅`

---

# Confirmation

Un analyste doit **confirmer** les vulnérabilités détectées.

Exemples :  
→ Vérifier qu'un patch manque  
→ Vérifier la version de l'OS  
→ Effectuer un test manuel/exploit contrôlé

Les autres sources utiles :

- Logs
    
- **SIEM**
    
- Configuration management systems
    

---

# Common Vulnerabilities

## Patch Management

→ Garder OS, applications et firmware **à jour**.

Une vulnérabilité fréquente dans les scans :  
→ logiciel/OS obsolète → **missing security patch**.

---

## Legacy / Unsupported Systems

**End-of-support (EOL)** → le fournisseur ne fournit plus normalement de security patches.

Solution :  
→ Upgrade vers une version supportée.

Si impossible :

→ **Isolation**  
→ Network restrictions  
→ Increased monitoring  
→ **Compensating controls**

---

## Weak Configurations

Exemples :

- Default settings dangereux
    
- Default credentials
    
- Unsecured accounts
    
- Ports/services inutiles ouverts
    
- Permissions excessives
    

→ Respecter le **Principle of Least Privilege**.

---

## Error Messages / Debug Mode

**Debug mode** → peut révéler :

- Structure de l'application
    
- Database details
    
- Authentication mechanisms
    
- Informations internes
    

→ **Disable debug mode on public-facing systems.**

---

# Insecure Protocols

### Telnet

→ Command-line remote access  
→ **No encryption**

### FTP

→ File transfer  
→ **No built-in security/encryption**

Alternatives :

**Telnet → SSH**

**FTP → SFTP / FTPS**

---

# Weak Encryption

Deux éléments essentiels :

**Encryption algorithm**  
+  
**Encryption key**

Un algorithme faible ou une clé faible/guessable peut être attaqué.

Exemple :  
→ **RC4** → insecure  
→ **AES** → secure alternative citée par le chapitre.

---

# CVSS

**CVSS = Common Vulnerability Scoring System**

→ Standard permettant de mesurer la **sévérité d'une vulnérabilité**.

Score :

**0 → 10**

Utilisé notamment pour **prioriser les réponses**.

## Les 8 métriques

### Exploitability

**AV — Attack Vector**

- **P** → Physical
    
- **L** → Local
    
- **A** → Adjacent
    
- **N** → Network
    

**AC — Attack Complexity**

- L → Low
    
- H → High
    

**PR — Privileges Required**

- N → None
    
- L → Low
    
- H → High
    

**UI — User Interaction**

- N → None
    
- R → Required
    

### Impact

**C — Confidentiality**

**I — Integrity**

**A — Availability**

Chaque impact :  
→ N / L / H

### Scope

**S — Scope**

- **U — Unchanged**
    
- **C — Changed**
    

---

# CVSS Severity

|Score|Rating|
|--:|---|
|**0.0**|None|
|**0.1–3.9**|Low|
|**4.0–6.9**|Medium|
|**7.0–8.9**|High|
|**9.0–10.0**|Critical|

⚠️ **À apprendre par cœur pour Security+.**

---

# Penetration Testing

**Penetration Test** → test **autorisé et légal** dans lequel des professionnels tentent de contourner les contrôles de sécurité comme le ferait un attaquant.

### Hacker Mindset

Le pentester cherche :  
→ **une seule vulnérabilité exploitable**

L'attaquant doit réussir **une fois**.

Le défenseur doit empêcher **toutes les attaques**.

---

# Types de Penetration Testing

### Physical

→ Bâtiments, portes, badges, surveillance.

### Offensive

→ Agir comme un attaquant et exploiter les vulnérabilités.

### Defensive

→ Tester la capacité à **détecter et bloquer** les attaques.

### Integrated

→ Combine **offensive + defensive**.

---

# Knowledge Levels

### Known Environment

→ Pentester possède **beaucoup d'informations** :

- Network diagrams
    
- IP ranges
    
- Credentials
    
- Configurations
    

→ Aussi appelé **white-box** dans la terminologie courante, mais retiens surtout _Known Environment_ pour le chapitre.

### Unknown Environment

→ Aucune information fournie.

→ Pentester doit faire sa propre **reconnaissance**.

### Partially Known Environment

→ Informations partielles.

→ Entre Known et Unknown.

---

# Rules of Engagement — RoE

**RoE** → règles définissant précisément comment le pentest doit être effectué.

À définir notamment :

- **Timeline**
    
- Targets inclus/exclus
    
- Third-party systems concernés
    
- Technical constraints
    
- Data handling
    
- Confidentiality
    
- Expected defensive behavior
    
- Resources
    

---

# Threat Hunting

**Threat Hunting** → chercher activement les **preuves d'une compromission** dans l'environnement.

### Philosophie

**Presumption of Compromise**

→ On part du principe que l'attaquant **a peut-être déjà réussi à entrer**.

Puis :

`Chercher les artifacts → détecter compromise → Contain → Eradicate → Recover`

### ⚠️ Pentest vs Threat Hunting

**Penetration Testing**  
→ « Est-ce que je peux entrer ? »

**Threat Hunting**  
→ « Est-ce que quelqu'un est déjà entré ? Et quelles traces a-t-il laissées ? »

---

# À RETENIR — SECURITY ASSESSMENT

|Concept|Association|
|---|---|
|**Vulnerability Scan**|Find known vulnerabilities|
|**Credentialed Scan**|More accurate / configuration access|
|**Noncredentialed**|External view|
|**Agent-based**|Inside-out|
|**SCAP**|Security automation standard|
|**CVE**|Vulnerability identifier|
|**CVSS**|Vulnerability severity score|
|**False Positive**|Scanner says vulnerable → actually safe|
|**False Negative**|Scanner says safe → actually vulnerable|
|**SAST**|Static / code not executed|
|**DAST**|Dynamic / code executed|
|**IAST**|Static + Dynamic|
|**Pentest**|Authorized attack simulation|
|**Threat Hunting**|Search for evidence of compromise|
|**Known Environment**|Full knowledge|
|**Partially Known**|Partial knowledge|
|**Unknown Environment**|No knowledge|
|**RoE**|Rules of engagement|
|**Legacy System**|Unsupported / no normal patches|
|**Telnet**|Replace with SSH|
|**FTP**|Replace with SFTP/FTPS|

# EXAM — LES PIÈGES À CONNAÎTRE

**CVE ≠ CVSS**

→ CVE = **identifie** la vulnérabilité  
→ CVSS = **score sa sévérité**

**Credentialed ≠ Noncredentialed**

→ Credentialed = accès aux informations/configuration  
→ Noncredentialed = vision externe

**False Positive ≠ False Negative**

→ FP = vulnérabilité annoncée mais inexistante  
→ FN = vulnérabilité réelle mais non détectée

**Pentest ≠ Vulnerability Scan**

→ Scan = **identifier**  
→ Pentest = **tenter d'exploiter**

**Pentest ≠ Threat Hunting**

→ Pentest = tester si on peut entrer  
→ Threat Hunting = chercher si quelqu'un est déjà entré

**Known ≠ Unknown**

→ Known = informations fournies  
→ Unknown = reconnaissance nécessaire

**SAST / DAST**

→ SAST = **Static**  
→ DAST = **Dynamic**

**Telnet → SSH**

**FTP → SFTP / FTPS**

**Unsupported system → Upgrade**, sinon isolation + compensating controls.

