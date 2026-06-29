# 83 - AI Fundamentals

## Overview
Artificial Intelligence (AI) refers to computer systems that perform tasks that typically require human intelligence. Understanding AI fundamentals is essential for AI security professionals.

---

## 1. Types of AI

### Machine Learning (ML)
Systems that learn from data without being explicitly programmed.
- **Supervised Learning**: Trained on labeled data (input → correct output)
- **Unsupervised Learning**: Finds patterns in unlabeled data
- **Reinforcement Learning**: Learns by trial and error, maximizing rewards

### Deep Learning (DL)
A subset of ML using neural networks with many layers.
- Excels at: image recognition, speech, NLP
- Requires large amounts of data and compute
- Examples: CNNs (images), RNNs (sequences), Transformers (text)

### Natural Language Processing (NLP)
AI that understands and generates human language.
- Tasks: text classification, sentiment analysis, translation, summarization
- Modern NLP is powered by Transformer models (BERT, GPT, Claude)

---

## 2. Training vs Inference

### Training
- Process of teaching a model by showing it data and adjusting its weights
- Computationally expensive (GPUs/TPUs for hours/days/weeks)
- Produces a model (set of weights/parameters)

### Inference
- Using a trained model to make predictions on new data
- Much faster than training
- Can run on CPU or specialized hardware (edge devices)

```
Training:  Data → Model Architecture → Training Process → Trained Model
Inference: New Input → Trained Model → Prediction/Output
```

---

## 3. Supervised vs Unsupervised Learning

### Supervised Learning
- **Input**: Labeled dataset (X, Y pairs)
- **Goal**: Learn a function f(X) → Y
- **Examples**: Spam detection, malware classification, fraud detection

### Unsupervised Learning
- **Input**: Unlabeled data (X only)
- **Goal**: Discover hidden structure or patterns
- **Examples**: Clustering, anomaly detection, dimensionality reduction

### Semi-Supervised Learning
- Mix of labeled and unlabeled data
- Common in security (few labeled attack samples, many unlabeled events)

---

## 4. Basic Algorithms

### Regression (Supervised — Continuous Output)
- **Linear Regression**: Predict a continuous value (e.g., predict threat score)
- **Logistic Regression**: Binary classification (malicious/benign — despite name)

### Classification (Supervised — Categorical Output)
- **Decision Trees**: Tree of if-then rules, interpretable
- **Random Forest**: Ensemble of decision trees, more accurate
- **Support Vector Machine (SVM)**: Finds optimal separating hyperplane
- **Neural Networks**: Layers of neurons, learns complex patterns

### Clustering (Unsupervised)
- **K-Means**: Groups data into K clusters by distance
- **DBSCAN**: Density-based clustering, handles irregular shapes
- Security use: Group similar network behaviors to detect anomalies

### Key Metrics
| Metric    | Formula                     | Meaning                             |
|-----------|-----------------------------|-------------------------------------|
| Accuracy  | (TP+TN)/(TP+TN+FP+FN)      | Overall correctness                 |
| Precision | TP/(TP+FP)                  | Of predicted positives, how many are correct? |
| Recall    | TP/(TP+FN)                  | Of actual positives, how many did we catch? |
| F1 Score  | 2×(Precision×Recall)/(P+R)  | Harmonic mean of Precision & Recall |
| AUC-ROC   | Area under ROC curve        | Overall model discrimination ability|
