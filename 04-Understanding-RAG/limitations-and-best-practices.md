# RAG: Limitations and Best Practices

## 1. Introduction

RAG can improve the usefulness of LLM applications by connecting them to external knowledge. However, a RAG system does not automatically guarantee accurate or reliable responses.

Its performance depends on document quality, retrieval effectiveness, prompt design, and the language model.

## 2. Common Limitations

### 2.1 Poor Document Quality

If the source documents contain outdated, incomplete, or incorrect information, the system may retrieve unreliable context.

**Best practice:** Regularly review and update the knowledge base.

### 2.2 Incorrect Chunking

Chunks that are too small may lose important context. Chunks that are too large may contain unrelated information.

**Best practice:** Choose chunk sizes based on document structure and retrieval requirements.

### 2.3 Irrelevant Retrieval

The retriever may return chunks that are related to the query but do not directly answer it.

**Best practice:** Evaluate retrieval results and consider hybrid search or reranking.

### 2.4 Hallucinations

An LLM may generate unsupported information even when relevant context is supplied.

**Best practice:** Use clear prompts that instruct the model to answer from the supplied context and acknowledge when the information is insufficient.

### 2.5 Latency and Cost

A RAG pipeline may involve document processing, embedding generation, vector search, and LLM inference.

These operations can increase response time and operating costs.

**Best practice:** Optimize retrieval, manage context length, and select models based on application requirements.

### 2.6 Data Privacy

Knowledge bases may contain confidential or sensitive information.

**Best practice:** Apply access controls, protect stored data, and ensure that retrieval respects user permissions.

## 3. Evaluating a RAG System

A RAG system should be evaluated at both the retrieval and generation stages.

### Retrieval Evaluation

- **Precision:** How many retrieved results are relevant?
- **Recall:** How much of the relevant information was retrieved?
- **Relevance:** Do the retrieved chunks address the user's question?

### Generation Evaluation

- **Faithfulness:** Is the answer supported by the retrieved context?
- **Answer relevance:** Does the answer address the user's question?
- **Completeness:** Does the response include the important information?

Evaluation should use representative questions and trusted reference answers where possible.

## 4. Best Practices Checklist

- [ ] Use reliable and updated source documents.
- [ ] Extract and clean document text carefully.
- [ ] Select chunking strategies appropriate to the content.
- [ ] Store useful metadata with each chunk.
- [ ] Evaluate embedding and retrieval quality.
- [ ] Use reranking when it improves relevance.
- [ ] Keep prompts clear and context-aware.
- [ ] Provide source references when appropriate.
- [ ] Test the system with different types of questions.
- [ ] Protect private information through access controls.

## 5. Conclusion

RAG is a useful approach for building applications that answer questions using external knowledge. However, good results require more than connecting a vector database to an LLM.

Reliable document processing, relevant retrieval, careful prompt design, and continuous evaluation are all important parts of building an effective RAG system.
