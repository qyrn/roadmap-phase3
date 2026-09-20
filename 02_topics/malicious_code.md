# Malicious Code

**Malware** = logiciel volontairement conçu pour nuire à un système, un appareil, un réseau ou un utilisateur.

Il peut notamment :

→ Détruire ou modifier des données  
→ Voler des informations  
→ Donner un accès non autorisé  
→ Maintenir l'accès d'un attaquant  
→ Perturber un système

---

# Ransomware

Malware qui **prend le contrôle d'un système et demande une rançon**.

### Crypto Malware

→ Chiffre les fichiers  
→ Les rend inutilisables  
→ Demande une rançon pour les récupérer

### Vecteurs fréquents

→ Phishing  
→ RDP  
→ Services vulnérables  
→ Applications exposées sur Internet

### IoCs

→ Communication **C&C**  
→ IP malveillantes  
→ Utilisation anormale d'outils légitimes  
→ **Lateral Movement**  
→ Chiffrement des fichiers  
→ Message de demande de rançon  
→ **Data Exfiltration** / gros transferts de fichiers

### Protection

→ **Backups** séparées du système  
→ Antivirus / Antimalware  
→ EDR  
→ Prévention du phishing

⚠️ Le backup doit être suffisamment isolé pour ne pas être chiffré lui aussi.

---

# Trojan

Un **Trojan / Trojan Horse** est un malware **déguisé en logiciel légitime**.

→ L'utilisateur pense installer une application normale  
→ Il l'exécute  
→ Le malware s'installe

### À retenir

**Trojan = nécessite généralement que l'utilisateur l'exécute**

### IoCs

→ Malware signatures  
→ Fichiers malveillants  
→ Hostnames / IP de C&C  
→ Fichiers ou dossiers créés sur le système

### RAT

**RAT = Remote Access Trojan**

→ Donne un accès distant à l'attaquant.

⚠️ Certains outils légitimes de remote access peuvent être détournés et utilisés comme RAT.

### Protection

→ User awareness  
→ Contrôle des applications autorisées  
→ Antimalware  
→ **EDR**

---

# Bots / Botnets / C&C

### Bot

Un système infecté contrôlé par un attaquant.

### Botnet

Ensemble de systèmes (**bots**) contrôlés de manière centralisée.

### C&C

**Command and Control**

→ Infrastructure permettant à l'attaquant d'envoyer des commandes aux machines compromises.

Les communications C&C peuvent notamment utiliser :

→ HTTP chiffré  
→ Plusieurs serveurs distants  
→ IRC

### IoC important

Un système qui communique régulièrement avec des **unknown / malicious hosts** peut être un signe de botnet.

---

# Worm

Un **Worm** est un malware qui **se propage automatiquement**.

Contrairement au Trojan :

**Worm → pas besoin d'action utilisateur pour chaque infection**

Il peut se propager via :

→ Vulnerable services  
→ Email attachments  
→ Network shares  
→ IoT devices  
→ Phones

### À retenir

**Worm = self-propagating**

---

# Stuxnet

**Stuxnet** est un exemple célèbre de worm utilisé comme cyberarme.

Il ciblait le programme nucléaire iranien.

Il utilisait notamment :

→ USB drives  
→ Zero-day vulnerabilities  
→ Trusted digital certificates  
→ ICS  
→ Techniques permettant de rester discret

Il pouvait manipuler les centrifugeuses tout en fournissant de fausses informations aux opérateurs.

### Défense contre les Worms

→ Firewalls  
→ IPS  
→ Network segmentation  
→ Patching  
→ Réduire l'Attack Surface

**Si les systèmes infectés ne peuvent pas communiquer avec d'autres systèmes vulnérables → la propagation est limitée.**

---

# Spyware

**Spyware** = malware conçu pour **collecter des informations** sur un utilisateur, un système ou une organisation.

Il peut récupérer :

→ Browsing habits  
→ Software installé  
→ Informations sensibles  
→ Données système

Il peut également permettre :

→ Remote access  
→ Web camera access  
→ Surveillance

### IoCs

→ Remote access indicators  
→ Known file fingerprints  
→ Malicious processes  
→ Browser injection

### Point important

Le comportement peut ressembler à celui d'un Trojan ou d'un Worm.

La différence principale est **l'objectif** :

**Spyware = collecter des informations**

---

# Bloatware

