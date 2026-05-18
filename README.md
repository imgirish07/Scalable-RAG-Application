# Scalable Multi-Agent RAG System

A production-grade, highly optimized **Retrieval-Augmented Generation (RAG)** system built for scalability, low latency, reliability, and intelligent multi-hop reasoning.

The system combines:

- Dense + Hybrid Retrieval
- Multi-Agent Query Decomposition
- Cross-Encoder Reranking
- Multi-Layer Caching
- Adaptive LLM Routing
- ONNX Optimizations
- Structure-Aware Chunking
- Semantic Search
- Parallel Retrieval Pipelines

---

# Architecture Overview

## Ingestion Pipeline

```text
PDF / Documents
      │
      ▼
DocumentCleaner
      │
      ▼
StructurePreserver
      │
      ▼
Chunker
      │
      ▼
Embeddings (BGE / SPLADE)
      │
      ▼
Qdrant Vector Store
```

### Features

- Boilerplate stripping
- Structure-aware chunking
- Heading propagation
- Table-aware splitting
- Metadata enrichment
- Dense + sparse embeddings

---

## Query Pipeline

```text
User Query
    │
    ▼
Cache Lookup
    │
    ├── Cache Hit → Return Response
    │
    └── Cache Miss
            │
            ▼
Complexity Detection
      ┌───────────────┴───────────────┐
      │                               │
      ▼                               ▼
SimpleRAG                       Agent Orchestrator
      │                               │
      ▼                               ▼
Retrieve → Rank → Generate      Query Decompose
                                Parallel Retrieval
                                Context Fusion
                                Final Synthesis
```

---

# Core Features

## Multi-Agent Query Decomposition

Complex queries are automatically decomposed into focused sub-queries using an intelligent planner.

### Capabilities

- Multi-hop reasoning
- Parallel retrieval
- Context fusion
- Sub-query quality validation
- Intelligent routing across collections

---

## Hybrid Retrieval System

Supports both:

- Dense Retrieval
- Sparse + Dense Hybrid Retrieval

### Technologies

- BGE Embeddings
- SPLADE Sparse Retrieval
- Qdrant Vector Search
- MMR Ranking
- Cross-Encoder Reranking

---

## Advanced Reranking

Uses ONNX-optimized cross-encoder rerankers for high precision retrieval.

### Optimizations

- CUDA-native ONNX inference
- Batched reranking
- Dynamic threshold filtering
- Coarse-to-fine retrieval

---

# Multi-Layer Cache Architecture

Three-layer cache system designed for low latency and reduced LLM cost.

| Layer | Purpose |
|---|---|
| L1 Memory Cache | Ultra-fast exact match |
| Redis Cache | Persistent distributed cache |
| Semantic Cache | Embedding similarity cache |

### Features

- Semantic paraphrase matching
- Query normalization
- Adaptive TTL policies
- Quality-gated cache writes
- In-flight request coalescing

---

# Adaptive LLM Infrastructure

Robust provider routing and failover handling.

### Features

- Multi-model Groq routing
- Gemini fallback support
- Rate limiting
- Provider health tracking
- Queue-based burst protection
- Automatic cooldown handling

---

# Performance Optimizations

The system implements **57 production-grade optimizations** across every layer.

## Retrieval & Embeddings

- ONNX Runtime acceleration
- Qdrant INT8 quantization
- Lazy SPLADE initialization
- gRPC transport optimization
- Embedding singleton caching

## Context Processing

- MMR ranking without re-embedding
- Token-aware context assembly
- Whole-chunk preservation
- Dynamic reranker thresholds

## Reliability

- Redis circuit breaker
- Provider health monitoring
- Burst protection queues
- Multi-layer rate limiting
- Quality-gated caching

## Scalability

- Parallel sub-query retrieval
- Async architecture
- Registry-based factories
- Modular pipeline design
- Config-driven orchestration

---

# RAG Variants

## SimpleRAG

Fast single-pass retrieval and generation pipeline.

### Best For

- Factual questions
- Low-latency applications
- Standard QA systems

---

## CorrectiveRAG

Adds retrieval evaluation and query rewriting.

### Best For

- Ambiguous queries
- Hallucination reduction
- Higher precision applications

---

## ChainRAG

Performs iterative multi-hop retrieval.

### Best For

- Complex reasoning
- Multi-document dependency resolution
- Research-style queries

---

# Technologies Used

## Vector Database

- Qdrant

## Embeddings

- BAAI BGE
- SPLADE

## LLM Providers

- Groq
- Gemini
- OpenAI-compatible APIs

## Frameworks & Libraries

- ONNX Runtime
- LangChain
- AsyncIO
- Redis
- Pydantic

---

# Key Design Principles

- Modular Architecture
- High Throughput
- Low Latency
- Production Reliability
- Scalable Retrieval
- Grounded Generation
- Cost Optimization
- Fault Tolerance

---

# Example Workflow

## Simple Query

```text
User Query
   │
   ▼
Dense Retrieval
   │
   ▼
Cross-Encoder Reranking
   │
   ▼
Context Assembly
   │
   ▼
LLM Generation
```

---

## Complex Query

```text
User Query
   │
   ▼
Query Planner
   │
   ▼
Sub-Query Decomposition
   │
   ▼
Parallel Retrieval
   │
   ▼
Context Fusion
   │
   ▼
LLM Synthesis
```

---

# Configuration

The system uses centralized configuration management via Pydantic settings.

### Configurable Components

- Retrieval mode
- Cache thresholds
- Reranker parameters
- LLM providers
- Rate limits
- Chunking strategy
- Token budgets

---

# Future Improvements

- GraphRAG Integration
- Multi-modal Retrieval
- Streaming Generation
- Distributed Semantic Cache
- Knowledge Graph Routing
- Tool-Augmented Agents
- Advanced Evaluation Benchmarks

---

# Use Cases

- Enterprise Knowledge Assistants
- AI Research Systems
- Internal Document Search
- Technical Documentation QA
- Multi-Document Reasoning
- Customer Support Agents
- Large-Scale Semantic Search

---

# Running the Pipeline

## Ingest Documents

```python
pipeline.ingest(file_path, collection_name)
```

## Query the System

```python
response = pipeline.query(
    query="Your question here",
    collection="docs",
    top_k=5
)
```

---

# Why This Project?

This project focuses not only on building a functional RAG pipeline, but on solving real production challenges:

- Retrieval quality
- Latency bottlenecks
- LLM reliability
- Cache efficiency
- Scaling concurrent workloads
- Reducing hallucinations
- Cost optimization
- Robust multi-provider orchestration

It demonstrates a complete production-oriented architecture for modern AI retrieval systems.
