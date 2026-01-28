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

Common Mistake:
- Forgetting positional encodings → model becomes word soup

---

### 4. Feed Forward Network (FFN)
Applied **independently** to each token.

Looks boring.  
Carries most of the parameters. Quietly important.

---

### 5. Residual Connections + LayerNorm
Keeps gradients sane.

Without this:
- Training collapses
- Loss goes NaN


---

## Architecture Overview

Encoder-only → BERT-style  
Decoder-only → GPT-style  
Encoder–Decoder → Translation models

---

## Training Objective

Depends on task:

- Language Modeling → Next-token prediction
- Translation → Cross-entropy over target sequence
- Classification → Pooled output + softmax

Beginner trap:
- Confusing **pretraining** with **fine-tuning**
- They are not the same game

---

## Practical Stack

Typical modern setup:
- PyTorch
- Hugging Face Transformers
- AdamW optimizer
- Learning rate warmup (don’t skip this)

Silent killer:
- Wrong attention mask → model cheats or breaks

---

## Advantages

- Parallel computation
- Handles long dependencies
- Scales with data + compute

## Limitations

- Quadratic attention cost (O(n²))
- Memory hog
- Overkill for tiny datasets

Yes, your 5k-row CSV does NOT need a transformer.

---

## When to Use Transformers

Use if:
- Sequence length matters
- Context matters
- You have data + compute

Don’t use if:
- Dataset is tiny
- Task is tabular regression
- You just want to sound cool

---

## Further Reading

- *Attention Is All You Need*
- Transformer variants: Longformer, Performer, Linformer
- Flash Attention (actual speedup, not vibes)

---

## TL;DR

Transformers = attention + scale + engineering discipline.  
Powerful, expensive, unforgiving.

Learn PyTorch first. Then transformers.  
Otherwise you’re just cargo-culting APIs.
