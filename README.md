# VeriRAG

A verification-driven Retrieval-Augmented Generation (RAG) framework designed to improve factual reliability by combining semantic retrieval, cross-encoder reranking, claim-level verification, contradiction detection, adaptive retrieval, and persistent failure memory.

Unlike conventional RAG systems that generate responses directly from retrieved context, VeriRAG performs multiple layers of deterministic validation before producing a final answer, significantly reducing hallucinations and unsupported claims.

---

## Overview

Large Language Models frequently generate plausible but unsupported information even when paired with Retrieval-Augmented Generation.

VeriRAG introduces a multi-stage verification pipeline that evaluates every generated response through evidence grounding, contradiction analysis, and adaptive reasoning before allowing an answer to be returned.

The framework is designed for applications requiring high factual reliability such as research assistance, technical documentation, legal retrieval, and enterprise knowledge systems.

---

## Architecture

```
                     User Query
                          │
                          ▼
               FAISS Vector Retrieval
                          │
                          ▼
               MMR Candidate Selection
                          │
                          ▼
          Cross-Encoder Re-ranking (BGE)
                          │
                          ▼
            Top Evidence Chunks Selected
                          │
                          ▼
               LLaMA 3 Response Draft
                          │
                          ▼
             Atomic Claim Extraction
                          │
                          ▼
          Claim-by-Claim Verification
                          │
          ┌───────────────┴───────────────┐
          │                               │
          ▼                               ▼
 Cross-Document Audit          Evidence Sufficiency Check
          │                               │
          └───────────────┬───────────────┘
                          ▼
             Hallucination Risk Analysis
                          │
                          ▼
         Adaptive Query Refinement (if needed)
                          │
                          ▼
        Persistent Failure Memory Learning
                          │
                          ▼
            Verified Final Response
```

---

## Features

- Hybrid Retrieval using FAISS and Ollama Embeddings
- Maximum Marginal Relevance (MMR) retrieval
- Cross-Encoder semantic reranking
- Atomic claim extraction
- Claim-level evidence verification
- Cross-document contradiction detection
- Evidence sufficiency scoring
- Hallucination risk estimation
- Adaptive query reformulation
- Persistent failure memory
- Deterministic reasoning trace generation
- Structured verification reports

---

## Technology Stack

| Component | Technology |
|------------|------------|
| Programming Language | Python |
| LLM Runtime | Ollama |
| Generator Model | LLaMA 3 |
| Embedding Model | nomic-embed-text |
| Vector Database | FAISS |
| Retrieval Framework | LangChain |
| Cross Encoder | BAAI/bge-reranker-base |
| Deep Learning | PyTorch |
| PDF Processing | PyMuPDF |

---

## Workflow

1. User submits a natural language query.
2. FAISS retrieves semantically relevant document chunks.
3. Maximum Marginal Relevance expands retrieval diversity.
4. Cross-Encoder reranks retrieved passages.
5. LLaMA 3 generates a draft response.
6. The response is decomposed into atomic factual claims.
7. Every claim is independently verified against the retrieved evidence.
8. Retrieved sources are analyzed for cross-document contradictions.
9. Evidence coverage and hallucination risk are calculated.
10. If verification fails, the query is automatically reformulated and retrieval is repeated.
11. Persistent failure memory records unsuccessful reasoning patterns for future adaptive retrieval.

---

## Project Structure

```
VeriRAG/
│
├── VeriRAG.ipynb
├── README.md
├── requirements.txt
├── faiss_index/
├── global_failure_memory.json
├── documents/
├── outputs/
└── models/
```

---

## Verification Metrics

The framework evaluates every response using multiple quality indicators:

- Evidence Coverage
- Context Relevance Score
- Hallucination Risk Index
- Unsupported Claim Detection
- Cross-Document Consistency
- Evidence Sufficiency
- Failure Localization
- Structured Reasoning Trace

---

## Applications

- Enterprise Knowledge Retrieval
- Research Assistants
- Scientific Literature Analysis
- Technical Documentation QA
- Legal Document Search
- Healthcare Knowledge Systems
- Regulatory Compliance
- Internal Organizational Knowledge Bases

---

## Future Improvements

- Multi-agent verification
- Knowledge graph integration
- Citation-aware answer generation
- Streaming retrieval
- Multi-modal document retrieval
- Long-context reasoning
- Incremental vector index updates
- Distributed retrieval pipelines

---

## Author

**Tallapalli Parameswara Reddy**

B.Tech – Robotics and Artificial Intelligence

Amrita Vishwa Vidyapeetham

GitHub: https://github.com/param77777

---

## License

This project is licensed under the MIT License.
