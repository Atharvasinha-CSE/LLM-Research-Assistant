# 🤖 Next-Gen AI Research Workspace: Local RAG Engine

A locally hosted Retrieval-Augmented Generation (RAG) engine that transforms dense academic papers into an interactive, AI-powered chat workspace. Built with Hugging Face, FAISS, and Gradio, it processes complex PDFs and delivers instant, context-aware answers through a highly customizable, locally hosted web interface.

This project was built to run entirely on consumer-tier cloud GPUs (like a free NVIDIA T4 on Google Colab) without relying on paid external APIs (like OpenAI), ensuring 100% data privacy and zero operational costs.

---

## 🚀 Key Features

- **API-Free Architecture:** Fully open-source local ecosystem utilizing open-weights models.
- **Manual Pipeline Control:** Explicit orchestration of document extraction, semantic embedding, vector search, and prompt synthesis, bypassing unpredictable orchestration wrappers for deterministic control.
- **Real-Time Source Context:** Dual-pane user interface that streams the exact source paragraphs retrieved from the database alongside the AI's generated response.
- **Persistent Local Indexing:** Fast layout-aware PDF tokenization combined with sub-millisecond semantic search.

---

## 📊 System Architecture & Data Flow

1. **Document Ingestion:** Academic paper PDFs are fetched directly and parsed layer-by-layer using standard layout extraction tools.
2. **Text Segmentation:** Text strings are recursively split into 1,000-character chunks with a 200-character rolling window overlap to preserve sentence boundaries and semantic context.
3. **Vector Space Embedding:** Chunks are vectorized into high-dimensional numerical arrays using the `all-MiniLM-L6-v2` transformer model.
4. **Vector Database Indexing:** Generated coordinates are indexed inside a Facebook AI Similarity Search (FAISS) vector database.
5. **Contextual Retrieval:** The system conducts a k-nearest neighbors (k=2) semantic search matching the user's query against the FAISS index.
6. **Inference Pipeline:** Retrieved context segments are injected into a structurally guarded prompt layout and processed locally on an NVIDIA T4 GPU via a `TinyLlama-1.1B-Chat` pipeline.

---

## 🛠️ Tech Stack

- **LLM Foundation:** `TinyLlama/TinyLlama-1.1B-Chat-v1.0`
- **Embedding Model:** `sentence-transformers/all-MiniLM-L6-v2`
- **Vector Database:** FAISS (Facebook AI Similarity Search)
- **Tokenization & Processing:** LangChain Core Components
- **Web Interface Dashboard:** Gradio Blocks Framework
- **Hardware Acceleration:** PyTorch / CUDA (NVIDIA T4 Environment)

---

## 📂 Project Structure & Notebook Implementation

The project is structured into modular execution blocks for stability and performance:

