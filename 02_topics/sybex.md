# Sybex — CompTIA Security+ (Chapitres 1 et 2)

# Cybersecurity Objectives

**CIA Triad :**

**Confidentiality :**  
Empêcher les personnes non autorisées d'accéder aux informations sensibles.

**Integrity :**  
Empêcher les modifications non autorisées des informations ou des systèmes.

**Availability :**  
S'assurer que les informations et systèmes sont disponibles lorsque les utilisateurs autorisés en ont besoin.

**Non-repudiation :**  
Empêcher quelqu'un de nier avoir effectué une action.  
→ Exemple : Digital signatures

---

# DAD Triad

Les 3 principales menaces en cybersécurité :

**Disclosure :**  
Exposition d'informations sensibles à des personnes non autorisées.  
→ Viole la **Confidentiality**  
→ Vol de données = **Data exfiltration**

**Alteration :**  
Modification non autorisée d'informations.  
→ Viole l'**Integrity**

**Denial :**  
Empêcher un utilisateur autorisé d'accéder à une information ou un système.  
→ Viole l'**Availability**  
→ Exemple : DDoS

---

# Risk Categories

**Financial Risk :**  
Pertes financières causées par un incident.  
→ Réparation, incident response, perte de revenus

**Reputational Risk :**  
Perte de confiance et mauvaise réputation après un incident.  
→ Clients qui perdent confiance

**Strategic Risk :**  
Le problème empêche l'entreprise d'atteindre ses objectifs importants.  
→ Retard ou échec d'un projet

**Operational Risk :**  
Le problème perturbe les opérations quotidiennes.  
→ Retards, ralentissements, travail manuel

**Compliance Risk :**  
L'entreprise ne respecte plus une loi ou une réglementation.  
→ Amendes, sanctions

Un même incident peut provoquer **plusieurs types de risques**.

---

# Control Objectives / Gap Analysis

**Control Objective :**  
L'état de sécurité que l'organisation souhaite atteindre.

**Security Control :**  
Mesure concrète permettant d'atteindre cet objectif.

**Gap Analysis :**  
Comparer l'objectif de sécurité avec les contrôles réellement présents.

Si les contrôles ne permettent pas d'atteindre l'objectif → **Gap**

Un gap représente un risque potentiel qui doit être corrigé.

---

# Security Control Categories

Les catégories répondent à :

**"QUI ou QUOI réalise le contrôle ?"**

**Technical :**  
Contrôles qui agissent dans l'espace numérique.  
→ Firewall, ACL, IPS, Encryption

**Managerial :**  
Contrôles liés à la gestion des risques, aux politiques et à la planification.  
→ Risk assessments, Security planning

**Operational :**  
Processus utilisés pour gérer la technologie de manière sécurisée.  
→ User access reviews, Log monitoring, Vulnerability management

**Physical :**  
Contrôles qui agissent dans le monde physique pour protéger les systèmes et infrastructures.  
→ Serrures, clôtures, éclairage, extincteurs, alarmes

---

# Security Control Types

Les types répondent à :

**"QUEL EST LE BUT du contrôle ?"**

**Preventive :**  
Empêche un problème avant qu'il arrive.  
→ Firewall, Encryption

**Deterrent :**  
Décourage un attaquant d'essayer.  
→ Guard dogs, barbed wire fences, warning signs

**Detective :**  
Détecte un événement de sécurité qui a déjà eu lieu.  
→ IDS, logs, motion detectors

**Corrective :**  
Corrige un problème qui a déjà eu lieu.  
→ Restaurer une backup après un ransomware

**Compensating :**  
Utilise une protection alternative lorsqu'on ne peut pas appliquer le contrôle original.  
→ Isoler un système vulnérable sur un réseau séparé

**Directive :**  
Indique aux utilisateurs ce qu'ils doivent faire pour atteindre les objectifs de sécurité.  
→ Policies, procedures, training

---

# Compensating Controls

Un **Compensating Control** permet d'atteindre un objectif de sécurité avec une **méthode alternative** lorsque le contrôle original ne peut pas être utilisé.

Exemple :

Un ancien OS doit être conservé car une application ne fonctionne que dessus.

Normalement → utiliser un OS à jour.