**Bloatware** = logiciel indésirable installé sur un système.

Exemple :

→ PC neuf avec beaucoup d'applications préinstallées inutiles.

⚠️ **Bloatware ≠ véritablement malware**

Il peut cependant :

→ Consommer CPU / RAM / disque  
→ Communiquer avec son fournisseur  
→ Contenir des vulnérabilités  
→ Augmenter l'Attack Surface

### Différence fondamentale

**Spyware → veut collecter des informations**

**Bloatware → simplement indésirable**

### Protection

→ Désinstallation  
→ Clean OS image

---

# Virus

Un **Virus** est un malware qui se **copie / réplique après activation**.

Contrairement au Worm :

**Virus → nécessite généralement un mécanisme d'infection / activation**

Exemples de mécanismes :

→ USB  
→ Network share  
→ Fichier infecté

Un virus possède généralement :

### Trigger

Condition qui déclenche l'exécution.

### Payload

Action effectuée par le virus.

---

# Types de Viruses

**Memory-resident**

→ Reste en mémoire pendant que le système fonctionne.

**Non-memory-resident**

→ S'exécute → se propage → s'arrête.

**Boot sector virus**

→ Infecte le boot sector d'un disque.

**Macro virus**

→ Utilise des macros/code de logiciels comme les traitements de texte.

**Email virus**

→ Se propage via les emails.

---

# Fileless Malware

Un **Fileless Attack** ne dépend pas du stockage classique d'un fichier malveillant.

Le malware peut :

→ Entrer via un navigateur / plugin vulnérable  
→ S'injecter en mémoire  
→ Utiliser PowerShell ou d'autres outils système  
→ Ajouter une persistence via Registry

### Protection

→ Patching  
→ Mise à jour des navigateurs/plugins  
→ Antimalware comportemental  
→ IPS  
→ Reputation-based protection

---

# Malware Removal

Supprimer un malware peut être difficile car il n'est pas toujours possible de savoir si **toutes les parties de l'infection** ont été supprimées.

Une bonne pratique consiste parfois à :

→ **Wipe the drive**  
→ Reinstall / Reimage  
→ Restore from a known good backup

⚠️ Certains malwares peuvent même résider dans le **BIOS/UEFI**, ce qui peut nécessiter des mesures supplémentaires.

---

# Keylogger

Un **Keylogger** capture les frappes clavier.

Il peut également capturer :

→ Mouse movements  
→ Touchscreen input  
→ Credit card input

### Objectif

→ Récupérer ce que l'utilisateur saisit  
→ Passwords  
→ Credentials  
→ Informations sensibles

### IoCs

→ File hashes / signatures  
→ C&C communications  
→ Process names  
→ Known URLs

### Protection

→ Patching  
→ Antimalware  
→ System management  
→ **MFA**

⚠️ MFA ne bloque pas le keylogger, mais peut **limiter son impact** si un mot de passe est volé.

---

# Logic Bomb

Une **Logic Bomb** est du code placé dans un autre programme qui s'active lorsqu'une **condition spécifique** est remplie.

Exemple conceptuel :

→ "Si la date = 1er janvier → exécuter l'action malveillante."

### Particularité

Ce n'est généralement **pas un programme malware indépendant**.

### Détection

→ **Code review**  
→ Analyse du code / des scripts

Les IoCs sont moins évidents que pour d'autres malwares.

---

# Malware Analysis

Plusieurs techniques permettent d'analyser un malware.

### VirusTotal

→ Vérifier si un fichier est connu  
→ Comparer les détections de plusieurs antivirus

### Sandbox

→ Exécuter le malware dans un environnement isolé  
→ Observer son comportement

### Manual Code Analysis

→ Examiner directement le code  
→ Particulièrement utile pour les scripts

### Strings

→ Rechercher des chaînes de caractères récupérables  
→ URLs, chemins, messages, etc.

---

# Rootkit

Un **Rootkit** est conçu pour :

→ Maintenir un accès à un système  
→ Fournir une **backdoor**  
→ **Se cacher de la détection**

Il peut modifier ou exploiter :

→ Filesystem drivers  
→ Startup code  
→ MBR  
→ OS components

### Pourquoi c'est dangereux ?

Le système infecté **ne peut plus être considéré comme fiable**.

Un rootkit peut modifier le fonctionnement du système pour cacher sa propre présence.

