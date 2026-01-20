# RAG__Vector-DB

# 📊 Data Embedder & Retrieval-Augmented QA System

This project demonstrates a **Retrieval-Augmented Generation (RAG)** pipeline built from scratch to understand how large language models work with **vector embeddings** instead of raw text.

The system is divided into two main stages:
1. **Data Embedding & Vector Database Creation**
2. **Retrieval + LLM-based Question Answering**

---

## 🧠 Project Overview

### 1️⃣ Data Embedding Pipeline
- Raw text data (Markdown files) is loaded from a directory.
- The data is split into smaller chunks using a recursive text splitter.
- Each chunk is converted into a **vector embedding** using an embedding model.
- These embeddings are stored in a **persistent vector database (Chroma)**.
- The vectors can be visualized in **3D space** (e.g., via t-SNE or PCA) to observe semantic clustering.

This step is performed **once**, and the resulting vector database is saved to disk.

---

### 2️⃣ Retrieval + Question Answering Pipeline
- The existing vector database is loaded from disk.
- A retriever searches for the most relevant chunks by comparing vector similarity.
- The retrieved chunks are passed as context to a **Large Language Model (LLM)**.
- The LLM answers questions **strictly based on the retrieved data**, not general knowledge.

This ensures responses are grounded in the embedded dataset.

---

## 🧩 Architecture (High Level)

