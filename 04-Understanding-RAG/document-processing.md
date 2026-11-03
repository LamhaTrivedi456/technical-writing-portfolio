# Document Processing in RAG

## 1. Introduction

Document processing is an important stage in a RAG system. Before information can be retrieved, source documents must be converted into a format that can be searched efficiently.

The process generally includes text extraction, cleaning, chunking, embedding generation, and indexing.

## 2. Text Extraction

The first step is to extract readable text from the source documents.

Common sources include:
- PDF files
- DOCX files
- TXT files
- HTML pages
- Knowledge-base articles

The extraction method depends on the document format. Scanned PDFs may require Optical Character Recognition (OCR).

## 3. Text Cleaning

Extracted text may contain unnecessary spaces, formatting artifacts, repeated headers, or other unwanted content.

Cleaning helps prepare the text for consistent processing.

Examples include:
- Removing unnecessary whitespace.
- Handling repeated page headers and footers.
- Normalizing text formatting.
- Removing irrelevant content where appropriate.

## 4. Document Chunking

Chunking divides a large document into smaller sections.

For example, a document containing 3,000 words can be divided into smaller chunks of approximately 500 words each.

### Why Is Chunking Necessary?

Sending an entire document to a model may be inefficient or exceed the available context window.

Smaller chunks allow the retrieval system to identify more specific pieces of information.

### Chunking Strategies

**Fixed-size chunking**

Splits text into chunks based on a predefined size.

**Sentence-based chunking**

Splits text using sentence boundaries to preserve more natural language structure.

**Paragraph-based chunking**

Uses paragraphs as the basic units of content.

**Recursive chunking**

Attempts to split text using larger structural boundaries first, then smaller boundaries when necessary.

### Chunk Overlap

Chunk overlap means retaining a small portion of text from the previous chunk in the next chunk.

For example:

- Chunk 1: Words 1–500
- Chunk 2: Words 450–950

The overlapping section can help preserve context across chunk boundaries.

## 5. Embeddings

An embedding is a numerical representation of text.

An embedding model converts a sentence, paragraph, or document chunk into a vector.

For example, the following sentences have related meanings:

- "How do I reset my password?"
- "I forgot my password. How can I change it?"

An embedding model may represent these sentences with vectors that are close in the embedding space.

This helps semantic search identify related content even when the exact words differ.

## 6. Vector Storage

After generating embeddings, the system stores them in a vector database along with associated content and metadata.

Metadata may include:

- Document name
- Page number
- Chunk identifier
- Source location
- Creation date

This information can help filter search results and identify the original source.

## 7. Summary

Document processing transforms raw documents into searchable chunks. Good extraction, chunking, and embedding practices help improve the quality of information retrieval.