### Détection

Idéalement :

→ Démarrer depuis un **trusted system**  
→ Examiner le disque depuis un autre système

Autres méthodes :

→ Integrity checking  
→ Data validation  
→ Anti-rootkit tools

### IoCs

→ File hashes / signatures  
→ C&C domains / IPs  
→ Création de services  
→ Modifications de configuration  
→ Nouveaux exécutables  
→ File access  
→ Command execution  
→ Open ports  
→ Reverse proxy tunnels

### Suppression

La méthode la plus fiable est souvent :

→ **Rebuild system**  
→ **Restore known good backup**

---

# À RETENIR — MALWARE

### Ransomware

→ **Encrypt + Ransom**

### Trojan

→ **Disguised as legitimate software**

### RAT

→ **Remote Access**

### Worm

→ **Self-spreading**

### Spyware

→ **Gather information**

### Bloatware

→ **Unwanted software**

### Virus

→ **Replicates after activation**

### Keylogger

→ **Captures keystrokes**

### Logic Bomb

→ **Executes when a condition is met**

### Rootkit

→ **Hide + Maintain access**

### Botnet

→ **Network of compromised bots**

### C&C

→ **Attacker controls compromised systems**

---

# EXAM — ASSOCIATIONS À CONNAÎTRE

**Fichiers chiffrés + demande de rançon**  
→ **Ransomware**

**Faux logiciel légitime**  
→ **Trojan**

**Accès distant à une machine**  
→ **RAT**

**Propagation automatique**  
→ **Worm**

**Collecte d'informations sur l'utilisateur**  
→ **Spyware**

**Logiciels inutiles préinstallés**  
→ **Bloatware**

**Capture des frappes clavier**  
→ **Keylogger**

**Code qui s'exécute lorsqu'une condition est remplie**  
→ **Logic Bomb**

**Maintenir un accès + cacher sa présence**  
→ **Rootkit**

**Réseau de machines infectées**  
→ **Botnet**

**Infrastructure qui donne des commandes aux machines infectées**  
→ **C&C**

**Pas besoin d'interaction utilisateur pour se propager**  
→ **Worm**

**Nécessite généralement une activation / interaction**  
→ **Virus**

**Analyse dans un environnement isolé**  
→ **Sandbox**

**Vérifier un fichier avec plusieurs moteurs AV**  
→ **VirusTotal**

**Standard de protection contre les ransomwares**  
→ **Backup isolé / connu comme sain**

**Système compromis par un rootkit**  
→ **Ne plus lui faire confiance → analyser depuis un système fiable**

**Code malveillant difficile à identifier sans regarder le code source**  
→ **Logic Bomb**

**Mot de passe volé par un keylogger mais MFA activé**  
→ **MFA peut limiter l'impact**

---
# Malicious Code

## Malware

**Malware** = software intentionally designed to cause harm, steal information, gain illicit access, etc.

### À connaître

- **Ransomware** → demande une rançon
    
- **Trojan** → se fait passer pour un logiciel légitime
    
- **Worm** → se propage automatiquement
    
- **Spyware** → collecte des informations
    
- **Bloatware** → logiciel indésirable
    
- **Virus** → se réplique après activation
    
- **Keylogger** → capture les frappes
    
- **Logic Bomb** → s'active sous une condition
    
- **Rootkit** → cache sa présence + maintient l'accès
    

---

# Ransomware

**Ransomware** → prend le contrôle d'un système et demande une **rançon**.

**Crypto malware** → chiffre les fichiers → demande une rançon.

### Vecteurs

- Phishing
    
- RDP
    
- Services vulnérables
    
- Applications exposées sur Internet
    

### IoCs

- C&C traffic
    
- Connexions vers des IP malveillantes
    
- Utilisation anormale d'outils légitimes
    
- **Lateral movement**
    
- **Encryption of files**
    
- Message de rançon
    
- **Data exfiltration / large file transfers**
    

### Protection

→ **Backups isolés / séparés**  
→ Antimalware / EDR  
→ Security awareness

⚠️ Payer la rançon **ne garantit pas** la récupération des fichiers.

---

# Trojan

**Trojan Horse** → malware **déguisé en logiciel légitime**.

Il repose généralement sur l'utilisateur qui télécharge/exécute le programme.

### IoCs

- Malware signatures
    
