# 98 - RAG (Retrieval Augmented Generation)
## What is RAG?
Combines vector retrieval with LLM generation to answer questions grounded in your own documents.
Solves: knowledge cutoff, hallucination, private data access.

## RAG vs Fine-Tuning
| | RAG | Fine-Tuning |
|--|-----|------------|
| Updates | Real-time | Requires retraining |
| Cost | Low | High compute |
| Transparency | Cites sources | Black box |

## RAG Pipeline
```
INDEXING: Documents -> Loader -> Text Splitter -> Embed -> Vector Store
QUERY:    Question -> Embed -> Search -> Top-K Chunks -> LLM -> Grounded Answer
```

## Full Code
```python
from langchain_anthropic import ChatAnthropic
from langchain_community.document_loaders import TextLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter
from langchain_community.vectorstores import Chroma
from langchain_community.embeddings import HuggingFaceEmbeddings
from langchain.chains import RetrievalQA

docs   = TextLoader('threat_intel.txt').load()
chunks = RecursiveCharacterTextSplitter(chunk_size=500, chunk_overlap=100).split_documents(docs)
emb    = HuggingFaceEmbeddings(model_name='all-MiniLM-L6-v2')
vs     = Chroma.from_documents(chunks, emb)
qa     = RetrievalQA.from_chain_type(
    llm=ChatAnthropic(model='claude-sonnet-4-6'),
    retriever=vs.as_retriever(search_kwargs={'k':4})
)
print(qa.invoke('What are the IOCs for APT-29?')['result'])
```

## Chunking Strategies
| Strategy | When |
|----------|------|
| Fixed size 500 tokens | General purpose |
| Sentence splitting | Preserve semantic units |
| Recursive character | Default, works well |
| Semantic chunking | Split by topic change |

## Advanced RAG
- Hybrid Search: dense (semantic) + sparse (BM25) retrieval combined
- Re-ranking: cross-encoder re-ranks top-K before LLM
- RAGAS: evaluation framework (Faithfulness, Answer Relevancy, Context Recall)