Impossible → isoler la machine sur un réseau séparé.

→ Le réseau isolé devient le **Compensating Control**.

Pour PCI DSS, le contrôle compensatoire doit :

- Respecter l'intention du contrôle original
    
- Fournir un niveau de protection similaire
    
- Être suffisamment fort pour compenser le risque
    

Il peut notamment être utilisé pour une **exception temporaire**.

---

# Data States

**Data at Rest :**  
Données stockées.  
→ Disque dur, cloud, backup

**Data in Transit :**  
Données qui circulent sur un réseau.  
→ Communication entre deux systèmes

**Data in Use :**  
Données actuellement utilisées par un système.  
→ Données présentes en mémoire pendant leur traitement

---

# Data Protection

**Encryption :**  
Rend les données illisibles sans la clé de déchiffrement.  
→ Protège les données **at rest** et **in transit**

**Data Loss Prevention (DLP) :**  
Systèmes permettant d'empêcher la perte ou le vol de données sensibles.  
→ Peut détecter et bloquer une tentative d'exfiltration.

### Types de DLP :

**Agent-based / Host-based DLP :**  
Logiciel installé directement sur les machines.

**Agentless / Network-based DLP :**  
Système placé sur le réseau qui surveille les données sortantes.

### Méthodes de détection DLP :

**Pattern Matching :**  
Recherche des formats ou mots caractéristiques de données sensibles.  
→ Numéro de carte bancaire, "Top Secret", etc.

**Watermarking :**  
Ajoute une marque électronique à un document afin de pouvoir l'identifier et le suivre.

---

# Data Minimization

Réduire la quantité de données sensibles conservées afin de réduire les risques.

Si les données ne sont plus nécessaires → **Destroy / Delete**

Si elles doivent être conservées → **Desidentification / Obfuscation**

**Hashing :**  
Transforme une donnée en une valeur de hash.  
→ Impossible de récupérer directement la valeur originale.

**Tokenization :**  
Remplace une donnée sensible par un identifiant unique.  
→ Réversible avec une **lookup table**

**Masking :**  
Cache une partie ou la totalité d'une donnée sensible.  
→ Exemple : XXXX-XXXX-XXXX-1234

---

# Access Restrictions

**Geographic Restrictions :**  
Limiter l'accès selon la localisation géographique.  
→ Base de données accessible uniquement depuis certains pays/régions.

**Permission Restrictions :**  
Limiter l'accès selon le rôle ou les autorisations de l'utilisateur.  
→ Seuls certains employés peuvent accéder aux données financières.

---

# Segmentation / Isolation

**Segmentation :**  
Placer des systèmes sensibles sur des réseaux séparés avec des communications limitées.

**Isolation :**  
Couper complètement un système des réseaux extérieurs.

→ **Isolation = plus strict que Segmentation**

---

# À RETENIR - TERMES ANGLAIS

### CIA Triad

**Confidentiality** → empêcher les personnes non autorisées de voir les données

**Integrity** → empêcher les modifications non autorisées

**Availability** → garder les systèmes et données accessibles

**Non-repudiation** → empêcher quelqu'un de nier avoir effectué une action

---

### DAD Triad

**Disclosure** → divulgation / fuite de données

**Alteration** → modification des données

**Denial** → empêcher l'accès

---

### Control Categories

**Technical** → technologie / systèmes

**Managerial** → management / règles / gestion

**Operational** → personnes / processus

**Physical** → monde physique / infrastructure

---

### Control Types

**Preventive** → **STOP** le problème

**Deterrent** → **DISCOURAGE** l'attaquant

**Detective** → **FIND** le problème

**Corrective** → **FIX** le problème

**Compensating** → **ALTERNATIVE** au contrôle original

**Directive** → **TELL** quoi faire

---

### Data States

**Data at Rest** → données stockées

**Data in Transit** → données qui circulent

**Data in Use** → données utilisées par le système

---

### Data Protection

**Encryption** → rendre les données illisibles sans clé

**Hashing** → transformer en hash, non réversible directement

**Tokenization** → remplacer par un token, réversible avec une lookup table

**Masking** → cacher une partie des données

**DLP** → empêcher la perte / exfiltration de données