- C&C hostnames / IPs
    
- Nouveaux fichiers ou dossiers
    

### RAT

**Remote Access Trojan (RAT)** → donne à l'attaquant un **accès distant** au système.

⚠️ Un outil légitime de remote access peut être détourné comme RAT.

### Protection

→ Security awareness  
→ Application/software control  
→ Antimalware  
→ **EDR**

---

# Bots / Botnets / C&C

**Bot** → système compromis contrôlé par l'attaquant.

**Botnet** → groupe de bots sous contrôle centralisé.

**C&C (Command and Control)** → infrastructure permettant à l'attaquant de commander les systèmes compromis.

### C&C

Peut utiliser :

- HTTPS/HTTP chiffré
    
- Hôtes distants qui changent fréquemment
    
- IRC, notamment **port 6667**
    

### IoC important

→ Une machine qui communique avec des **unknown hosts** peut être membre d'un botnet.

---

# Worm

**Worm** → malware qui **se propage automatiquement**.

Contrairement au Trojan :  
→ **pas besoin d'interaction utilisateur pour chaque infection.**

### Propagation

- Services vulnérables
    
- Email attachments
    
- Network shares
    
- IoT
    
- Smartphones
    
- Autres mécanismes automatisés
    

### Stuxnet

**Stuxnet** = exemple célèbre de worm utilisé comme **cyberweapon**.

→ Cible : programme nucléaire iranien  
→ Utilisait notamment des **USB drives** pour atteindre des systèmes **air-gapped**.

### Raspberry Robin

Worm moderne associé à des activités **pre-ransomware**.

IoCs :

- Malicious files
    
- Téléchargements de composants supplémentaires
    
- C&C
    
- Utilisation anormale de `cmd.exe`, `msiexec.exe`, etc.
    
- Hands-on-keyboard activity
    

### Protection

→ Firewalls  
→ IPS  
→ **Network segmentation**  
→ Patching  
→ Réduction de l'attack surface  
→ Antimalware / EDR

---

# Spyware

**Spyware** → malware dont l'objectif principal est de **collecter des informations**.

Peut surveiller :

- Browsing habits
    
- Software installé
    
- Données sensibles
    
- Webcam
    
- Système/utilisateur
    

### IoCs

- Remote access/control
    
- Known file fingerprints
    
- Processus malveillants déguisés en processus système
    
- Browser injection
    

### ⚠️ Point important Security+

Le comportement ne suffit pas toujours à identifier un spyware.

→ **L'intention compte.**

Même s'il utilise une méthode de propagation de type Trojan/Worm/Virus :

**Objectif = collecter des informations → Spyware**.

---

# Bloatware

**Bloatware** → logiciels **indésirables** préinstallés ou ajoutés avec d'autres logiciels.

Contrairement au malware :  
→ **pas nécessairement conçu pour être malveillant.**

Problèmes possibles :

- Consomme CPU/RAM/disque
    
- Peut être vulnérable
    
- Peut augmenter l'**attack surface**
    
- Peut communiquer avec l'extérieur
    

### Protection

→ Uninstall / remove  
→ Clean OS image

### ⚠️ Spyware vs Bloatware

**Spyware** → intention = **collecter des informations**

**Bloatware** → intention = **logiciel simplement indésirable**

---

# Virus

**Virus** → programme malveillant qui **se copie/se réplique après activation**.

### Virus vs Worm

**Virus**  
→ nécessite un mécanisme d'infection  
→ généralement besoin d'une activation/exécution

**Worm**  
→ **self-spreading**  
→ propagation automatisée

### Trigger vs Payload

**Trigger** → condition qui déclenche le virus.

**Payload** → action réalisée par le virus.

### Types

- **Memory-resident** → reste en mémoire
    
- **Non-memory-resident** → exécute → se propage → s'arrête
    
- **Boot sector virus** → boot sector
    
- **Macro virus** → macros
    
- **Email virus** → email/attachments
    
- **Fileless** → fonctionne principalement en mémoire
    

---

# Fileless Malware

**Fileless** → malware qui ne nécessite pas de fichier local classique pour fonctionner.

→ Injection en mémoire  
→ Peut utiliser PowerShell/scripts  
→ Persistence possible via Registry

### Protection

→ Patching  
→ Browser/plugin updates  
→ Behavioral detection  
→ PowerShell monitoring  
→ IPS  
→ Reputation-based protection

