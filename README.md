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

Text Files
↓
Text Splitter
↓
Embedding Model
↓
Vector Database (Chroma)
↓
Retriever (Similarity Search)
↓
LLM (Gemini)
↓
Answer


---

## 🚀 How to Use

### 1️⃣ Prerequisites

- Python 3.9+
- Google Gemini API Key

Set your API key as an environment variable:

```
export GOOGLE_API_KEY="your_gemini_api_key"


(Windows PowerShell)

setx GOOGLE_API_KEY "your_gemini_api_key"

2️⃣ Install Dependencies
pip install -U \
  langchain \
  langchain-community \
  langchain-google-genai \
  langchain-chroma \
  langchain-text-splitters \
  sentence-transformers

3️⃣ Step 1: Create the Vector Database

Run the embedding script:

python create_vector_db.py


This will:

Load data files

Split them into chunks

Embed them into vectors

Store the vectors persistently in a local directory

You only need to do this once, unless the data changes.

4️⃣ Step 2: Ask Questions Using the Retriever + LLM

Run the QA script:

python query_with_llm.py


This script:

Loads the existing vector database

Retrieves relevant chunks based on your question

Uses Gemini to generate an answer grounded in the data

🔐 Important Notes

The embedding model must remain the same when creating and querying the vector database.

The LLM does not access the vector database directly — it only sees retrieved content.

No fine-tuning is involved; this is retrieval-based grounding.

🎯 Use Cases

Learning how vector embeddings work

Visualizing semantic similarity in 3D space

Building RAG systems

Domain-specific question answering

Understanding how LLMs interact with external knowledge

📌 Summary

This project provides a clear, hands-on implementation of:

Text chunking

Embedding generation

Vector storage

Semantic retrieval

LLM-based answer generation

It is designed for learning, experimentation, and visualization, not just usage.
