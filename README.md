# Self-Supervised Learning Based Modified Two-Pair BYOL Model

This project implements and compares three self-supervised learning models:

- Original BYOL (Bootstrap Your Own Latent)
- Modified Two-Pair BYOL (Proposed)
- Multi-Target BYOL



---

## 📌 Overview

Self-supervised learning (SSL) allows models to learn useful representations without labeled data.

BYOL is a popular SSL method that learns by predicting different augmented views of the same image without using negative samples.

This project extends BYOL by introducing:
- Cross-network learning (Two-Pair BYOL)
- Multi-target supervision (Multi-Target BYOL)

---

## 🧠 Models

### 1. Original BYOL
- One online network and one target network
- Uses exponential moving average (EMA)
- No negative samples

Pros:
- Stable training
- Simple architecture

Cons:
- Limited representation diversity

---

### 2. Modified Two-Pair BYOL (Proposed)

Key idea:
Use two online networks and two target networks with cross-consistency learning.

Learns:
- View1 (Network A) ↔ View2 (Network B)
- View2 (Network A) ↔ View1 (Network B)

Pros:
- Better representations
- Improved generalization
- More stable than complex variants
- Less computational time then Multi-Target BYOL

Cons:
- Higher GPU usage

---

### 3. Multi-Target BYOL

Key idea:
Use multiple target projections instead of a single target.

Pros:
- Strong supervision signal
- Potentially best performance

Cons:
- Hard to tune
- Less stable
- More compute required

---

## 🖼️ Dataset
STL-10 :
- 5000 images (96x96 RGB)
- 10 classes
- Used without labels during pretraining
  
CIFAR-10:
- 60,000 images (32x32 RGB)
- 10 classes
- Used without labels during pretraining



---

## ⚙️ Training Details

- Backbone: Resnet-50 & ResNet-18 
- Projection Head: MLP
- Predictor: MLP
- Optimizer: Adam / LARS
- Batch Size: 256
- EMA Decay: 0.996

---

## 📊 Evaluation

After pretraining:
- Extract features
- Train a linear classifier on frozen encoder

This evaluates representation quality.

---

## 📈 Results (Typical)

| Model              | Accuracy | Stability | Complexity |
|-------------------|---------|----------|-----------|
| Original BYOL     | Medium  | High     | Low       |
| Two-Pair BYOL     | High    | High     | Medium    |
| Multi-Target BYOL | High    | Medium   | High      |

---


## 👨‍💻 Author
```bash
Dr. Sushma Kumari, Ritik Kumar  
M.Tech Data Science, 2024-2026  
```
---