---

# Malware Removal

La suppression complète d'un malware peut être difficile.

### Méthode fiable

**Wipe → Reinstall/Reimage → Known-good backup**

⚠️ Certains malwares peuvent résider dans :  
→ **BIOS/UEFI**

Donc même une réinstallation classique peut ne pas suffire dans certains cas.

---

# Keylogger

**Keylogger** → capture les **keystrokes**.

Peut également capturer :

- Mouse input
    
- Touchscreen input
    
- Card reader input
    

### Objectif

→ Capturer les informations saisies par l'utilisateur, notamment les **credentials**.

### Protection

→ Patching  
→ System management  
→ Antimalware  
→ **MFA**

⚠️ MFA ne bloque pas nécessairement le keylogger, mais **limite son impact** si le mot de passe est capturé.

---

# Logic Bomb

**Logic Bomb** → code placé dans un programme qui s'exécute lorsqu'une **condition spécifique** est remplie.

Exemple conceptuel :

`IF condition → execute malicious action`

### Détection

Les IoCs sont moins évidents.

→ **Code review** principalement.

---

# Analyzing Malware

### VirusTotal

→ Vérifier si un fichier est connu comme malware  
→ Comparer les détections de plusieurs AV

### Sandbox

→ Exécuter/analyser le malware dans un **environnement isolé**.

### Manual Code Analysis

→ Analyse du code, particulièrement pour :

- Scripts
    
- Python
    
- Perl
    

### `strings`

→ Chercher des chaînes/artifacts récupérables dans un fichier.

---

# Rootkit

**Rootkit** → malware conçu pour :

1. **Maintenir un accès**
    
2. **Cacher sa présence**
    

Peut :

- Modifier/hooker des filesystem drivers
    
- Modifier le démarrage
    
- Infecter le **MBR**
    
- Contourner certaines protections
    

### Pourquoi il est difficile à détecter ?

Le système infecté **ne peut plus être considéré comme fiable**.

### Détection

→ Analyser depuis un **trusted system/device**

Autres techniques :

- Integrity checking
    
- Data validation
    
- Anti-rootkit tools
    

### IoCs

- File hashes/signatures
    
- C&C domains/IPs
    
- Création de services
    
- Nouveaux executables
    
- Configuration changes
    
- File access
    
- Command invocation
    
- Open ports
    
- Reverse proxy tunnels
    

### Removal

→ **Rebuild system**  
→ **Restore from known-good backup**

### Protection

→ Patching  
→ Secure configuration  
→ Privilege management  
→ **Secure Boot**

---

# À RETENIR — MALWARE

|Malware|Association|
|---|---|
|**Ransomware**|Encrypt + Ransom|
|**Trojan**|Disguised as legitimate software|
|**RAT**|Remote Access|
|**Bot**|Compromised system|
|**Botnet**|Group of compromised systems|
|**C&C**|Attacker controls compromised systems|
|**Worm**|Self-spreading|
|**Spyware**|Gather information|
|**Bloatware**|Unwanted software|
|**Virus**|Replicates after activation|
|**Keylogger**|Captures keystrokes|
|**Logic Bomb**|Condition → malicious action|
|**Rootkit**|Hide + maintain access|

# EXAM — ASSOCIATIONS À CONNAÎTRE

**Files encrypted + ransom demand**  
→ **Ransomware**

**Fake legitimate application**  
→ **Trojan**

**Remote access by attacker**  
→ **RAT**

**Automatic propagation**  
→ **Worm**

**Collecting information**  
→ **Spyware**

**Unwanted preinstalled software**  
→ **Bloatware**

**Capturing keystrokes**  
→ **Keylogger**

**Malicious code activated by a condition**  
→ **Logic Bomb**

**Hide malicious activity + maintain foothold**  
→ **Rootkit**

**Group of compromised machines**  
→ **Botnet**

**Attacker command infrastructure**  
→ **C&C**

**Malware analysis in isolated environment**  
→ **Sandbox**

**Check known malware / multiple AV detections**  
→ **VirusTotal**

**Rootkit detection**  
→ **Trusted system**

**Reliable malware removal**  
→ **Reimage/reinstall + known-good backup**

**Keylogger impact reduction**  
→ **MFA**

**Worm prevention**  
→ **Firewall + IPS + Network Segmentation + Patching**