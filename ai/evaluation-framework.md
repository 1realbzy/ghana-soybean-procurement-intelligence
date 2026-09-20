# Evaluation framework (PROPOSED metrics)

No scores are reported yet. Metrics below define how a future prototype would be judged.

| Metric | Type | Definition (sketch) | Pass idea (to be set pre-test) |
|--------|------|---------------------|--------------------------------|
| Retrieval precision@k | RAG | Relevant docs in top-k | Pre-registered threshold |
| Grounded answer accuracy | RAG | Human raters: supported / partial / hallucinated | Hallucination rate below threshold |
| Extraction F1 | NLP | Fields vs gold requirements | Pre-registered |
| Forecast MAE/MAPE | ML | Vs held-out seasons | Better than naive baseline |
| Match NDCG / precision@n | ML | Vs officer gold shortlists | Beats random/heuristic |
| Procurement lead time | Outcome | Days from need to secured tonnage | Pilot A/B if ethical/feasible |
| Supply visibility score | Outcome | % of required tonnage with named sources ≥N days ahead | Interview + logs |
| Task completion | UX | Officer completes RFQ shortlist unaided | Usability study |
| Latency | Systems | p50/p95 response time | Fit for low bandwidth |
| Compute cost | Systems | ¢ per query | Sustainability bound |
| Offline / low-connectivity mode | Systems | Task success on degraded link | Defined scenarios |

**Rule:** Do not publish marketing performance claims without the eval set, protocol, and confidence intervals.
