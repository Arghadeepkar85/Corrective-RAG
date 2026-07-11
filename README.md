# Corrective Retrieval-Augmented Generation (CRAG)

## 📖 About

Traditional Retrieval-Augmented Generation (RAG) systems improve Large Language Models (LLMs) by retrieving relevant documents before generating an answer. However, they rely on one strong assumption:

> **The retrieved documents are always relevant and sufficient.**

In practice, this assumption often fails.

A retriever may return:
- Irrelevant documents
- Incomplete information
- Noisy context
- Missing evidence required to answer the query

When incorrect or incomplete context is passed to the LLM, even state-of-the-art models can generate inaccurate or hallucinated responses.

The CRAG paper addresses this limitation by introducing a **correction mechanism** before generation, making Retrieval-Augmented Generation significantly more reliable.

---

# 💡 Key Insight from the Paper

One of the biggest takeaways from CRAG is:

> **Hallucinations in RAG systems are often caused by retrieval failures rather than generation failures.**

Instead of making the language model larger or more powerful, CRAG focuses on improving **the quality of retrieved knowledge** before passing it to the LLM.

This shift in perspective makes the system more robust while requiring only minimal changes to existing RAG pipelines.

---

# 🚀 Why CRAG is Better than Traditional RAG

Traditional RAG follows a simple pipeline:

```
User Query
      ↓
Retriever
      ↓
Retrieved Documents
      ↓
LLM
      ↓
Answer
```

This pipeline assumes retrieval is always correct.

CRAG introduces an additional verification layer:

```
User Query
      ↓
Retriever
      ↓
Retrieval Evaluator
      ↓
Good Retrieval? ────────────── No
      │                         │
     Yes                        ▼
      │                 Web Search
      │                         │
      ▼                         ▼
Retrieval Refinement ←──────────┘
      │
      ▼
LLM
      ▼
Final Answer
```

Instead of blindly trusting retrieved documents, CRAG verifies and corrects them before generation.

---

# 📂 Repository Structure

This repository contains educational implementations of the core CRAG concepts.

```
1_basic_rag.ipynb
```

## 1️⃣ Basic RAG

Implements the standard Retrieval-Augmented Generation pipeline.

Workflow:

- Load documents
- Create embeddings
- Store vectors
- Retrieve relevant chunks
- Generate response using an LLM

This notebook serves as the **baseline** for understanding why CRAG is needed.

---

```
2_retrieval_refinement.ipynb
```

## 2️⃣ Retrieval Refinement

Retrieved documents often contain:

- Duplicate information
- Irrelevant sentences
- Noisy chunks

This notebook demonstrates how retrieved knowledge can be refined before passing it to the language model.

Goal:

- Reduce noise
- Improve context quality
- Increase answer reliability

---

```
3_retrieval_evaluator.ipynb
```

## 3️⃣ Retrieval Evaluator

This is the **core contribution of the CRAG paper.**

Instead of assuming retrieved documents are correct, CRAG evaluates their quality.

The evaluator estimates whether the retrieved context is:

- Relevant
- Complete
- Reliable

If confidence is high:

```
Retrieve
    ↓
Generate
```

Otherwise:

```
Retrieve
    ↓
Evaluate
    ↓
Correct
```

This prevents the language model from generating answers using poor-quality retrieval.

---

```
4_web_search_refinement.ipynb
```

## 4️⃣ Web Search Fallback

When retrieval quality is insufficient, CRAG performs an additional external search.

Instead of forcing the LLM to answer with limited knowledge, the system retrieves fresh information and combines it with the original context.

Benefits:

- Better coverage
- More complete answers
- Reduced hallucinations

---

# 🧠 What I Learned from the Paper

Reading CRAG changed the way I think about Retrieval-Augmented Generation.

Before reading the paper, I assumed improving a RAG system mostly meant:

- Better embeddings
- Better vector databases
- Better LLMs

CRAG showed that another equally important factor is:

> **Retrieval Quality**

If the retrieved information is poor, even the strongest LLM will struggle.

Rather than making the generator smarter, CRAG makes the **retrieval pipeline smarter**, leading to more reliable AI systems.

---

# 🛠️ Technologies Used

- Python
- LangChain
- LangGraph
- Vector Database
- Embedding Models
- Large Language Models (LLMs)

---

# ⚠️ Note

This repository is **an educational implementation inspired by the CRAG research paper** and is intended to help understand its core ideas.

It is **not the official implementation released by the paper's authors.**

---

# 📚 Reference

**Corrective Retrieval-Augmented Generation (CRAG)**

Shi-Qi Yan, Jia-Chen Gu, Yun Zhu, Zhen-Hua Ling

https://arxiv.org/abs/2401.15884

---

## ⭐ If you found this repository useful, consider giving it a star.
