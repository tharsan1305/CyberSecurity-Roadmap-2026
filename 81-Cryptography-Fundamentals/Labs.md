# 81 - Cryptography Fundamentals - Labs

## Lab 1: Hands-On with OpenSSL

### Generate RSA Key Pair
```bash
# Generate private key (2048-bit RSA)
openssl genrsa -out private.key 2048

# Extract public key from private key
openssl rsa -in private.key -pubout -out public.key

# View the private key contents
openssl rsa -in private.key -text -noout
```

### Encrypt and Decrypt a File
```bash
# Encrypt a file using public key
openssl rsautl -encrypt -inkey public.key -pubin -in secret.txt -out secret.enc

# Decrypt using private key
openssl rsautl -decrypt -inkey private.key -in secret.enc -out decrypted.txt
```

### Generate and Verify SHA256 Hash
```bash
echo "Hello World" | sha256sum
sha256sum filename.txt
# Verify integrity: hash file before and after transfer, compare hashes
```

### Create a Self-Signed Certificate
```bash
openssl req -new -x509 -key private.key -out certificate.crt -days 365   -subj "/CN=mysite.local/O=MyOrg/C=IN"

# View the certificate
openssl x509 -in certificate.crt -text -noout
```

---

## Lab 2: Understand TLS with Wireshark

### Steps
1. Open Wireshark → start capture on your network interface
2. Visit https://example.com in your browser
3. Filter: `ssl` or `tls`
4. Find the TLS Handshake packets:
   - Client Hello (client's supported cipher suites)
   - Server Hello (server's chosen cipher suite)
   - Certificate (server sends its cert)
   - Key Exchange
   - Change Cipher Spec
   - Application Data (encrypted)
5. Right-click the certificate → View certificate details
6. Document: What cipher suite was negotiated? What CA signed it?

---

## Lab 3: Password Hashing Comparison

```python
import hashlib, bcrypt, time

password = "MyPassword123"

# MD5 (FAST = BAD for passwords)
start = time.time()
md5_hash = hashlib.md5(password.encode()).hexdigest()
print(f"MD5:    {md5_hash} ({time.time()-start:.5f}s)")

# SHA256 (fast = also not great for passwords alone)
start = time.time()
sha256_hash = hashlib.sha256(password.encode()).hexdigest()
print(f"SHA256: {sha256_hash} ({time.time()-start:.5f}s)")

# bcrypt (SLOW by design = good for passwords)
start = time.time()
bcrypt_hash = bcrypt.hashpw(password.encode(), bcrypt.gensalt(rounds=12))
print(f"bcrypt: {bcrypt_hash} ({time.time()-start:.5f}s)")
# Notice bcrypt takes ~0.3s — makes brute force impractical
```

---

## Practice Challenges
- [ ] Use openssl to encrypt a file with AES-256-CBC symmetric encryption
- [ ] Create a PKI with Root CA → Intermediate CA → Server certificate using openssl
- [ ] Crack MD5 hashes from a sample list using Hashcat (educational)
- [ ] Inspect the TLS certificate of 5 websites using browser or openssl s_client
- [ ] Research and explain why SHA-1 is considered broken
