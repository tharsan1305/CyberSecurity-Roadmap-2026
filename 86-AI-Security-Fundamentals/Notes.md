# 86 - AI Security Fundamentals
## Overview
AI Security covers risks unique to AI/ML systems: data privacy, model security, adversarial threats, and governance.

## 1. AI-Specific Risk Landscape
| Risk | Description |
|------|-------------|
| Adversarial Attacks | Inputs crafted to fool the model at inference |
| Data Poisoning | Corrupting training data to alter model behavior |
| Model Extraction | Reconstructing model via repeated API queries |
| Model Inversion | Inferring training data from model outputs |
| Prompt Injection | Hijacking LLM behavior via malicious input |
| Hallucination | Model generates false but confident output |
| Supply Chain | Malicious ML libraries or pre-trained models |

## 2. Data Privacy in AI
- **Memorization**: LLMs can reproduce PII from training data verbatim
- **GDPR complexity**: Right to erasure is hard when data is baked into model weights
- **Inference risk**: User queries to cloud LLMs may be stored and used for retraining
- **Mitigation**: Differential privacy, PII scrubbing before training, federated learning, data minimization

## 3. Model Security Basics
- Encrypt model weights at rest and in transit
- Access control: who can download or fine-tune the model?
- Rate limiting on inference APIs (prevents extraction attacks)
- Input validation: reject malformed or oversized inputs
- Output filtering: detect and block harmful/sensitive model outputs
- Comprehensive audit logging of all inference requests

## 4. AI Governance Frameworks
| Framework | Org | Focus |
|-----------|-----|-------|
| NIST AI RMF | NIST | Risk management lifecycle for AI |
| EU AI Act | EU | Regulatory tiers based on risk level |
| MITRE ATLAS | MITRE | Adversarial threat landscape for AI |
| ISO/IEC 42001 | ISO | AI Management System standard |
| Google SAIF | Google | Secure AI Framework |
| OWASP LLM Top 10 | OWASP | LLM vulnerability taxonomy |

## 5. AI-Specific Attack Surface
```
Training Pipeline:  Dataset collection → Preprocessing → Training → Evaluation
                    Attacks: data poisoning, supply chain, model theft

Inference Pipeline: User input → Model → Output
                    Attacks: prompt injection, adversarial examples, extraction, evasion

Deployment:         API endpoints, model files, logs
                    Attacks: API abuse, weight theft, log analysis
```
