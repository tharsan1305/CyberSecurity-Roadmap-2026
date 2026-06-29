# 101 - LLM, SLM & MLM - Labs

## Lab 1: Run and Compare Local SLMs
```bash
curl -fsSL https://ollama.ai/install.sh | sh
ollama pull llama3.2:3b
ollama pull phi3.5
ollama pull mistral:7b

# Compare same security question across models
for model in llama3.2:3b phi3.5 mistral:7b; do
  echo "=== $model ==="
  ollama run $model 'In 2 sentences: what is SQL injection and how to prevent it?'
done
```
Score each: Accuracy (1-5), Detail (1-5), Speed (tokens/sec).

## Lab 2: BERT for Security Log Classification
```python
# pip install transformers torch
from transformers import AutoTokenizer, AutoModelForSequenceClassification, Trainer, TrainingArguments
from datasets import Dataset
import torch

logs = [
    ('Failed login from 192.168.1.5 for admin - 500 attempts', 1),
    ('User john logged in from corporate VPN successfully', 0),
    ('PowerShell executed with -encodedcommand parameter', 1),
    ('Routine backup completed at 02:00 AM', 0),
    ('LSASS memory read by unknown process malware.exe', 1),
    ('Windows Update KB5030219 installed successfully', 0),
]
texts, labels = zip(*logs)

tokenizer = AutoTokenizer.from_pretrained('bert-base-uncased')
model = AutoModelForSequenceClassification.from_pretrained('bert-base-uncased', num_labels=2)

def tokenize(ex): return tokenizer(ex['text'], padding=True, truncation=True, max_length=128)
ds = Dataset.from_dict({'text':list(texts),'label':list(labels)}).map(tokenize,batched=True)

args = TrainingArguments('./security-bert', num_train_epochs=3, per_device_train_batch_size=4)
Trainer(model=model, args=args, train_dataset=ds).train()

test = 'New scheduled task running cmd.exe created at system startup'
inp  = tokenizer(test, return_tensors='pt')
pred = torch.argmax(model(**inp).logits).item()
print('MALICIOUS' if pred==1 else 'BENIGN')
```

## Lab 3: Benchmark LLM vs SLM
Run these 5 tasks on Claude claude-sonnet-4-6 (API) and Llama 3.2 3B (Ollama):
1. Explain buffer overflow attack
2. Classify severity: PowerShell download cradle from Word
3. List 5 ransomware indicators
4. MITRE technique for lateral movement via SMB
5. Write YARA rule for encoded PowerShell

Compare: accuracy, detail, speed.

## Practice Challenges
- [ ] Benchmark 3 SLMs on 10 security questions, build comparison table
- [ ] Fine-tune BERT on 50 security log examples
- [ ] Research INT4 vs FP16: accuracy vs speed tradeoff
- [ ] Build a local security chatbot with Ollama + LangChain
