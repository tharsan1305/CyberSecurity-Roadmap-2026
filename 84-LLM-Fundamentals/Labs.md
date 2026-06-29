# 84 - LLM Fundamentals - Labs

## Lab 1: Token Counting with tiktoken

```python
import tiktoken  # pip install tiktoken

# GPT-4 encoder (also used by many other models)
enc = tiktoken.get_encoding("cl100k_base")

texts = [
    "Hello, world!",
    "cybersecurity threat analysis",
    "The quick brown fox jumps over the lazy dog",
    "SELECT * FROM users WHERE id = 1; DROP TABLE users;--"
]

for text in texts:
    tokens = enc.encode(text)
    print(f"Text: '{text}'")
    print(f"Tokens: {tokens}")
    print(f"Token count: {len(tokens)}")
    print(f"Decoded: {[enc.decode([t]) for t in tokens]}")
    print()
```

---

## Lab 2: Working with Embeddings (Semantic Search)

```python
from sentence_transformers import SentenceTransformer  # pip install sentence-transformers
from sklearn.metrics.pairwise import cosine_similarity
import numpy as np

model = SentenceTransformer('all-MiniLM-L6-v2')

# Security knowledge base
documents = [
    "SQL injection is a web vulnerability that manipulates database queries",
    "Phishing attacks trick users into revealing their credentials",
    "A firewall filters network traffic based on defined rules",
    "Ransomware encrypts files and demands payment for decryption",
    "MFA adds an extra verification step beyond just a password",
]

query = "How do attackers steal passwords?"

# Generate embeddings
doc_embeddings = model.encode(documents)
query_embedding = model.encode([query])

# Find most similar document
similarities = cosine_similarity(query_embedding, doc_embeddings)[0]
best_match_idx = np.argmax(similarities)

print(f"Query: {query}")
print(f"Best match: {documents[best_match_idx]}")
print(f"Similarity score: {similarities[best_match_idx]:.3f}")
```

---

## Lab 3: Call an LLM API

```python
import anthropic  # pip install anthropic

client = anthropic.Anthropic(api_key="YOUR_API_KEY")

message = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "Explain what a transformer architecture is in 3 sentences."}
    ]
)

print(message.content[0].text)
print(f"Input tokens: {message.usage.input_tokens}")
print(f"Output tokens: {message.usage.output_tokens}")
```

---

## Practice Challenges
- [ ] Count tokens for various cybersecurity terms and documents using tiktoken
- [ ] Build a simple semantic search over 20 security documents using sentence-transformers
- [ ] Read the original "Attention is All You Need" paper abstract and summarize
- [ ] Compare context windows of 5 major LLMs (research + table)
- [ ] Experiment with temperature setting (0 vs 0.7 vs 1.5) and observe output differences
