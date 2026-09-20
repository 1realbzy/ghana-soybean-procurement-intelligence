# System architecture (proposed)

```
User interface
    ↓
Procurement intelligence layer (answers, shortlists, alerts, uncertainty)
    ↓
Language/model layer (candidate)  ↔  Classical forecast/match/risk methods
    ↓
Retrieval index + structured agricultural data
    ↓
Validation / normalisation / provenance
    ↓
Ingestion (public stats, consented private records, documents, geo/weather)
```

| Component | Status |
|-----------|--------|
| All layers above | Proposed — not implemented in this repository |
| Stub APIs / demo backends | Intentionally omitted |

Deployment (cloud vs on-prem vs edge-light) is undecided and depends on partner security requirements after validation.
