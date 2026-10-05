# AI Asistant
> Memory-Enabled AI Assistant with RAG
> A minimal architecture that scales: ingestion, retrieval, conversation state, and observability.

## Resources
- [Quickstart: Build a Memory-Enabled AI Assistant with RAG in a Weekend](https://blog.paulserban.eu/post/quickstart-build-a-memory-enabled-ai-assistant-with-rag-in-a-weekend/)

## What it is?
- working system that can ingest documents, answer questions with source attribution, maintain conversation context, and provide visibility into retrieval quality

## Characteristics
- Memory-Enabled: Use RAG to store and retrieve information
- Scalable: Ingestion, retrieval, conversation state, and observability
- Minimal: Minimal dependencies and LLM usege

## Architecture
### Two Phased Architecture
1. Offline ingestion pipeline: 
   - source documents are split into chunks, converted to vector embeddings using an encoder model, and stored in a vector database alongside metadata
2. Online retrieval loop: 
   - user questions are similarly embedded and used to search for semantically similar chunks via nearest-neighbor search
   - retrieved context is then injected into the LLM prompt, allowing the model to generate answers based on specific source material rather than general training data

### Memory
Memory in this context operates at multiple layers. 
- Short-term memory lives in conversation state-the rolling window of recent messages that provides dialogue coherence. 
- Long-term memory resides in the vector store, containing all ingested documents that might be relevant across sessions.

### Foundational components
- a document ingestion pipeline
- a vector storage and retrieval layer
- a conversation state manager
- an observability framework

## Tech Stack
- programming language: JS/TS
- vector database: LanceDB
- raw content format: mdx
- api service: Fastify
