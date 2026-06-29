# 98 - RAG - Labs

## Lab 1: Threat Intel RAG
```python
# Create sample threat intel file
with open('threat_intel.txt', 'w') as f:
    f.write('APT-29 Cozy Bear SolarWinds Campaign\n'
            'Initial Access: Supply chain via SolarWinds Orion update T1195.002\n'
            'Backdoor: SUNBURST malicious DLL\n'
            'C2: HTTP beaconing to avsvmcloud.com every 12-14 days\n'
            'Lateral Movement: Golden SAML token forging\n'
            'IOC Hash: b91ce2fa41029f6955bff20079468448\n'
            'IOC Domain: avsvmcloud.com\n'
            'Detection: YARA signatures for SUNBURST in memory')

# Build RAG pipeline (see Notes.md for full code)
# Test questions:
questions = [
    'What is APT-29 initial access technique?',
    'What is the IOC hash?',
    'How do I detect this campaign?',
]
```

## Lab 2: RAG vs Direct LLM Comparison
```python
from langchain_anthropic import ChatAnthropic
llm = ChatAnthropic(model='claude-sonnet-4-6')
q = 'What is the SUNBURST backdoor IOC hash?'
print('WITHOUT RAG:', llm.invoke(q).content)  # may hallucinate
print('WITH RAG:', qa.invoke(q)['result'])     # returns exact hash from doc
```

## Lab 3: RAG Evaluation
```python
# pip install ragas datasets
from ragas import evaluate
from ragas.metrics import faithfulness, answer_relevancy
from datasets import Dataset
test = {
    'question': ['What is the SUNBURST IOC hash?'],
    'answer': ['The hash is b91ce2fa41029f6955bff20079468448'],
    'contexts': [['IOC Hash: b91ce2fa41029f6955bff20079468448']],
    'ground_truth': ['b91ce2fa41029f6955bff20079468448']
}
results = evaluate(Dataset.from_dict(test), metrics=[faithfulness, answer_relevancy])
print(results)
```

## Practice Challenges
- [ ] Build RAG over MITRE ATT&CK JSON
- [ ] Add source citations to every answer
- [ ] Implement hybrid search and compare quality
- [ ] Evaluate on 20 questions with RAGAS
- [ ] Build Streamlit UI for threat intel RAG bot
