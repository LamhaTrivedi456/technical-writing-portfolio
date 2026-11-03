# Understanding Retrieval-Augmented Generation (RAG)

## Overview

Retrieval-Augmented Generation (RAG) is an approach that improves the responses of Large Language Models (LLMs) by providing relevant information from external knowledge sources.

Instead of relying only on information learned during training, an LLM can retrieve relevant documents and use their content to generate a more context-aware response.

This guide explains the main concepts behind RAG, its architecture, document processing, retrieval pipeline, and practical considerations.

## What You Will Learn

- What Retrieval-Augmented Generation is
- Why RAG is useful
- How document chunking and embeddings work
- How vector databases support semantic search
- How information is retrieved and passed to an LLM
- Common limitations and best practices

## RAG Workflow

1. Collect documents from knowledge sources.
2. Split documents into smaller chunks.
3. Convert chunks into vector embeddings.
4. Store embeddings in a vector database.
5. Convert the user's question into an embedding.
6. Retrieve relevant document chunks.
7. Provide the retrieved context to the LLM.
8. Generate a response using the supplied context.

## Documentation

| Document | Description |
|---|---|
| [RAG Architecture](rag-architecture.md) | Components and overall system architecture |
| [Document Processing](document-processing.md) | Chunking, embeddings, and indexing |
| [Retrieval Pipeline](retrieval-pipeline.md) | How user queries retrieve relevant information |
| [Limitations and Best Practices](limitations-and-best-practices.md) | Challenges, evaluation, and improvements |

## Intended Audience

This guide is intended for students, developers, and beginners who want to understand how RAG systems work.

## Key Takeaway

RAG connects the language-generation capabilities of an LLM with relevant external information. This can make responses more grounded in a specific knowledge base, although the quality of the result depends on retrieval quality and the model's use of the retrieved context.
