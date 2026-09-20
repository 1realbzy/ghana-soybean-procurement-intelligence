# Technical direction

## Separation of concerns

| Task type | Preferred approach | Reason |
|-----------|-------------------|--------|
| Language queries, extraction, document Q&A | Candidate LLM + retrieval with citations | Flexible over messy text |
| Volume/price forecasts, match scores | Classical statistics / ML | Calibrated error, auditability |
| Missing numbers | Refuse or mark estimate from a named model | Avoid silent hallucination |

## Proposed pipeline

Ingestion → provenance-tagged store → hybrid retrieval → optional language layer ↔ classical scorers/forecasts → UI with SOURCE / ESTIMATE / UNKNOWN badges.

## Status

Design only. No training runs, no vector index, no production inference in this repository.
