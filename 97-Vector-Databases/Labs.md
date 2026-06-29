# 97 - Vector Databases - Labs

## Lab 1: Security KB
```python
import chromadb
client = chromadb.PersistentClient(path='./security_kb')
col = client.get_or_create_collection('kb')
docs = [
    'SQL injection: parameterized queries prevent it',
    'Phishing: MFA and training prevent credential theft',
    'Ransomware: offline backups and EDR are key defenses',
    'IDOR: server-side authorization checks prevent it',
    'DDoS: CDN and rate limiting mitigate it',
]
col.add(documents=docs, ids=[f'd{i}' for i in range(len(docs))])
for q in ['prevent database attacks', 'files encrypted bitcoin demanded', 'user sees other users records']:
    r = col.query(query_texts=[q], n_results=1)
    print(f'Q: {q}')
    print(f'A: {r["documents"][0][0][:100]}')
```

## Lab 2: Alert Deduplication
```python
import chromadb, hashlib
client = chromadb.Client()
seen = client.create_collection('seen_alerts')

def is_duplicate(alert, threshold=0.85):
    if seen.count() == 0: return False
    r = seen.query(query_texts=[alert], n_results=1)
    return (1 - r['distances'][0][0]) >= threshold

def add_alert(alert):
    seen.add(documents=[alert], ids=[hashlib.md5(alert.encode()).hexdigest()])

alerts = [
    'Failed login from 192.168.1.5 for admin - 50 attempts',
    'Login failure: IP 192.168.1.5, account admin, 50 tries',
    'Ransomware detected: mass file encryption on FILE-SERVER-01',
]
for a in alerts:
    if is_duplicate(a):
        print(f'[DUPLICATE] {a[:60]}')
    else:
        print(f'[NEW ALERT] {a[:60]}')
        add_alert(a)
```

## Practice Challenges
- [ ] Index MITRE ATT&CK techniques into ChromaDB and build semantic search
- [ ] Compare ChromaDB vs Qdrant speed on 10,000 docs
- [ ] Implement metadata filtering (severity + semantic similarity combined)
- [ ] Build CVE semantic search using NVD API data
