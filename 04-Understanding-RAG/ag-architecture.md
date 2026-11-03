# RAG Architecture

## 1. Introduction

Retrieval-Augmented Generation (RAG) combines information retrieval with text generation.

A traditional LLM generates responses based on patterns learned during training. A RAG system first retrieves relevant information from an external knowledge source and then provides that information to the LLM as context.

This approach is useful when an application needs to answer questions using a specific collection of documents.

## 2. Main Components

### 2.1 Knowledge Source

The knowledge source contains the information that the system can retrieve.

Examples include:
- PDF documents
- Text files
- Documentation
- Knowledge-base articles
- Internal company documents

### 2.2 Document Processor

The document processor extracts text from source documents and prepares it for indexing.

Typical operations include text extraction, cleaning, splitting, and metadata preparation.

### 2.3 Embedding Model

An embedding model converts text into numerical vectors.

These vectors represent semantic information and help the system identify content that is conceptually related to a query.

### 2.4 Vector Database

A vector database stores embeddings and associated information.

It supports similarity searches to identify chunks that are relevant to a user's question.

### 2.5 Retriever

The retriever searches the indexed knowledge base and returns relevant document chunks.

### 2.6 Large Language Model

The LLM receives the user's question along with the retrieved context and generates a natural-language response.

## 3. High-Level Architecture

```text
             DOCUMENT INGESTION

 Documents
     |
     v
 Text Extraction
     |
     v
 Text Cleaning
     |
     v
 Chunking
     |
     v
 Embedding Model
     |
     v
 Vector Database


              QUERY PROCESSING

 User Question
     |
     v
 Query Embedding
     |
     v
 Similarity Search
     |
     v
 Relevant Chunks
     |
     v
 Context + User Question
     |
     v
 Large Language Model
     |
     v
 Generated Response
```

## 4. How the Components Work Together

The ingestion process prepares documents before users ask questions.

When a question arrives, the system converts it into an embedding and searches for relevant content. The retrieved chunks are then included in the prompt sent to the LLM.

The LLM uses the provided context to generate a response.

## 5. Why Use RAG?

RAG can help applications:

- Answer questions using private or domain-specific documents.
- Incorporate updated information without retraining the LLM.
- Provide responses grounded in retrieved content.
- Support document-based question-answering systems.

## 6. Summary

RAG is not a replacement for an LLM. It is a system design approach that connects an LLM with an external information retrieval process.
