# 81 - Cryptography Fundamentals

## Overview
Cryptography is the science of securing information by transforming it into an unreadable format that only authorized parties can decode. It is the foundation of secure communications, authentication, and data integrity.

---

## 1. Symmetric vs Asymmetric Encryption

### Symmetric Encryption
- Same key used to encrypt and decrypt
- Fast, efficient — used for bulk data encryption
- Key distribution problem: how to share the key securely?

| Algorithm | Key Size       | Use Case              |
|-----------|----------------|-----------------------|
| AES-128   | 128-bit        | File encryption, TLS  |
| AES-256   | 256-bit        | Highly sensitive data |
| 3DES      | 168-bit        | Legacy systems        |
| ChaCha20  | 256-bit        | Mobile/TLS 1.3        |

### Asymmetric Encryption
- Key pair: Public Key (encrypt) + Private Key (decrypt)
- Slow — used for key exchange and digital signatures
- Solves key distribution problem

| Algorithm | Key Size       | Use Case                   |
|-----------|----------------|----------------------------|
| RSA-2048  | 2048-bit       | Key exchange, signatures   |
| RSA-4096  | 4096-bit       | High security signatures   |
| ECC P-256 | 256-bit        | TLS, mobile (efficient)    |
| Diffie-Hellman | Variable  | Key exchange in TLS        |

### Hybrid Encryption (How TLS Works)
```
1. Client and server use asymmetric crypto (RSA/ECC) to exchange a session key
2. All actual data transmission uses symmetric crypto (AES) with that session key
Best of both worlds: secure key exchange + fast bulk encryption
```

---

## 2. Hashing Algorithms

### What is Hashing?
A one-way function that produces a fixed-size digest from any input. Cannot be reversed. Used for integrity verification, password storage, digital signatures.

| Algorithm | Output Size | Status          | Use Case              |
|-----------|-------------|-----------------|----------------------|
| MD5       | 128-bit     | Broken (weak)   | Legacy, file checksums|
| SHA-1     | 160-bit     | Deprecated      | Legacy only           |
| SHA-256   | 256-bit     | Secure          | TLS, certificates, password hashing |
| SHA-3     | Variable    | Secure (newest) | Alternative to SHA-2  |
| bcrypt    | 184-bit     | Secure          | Password storage      |
| Argon2    | Variable    | Secure (winner) | Password storage (recommended) |

### Hash Example
```bash
echo "hello" | sha256sum
# Output: 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824

# Same input ALWAYS produces same output
# Any change to input = completely different hash (avalanche effect)
```

### Rainbow Tables & Salting
- **Rainbow Table Attack**: Pre-computed table of hashes for common passwords
- **Salt**: Random string added to password before hashing — defeats rainbow tables
- **bcrypt/Argon2** handle salting automatically

---

## 3. PKI – Public Key Infrastructure

### Components of PKI
| Component             | Role                                                  |
|-----------------------|-------------------------------------------------------|
| Certificate Authority (CA) | Issues and signs digital certificates           |
| Root CA               | Top of the trust chain, self-signed               |
| Intermediate CA       | Signs end-entity certificates, subordinate to Root CA|
| End-Entity Certificate| Issued to websites, users, servers                |
| CRL                   | Certificate Revocation List — lists revoked certs |
| OCSP                  | Online Certificate Status Protocol — real-time revocation check |

### Certificate Trust Chain
```
Root CA (trusted by OS/browser)
  └── Intermediate CA (signed by Root CA)
        └── Website Certificate (signed by Intermediate CA)
```

### X.509 Certificate Fields
- Subject (who it's for)
- Issuer (who signed it)
- Public Key
- Valid From / Valid To
- Serial Number
- Signature Algorithm

---

## 4. Digital Signatures & Certificates

### How Digital Signatures Work
```
SIGNING:
  1. Hash the document → Digest
  2. Encrypt Digest with SENDER'S PRIVATE KEY → Signature
  3. Send Document + Signature

VERIFICATION:
  1. Decrypt Signature with SENDER'S PUBLIC KEY → Digest
  2. Hash the received document → New Digest
  3. Compare: If Digest matches → signature valid, content unmodified
```

### TLS Certificate Process
1. Web server presents its certificate
2. Browser checks: Is it signed by a trusted CA? Is it expired? Does domain match?
3. If valid → establish encrypted TLS session
4. Padlock icon appears in browser

### Certificate Types
| Type          | Validation Level | Use Case                 |
|---------------|-----------------|--------------------------|
| DV (Domain Validation) | Low | Basic HTTPS, free (Let's Encrypt) |
| OV (Organization Validation)| Medium | Business websites |
| EV (Extended Validation) | High | Banks, e-commerce |
| Wildcard (*.example.com)| Any | Covers all subdomains |
