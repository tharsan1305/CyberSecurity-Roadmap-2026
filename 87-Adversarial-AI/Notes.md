# 87 - Adversarial AI
## Overview
Adversarial AI studies attacks that manipulate ML systems by exploiting their statistical nature. Critical knowledge for building robust AI-powered security tools.

## 1. Evasion Attacks
Craft inputs to cause model misclassification WITHOUT changing the model.
| Attack | Description | Strength |
|--------|-------------|---------|
| FGSM | Fast Gradient Sign Method — single step | Fast, weak |
| PGD | Projected Gradient Descent — iterative | Slower, strong |
| C&W | Carlini & Wagner — optimization based | Very strong |
| Square | Black-box, no gradient access | Transferable |

Real-world: Stop sign + printed stickers = car reads as 45mph sign.
Malware + benign byte padding = ML antivirus evades detection.

## 2. Data Poisoning
Corrupt training data so model learns wrong behavior.
- **Backdoor attack**: Attacker injects samples with a trigger. Model is normal EXCEPT when trigger present.
- **Clean-label poisoning**: Correct labels, subtly crafted to shift decision boundary.
- **Defense**: Data sanitization, outlier detection, dataset provenance tracking, robust training.

## 3. Model Inversion and Extraction
- **Model Inversion**: Query model repeatedly to reconstruct approximate training data (PII risk).
- **Model Extraction**: Many queries build a shadow model that mimics the original (IP theft).
- **Defense**: Rate limiting, return top-1 only (not probabilities), differential privacy, watermarking outputs.

## 4. Adversarial Examples in Security
| Domain | Attack |
|--------|--------|
| Malware detection | Add benign bytes to PE file without changing functionality |
| Spam filters | Adversarial text tokens that bypass NLP classifier |
| Intrusion Detection | Crafted packets to evade ML-based IDS |
| Face recognition | Adversarial glasses/makeup to spoof biometric auth |

## Defenses
| Defense | Description |
|---------|-------------|
| Adversarial Training | Train on mix of clean + adversarial examples |
| Input Preprocessing | Denoise / smooth inputs before inference |
| Ensemble Models | Multiple diverse models — harder to fool all simultaneously |
| Certified Defenses | Mathematically proven robustness bounds (randomized smoothing) |
