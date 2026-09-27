# Social Engineering & Password Attacks

## Social Engineering

**Social Engineering** → manipulation de personnes pour les pousser à faire quelque chose qu'elles n'auraient normalement pas fait.

### Principes utilisés

- **Authority** → « Je suis ton responsable / le gouvernement »
    
- **Intimidation** → faire peur / menacer
    
- **Consensus / Social Proof** → « Tout le monde l'a déjà fait »
    
- **Scarcity** → « Dernière chance / plus qu'une place »
    
- **Familiarity** → exploiter quelque chose/personne de familier
    
- **Trust** → créer une relation de confiance
    
- **Urgency** → pousser à agir immédiatement
    

⚠️ Les attaques combinent souvent plusieurs principes.  
Exemple → **Authority + Urgency + Intimidation**.

---

# Phishing

**Phishing** → tentative frauduleuse visant à obtenir des informations, souvent :

- Username / password
    
- Informations personnelles
    
- Données bancaires
    

Généralement par **email**.

### Variantes

**Spear phishing**  
→ cible une personne ou un groupe précis.

**Whaling**  
→ cible des personnes importantes : **CEO, CFO, dirigeants**.

### Protection

→ Security awareness  
→ Phishing simulations  
→ Email filtering  
→ Reputation checking  
→ Pattern matching

---

# Vishing

**Vishing = Voice Phishing**

→ Phishing par **appel téléphonique / voicemail**.

Objectif :

- Informations personnelles
    
- Informations financières
    
- Argent
    
- Faire réaliser une action
    

Souvent basé sur :  
→ **Urgency + Authority**

---

# Smishing

**Smishing = SMS Phishing**

→ Phishing par **SMS**.

Le message contient souvent un lien vers :

- Faux site → credentials
    
- Malware
    
- Demande de code **MFA**
    
- Autre action malveillante
    

---

# Misinformation vs Disinformation

### Misinformation

→ Information incorrecte **sans nécessairement intention malveillante**.

### Disinformation

→ Information fausse/inexacte **délibérément diffusée** pour atteindre un objectif.

### À retenir

**Misinformation**  
→ False information

**Disinformation**  
→ False information **+ intentional**

### MDM

**MDM** =

- Misinformation
    
- Disinformation
    
- Malinformation
    

---

# Impersonation

**Impersonation** → se faire passer pour quelqu'un d'autre.

Exemples :  
→ faux employé  
→ faux livreur  
→ faux fournisseur  
→ personne prétendant être un responsable

**Identity theft/fraud** → utilisation de l'identité de quelqu'un d'autre.

---

# Business Email Compromise — BEC

**BEC** → utiliser des emails qui semblent légitimes pour réaliser une attaque ou une arnaque.

Exemples :

- Invoice scam
    
- Gift card scam
    
- Data theft
    
- Account compromise
    

Techniques :

- Compromised account
    
- Spoofed email
    
- Fake/similar domain
    
- Malware
    

### Protection

→ **MFA**  
→ Security awareness  
→ Policies

---

# Pretexting

**Pretexting** → inventer un **scénario crédible** pour justifier une demande.

Exemple :

> « Je suis du service IT, j'ai besoin de ton mot de passe pour vérifier ton compte. »

Souvent combiné avec **Impersonation**.

### Défense

→ Demander une vérification  
→ Appeler le service concerné directement

---

# Watering Hole

**Watering Hole Attack** → compromettre un site que les victimes ciblées **visitent fréquemment**.

Logique :

`Victimes fréquentent un site → Attaquant compromet le site → Victimes visitent → Attaque`

Le site devient littéralement le « watering hole » où les victimes viennent d'elles-mêmes.

---

# Brand Impersonation

**Brand Impersonation / Brand Spoofing** → email/site qui semble provenir d'une **marque légitime**.

Exemples :

- Banque
    
- PayPal
    
- Amazon
    
- Microsoft
    

Objectifs :  
→ Voler credentials  
→ Demander un paiement  
→ Voler des informations  
→ Distribuer du malware

---

# Typosquatting

**Typosquatting** → utiliser une URL très similaire à la vraie mais avec une **faute de frappe**.

Exemple :

`amazon.com`  
↓  
`amaz0n.com`

L'utilisateur fait une faute → arrive sur le faux site.

### Objectifs

