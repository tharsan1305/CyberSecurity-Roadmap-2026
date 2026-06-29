# 84 - LLM Fundamentals

## Overview
Large Language Models (LLMs) are AI models trained on massive text datasets to understand and generate human language. They power tools like ChatGPT, Claude, Gemini, and Copilot.

---

## 1. Transformer Architecture

### The Transformer (2017 – "Attention is All You Need")
The foundational architecture for all modern LLMs.

### Key Components
```
Input Text → Tokenizer → Embeddings → Positional Encoding
→ [Encoder/Decoder Blocks × N]
  → Multi-Head Self-Attention
  → Feed-Forward Network
  → Layer Normalization
→ Output Logits → Softmax → Predicted Token
```

### Self-Attention Mechanism
- Allows each token to "attend" to all other tokens in the context
- Captures long-range dependencies in text
- Multi-head: multiple attention patterns learned in parallel

### Encoder vs Decoder Models
| Type    | Examples          | Use Case                      |
|---------|-------------------|-------------------------------|
| Encoder | BERT, RoBERTa     | Classification, NER, embedding|
| Decoder | GPT, LLaMA, Claude| Text generation, chat         |
| Both    | T5, BART          | Translation, summarization    |

---

## 2. Tokens & Embeddings

### Tokens
- LLMs don't process words — they process tokens (subword units)
- Rule of thumb: 1 token ≈ 4 characters ≈ 0.75 words
- Common tokenizer: Byte Pair Encoding (BPE), SentencePiece

### Tokenization Example
```
"Hello, world!" → ["Hello", ",", " world", "!"] → [15496, 11, 995, 0]
"cybersecurity"  → ["cyber", "security"] → [2 tokens]
"supercalifragilistic" → ["super", "cal", "if", "rag", "il", "istic"] → [6 tokens]
```

### Embeddings
- Each token is converted to a high-dimensional vector (e.g., 4096 dimensions)
- Similar meaning → similar vectors (measured by cosine similarity)
- "King" - "Man" + "Woman" ≈ "Queen" (classic example)

### Vocabulary Size
- GPT-2: 50,257 tokens
- Claude/GPT-4: ~100,000 tokens

---

## 3. Training Process

### Pretraining
- **Data**: Trillions of tokens from internet, books, code, papers
- **Objective**: Next-token prediction (predict the next word)
- **Scale**: Weeks/months on thousands of GPUs
- **Result**: Base model (knows language, knowledge, but not how to chat)

### Fine-Tuning
- **SFT (Supervised Fine-Tuning)**: Train on high-quality Q&A examples
- **RLHF (Reinforcement Learning from Human Feedback)**:
  1. Collect human preference data (which response is better?)
  2. Train a Reward Model on preferences
  3. Use RL (PPO) to optimize model output to maximize reward
- **Result**: Instruction-following, helpful, safe assistant

### PEFT – Parameter-Efficient Fine-Tuning
- Full fine-tuning is expensive → PEFT techniques:
- **LoRA**: Add small trainable weight matrices, freeze base model
- **QLoRA**: LoRA + 4-bit quantization (fits on consumer GPU)

---

## 4. Context Windows

### What is a Context Window?
The maximum amount of text (in tokens) an LLM can process in a single request.

| Model          | Context Window |
|----------------|---------------|
| GPT-3          | 4,096 tokens  |
| GPT-4          | 128K tokens   |
| Claude 3.5     | 200K tokens   |
| Gemini 1.5 Pro | 1M tokens     |
| LLaMA 3        | 128K tokens   |

### Why Context Window Matters
- Long documents: Need large context to read a full PDF
- Multi-turn chat: Earlier conversation must fit in context
- RAG: Retrieved chunks must fit alongside the query

### Context Window Limitations
- Cost scales with context size
- Attention is quadratic in sequence length (computation issue)
- "Lost in the middle" problem: LLMs struggle with info in the middle of very long contexts