**Pattern Matching** → rechercher des motifs de données sensibles

**Watermarking** → marquer les données pour pouvoir les identifier

**Segmentation** → séparer les réseaux

**Isolation** → couper complètement les connexions extérieures

-----

# Cybersecurity Threats

Les **Threat Actors** sont les personnes ou groupes qui peuvent représenter une menace pour une organisation. Ils se différencient principalement par :

- **Internal vs. External** → viennent de l'intérieur ou de l'extérieur
    
- **Sophistication / Capability** → niveau de compétence technique
    
- **Resources / Funding** → temps et argent disponibles
    
- **Intent / Motivation** → raison de l'attaque
    

Ces caractéristiques permettent d'identifier le type d'attaquant et de mieux choisir les protections.

---

# Hacker Hats

### White Hat

Attaquant **autorisé** qui cherche des vulnérabilités pour améliorer la sécurité.

→ Pentester  
→ Security researcher  
→ Travaille avec l'autorisation de l'organisation

### Black Hat

Attaquant **non autorisé** avec une intention malveillante.

→ Cherche à compromettre la **Confidentiality, Integrity ou Availability**

### Gray Hat

Attaquant qui agit **sans autorisation**, mais qui cherche généralement à révéler les vulnérabilités plutôt qu'à causer directement des dégâts.

→ Bonne intention ≠ légal

Un Gray Hat peut tout de même enfreindre la loi.

---

# Threat Actors

## Unskilled Attackers / Script Kiddies

Attaquants avec peu de compétences techniques.

Ils utilisent principalement :

→ Automated tools  
→ Scripts trouvés sur Internet  
→ Outils de DoS, malware, ransomware, etc.

Ils choisissent souvent des cibles vulnérables **au hasard**.

### Caractéristiques

- Faible compétence
    
- Peu de ressources
    
- Souvent seuls
    
- Peu de temps et d'argent
    
- Motivés par le défi ou l'envie de prouver leurs compétences
    

⚠️ Même un attaquant peu compétent peut être dangereux car les outils d'attaque sont facilement accessibles.

---

## Hacktivists

Hackers motivés par une **cause politique, idéologique ou sociale**.

→ Defacement d'un site  
→ DDoS  
→ Publication d'informations

Ils pensent généralement agir pour le **greater good**.

Leur niveau peut aller de très faible à très élevé.

### À retenir

**Hacktivist = hacking + activism**

La peur d'être arrêté peut être moins efficace contre eux car ils peuvent considérer leur arrestation comme un sacrifice pour leur cause.

---

## Organized Crime

Groupes criminels dont l'objectif principal est le **Financial Gain**.

→ Ransomware  
→ Fraud  
→ Credit card theft  
→ BEC  
→ DDoS  
→ Data theft  
→ Dark web

### Caractéristiques

- Motivation → **argent**
    
- Compétence → moyenne à élevée
    
- Ressources → importantes
    
- Cherchent généralement à rester discrets
    

Ils sont prêts à investir du temps et de l'argent pour obtenir un retour financier.

---

## Nation-State / APT

Les **Advanced Persistent Threats (APT)** sont généralement associés à des acteurs disposant de très importantes ressources, notamment des États.

### APT signifie :

**Advanced**  
→ Techniques sophistiquées

**Persistent**  
→ Attaques qui peuvent durer très longtemps

**Threat**  
→ Menace ciblée contre une organisation ou une cible stratégique

### Caractéristiques

- Très haute compétence
    
- Beaucoup de ressources
    
- Beaucoup de temps
    
- Attaques très ciblées
    
- Peuvent rester actives pendant des années
    

### Motivations

→ Political objectives  
→ Espionage  
→ Vol de propriété intellectuelle  
→ Avantage économique

---

# Zero-Day Attacks

Une **Zero-Day Vulnerability** est une vulnérabilité inconnue du fournisseur ou pour laquelle aucun correctif n'est encore disponible.

Une attaque qui exploite cette vulnérabilité est une :

**Zero-Day Attack**

### Pourquoi c'est dangereux ?

→ Le fournisseur ne connaît pas encore la vulnérabilité  
→ Aucun patch disponible  
→ Les défenses peuvent être incapables de bloquer l'exploitation

