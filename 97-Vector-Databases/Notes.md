# 97 - Vector Databases
## Embeddings
```python
from sentence_transformers import SentenceTransformer
model = SentenceTransformer('all-MiniLM-L6-v2')
texts = ['ransomware encrypts files', 'cryptolocker is malware', 'sunny weather']
embeddings = model.encode(texts)  # (3,384) vectors
```

## Similarity Metrics
| Metric | Use |
|--------|-----|
| Cosine | Text similarity (most common) |
| Euclidean | When magnitude matters |
| Dot Product | Fast, used in many models |

## Vector DB Comparison
| Tool | Type | Best For |
|------|------|----------|
| ChromaDB | Local open-source | Dev and small scale |
| Pinecone | Cloud managed | Production at scale |
| Weaviate | Open-source/cloud | Hybrid search |
| Qdrant | Open-source | High-performance self-hosted |

## ChromaDB Quick Start
```python
import chromadb
client = chromadb.Client()
col = client.create_collection('security_kb')
docs = [
    'SQL injection manipulates database queries via unsanitized input',
    'Phishing emails steal credentials by impersonating trusted entities',
    'Ransomware encrypts files and demands Bitcoin payment',
    'MFA adds a second verification step beyond passwords',
]
col.add(documents=docs, ids=[f'doc_{i}' for i in range(len(docs))])
results = col.query(query_texts=['how do attackers steal passwords?'], n_results=2)
print(results['documents'])
```

## Security Use Cases
| Use Case | Description |
|----------|-------------|
| Threat Intel RAG | Natural language queries over threat reports |
| CVE Semantic Search | Find CVEs by description not just keyword |
| Alert Deduplication | Find alerts similar to known incidents |
| Policy Q&A | Ask questions about security policies |
