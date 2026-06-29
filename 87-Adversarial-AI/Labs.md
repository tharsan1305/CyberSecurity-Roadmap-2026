# 87 - Adversarial AI - Labs

## Lab 1: FGSM Evasion Attack with IBM ART
```python
# pip install adversarial-robustness-toolbox tensorflow
import numpy as np, tensorflow as tf
from art.attacks.evasion import FastGradientMethod
from art.estimators.classification import TensorFlowV2Classifier

model = tf.keras.Sequential([
    tf.keras.layers.Flatten(input_shape=(28,28)),
    tf.keras.layers.Dense(128, activation='relu'),
    tf.keras.layers.Dense(10, activation='softmax')
])
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
(x_tr,y_tr),(x_te,y_te) = tf.keras.datasets.mnist.load_data()
x_tr = x_tr.astype(np.float32)/255.0; x_te = x_te.astype(np.float32)/255.0
model.fit(x_tr, y_tr, epochs=3, verbose=0)

clf = TensorFlowV2Classifier(model=model, nb_classes=10, input_shape=(28,28))
attack = FastGradientMethod(estimator=clf, eps=0.2)
x_adv = attack.generate(x_te[:200])

acc_c = np.mean(np.argmax(clf.predict(x_te[:200]),1)==y_te[:200])
acc_a = np.mean(np.argmax(clf.predict(x_adv),1)==y_te[:200])
print(f"Clean accuracy:       {acc_c:.2%}")
print(f"Adversarial accuracy: {acc_a:.2%}")
# Expected: accuracy drops from ~98% to ~20-40%
```

## Lab 2: Data Poisoning Simulation
```python
import numpy as np
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
from sklearn.model_selection import train_test_split

np.random.seed(42)
X = np.random.randn(300, 5)
y = (X[:,0] + X[:,1] > 0).astype(int)

# Poison 20% of labels
y_p = y.copy()
y_p[np.random.choice(300,60,replace=False)] ^= 1

Xtr,Xte,yc,yte = train_test_split(X,y,test_size=0.2)
_,_,yp,_ = train_test_split(X,y_p,test_size=0.2)

mc = LogisticRegression().fit(Xtr,yc)
mp = LogisticRegression().fit(Xtr,yp)
print(f"Clean model:    {accuracy_score(yte,mc.predict(Xte)):.2%}")
print(f"Poisoned model: {accuracy_score(yte,mp.predict(Xte)):.2%}")
```

## Lab 3: FGSM Epsilon Study
Run FGSM with eps=0.05, 0.1, 0.15, 0.2, 0.3. Plot accuracy vs epsilon to understand the trade-off between perturbation size and attack strength.

## Practice Challenges
- [ ] Run FGSM with 5 different epsilon values and chart accuracy drop
- [ ] Research 3 real-world adversarial AI incidents (autonomous vehicles, spam filters, malware AV)
- [ ] Implement adversarial training as defense and measure improvement
- [ ] Explore MITRE ATLAS case studies on model evasion
- [ ] Research CleverHans and TextAttack libraries
