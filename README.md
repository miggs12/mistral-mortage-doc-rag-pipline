# Mistral Local RAG Pipeline for Document Q&A

## Overview
A fully local Retrieval-Augmented Generation (RAG) system for intelligent document understanding of noisy, multi-format PDFs (resumes, mortgage documents, payslips). The pipeline performs OCR, semantic chunking, metadata-aware retrieval, and grounded question answering using a local Mistral-7B LLM.

# Problem Statement
Manual document review in finance and compliance workflows is slow, inconsistent, and error-prone.
Documents vary widely in structure, quality, and layout, and OCR noise makes semantic understanding difficult.

# Pipeline Diagram

  PDF Documents
      │
      ▼
OCR Processing (PyMuPDF + Tesseract)
      │
      ▼
Semantic Chunking + Metadata Tagging
      │
      ▼
Embedding Generation (Nomic SentenceTransformer)
      │
      ▼
FAISS Vector Store
      │
      ▼
Semantic Retrieval (Top-K + Filters)
      │
      ▼
Local Mistral-7B Instruct (llama.cpp)
      │
      ▼
Gradio Interactive Q&A Interface


## Retrieval & System Performance Evaluation

# Key Results
# Retrieval Performance

Recall@6: 100%
MRR: 1.00
Precision@K: 67%
Hit Rate: 67%
Strong retrieval coverage with consistently top-ranked relevant chunks. Precision can be further improved with reranking.

# End-to-End Answer Quality
Answer Accuracy: 100%
Citation Accuracy: 100%
Factual Consistency: High (no hallucinations observed)

# System Performance
Average Response Time: ~9.1 seconds
Retrieval Latency: ~200–400 ms
LLM Generation: ~7 seconds (local inference)
Document Processing: ~20–40s per document (OCR + indexing)

## Demo
- **Loom Walkthrough (3 min):** https://www.loom.com/share/2099d0de777c4476958b5ab29ae8b819
- **Google Colab Notebook:** https://drive.google.com/file/d/1oJxt1QuhVOMU7Uw8lnYj2y9ONSkumRDN/view

## How to Run Locally (Quick Start)
Full setup, evaluation, and configuration details are documented in the notebook.

1. Install dependencies
pip install -r requirements.txt

2. Run the Gradio app
demo = create_interface()
demo.launch()

The app launches a local UI for uploading PDFs and querying documents.

# Limitations & Next Steps

- Cross-encoder reranker for improved precision
- Table-aware parsing for financial line items
- Multi-language OCR support
- Batch processing & persistence layer for production use

# Why This Matters
This project demonstrates how local LLMs + retrieval systems can deliver reliable document intelligence without external APIs. Suitable for finance, compliance, and privacy-sensitive workflows.
