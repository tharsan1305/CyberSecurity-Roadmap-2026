# 91 - Post-Quantum Cryptography - Labs

## Lab 1: Key Size Comparison Table
Research and complete this table:
| Algorithm | Type | Public Key | Private Key | Signature | Security |
|-----------|------|-----------|------------|-----------|---------|
| RSA-2048 | Classical | 256 B | 1192 B | 256 B | ~112-bit |
| ECC P-256 | Classical | 65 B | 32 B | 64 B | ~128-bit |
| Kyber-768 | PQC KEM | 1184 B | 2400 B | N/A | ~180-bit |
| Dilithium3 | PQC Sig | 1952 B | 4000 B | 3293 B | ~128-bit |
| SPHINCS+-128 | PQC Sig | 32 B | 64 B | 8080 B | ~128-bit |

Answer: Why are PQC keys larger? What is the performance tradeoff?

## Lab 2: Generate PQC Keys with Open Quantum Safe
```bash
# Install liboqs Python bindings
pip install liboqs-python

python3 << 'PQEOF'
import oqs

# Key Encapsulation with Kyber
with oqs.KeyEncapsulation("Kyber768") as kem:
    public_key = kem.generate_keypair()
    ciphertext, shared_secret_enc = kem.encap_secret(public_key)
    shared_secret_dec = kem.decap_secret(ciphertext)
    print(f"Public key size  : {len(public_key)} bytes")
    print(f"Ciphertext size  : {len(ciphertext)} bytes")
    print(f"Shared secret match: {shared_secret_enc == shared_secret_dec}")

# Digital Signatures with Dilithium
with oqs.Signature("Dilithium3") as sig:
    public_key = sig.generate_keypair()
    message = b"Security policy document v1.0"
    signature = sig.sign(message)
    valid = sig.verify(message, signature, public_key)
    print(f"Signature size : {len(signature)} bytes")
    print(f"Signature valid: {valid}")
PQEOF
```

## Lab 3: HNDL Threat Assessment
For a fictional hospital:
1. Identify data that must remain confidential for 10+ years (patient records, research)
2. List all systems using RSA or ECC (TLS, VPN, email signing, code signing)
3. Prioritize by: sensitivity × years of required confidentiality
4. Write a 1-page PQC migration plan with 3-year timeline

## Practice Challenges
- [ ] Install OQS and test all three NIST PQC algorithms
- [ ] Read NIST FIPS 203 executive summary and list key properties
- [ ] Research Chrome's X25519Kyber768 hybrid TLS experiment
- [ ] Compare PQC performance: key generation and signing speed vs RSA
- [ ] Write a 500-word explanation of why Shor's algorithm breaks RSA
