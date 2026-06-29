# 91 - Post-Quantum Cryptography
## Overview
Quantum computers threaten to break RSA and ECC. Post-Quantum Cryptography (PQC) provides quantum-resistant replacements standardized by NIST in 2024.

## 1. Quantum Threat to Current Crypto
### Shor's Algorithm
- Efficiently factors large integers and solves discrete logarithm on a quantum computer
- **Breaks**: RSA, ECC, Diffie-Hellman — all current public-key systems
- A powerful enough quantum computer = all current encrypted communications broken

### Grover's Algorithm
- Quadratically speeds up brute-force search
- **Weakens** symmetric crypto: AES-128 becomes 64-bit security
- **Fix**: AES-256 remains safe; double all symmetric key sizes

### Harvest Now, Decrypt Later (HNDL)
- Nation-states are capturing encrypted traffic TODAY to decrypt LATER when quantum is ready
- Any long-lived secret encrypted today with RSA/ECC is at risk
- Organizations must start migrating high-value, long-lived data NOW

## 2. Lattice-Based Cryptography
- Based on hard mathematical problems in high-dimensional lattices
- Problems: Learning With Errors (LWE), Short Integer Solution (SIS)
- Resistant to both classical and quantum computers
- Foundation of CRYSTALS-Kyber and CRYSTALS-Dilithium

## 3. CRYSTALS-Kyber — Key Encapsulation
- **Purpose**: Replaces RSA/ECDH for key exchange
- **NIST Standard**: FIPS 203 (2024) — also called ML-KEM
- **Security basis**: Module Learning With Errors (MLWE)

| Parameter Set | Security Level | Public Key Size |
|--------------|---------------|----------------|
| Kyber-512 | AES-128 equivalent | 800 bytes |
| Kyber-768 | AES-192 equivalent | 1184 bytes |
| Kyber-1024 | AES-256 equivalent | 1568 bytes |

## 4. CRYSTALS-Dilithium — Digital Signatures
- **Purpose**: Replaces RSA/ECDSA for digital signatures
- **NIST Standard**: FIPS 204 (2024) — also called ML-DSA
- **Use cases**: TLS authentication, code signing, certificate signing

### All 2024 NIST PQC Standards
| Standard | Algorithm | Type |
|----------|-----------|------|
| FIPS 203 | ML-KEM (Kyber) | Key encapsulation |
| FIPS 204 | ML-DSA (Dilithium) | Digital signatures |
| FIPS 205 | SLH-DSA (SPHINCS+) | Hash-based signatures |

## 5. Migration Roadmap
1. **Inventory**: Find all RSA, ECC, DH usage in your systems
2. **Prioritize**: Long-lived secrets and sensitive data first
3. **Hybrid**: Run classical + PQC in parallel during transition
4. **Test**: Deploy PQC in staging environments
5. **Migrate**: Replace key exchange with ML-KEM, signatures with ML-DSA
