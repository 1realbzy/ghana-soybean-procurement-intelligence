# RAG architecture (PROPOSED)

## Goal

Answer procurement questions **only** with retrieved passages/tables, or explicitly say data are missing.

## Pipeline

1. Ingest documents & tables → chunk with metadata (`source_id`, `date`, `district`, `doc_type`).  
2. Embed + lexical index (hybrid retrieval).  
3. Retrieve top-k; optional rerank.  
4. Prompt Mistral with: user question, retrieved snippets, hard rule “no unsupported numbers.”  
5. Return answer + citation list + confidence/coverage flags.

## Anti-hallucination rules

- Numeric claims must appear in retrieved cells or be marked ESTIMATE from a named model.  
- If retrieval coverage < threshold → refuse with gap message.  
- Separate UI badges: **SOURCE**, **MODEL ESTIMATE**, **UNKNOWN**.

## Status

Design only. No vector DB, embeddings, or eval runs in this repository.
