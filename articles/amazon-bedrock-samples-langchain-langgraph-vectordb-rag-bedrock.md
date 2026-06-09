# KB Article: LangChain, LangGraph, VectorDB, RAG, and Amazon Bedrock in `aws-samples/amazon-bedrock-samples`

## Overview
The `aws-samples/amazon-bedrock-samples` repository is a large collection of Amazon Bedrock examples. Across its Jupyter notebooks, it demonstrates how to build generative AI applications using:

- **Amazon Bedrock** foundation models and runtime APIs
- **RAG** workflows for document-grounded responses
- **Vector databases** for similarity search and retrieval
- **LangChain** for orchestration and chaining
- **LangGraph-style** agentic patterns for planning and execution
- multimodal retrieval and knowledge base workflows

## Repository Context
- **Source repository:** `aws-samples/amazon-bedrock-samples`
- **Primary language:** Jupyter Notebook
- **Focus:** Bedrock-powered generative AI, retrieval, agents, embeddings, and multimodal workflows

## Notebook Areas That Match the Topic
The notebook search surfaced several relevant examples, including:

- `embeddings/Titan-V2-Embeddings.ipynb`
- `multi-modal/Claude3/Claude3-Sonnet-Multimodal-Example.ipynb`
- `custom-models/bedrock-fine-tuning/nova/canvas/1-CanvasFT-customization-job.ipynb`
- `multi-modal/TwelveLabs/bedrock-twelvelabs-embedding-s3vectors-marengo-2.7.ipynb`
- `introduction-to-bedrock/prompt-caching/converse_api/notebooks/02_system_prompt_caching.ipynb`
- `introduction-to-bedrock/bedrock_apis/03_knowledgebases_api.ipynb`
- `agents-and-function-calling/open-source-agents/llamaindex/ReAct_Agent.ipynb`
- `articles-guides/prompt-engineering/session-4/Chat_application.ipynb`
- `multi-modal/Titan/titan-multimodal-embeddings/rag/1_multimodal_rag.ipynb`
- `rag/knowledge-bases/use-case-examples/agentic-rag-using-metadata-filters/02-agentic-rag-converse-api.ipynb`

> Note: notebook search results are limited by GitHub code search, so this list may be incomplete. You can review more notebook matches here:
> https://github.com/aws-samples/amazon-bedrock-samples/search?q=path%3A%2F.*%5C.ipynb%24&type=code

## Core Concepts Covered

### 1) Amazon Bedrock as the foundation layer
Several notebooks show Amazon Bedrock as the core inference and orchestration service:

- `multi-modal/Claude3/Claude3-Sonnet-Multimodal-Example.ipynb`
- `introduction-to-bedrock/prompt-caching/converse_api/notebooks/02_system_prompt_caching.ipynb`
- `introduction-to-bedrock/bedrock_apis/03_knowledgebases_api.ipynb`
- `custom-models/bedrock-fine-tuning/nova/canvas/1-CanvasFT-customization-job.ipynb`

Bedrock is used for:
- invoking foundation models through `bedrock-runtime`
- multimodal prompting
- prompt caching with Converse / ConverseStream APIs
- knowledge base retrieval and generation
- model customization and fine-tuning workflows

### 2) RAG workflows
RAG appears in multiple notebooks as the primary pattern for grounding responses in external data.

Examples:
- `introduction-to-bedrock/bedrock_apis/03_knowledgebases_api.ipynb`
- `articles-guides/prompt-engineering/session-4/Chat_application.ipynb`
- `multi-modal/Titan/titan-multimodal-embeddings/rag/1_multimodal_rag.ipynb`
- `rag/knowledge-bases/use-case-examples/agentic-rag-using-metadata-filters/02-agentic-rag-converse-api.ipynb`

Common RAG flow:
1. ingest documents or product data
2. chunk and embed content
3. store embeddings in a vector store
4. retrieve relevant passages or documents
5. pass retrieved context to an LLM
6. generate grounded answers with citations or reasoning

Observed RAG capabilities:
- chat with documents
- conversational RAG
- multimodal RAG
- agentic RAG with metadata filters
- knowledge-base-backed retrieval and generation

### 3) VectorDB / vector storage
Vector search is central to retrieval in several notebooks.

Examples:
- `embeddings/Titan-V2-Embeddings.ipynb`
- `multi-modal/Titan/titan-multimodal-embeddings/rag/1_multimodal_rag.ipynb`
- `rag/knowledge-bases/use-case-examples/agentic-rag-using-metadata-filters/02-agentic-rag-converse-api.ipynb`

