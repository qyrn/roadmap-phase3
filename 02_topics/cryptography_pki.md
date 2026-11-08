# Chapter 7 — Cryptography and the PKI

## 1. Cryptography — objectifs

La **cryptography** sert principalement à protéger :

|Objectif|Signification|
|---|---|
|**Confidentiality**|empêcher la lecture non autorisée|
|**Integrity**|empêcher/modifier détecter une modification|
|**Authentication**|vérifier l'identité|
|**Non-repudiation**|prouver l'origine d'un message|

⚠️ **CIA triad** : le `A` signifie **Availability**, pas Authentication.

---

# 2. Encryption

**Plaintext → Encryption + Key → Ciphertext**

Puis :

**Ciphertext → Decryption + Key → Plaintext**

### Data states

- **Data at rest** → données stockées
    
- **Data in transit** → données qui circulent
    
- **Data in use** → données présentes en mémoire
    

**TLS** protège notamment les données **in transit**.

---

# 3. Encryption Levels

À connaître pour le Security+ :

|Niveau|Protège|
|---|---|
|**Full-disk encryption (FDE)**|disque entier|
|**Partition encryption**|partition|
|**File-level encryption**|fichiers individuels|
|**Volume encryption**|volume|
|**Database encryption**|base de données|
|**Record-level encryption**|enregistrements individuels|

### FDE

**Full Disk Encryption**

→ protège tout le disque, OS compris.

⚠️ Une fois le système démarré et compromis, les données peuvent rester accessibles.

---

# 4. Symmetric vs Asymmetric

## Symmetric

**1 clé partagée**

```text
Alice ──[SECRET KEY]──> Bob
```

Même clé pour :

**Encrypt + Decrypt**

### Avantages

- très rapide
    
- excellent pour **bulk encryption**
    
- adapté aux gros volumes de données
    

### Inconvénients

- problème de **key exchange**
    
- difficilement scalable
    
- pas de **non-repudiation**
    

---

## Asymmetric

**2 clés :**

- **Public key** → peut être partagée
    
- **Private key** → doit rester secrète
    

Pour envoyer un message à Bob :

**Bob's public key → Encrypt**

**Bob's private key → Decrypt**

### Avantages

- scalable
    
- facilite le key exchange
    
- authentication
    
- integrity
    
- **non-repudiation**
    
- digital signatures
    

### Inconvénient

→ beaucoup plus lent que le symmetric.

C'est pourquoi on utilise souvent :

**Asymmetric → établir la connexion / échanger une clé**

puis

**Symmetric → chiffrer les données**

---

# 5. EXAM — Symmetric vs Asymmetric

|Symmetric|Asymmetric|
|---|---|
|1 shared key|Public + Private|
|Fast|Slow|
|Bulk encryption|Small data / signatures / certificates|
|Key exchange difficile|Key exchange facilité|
|Not scalable|Scalable|
|Confidentiality|Confidentiality + authentication + integrity + non-repudiation|

---

# 6. Key Length

**Plus la clé est longue → plus le brute force est difficile.**

Exemple du livre :

- **DES = 56-bit → insecure**
    
- AES moderne → **128 / 192 / 256-bit**
    

⚠️ Une clé plus longue demande également davantage de ressources de calcul.

---

# 7. AES

**AES — Advanced Encryption Standard**

Symmetric + block cipher.

### AES

- **AES-128** → 10 rounds
    
- **AES-192** → 12 rounds
    
- **AES-256** → 14 rounds
    

AES utilise des blocs de **128 bits**.

### À retenir

**AES = symmetric + fast + bulk encryption**

---

# 8. DES / 3DES

### DES

**56-bit → obsolete/insecure**

### 3DES

→ DES appliqué trois fois.

Mais **3DES est également considéré comme insecure** dans le contexte du livre.

**EXAM :**

`DES ❌`  
`3DES ❌`  
`AES ✅`

---

# 9. Diffie-Hellman

**Diffie-Hellman = key exchange**

Il permet à deux personnes qui ne possèdent pas déjà une clé secrète commune de générer un **secret partagé** via une communication publique.

Schéma :

**Alice → paramètres publics ← Bob**

→ calculs mathématiques

→ **Shared Secret**

⚠️ DH sert à **établir une clé**, pas à chiffrer directement toutes les données de la session.

---

# 10. Key Management

La sécurité dépend énormément de la protection des clés.

Key management comprend :

- Creation
    
- Distribution
    
- Storage
    
- Destruction
    
- Recovery
    
- **Escrow**
    

### Split Knowledge

Une clé sensible peut être divisée entre plusieurs personnes.

**Person A + Person B → reconstituer la clé**

### Key Escrow

Une **third party** conserve une copie protégée de la clé.

→ récupération possible en cas de perte ou d'urgence.