Les APT peuvent rechercher eux-mêmes des vulnérabilités inconnues et les conserver pour une utilisation future.

→ Exemple connu : **Stuxnet**

---

# Insider Threat

Un **Insider Threat** vient d'une personne qui possède déjà un accès autorisé.

Cela peut être :

→ Employee  
→ Contractor  
→ Vendor  
→ Autre personne disposant d'un accès légitime

L'insider peut utiliser cet accès pour :

→ Disclosure de données  
→ Alteration d'informations  
→ Disruption des opérations

### Motivations possibles

- Financial gain
    
- Revenge
    
- Activism
    
- Frustration
    
- Mécontentement
    

### Pourquoi c'est dangereux ?

L'insider possède déjà :

→ Access  
→ Knowledge of the environment

Les **Behavioral Assessments** peuvent aider à identifier des comportements inhabituels.

---

# Shadow IT

**Shadow IT** = utilisation de technologies ou services **non approuvés par l'organisation**.

Exemple :

Un employé utilise son compte personnel Dropbox pour stocker ou synchroniser des fichiers professionnels.

⚠️ Shadow IT n'est pas forcément malveillant.

Le problème est que les données peuvent se retrouver chez des fournisseurs que l'entreprise ne contrôle pas.

### À retenir

**Shadow IT = technologie utilisée sans approbation de l'IT**

Sa présence peut également indiquer que les besoins des employés ne sont pas correctement couverts par l'équipe IT officielle.

---

# Competitors

Les concurrents peuvent réaliser de la **Corporate Espionage** pour obtenir un avantage commercial.

Ils peuvent chercher :

→ Customer information  
→ Proprietary software  
→ Product development plans  
→ Intellectual property  
→ Confidential business information

Ils peuvent obtenir ces informations :

→ Directement  
→ Via un disgruntled insider  
→ Via des informations vendues sur le dark web

---

# Attacker Motivations

Les attaquants peuvent avoir différentes motivations.

### Data Exfiltration

Obtenir des données sensibles ou propriétaires.

→ Customer data  
→ Intellectual property

### Espionage

Voler des informations secrètes.

→ Nation-state espionage  
→ Corporate espionage

### Service Disruption

Interrompre ou détruire des services importants.

→ Banking systems  
→ Healthcare networks

### Blackmail

Menacer la victime pour obtenir de l'argent ou autre chose.

→ "Pay us or we'll release your data."

### Financial Gain

Chercher à gagner de l'argent.

→ Fraud  
→ Theft  
→ Ransomware

### Philosophical / Political Belief

Attaque motivée par une idéologie ou une cause politique.

→ Hacktivists

### Ethical

Chercher à découvrir des vulnérabilités afin d'améliorer la sécurité.

→ White-hat hacking  
→ Pentesting

### Revenge

Se venger d'une personne ou d'une organisation.

### Disruption / Chaos

Créer du chaos et perturber les opérations.

### War

Utiliser des cyberattaques dans le contexte d'un conflit militaire.

---

# Attack Surface vs. Threat Vector

## Attack Surface

L'**Attack Surface** représente l'ensemble des systèmes, applications ou services qu'un attaquant pourrait exploiter.

→ Plus l'attack surface est grande, plus il existe potentiellement de possibilités d'attaque.

### Objectif de sécurité

**Reduce the Attack Surface**

→ Désactiver les services inutiles  
→ Réduire les accès  
→ Corriger les vulnérabilités

## Threat Vector

Le **Threat Vector** est le **moyen utilisé pour obtenir l'accès**.

### Exemple

Un serveur vulnérable = **Attack Surface**

Une vulnérabilité exploitée pour entrer = **Threat Vector**

---

# Common Threat Vectors

## Message-Based

Les messages sont un vecteur d'attaque très courant.

→ Email  
→ SMS  
→ IM  
→ Voice calls  
→ Social media

### Exemples

**Phishing** → email frauduleux

**Smishing** → phishing par SMS

**Vishing** → phishing par appel vocal

Les réseaux sociaux peuvent également être utilisés pour récupérer des informations sur une victime.

---

## Wired Networks

Un attaquant peut obtenir un accès physique à une organisation puis utiliser :

