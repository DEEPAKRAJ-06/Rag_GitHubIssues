# RAG Zephyr Project

I built this project to explore how Retrieval-Augmented Generation (RAG) can make LLMs more reliable and context-aware. Instead of fine-tuning a model every time new information appears, I wanted a system that could **fetch relevant knowledge on the fly** and use it to answer queries more accurately.  

---

## Project Overview

At its core, this project connects a **lightweight LLM** with a **retriever backed by FAISS** to handle real-world data from GitHub issues. Here’s how it comes together:

- **Model**: `HuggingFaceH4/zephyr-7b-beta`, chosen for its speed and strong instruction-following ability.  
- **Retriever**: FAISS, storing embeddings so the model can pull in the most relevant chunks at query time.  
- **Knowledge Source**: GitHub issues (open + closed), which simulate a dynamic knowledge base that keeps changing.  

The result is a system that doesn’t just generate generic answers—it uses fresh, specific context from GitHub discussions to ground its responses.  

---

## Why I Built This

One thing I noticed while experimenting with LLMs is that they’re often **out of date** or just **guess when they don’t know something**. That’s fine for small talk, but not if you want trustworthy answers.  

Fine-tuning is one option, but it’s expensive and can even make the model worse if not done carefully. RAG, on the other hand, lets the model stay **plugged into external data sources** without retraining.  

That’s why I put this together: to show how you can take a strong general model and give it domain knowledge instantly—whether that’s GitHub issues, documentation, or anything else.  
