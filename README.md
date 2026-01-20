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

### 1️⃣ Create a `.env` File

In the root of the project, create a file named `.env` and add your Gemini API key:

GEMINI_API_KEY=your_api_key_here
Make sure this file is not committed to version control.

2️⃣ Prepare the Knowledge Base
Ensure a folder (for example, knowledge_base/) exists and contains Markdown files (.md) with the data you want to embed.

You can:

Use the provided sample files, or

Add your own Markdown files of any domain (football, notes, documentation, etc.)

3️⃣ Run the Data Embedding Script
Run the script responsible for creating embeddings and storing them in the vector database:

bash
Copy code
python Data_embeddings.py
This step will:

Load files from the knowledge base folder

Split the text into chunks

Convert chunks into vector embeddings

Store them persistently in the vector database

⚠️ This step needs to be run only once, unless the data changes.

4️⃣ Run the Retriever + LLM Script
After the vector database is created, run:

bash
Copy code
python LLM_Retriever.py
This script will:

Load the existing vector database

Retrieve the most relevant chunks based on your query

Use the Gemini LLM to answer questions strictly based on the stored data

✅ Notes
The knowledge base folder must exist before running the embedding script.

You may add or modify Markdown files, but you must re-run Data_embeddings.py after doing so.

The same embedding model is used for both storing and retrieving data to ensure semantic consistency.
