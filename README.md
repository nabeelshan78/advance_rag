# Advanced RAG Techniques: From Chunking to Controlled Generation 🚀

## 📜 Overview

This repository is a comprehensive exploration of the advanced techniques required to build robust and intelligent Retrieval-Augmented Generation (RAG) systems. Moving beyond basic RAG implementations, this project provides a series of hands-on experiments in Jupyter notebooks that dissect the critical components of a sophisticated RAG pipeline.

The goal is to provide a practical guide and reusable code for understanding and implementing the nuanced decisions that separate a prototype from a production-grade AI application. We cover the full lifecycle: from intelligent data preparation and advanced retrieval strategies to fine-grained control over the Large Language Model's (LLM) generation process.

- The impact of chunking strategies on retrieval quality.
- Modern vector search techniques, including hybrid search and reranking.
- LLM orchestration for routing user intent.
- Controlling LLM generation for creative vs. factual tasks.
- Managing conversational context for chatbot-like applications.

## ✨ Key Features

- **Systematic Chunking Analysis**: Compare and contrast fixed-size, overlap, semantic, and hybrid chunking methods.
- **Advanced Retrieval with Weaviate**: Implement semantic, keyword (BM25), hybrid search, and reranking in a modern vector database.
- **LLM Task Orchestration**: Use an LLM to classify user queries and dynamically adapt its own behavior.
- **Fine-Grained Generation Control**: Experiment with temperature, top_p, top_k, and repetition_penalty to tailor LLM outputs.
- **Stateful Conversation Management**: Build a simple, context-aware chatbot that remembers previous turns.

## 📂 Repository Structure

The repository is organized into modules, each focusing on a core stage of the advanced RAG pipeline.

```bash
├── advance_chunking/
│ ├── Chunking_and_Vec_Search.ipynb # Notebook exploring various text chunking strategies.
| ├── travel_search_with_weaviate.ipynb # Advanced search, filtering, and reranking.
│ └── ...
├── llm-task-orchestration/
│ ├── llm_task_control_and_structured_outputs.ipynb # Classifying queries and tuning parameters.
│ └── ...
├── llm_context_experiments/
│ ├── llm_context_and_generation.ipynb # Managing conversation history and generation parameters.
│ └── ...
└── README.md
```


## 🔬 Core Concepts Explored

### 1. Advanced Chunking Strategies (advance_chunking)

This module investigates the critical first step of any RAG pipeline: text chunking. The quality of your chunks directly impacts the quality of your retrieval.

**Chunking_and_Vec_Search.ipynb**: This notebook demonstrates:
- **Fixed-Size Chunking**: The baseline approach, highlighting its tendency to break semantic context.
- **Chunking with Overlap**: An improvement to maintain context across chunk boundaries.
- **Semantic Chunking**: Using document structure (e.g., paragraphs, section headers) to create more meaningful chunks.
- **Hybrid Strategy**: A robust method that combines semantic splitting with a minimum chunk size to avoid overly small, context-poor chunks.

### 2. Modern Retrieval Systems (advance_chunking)

This section showcases a modern vector database, Weaviate, to implement sophisticated retrieval techniques that go far beyond simple vector similarity.

**travel_search_with_weaviate.ipynb**: This notebook covers:
- **Collection & Schema Definition**: Setting up a vector store with appropriate data types and vectorizer configurations.
- **Metadata Filtering**: Combining semantic search with structured filters (e.g., budget='Low').
- **Hybrid Search**: Using Reciprocal Rank Fusion (RRF) to combine the strengths of keyword-based (BM25) and semantic (vector) search for superior relevance.
- **Reranking**: Using a secondary model to re-order the initial retrieved results based on a more specific criterion, significantly boosting precision.

### 3. LLM Orchestration & Generation Control (llm-task-orchestration & llm_context_experiments)

Once documents are retrieved, controlling the LLM's reasoning and generation is paramount. These notebooks explore how to guide the LLM for more reliable and tailored outputs.

**llm_task_control_and_structured_outputs.ipynb**:
- **Query Classification**: Using an LLM as a "router" to determine user intent (e.g., technical vs. creative query).
- **Dynamic Parameter Tuning**: Based on the classified intent, automatically adjusting generation parameters like temperature for optimal output.

**llm_context_and_generation.ipynb**:
- **Parameter Deep Dive**: A systematic analysis of key generation parameters:
  - **temperature**: Controls randomness. Low for facts, high for creativity.
  - **top_p (Nucleus Sampling)**: Samples from the smallest set of tokens whose cumulative probability exceeds p.
  - **top_k**: Samples from the k most likely tokens.
  - **repetition_penalty**: Discourages the model from repeating itself.
- **Context Management**: Implements a `call_llm_with_context` function to maintain conversation history, enabling multi-turn dialogues.
- **Simple Chatbot**: A practical example that combines context management and dynamic generation into an interactive chat loop.