→ Un network jack non sécurisé  
→ Un ordinateur accessible  
→ Un network device

⚠️ Principe important :

**Si un attaquant peut physiquement toucher un équipement, il faut considérer que cet équipement peut être compromis.**

→ Importance de la **Physical Security**

---

## Wireless Networks

Les réseaux Wi-Fi peuvent être attaqués sans accès physique direct au bâtiment.

Exemple :

→ Attaquant dans un parking  
→ Wi-Fi mal sécurisé  
→ Connexion au réseau

Les appareils Bluetooth mal configurés peuvent également permettre des connexions non autorisées.

---

## Systems

Un système peut devenir un **Threat Vector** à cause de sa configuration ou de ses logiciels.

Exemples :

→ Ports inutiles ouverts  
→ Default credentials  
→ Software vulnerabilities  
→ Legacy systems  
→ Unsupported operating systems

### À retenir

**Default credentials + unnecessary open ports + unpatched software = attack opportunities**

---

## Files and Images

Un fichier peut contenir du **malicious code**.

L'attaquant doit ensuite convaincre l'utilisateur de l'ouvrir.

→ Malicious document  
→ Malicious image  
→ Malware attachment

Le fichier peut être envoyé par email ou stocké sur un serveur de fichiers.

---

## Removable Devices

Les périphériques amovibles peuvent être utilisés pour distribuer du malware.

→ USB drive  
→ External storage

Exemple classique :

Un attaquant abandonne des clés USB dans un lieu public.

Une personne trouve la clé → la branche → malware.

### Principe

**Curiosity can become an attack vector.**

---

## Cloud

Le Cloud constitue également une **Attack Surface**.

Les attaquants peuvent rechercher :

→ Improper access controls  
→ Vulnerable cloud systems  
→ Exposed API keys  
→ Exposed passwords  
→ Publicly accessible files

### À retenir

**Cloud security doit faire partie intégrante du programme de sécurité.**

---

# Supply Chain

La **Supply Chain** correspond aux fournisseurs et services dont dépend une organisation.

→ Hardware providers  
→ Software providers  
→ Service providers  
→ MSPs

Un attaquant peut attaquer le fournisseur plutôt que l'organisation directement.

### Exemples

**Hardware**

Modifier un équipement avant sa livraison.

→ Backdoor intégrée

**Software**

Modifier un logiciel avant sa distribution.

→ Vulnerability  
→ Backdoor

**Software Updates**

Compromettre un mécanisme officiel de mise à jour.

→ Le logiciel malveillant arrive via une update légitime.

**MSP**

Compromettre un **Managed Service Provider** pour ensuite accéder aux systèmes de ses clients.

### Pourquoi c'est dangereux ?

L'organisation peut faire confiance au fournisseur et donc ne pas détecter immédiatement la compromission.

→ **Third-party risk**

Une bonne **Vendor Management** permet d'identifier et réduire ces risques.

---

# À RETENIR - TERMES ANGLAIS

## Threat Actor Characteristics

**Internal** → vient de l'organisation

**External** → vient de l'extérieur

**Sophistication / Capability** → niveau de compétence

**Resources / Funding** → ressources disponibles

**Intent / Motivation** → objectif de l'attaquant

---

## Hacker Hats

**White Hat** → autorisé / éthique

**Black Hat** → malveillant / non autorisé

**Gray Hat** → non autorisé mais cherche généralement à révéler les vulnérabilités

---

## Threat Actors

**Script Kiddie** → attaquant peu compétent utilisant des outils existants

**Hacktivist** → hacking pour une cause politique / idéologique

**Organized Crime** → **Financial Gain**

**Nation-State / APT** → très compétent, très financé, attaque persistante

**Insider Threat** → personne disposant déjà d'un accès autorisé

**Shadow IT** → technologie non approuvée par l'organisation

**Competitor** → Corporate Espionage

---

## Motivations

**Data Exfiltration** → voler des données

**Espionage** → voler des secrets

**Service Disruption** → interrompre un service

**Blackmail** → extorquer / faire chanter

**Financial Gain** → gagner de l'argent

**Philosophical / Political Belief** → idéologie / politique

**Ethical** → améliorer la sécurité

**Revenge** → vengeance

**Disruption / Chaos** → provoquer le chaos

**War** → conflit militaire

---

## Attack Surface / Vector

**Attack Surface** → ce qui peut être attaqué

**Threat Vector** → moyen utilisé pour obtenir l'accès

---

## Common Threat Vectors

**Phishing** → phishing par email

**Smishing** → phishing par SMS

**Vishing** → phishing vocal

**Wired Network** → réseau filaire

**Wireless Network** → Wi-Fi / Bluetooth

**Systems** → OS, logiciels, ports, credentials

**Files / Images** → fichiers malveillants

**Removable Devices** → USB / supports amovibles

**Cloud** → services et ressources Cloud

**Supply Chain** → fournisseurs / partenaires

**MSP** → Managed Service Provider

---

# EXAM - LES ASSOCIATIONS À CONNAÎTRE

**Ransomware + argent**  
→ **Organized Crime / Financial Gain**

**Cause politique / idéologique**  
→ **Hacktivist**

**Très sophistiqué + très financé + attaque longue**  
→ **APT / Nation-State**

**Employé avec accès légitime qui attaque**  
→ **Insider Threat**

**Technologie non approuvée par l'IT**  
→ **Shadow IT**

**Concurrent qui vole des secrets commerciaux**  
→ **Corporate Espionage**

**Vulnérabilité inconnue + aucun patch**  
→ **Zero-Day**

**Email frauduleux**  
→ **Phishing**

**SMS frauduleux**  
→ **Smishing**

**Appel frauduleux**  
→ **Vishing**

**Ce qui peut être attaqué**  
→ **Attack Surface**

**Moyen utilisé pour entrer**  
→ **Threat Vector**

**Attaque via un fournisseur**  
→ **Supply Chain Attack**

**Compromission d'un fournisseur de services IT**  
→ **MSP / Supply Chain**

**Outil de hacking utilisé par un débutant**  
→ **Script Kiddie**

**Hacker autorisé**  
→ **White Hat**

**Hacker malveillant**  
→ **Black Hat**

**Hacker sans autorisation mais cherchant à révéler une faille**  
→ **Gray Hat**

---

# Threat Data and Intelligence

**Threat Intelligence** = ensemble des informations, ressources et activités permettant aux professionnels de la cybersécurité de comprendre les menaces actuelles et d'anticiper les risques futurs.

---

# Threat Intelligence

Une organisation utilise la Threat Intelligence pour :

→ connaître les menaces actuelles  
→ identifier les vulnérabilités  
→ améliorer ses défenses  
→ anticiper les risques  
→ détecter une compromission

Les **Threat Feeds** fournissent des informations régulièrement mises à jour sur les menaces.

Ils peuvent contenir :

- **IP addresses**
    
- **Hostnames**
    
- **Domains**
    
- **Email addresses**
    
- **URLs**
    
- **File hashes**
    
- **File paths**
    
- **CVE numbers**
    
- Informations sur les threat actors
    
- Motivations et méthodes des attaquants
    

---

# IoC - Indicators of Compromise

**IoC** = signe indiquant qu'une attaque ou compromission a probablement eu lieu.

Exemples :

→ File signatures  
→ Log patterns  
→ Traces laissées par un attaquant

Les IoCs permettent donc de rechercher des preuves d'une attaque dans les systèmes.

---

# Vulnerability Databases

Les bases de données de vulnérabilités permettent de :

→ connaître les vulnérabilités découvertes  
→ orienter les efforts de défense  
→ comprendre les exploits utilisés ou développés

Les **CVE** font partie des informations couramment utilisées dans les Threat Feeds.

---

# Open Source Intelligence - OSINT

**OSINT** = Threat Intelligence provenant de **sources publiques**.

Exemples de sources :

→ Government websites  
→ Security vendors  
→ Security communities  
→ Public threat feeds  
→ Technical publications

Le principal problème n'est pas forcément de trouver des informations, mais de déterminer :

→ si elles sont **reliable**  
→ si elles sont **up-to-date**  
→ si elles sont **relevant**

---

# Government / Public Sources

Exemples importants :

**CISA**  
→ Cybersecurity & Infrastructure Security Agency

**DC3**  
→ Department of Defense Cyber Crime Center

