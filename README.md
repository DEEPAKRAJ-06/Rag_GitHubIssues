# RAG Zephyr Project

**Effortlessly build a Retrieval-Augmented Generation (RAG) system using Zephyr and LangChain, with GitHub issues as your knowledge base.**

---

##  Project Overview

This project showcases a streamlined RAG pipeline that combines:

- A lightweight yet powerful LLM: **`HuggingFaceH4/zephyr-7b-beta`**  
- A fast, in-memory retriever built using **LangChain** and **FAISS**  
- GitHub issue data (both open and closed) as a real-world knowledge source

It pulls relevant context at query time, preventing hallucination and ensuring fresh, on-point responses—no model fine-tuning required. :contentReference[oaicite:1]{index=1}

---

##  Why It Matters

Modern LLMs often lack awareness of emerging or proprietary content (e.g., newly opened GitHub issues). Fine-tuning is costly and can shift model behavior over time.

**RAG solves this by dynamically retrieving embeddings as context**, so your model is always aware of the latest content. Plus, swapping out to a better LLM is seamless. :contentReference[oaicite:2]{index=2}

---

##  Features at a Glance

| Component               | Technology Used                          | Purpose                                  |
|-------------------------|-------------------------------------------|------------------------------------------|
| Data Loader             | `GitHubIssuesLoader` from LangChain       | Pulls issues (excluding PRs) via GitHub API |
| Chunking                | `RecursiveCharacterTextSplitter`          | Safely splits long issue content         |
| Embeddings              | `HuggingFaceEmbeddings` using bge-base-en  | Converts text chunks to vector embeddings |
| Vector Store            | `FAISS`                                   | Stores embeddings & retrieves nearest contexts |
| Retrieval               | `db.as_retriever()`                       | Finds relevant chunks for a given query  |
| Language Model          | `zephyr-7b-beta` compressed to 4-bit       | Generates responses with low memory use  |
| Prompting & Chaining    | LangChain (PromptTemplate + pipeline)      | Formats RAG prompt and runs inference    |
| Output Processing       | `StrOutputParser`                         | Extracts clean text from model output    | :contentReference[oaicite:3]{index=3}

```bash
pip install torch transformers accelerate bitsandbytes sentence-transformers faiss-cpu langchain langchain-community
