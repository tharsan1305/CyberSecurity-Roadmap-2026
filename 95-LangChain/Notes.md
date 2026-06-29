# 95 - LangChain
## Overview
LangChain is a framework for building LLM-powered apps: chains, agents, memory, document loading, and RAG.

## Basic Chain
```python
from langchain_anthropic import ChatAnthropic
from langchain.prompts import ChatPromptTemplate

llm = ChatAnthropic(model="claude-sonnet-4-6")
prompt = ChatPromptTemplate.from_messages([
    ("system", "You are a SOC analyst. Analyze alerts concisely."),
    ("human", "{alert}")
])
chain = prompt | llm
result = chain.invoke({"alert": "500 failed logins from 185.220.101.5"})
print(result.content)
```

## Document Loaders
```python
from langchain_community.document_loaders import PyPDFLoader, TextLoader, WebBaseLoader
docs = PyPDFLoader("report.pdf").load()
docs = TextLoader("notes.txt").load()
```

## Text Splitter
```python
from langchain.text_splitter import RecursiveCharacterTextSplitter
chunks = RecursiveCharacterTextSplitter(chunk_size=500, chunk_overlap=100).split_documents(docs)
```

## RAG Pipeline
```python
from langchain_community.vectorstores import Chroma
from langchain_community.embeddings import HuggingFaceEmbeddings
from langchain.chains import RetrievalQA

emb = HuggingFaceEmbeddings(model_name="all-MiniLM-L6-v2")
vs  = Chroma.from_documents(chunks, emb)
qa  = RetrievalQA.from_chain_type(llm=llm, retriever=vs.as_retriever(search_kwargs={"k":3}))
ans = qa.invoke("What TTPs does APT-29 use?")
print(ans["result"])
```

## Output Parser
```python
from langchain.output_parsers import StructuredOutputParser, ResponseSchema
schemas = [
    ResponseSchema(name="severity", description="Critical/High/Medium/Low"),
    ResponseSchema(name="mitre",    description="MITRE technique ID"),
    ResponseSchema(name="action",   description="Immediate step"),
]
parser = StructuredOutputParser.from_response_schemas(schemas)
chain  = prompt | llm | parser
result = chain.invoke({"alert": "...", "format_instructions": parser.get_format_instructions()})
# Returns dict: {"severity":"High","mitre":"T1059.001","action":"Isolate host"}
```

## Use Cases
- RAG over threat reports and CVEs
- Structured log analysis with output parsers
- Tool-calling security agents
- Chatbot with memory for incident investigations