→ Publicité  
→ Vente frauduleuse  
→ Phishing  
→ Vol d'informations

---

# Pharming

**Pharming** ≠ Typosquatting.

Pharming → redirection vers un faux site en modifiant :

- Hosts file
    
- DNS configuration
    

Donc :

**Typosquatting** → utilisateur fait une faute dans l'URL.

**Pharming** → système/DNS est manipulé pour rediriger l'utilisateur.

---

# Password Attacks

Security+ se concentre principalement sur :

- **Brute Force**
    
- **Password Spraying**
    

## Brute Force

**Brute Force** → essayer de nombreuses combinaisons jusqu'à trouver la bonne.

`Password1 → Password2 → Password3 → ...`

Peut utiliser :

- Wordlists
    
- Passwords communs
    
- Informations sur la cible
    
- Modification rules
    

---

# Password Spraying

**Password Spraying** → utiliser **un même mot de passe** ou un petit nombre de mots de passe contre **beaucoup de comptes**.

Exemple :

```text
admin → Winter2026
alice → Winter2026
bob → Winter2026
charlie → Winter2026
```

### Différence fondamentale

**Brute Force**  
→ Beaucoup de passwords → **1 compte**

**Password Spraying**  
→ Peu de passwords → **beaucoup de comptes**

### EXAM

Si tu vois :

> « Try the same common password against many usernames »

→ **PASSWORD SPRAYING**

---

# Dictionary Attack

**Dictionary Attack** → brute-force utilisant une **liste de mots/passwords**.

Outil connu :

**John the Ripper**

⚠️ Important pour l'examen :

→ Dictionary attacks existent, mais le **SY0-701 met surtout l'accent sur Brute Force + Spraying**.

---

# Online vs Offline Password Attacks

### Online

Attaque directement le système vivant.

`Attacker → Login system → Password attempts`

→ Peut rencontrer :

- Account lockout
    
- Rate limiting
    
- MFA
    
- Detection
    

### Offline

L'attaquant possède déjà le **password store/hash database**.

`Password hash → cracking offline`

→ Pas besoin d'interagir avec le système de login.

---

# Rainbow Tables

**Rainbow Table** → base de données de **precomputed hashes**.

Principe :

`Password → Hash`

Une rainbow table contient énormément de :

`Hash ↔ Password`

→ Permet de retrouver rapidement le plaintext correspondant à certains hashes.

⚠️ Les rainbow tables **ne "décryptent" pas le hash** : elles utilisent des valeurs pré-calculées pour retrouver une correspondance.

---

# Password Storage

Les mots de passe ne devraient **pas être stockés en plaintext**.

→ Utiliser un **password hash** adapté.

### Salt

**Salt** → donnée supplémentaire ajoutée avant le hashing.

→ Rend les attaques pré-calculées comme les rainbow tables plus difficiles.

### Pepper

**Pepper** → donnée supplémentaire utilisée avec le password avant hashing.

→ Ajoute une protection supplémentaire contre certaines attaques.

---

# À RETENIR — SOCIAL ENGINEERING

| Technique               | Association                                  |
| ----------------------- | -------------------------------------------- |
| **Social Engineering**  | Manipulate humans                            |
| **Phishing**            | Email                                        |
| **Spear Phishing**      | Specific target                              |
| **Whaling**             | CEO / CFO / executives                       |
| **Vishing**             | Voice / phone                                |
| **Smishing**            | SMS                                          |
| **Misinformation**      | False information                            |
| **Disinformation**      | False information + intent                   |
| **Impersonation**       | Pretend to be someone                        |
| **BEC**                 | Fraudulent legitimate-looking business email |
| **Pretexting**          | Fake scenario                                |
| **Watering Hole**       | Compromise frequently visited website        |
| **Brand Impersonation** | Fake legitimate brand                        |
| **Typosquatting**       | Fake URL with typo                           |
| **Pharming**            | DNS / hosts redirection                      |

# EXAM — PASSWORD ATTACKS

**Many passwords → one account**  
→ **Brute Force**

**One/few passwords → many accounts**  
→ **Password Spraying**

**Word list → passwords**  
→ **Dictionary Attack**

**Captured password hashes → attack offline**  
→ **Password Cracking**

**Precomputed hashes**  
→ **Rainbow Tables**

**Extra random data before hashing**  
→ **Salt**

**Password storage**  
→ **Hash, NOT encryption**

