# 101 - LLM, SLM & MLM
## LLM (Large Language Models)
Decoder-only transformers trained on massive text for generation.

| Model | Org | Context | Notes |
|-------|-----|---------|-------|
| GPT-4o | OpenAI | 128K | Multimodal, strong reasoning |
| Claude 3.5 Sonnet | Anthropic | 200K | Strong coding and analysis |
| Gemini 1.5 Pro | Google | 1M | Largest context |
| LLaMA 3.1 405B | Meta | 128K | Open weights, self-hostable |

### Pretraining
- Dataset: Common Crawl, books, code, Wikipedia (trillions of tokens)
- Objective: predict next token
- Compute: 10,000+ A100 GPUs for months

### RLHF (Reinforcement Learning from Human Feedback)
1. Supervised fine-tuning on curated Q&A examples
2. Collect human preference data (which response is better?)
3. Train reward model on preferences
4. PPO optimizer maximizes reward model score

## SLM (Small Language Models)
Compact models for edge, speed, and low cost.

| Model | Params | Notes |
|-------|--------|-------|
| Phi-3.5 Mini | 3.8B | Microsoft, strong reasoning per param |
| Gemma 2 2B | 2B | Google, open weights |
| Mistral 7B | 7B | Strong general purpose |
| LLaMA 3.2 3B | 3B | Meta, fast and good quality |

```bash
# Run SLMs locally with Ollama
curl -fsSL https://ollama.ai/install.sh | sh
ollama pull llama3.2:3b
ollama run llama3.2:3b 'What is SQL injection?'
```

## Quantization for SLMs
| Method | Size Reduction | Quality Loss |
|--------|---------------|-------------|
| FP16 | 2x vs FP32 | None |
| INT8 | 4x | Minimal |
| INT4 (GGUF) | 8x | Small |
| NF4 (QLoRA) | 8x | Minimal |

## MLM (Masked Language Models)
Encoder-only transformers trained by predicting masked tokens.

Training: 'The attacker used [MASK] injection' -> model predicts 'SQL'
Bidirectional context: sees both left AND right of masked token.

| Model | Notes |
|-------|-------|
| BERT-base | Original, 110M params |
| RoBERTa | Improved BERT training |
| SecBERT | Fine-tuned for cybersecurity text |
| CyBERT (IBM) | Cybersecurity NER and classification |

### MLM Security Use Cases
- Malware family classification from descriptions
- NER: extract IPs, CVEs, malware names from threat reports
- Log classification by type and severity
- Similar alert/CVE detection via embeddings