**AIS**  
→ Automated Indicator Sharing

**ISAOs**  
→ Information Sharing and Analysis Organizations

D'autres pays disposent également de leurs propres organismes de cybersécurité.

---

# Vendor Intelligence

Les fournisseurs de sécurité peuvent publier leurs propres informations.

Exemples :

→ Microsoft Threat Intelligence  
→ Cisco Security Advisories  
→ Cisco Talos

Ils peuvent fournir :

→ Threat Research  
→ Security Advisories  
→ Reputation information  
→ Threat feeds

---

# Dark Web

Le **Dark Web** utilise plusieurs couches de chiffrement pour permettre des communications anonymes.

Il peut être utilisé par des attaquants pour :

→ vendre des credentials volés  
→ vendre des données volées  
→ partager des informations

Les équipes de Threat Intelligence peuvent rechercher leurs propres credentials sur les marketplaces du Dark Web.

### ⚠️ Point important

Si les credentials d'une organisation apparaissent soudainement sur le Dark Web :

→ cela peut indiquer qu'une **attaque réussie a eu lieu**  
→ une investigation doit être menée.

---

# Proprietary / Closed-Source Intelligence

**Closed-Source Intelligence** = intelligence provenant de sources privées ou propriétaires.

Elle peut être produite par :

→ Security vendors  
→ Governments  
→ Security organizations

Ces organisations peuvent utiliser :

→ Custom tools  
→ Proprietary research  
→ Custom analysis models  
→ Private threat feeds

### Pourquoi utiliser du Closed-Source ?

→ Garder les données secrètes  
→ Vendre/licencier l'intelligence  
→ Protéger les méthodes et sources  
→ Empêcher les threat actors de savoir ce qui est surveillé

---

# Threat Feeds

Un **Threat Feed** fournit des informations actualisées sur les menaces.

⚠️ Un problème fréquent :

Un feed peut être **trop lent**.

Une vulnérabilité peut être exploitée avant que le fournisseur ne fournisse une règle de détection.

### Bonne pratique

Utiliser **plusieurs Threat Feeds** et les comparer.

→ Un feed peut publier une information avant les autres.

**Multiple reliable feeds > single feed**

---

# Threat Maps

Les **Threat Maps** représentent géographiquement les menaces et attaques.

Elles peuvent donner une vision générale du Threat Landscape.

⚠️ Mais :

**Geographic attribution = unreliable**

Pourquoi ?

Les attaquants peuvent passer par :

→ Cloud services  
→ Compromised networks  
→ Proxies / relais

L'adresse géographique affichée peut donc ne **pas être la véritable origine de l'attaque**.

---

# Assessing Threat Intelligence

Avant de faire confiance à une information, il faut l'évaluer selon **3 critères principaux** :

### 1. Timely

L'information est-elle **à jour** ?

→ Une information trop ancienne peut faire rater une menace.

### 2. Accurate

L'information est-elle **correcte** ?

→ Peut-on lui faire confiance ?  
→ Est-elle confirmée par plusieurs sources ?

### 3. Relevant

L'information concerne-t-elle **réellement notre environnement** ?

Une information peut être :

→ récente  
→ exacte  
→ mais complètement **irrelevant** pour notre organisation.

---

# Confidence Score

Le **Confidence Score** indique à quel point on peut faire confiance à une information de Threat Intelligence.

### Exemple de classification

**Confirmed - 90–100**

→ Confirmé par plusieurs sources ou analyse directe.

**Probable - 70–89**

→ Très probable mais pas directement confirmé.

**Possible - 50–69**

→ Certains éléments correspondent, mais pas confirmé.

**Doubtful - 30–49**

→ Possible mais peu probable ou impossible à confirmer.

**Improbable - 2–29**

→ Peu probable ou contredit par d'autres informations.

**Discredited - 1**

→ Information confirmée comme incorrecte.

---

# STIX

**STIX = Structured Threat Information eXpression**

STIX est un langage permettant de **standardiser et structurer les Threat Intelligence data**.

Il permet notamment de représenter :

→ Attack patterns  
→ Identities  
→ Malware  
→ Threat actors  
→ Tools

Les informations peuvent ensuite être utilisées par des systèmes automatisés.

