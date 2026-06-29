# 83 - AI Fundamentals - Labs

## Lab 1: Train a Simple ML Classifier (Python)

### Objective
Train a spam/not-spam classifier using scikit-learn.

```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.naive_bayes import MultinomialNB
from sklearn.metrics import classification_report
from sklearn.model_selection import train_test_split

# Sample data
emails = [
    "Win a free iPhone now click here",
    "Meeting tomorrow at 9am in conference room",
    "You have won 1 million dollars claim now",
    "Please review the attached project proposal",
    "Congratulations you are selected for prize",
    "Hi team, quarterly report is attached",
]
labels = [1, 0, 1, 0, 1, 0]  # 1=spam, 0=not spam

# Feature extraction
vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(emails)

# Train
X_train, X_test, y_train, y_test = train_test_split(X, labels, test_size=0.33)
model = MultinomialNB()
model.fit(X_train, y_train)

# Evaluate
y_pred = model.predict(X_test)
print(classification_report(y_test, y_pred))

# Test new email
new_email = ["Claim your free gift today limited offer"]
print(model.predict(vectorizer.transform(new_email)))
```

---

## Lab 2: Network Anomaly Detection with Clustering

```python
import numpy as np
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

# Simulate network traffic features: [packet_size, duration, bytes_transferred]
np.random.seed(42)
normal_traffic = np.random.normal(loc=[500, 1.0, 1000], scale=[100, 0.5, 200], size=(100, 3))
anomalous_traffic = np.array([[5000, 0.01, 50000], [10, 100, 5]])  # Clear anomalies

data = np.vstack([normal_traffic, anomalous_traffic])

# Cluster
kmeans = KMeans(n_clusters=2)
labels = kmeans.fit_predict(data)

print("Cluster assignments:", labels[-5:])
print("Points in cluster 0:", sum(labels == 0))
print("Points in cluster 1:", sum(labels == 1))
# Anomalies should be in the smaller cluster
```

---

## Lab 3: Confusion Matrix & Metrics Practice

```python
from sklearn.metrics import confusion_matrix, classification_report
import seaborn as sns
import matplotlib.pyplot as plt

# Simulated model predictions for malware detection
y_true = [0,0,0,1,1,1,0,1,0,1]  # 0=benign, 1=malware
y_pred = [0,0,1,1,1,0,0,1,0,1]

cm = confusion_matrix(y_true, y_pred)
print("Confusion Matrix:")
print(cm)
print(classification_report(y_true, y_pred, target_names=['Benign','Malware']))
```

---

## Practice Challenges
- [ ] Complete fast.ai Practical Deep Learning Course (free, lesson 1)
- [ ] Train a decision tree on the Iris dataset using scikit-learn
- [ ] Research and explain how Netflix uses ML for recommendations
- [ ] Complete TryHackMe "Introduction to AI" room
- [ ] Read Google's ML Crash Course and complete exercises (free)
