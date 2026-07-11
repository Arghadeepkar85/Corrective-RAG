# Corrective Retrieval-Augmented Generation (CRAG)

> A hands-on implementation of the core concepts presented in the **Corrective Retrieval-Augmented Generation (CRAG)** research paper using **LangChain** and **LangGraph**.

## 📖 Overview

Retrieval-Augmented Generation (RAG) significantly improves Large Language Models by grounding responses in external knowledge. However, traditional RAG assumes that retrieved documents are always relevant and sufficient.

The CRAG paper challenges this assumption.

Instead of blindly trusting retrieved documents, CRAG introduces a **Retrieval Evaluator** that estimates retrieval quality before generation. When retrieval quality is low, the pipeline performs corrective actions such as knowledge refinement and external web search to improve the final response.

This repository explores these core concepts through an educational implementation.

---

## 📚 Research Paper

**Corrective Retrieval-Augmented Generation (CRAG)**

**Authors**
- Shi-Qi Yan
- Jia-Chen Gu
- Yun Zhu
- Zhen-Hua Ling

Paper:
https://arxiv.org/abs/2401.15884

---

# 🎯 Motivation

Traditional RAG follows:

```
User Query
     │
     ▼
Retriever
     │
     ▼
Retrieved Documents
     │
     ▼
LLM
     │
     ▼
Answer
```

The problem?

If retrieval is poor, even a powerful LLM can produce incorrect or hallucinated answers.

CRAG introduces a correction layer before generation.

```
User Query
      │
      ▼
Retriever
      │
      ▼
Retrieved Documents
      │
      ▼
Retrieval Evaluator
      │
 ┌────┴─────┐
 │          │
Good      Poor
 │          │
 ▼          ▼
Generate   Web Search
 │          │
 └────┬─────┘
      ▼
Knowledge Refinement
      ▼
LLM
      ▼
Final Answer
```

---

# 🚀 Features

- Basic RAG Pipeline
- Retrieval Evaluation
- Retrieval Refinement
- Query Rewriting
- Web Search Augmentation
- LangGraph Workflow
- End-to-End CRAG Pipeline

---

# 📂 Project Structure

```
.
├── 1_basic_rag.ipynb
├── 2_retrieval_refinement.ipynb
├── 3_retrieval_evaluator.ipynb
├── 4_web_search_refinement.ipynb
├── 5_query_rewrite.ipynb
├── 6_ambiguous.ipynb
└── README.md
```

---

# 🧠 Key Learnings

While studying the paper and exploring its implementation, I learned that:

- Hallucinations are often caused by poor retrieval rather than weak language models.
- Evaluating retrieval quality before generation improves reliability.
- Better context leads to better responses.
- External search acts as a useful fallback when internal knowledge is insufficient.
- Production RAG systems require intelligent orchestration rather than a simple retrieve-and-generate pipeline.

---

# ⚙️ Tech Stack

- Python
- LangChain
- LangGraph
- OpenAI / Gemini
- FAISS / Vector Database
- Tavily Search
- Jupyter Notebook

---

# 📌 Challenges Explored

While implementing the core concepts, several practical challenges became evident:

- Selecting an appropriate retrieval confidence threshold.
- Balancing retrieval quality with latency.
- Managing branching workflows using LangGraph.
- Preserving user intent during query rewriting.
- Combining vector retrieval with external web search efficiently.

---

# 📈 Future Improvements

- Hybrid Search (BM25 + Dense Retrieval)
- Cross-Encoder Re-ranking
- Adaptive Retrieval
- Self-RAG Integration
- Reflection-based Answer Verification
- Production Deployment

---

# 🙏 Acknowledgements

This project is an educational implementation inspired by the **Corrective Retrieval-Augmented Generation (CRAG)** research paper.

The implementation is intended to understand the architecture, workflow, and design decisions presented in the paper rather than reproduce the original research implementation.

---

## ⭐ If you found this repository useful, consider giving it a star!