Vector database roles:
- store embeddings generated from text, images, audio, or video
- support nearest-neighbor similarity search
- provide retrieval for RAG and semantic search workflows

Vector-related technologies mentioned:
- FAISS for in-memory search
- Amazon OpenSearch Serverless vector engine
- pgvector for PostgreSQL
- Amazon S3 Vectors
- Amazon Bedrock Knowledge Bases

### 4) LangChain
LangChain appears as an application-layer framework for retrieval and orchestration.

Examples:
- `articles-guides/prompt-engineering/session-4/Chat_application.ipynb`
- `agents-and-function-calling/open-source-agents/llamaindex/ReAct_Agent.ipynb`

LangChain’s role:
- building chains for question answering
- connecting retrievers with LLM prompts
- orchestrating document ingestion and query flows
- supporting chatbot-style applications

### 5) LangGraph-style agentic workflows
The repository includes agentic RAG and planning/execution patterns that align with LangGraph concepts, even where LangGraph is not explicitly named in the notebook snippet.

Best example:
- `rag/knowledge-bases/use-case-examples/agentic-rag-using-metadata-filters/02-agentic-rag-converse-api.ipynb`

Agentic workflow pattern:
- one model plans retrieval
- another model executes specific queries
- metadata filters narrow the search
- the system reasons over which documents or chunks to retrieve

This is similar to a graph-based agent workflow, where the application dynamically decides which step to take next.

## Notebook-by-Notebook Highlights

### `introduction-to-bedrock/bedrock_apis/03_knowledgebases_api.ipynb`
Demonstrates Amazon Bedrock Knowledge Bases for RAG:
- secure Q&A over documents
- retrieval and generation
- direct `RetrieveAndGenerate` and `Retrieve` APIs
- integration with agents
- citation-grounded responses

### `articles-guides/prompt-engineering/session-4/Chat_application.ipynb`
Demonstrates RAG-enhanced chat applications:
- conversational memory
- contextual retrieval
- use of LangChain and vector search libraries
- chatbot architecture patterns

### `multi-modal/Titan/titan-multimodal-embeddings/rag/1_multimodal_rag.ipynb`
Demonstrates multimodal RAG:
- image + text embeddings
- FAISS vector search
- optional persistent vector stores
- retrieval followed by reasoning with Claude

### `rag/knowledge-bases/use-case-examples/agentic-rag-using-metadata-filters/02-agentic-rag-converse-api.ipynb`
Demonstrates agentic RAG:
- document summaries first
- chunk-level retrieval second
- metadata filters for relevance
- planning/execution split across models

### `embeddings/Titan-V2-Embeddings.ipynb`
Focuses on Titan embeddings:
- dense vector representations
- multilingual support
- embedding dimensionality tradeoffs
- foundational step for any vector database / RAG architecture

### `multi-modal/Claude3/Claude3-Sonnet-Multimodal-Example.ipynb`
Shows Bedrock multimodal prompting:
- image + text input
- Claude 3 Sonnet via Messages API
- useful for multimodal assistants and document/image understanding

### `introduction-to-bedrock/prompt-caching/converse_api/notebooks/02_system_prompt_caching.ipynb`
Covers Converse API prompt caching:
- cache stable system prompts
- reduce repeated token costs
- useful for long-lived assistants and repeated interactions

## Practical Architecture Summary
A typical architecture reflected in these notebooks looks like this:

1. **Ingest content**
   - documents, product data, images, or summaries

2. **Create embeddings**
   - Bedrock Titan embeddings or other embedding models

3. **Store in a vector database**
   - FAISS, OpenSearch, S3 Vectors, pgvector, or Knowledge Bases

4. **Retrieve context**
   - semantic search, metadata filters, or agent-selected retrieval

5. **Generate answers**
   - Bedrock LLMs such as Claude, Nova, or other supported models

6. **Orchestrate with framework**
   - LangChain for chains
   - LangGraph-style flows for planning and dynamic routing

## Key Takeaways
- **Bedrock** is the core model runtime and orchestration layer.
- **RAG** is a repeated pattern throughout the repository.
- **VectorDBs** are essential for retrieval and grounding.
- **LangChain** supports retrieval and chain composition.
- **LangGraph-style agentic patterns** appear in multi-step retrieval and planning workflows.

## Suggested Tags
- Amazon Bedrock
- LangChain
- LangGraph
- Vector Database
- RAG
- Embeddings
- Knowledge Bases
- Multimodal AI
- Agents

## Suggested File Location
`articles/amazon-bedrock-samples-langchain-langgraph-vectordb-rag-bedrock.md`
