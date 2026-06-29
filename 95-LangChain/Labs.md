# 95 - LangChain - Labs

## Lab 1: Security Log Analyzer
```python
from langchain_anthropic import ChatAnthropic
from langchain.prompts import ChatPromptTemplate

llm = ChatAnthropic(model="claude-sonnet-4-6")
prompt = ChatPromptTemplate.from_messages([
    ("system", "SOC analyst. Output: SEVERITY | ATTACK_TYPE | MITRE | ACTION"),
    ("human", "{log}")
])
chain = prompt | llm

for log in [
    "500 failed SSH logins from 203.0.113.5 for root",
    "powershell.exe -enc SQBFAFgA... spawned from winword.exe",
    "Mass SMB from WORKSTATION-01 to 15 hosts in 2 minutes",
]:
    print(f"LOG: {log[:60]}")
    print(chain.invoke({"log": log}).content)
    print("---")
```

## Lab 2: Threat Intel RAG
```python
# pip install langchain langchain-anthropic langchain-community chromadb sentence-transformers
with open("ti.txt","w") as f:
    f.write("APT-29 uses spearphishing T1566.001 for initial access. "
            "SUNBURST backdoor deployed via SolarWinds DLL. "
            "C2 via HTTP to avsvmcloud.com. IOC hash: b91ce2fa41029f6955bff20079468448. "
            "Lateral movement via Golden SAML token forging.")

from langchain_community.document_loaders import TextLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter
from langchain_community.vectorstores import Chroma
from langchain_community.embeddings import HuggingFaceEmbeddings
from langchain.chains import RetrievalQA

docs   = TextLoader("ti.txt").load()
chunks = RecursiveCharacterTextSplitter(chunk_size=200, chunk_overlap=40).split_documents(docs)
emb    = HuggingFaceEmbeddings(model_name="all-MiniLM-L6-v2")
vs     = Chroma.from_documents(chunks, emb)
qa     = RetrievalQA.from_chain_type(llm=ChatAnthropic(model="claude-sonnet-4-6"),
             retriever=vs.as_retriever())

for q in ["APT-29 initial access?", "What is the IOC hash?", "How do they move laterally?"]:
    print(f"Q: {q}")
    print(f"A: {qa.invoke(q)['result']}
")
```

## Practice Challenges
- [ ] Build RAG over MITRE ATT&CK JSON from attack.mitre.org
- [ ] Add ConversationBufferMemory to a security chatbot
- [ ] Create a 3-tool agent: check_ip, check_hash, search_cve
- [ ] Build: extract IOCs -> enrich -> summarize -> generate report (multi-step chain)
