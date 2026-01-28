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