### À retenir

**STIX = structure / format des Threat Intelligence**

---

# TAXII

**TAXII = Trusted Automated eXchange of Intelligence Information**

TAXII est un **protocole d'échange** permettant de transmettre des Cyber Threat Intelligence.

→ Fonctionne au niveau application  
→ Utilise HTTPS  
→ Conçu pour supporter l'échange de données **STIX**

### Mémo

**STIX = WHAT / FORMAT**

**TAXII = HOW / EXCHANGE**

---

# Multiple Threat Feeds

Utiliser un seul Threat Feed peut être insuffisant.

Les organisations peuvent utiliser plusieurs feeds pour obtenir :

→ plus d'informations  
→ des informations plus rapides  
→ une meilleure couverture

⚠️ Problème :

Les feeds peuvent utiliser des :

→ Formats différents  
→ Classifications différentes  
→ Terminologies différentes

STIX peut aider à standardiser les informations.

---

# ISAC

**ISAC = Information Sharing and Analysis Center**

Les ISAC permettent aux organisations d'un même secteur de partager :

→ Threat Intelligence  
→ Vulnerability information  
→ Incident information

Ils fonctionnent sur un modèle de **trust**.

Ils peuvent également fournir :

→ Incident Response  
→ Threat Analysis

---

# Conducting Your Own Research

Un professionnel de la cybersécurité doit également effectuer ses propres recherches.

Sources possibles :

→ Vendor security websites  
→ Vulnerability feeds  
→ Threat feeds  
→ Government agencies  
→ Academic journals  
→ Technical publications  
→ RFCs  
→ Security conferences  
→ Industry groups  
→ Social media de professionnels de la sécurité

Il faut particulièrement surveiller les :

**TTPs - Tactics, Techniques and Procedures**

→ Comprendre comment les attaquants opèrent permet d'améliorer la Threat Intelligence.

---

# À RETENIR - TERMES ANGLAIS

### Threat Intelligence

**Threat Intelligence** → informations permettant de comprendre et anticiper les menaces

**Threat Feed** → flux d'informations sur les menaces

**IoC** → preuve/signe indiquant une compromission

**CVE** → identifiant d'une vulnérabilité

---

### Sources

**OSINT** → informations provenant de sources publiques

**Closed-Source Intelligence** → informations propriétaires / privées

**Dark Web** → réseau permettant notamment des communications anonymes et utilisé pour vendre/échanger des données volées

**Threat Map** → représentation géographique des menaces

---

### Évaluation

**Timely** → à jour

**Accurate** → exact

**Relevant** → pertinent

**Confidence Score** → niveau de confiance accordé à l'information

---

### Standards

**STIX** → structure/format des Threat Intelligence

**TAXII** → protocole d'échange des Threat Intelligence

**ISAC** → organisation permettant le partage d'informations de sécurité entre acteurs d'un secteur

**TTPs** → Tactics, Techniques and Procedures

---

# EXAM - LES ASSOCIATIONS À CONNAÎTRE

**Informations publiques sur les menaces**  
→ **OSINT**

**Signe qu'une attaque a eu lieu**  
→ **IoC**

**Adresse IP, domaine, hash, URL, CVE...**  
→ **Threat Feed**

**Information récente**  
→ **Timely**

**Information correcte**  
→ **Accurate**

**Information adaptée à ton organisation**  
→ **Relevant**

**90–100**  
→ **Confirmed**

**70–89**  
→ **Probable**

**50–69**  
→ **Possible**

**30–49**  
→ **Doubtful**

**2–29**  
→ **Improbable**

**1**  
→ **Discredited**

**Standardiser les Threat Intelligence**  
→ **STIX**

**Échanger des données STIX via HTTPS**  
→ **TAXII**

**Partager des informations entre organisations d'un même secteur**  
→ **ISAC**

**Rechercher des credentials de l'organisation sur le Dark Web**  
→ Peut révéler une **compromission**

**Plusieurs Threat Feeds**  
→ Meilleure couverture / possibilité de comparer les informations

**Threat Map**  
→ À interpréter avec prudence car l'origine géographique peut être trompeuse

**Comment comprendre les méthodes des attaquants ?**  
→ Étudier leurs **TTPs**