---

# 11. RSA & ECC

## RSA

**Asymmetric**

Basé sur la difficulté de **factoring large prime numbers**.

## ECC — Elliptic Curve Cryptography

Basé sur le **elliptic curve discrete logarithm problem**.

→ fournit une forte sécurité avec des clés relativement courtes.

---

# 12. Hashing

Un **hash** transforme une donnée de taille quelconque en une sortie de taille fixe.

```text
Input
  ↓
Hash Function
  ↓
Hash / Digest
```

Propriétés :

- **One-way**
    
- sortie de taille fixe
    
- relativement rapide à calculer
    
- même input → même hash
    
- extrêmement difficile de retrouver l'input
    
- difficile de trouver une **collision**
    

### Hash ≠ Encryption

**Encryption**  
→ réversible avec une clé.

**Hash**  
→ normalement **non réversible**.

---

# 13. Collision

**Collision = deux inputs différents produisent le même hash.**

```text
Message A ──→ HASH X
Message B ──→ HASH X
```

→ problème de sécurité.

---

# 14. SHA

### SHA-1

→ **insecure / weaknesses demonstrated**

### SHA-2

Variantes importantes :

- SHA-224
    
- SHA-256
    
- SHA-384
    
- SHA-512
    

### SHA-3

→ nouvelle génération de SHA.

**EXAM :**

`SHA-1 ❌`

`SHA-256 / SHA-384 / SHA-512 ✅`

---

# 15. MD5

**MD5 = 128-bit**

⚠️ vulnérable aux **collisions**.

→ ne pas utiliser pour garantir l'intégrité cryptographique.

---

# 16. Digital Signature

Une signature numérique combine :

**Hashing + Asymmetric cryptography**

Alice :

```text
Message
   ↓
Hash
   ↓
Encrypt hash avec PRIVATE KEY
   ↓
Digital Signature
```

Bob :

```text
Digital Signature
   ↓
Decrypt avec PUBLIC KEY
   ↓
Hash reçu
   ↓
Compare
```

Si les hashes correspondent :

→ intégrité  
→ authentification de l'origine  
→ non-repudiation

⚠️ **Digital signature ≠ confidentiality**

Elle ne chiffre pas le message à elle seule.

---

# 17. HMAC

**HMAC — Hash-Based Message Authentication Code**

→ garantit l'**integrity** du message.

Mais :

❌ pas de **non-repudiation**

Pourquoi ?

Parce que les deux parties possèdent le secret partagé.

---

# 18. Steganography

**Steganography = cacher un message dans un autre fichier.**

Exemple :

```text
Image normale
     +
message secret
     ↓
image apparemment normale
```

Le message peut être caché dans :

- images
    
- audio
    
- vidéo
    
- autres fichiers
    

### À ne pas confondre

**Encryption** → rendre le contenu illisible.

**Steganography** → cacher l'existence du contenu.

---

# À RETENIR

|Concept|Association|
|---|---|
|**Symmetric**|1 shared secret key|
|**Asymmetric**|Public + Private key|
|**AES**|Symmetric / fast|
|**RSA**|Asymmetric / factoring|
|**ECC**|Asymmetric / elliptic curves|
|**Diffie-Hellman**|Key exchange|
|**Hash**|One-way / integrity|
|**SHA-256**|Hash|
|**SHA-1**|Weak/insecure|
|**MD5**|Collision vulnerability|
|**Digital signature**|Integrity + authentication + non-repudiation|
|**HMAC**|Integrity + authentication, pas non-repudiation|
|**Steganography**|Hide message inside another file|
|**FDE**|Entire disk|
|**TLS**|Data in transit|
|**Key escrow**|Third party stores key copy|
|**Split knowledge**|Multiple people reconstruct key|
|**Key length**|Longer → harder brute force|

## EXAM — ASSOCIATIONS À CONNAÎTRE

**1 clé + rapide + gros volume** → **Symmetric**

**Public + Private** → **Asymmetric**

**Chiffrer pour Bob** → **Bob's Public Key**

**Déchiffrer pour Bob** → **Bob's Private Key**

**Signature de Bob** → **Bob's Private Key**

**Vérifier signature de Bob** → **Bob's Public Key**

**Échanger une clé sans canal sécurisé préexistant** → **Diffie-Hellman**

**Intégrité / one-way** → **Hash**

**Deux messages → même hash** → **Collision**

**56-bit obsolete** → **DES**

**Symmetric moderne** → **AES**

**SHA-1 / MD5** → **à éviter pour la sécurité cryptographique**

**Intégrité + non-repudiation** → **Digital Signature**

**Intégrité sans non-repudiation** → **HMAC**

**Cacher un message dans une image** → **Steganography**

**Copie de clé conservée par un tiers** → **Key Escrow**

