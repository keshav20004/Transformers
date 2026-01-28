# Transformers

Transformers are a neural network architecture designed for sequence modeling.  
They ditch recurrence and convolutions and rely entirely on **self-attention**.  
Result: parallelism, scalability, and absurd performance on language tasks.

> Introduced in *Attention Is All You Need* (2017). Yes, that paper.

---
## Why Transformers Exist

RNNs:
- Slow (sequential)
- Forget long-range dependencies
- Painful to scale

Transformers:
- Fully parallelizable
- Long-context friendly


---
## Core Components

### 1. Self-Attention
Each token attends to every other token.
It answers: *“Which parts of the sequence matter rn?”*

Formula (scaled dot-product attention):

Beginner miss:
- Attention ≠ understanding
- It’s weighted averaging, not magic

---

### 2. Multi-Head Attention
Multiple attention mechanisms run in parallel.

Why?
- Each head learns different relations (syntax, semantics, position, vibes)

Pitfall:
- More heads ≠ better model
- You’re trading compute for marginal gains

---

### 3. Positional Encoding
Transformers are permutation-invariant.  
So we inject position info manually.

Types:
- Sinusoidal (original paper)
- Learned embeddings (most modern models)

Common L:
- Forgetting positional encodings → model becomes word soup

---

### 4. Feed Forward Network (FFN)
Applied **independently** to each token.


