# Understanding the RAG Retrieval Pipeline

## 1. Introduction

The retrieval pipeline is responsible for finding information relevant to a user's question.

After documents have been processed and indexed, the system can search the knowledge base whenever a user submits a query.

## 2. Step-by-Step Workflow

### Step 1: User Query

The user submits a question.

Example:

"What are the steps to reset my account password?"

### Step 2: Query Embedding

The embedding model converts the question into a numerical vector.

The query vector represents the semantic meaning of the question.

### Step 3: Similarity Search

The system compares the query embedding with document embeddings stored in the vector database.

Common similarity measures include:

- Cosine similarity
- Dot product
- Euclidean distance

The database returns chunks that are considered relevant to the query.

### Step 4: Retrieve Relevant Chunks

The retriever selects the most relevant chunks.

A system may use a top-k strategy, where the top k matching chunks are returned.

For example, if k = 3, the retriever returns three candidate chunks.

### Step 5: Context Construction

The retrieved chunks are combined with the original user question to construct a prompt.

The prompt provides the LLM with information that may help it answer accurately.

### Step 6: Response Generation

The LLM processes the question and retrieved context to generate a response.

### Step 7: Return the Answer

The generated response is returned to the user.

If the system is designed to provide citations, it can also identify the source documents used for the answer.

## 3. Retrieval Example

Suppose a knowledge base contains three documents:

- Document A: Account registration
- Document B: Password reset instructions
- Document C: Payment methods

The user asks:

"How can I change my forgotten password?"

The retrieval system may identify Document B as the most relevant source.

The selected content is then passed to the LLM to generate an answer.

## 4. Retrieval Techniques

### Dense Retrieval

Uses vector embeddings to find semantically related content.

It can identify related information even when the query and document use different words.

### Keyword Retrieval

Uses matching terms to find documents containing specific words or phrases.

### Hybrid Retrieval

Combines keyword-based and semantic retrieval.

This can be useful when both exact terminology and broader meaning matter.

## 5. Reranking

A reranker evaluates retrieved candidates and reorders them based on their relevance to the query.

It can help improve the quality of the context supplied to the LLM.

## 6. Summary

The retrieval pipeline connects a user's question with relevant information from an indexed knowledge base. Its quality directly affects the usefulness of the final generated response.
