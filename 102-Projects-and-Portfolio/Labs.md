# 102 - Projects & Portfolio - Labs

## Lab 1: Build Project 3 - Threat Intel RAG Bot (Starter)
```bash
mkdir threat-intel-rag && cd threat-intel-rag
pip install langchain langchain-anthropic langchain-community chromadb sentence-transformers streamlit python-dotenv
```

```python
# app.py
import streamlit as st, os
from langchain_anthropic import ChatAnthropic
from langchain_community.vectorstores import Chroma
from langchain_community.embeddings import HuggingFaceEmbeddings
from langchain.chains import RetrievalQA

st.title('Threat Intelligence Assistant')

@st.cache_resource
def load_qa():
    emb = HuggingFaceEmbeddings(model_name='all-MiniLM-L6-v2')
    vs  = Chroma(persist_directory='./chroma_db', embedding_function=emb)
    llm = ChatAnthropic(model='claude-sonnet-4-6', api_key=os.getenv('ANTHROPIC_API_KEY'))
    return RetrievalQA.from_chain_type(llm=llm, retriever=vs.as_retriever(search_kwargs={'k':4}))

qa = load_qa()
query = st.text_input('Ask about threats, TTPs, IOCs, or CVEs:')
if query:
    with st.spinner('Searching...'):
        result = qa.invoke(query)
        st.write(result['result'])
# Run: streamlit run app.py
```

## Lab 2: GitHub Profile README
Create repo: yourusername/yourusername with README.md:
```markdown
# Hi, I am [Name]

## Cybersecurity + AI Security Engineer
I build AI-powered security tools specializing in:
- LLM Security and AI Red Teaming
- SOC Automation and SOAR
- Threat Intelligence and DFIR
- Adversarial AI and LLM Applications

## Featured Projects
| Project | Description | Stack |
|---------|-------------|-------|
| Threat Intel Bot | RAG-powered threat intel assistant | LangChain, ChromaDB, Claude |
| SOC Automation | Automated alert triage with SOAR | n8n, Wazuh, VirusTotal |
| AI Security Scanner | LLM-powered vulnerability analysis | Python, Streamlit, Claude |

## Certifications
- CompTIA Security+
- [Add yours]
```

## Lab 3: Write a Technical Blog Post
Pick one topic:
1. 'Building a RAG Threat Intel Bot with LangChain and Claude'
2. 'Automating SOC Alert Triage with n8n and AI'
3. 'Prompt Injection: The Hidden Threat to AI Agents'

Structure: Hook -> Problem -> Architecture -> Code walkthrough -> Demo -> Lessons learned -> GitHub link
Publish on: Medium, Dev.to, or LinkedIn

## Practice Challenges
- [ ] Complete and deploy all 4 featured projects
- [ ] Write a technical blog post for each project
- [ ] Complete 3 CTF competitions and write up 1 challenge from each
- [ ] Apply to 5 bug bounty programs and submit at least 1 report
- [ ] Record a 5-minute demo video of your best project
- [ ] Prepare answers to 20 common cybersecurity interview questions
