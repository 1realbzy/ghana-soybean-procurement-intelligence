# System architecture

Proposed. Not implemented.

```
User interface
    ↓
Procurement intelligence (answers, shortlists, alerts, uncertainty)
    ↓
Language model layer (open-weight candidates)
    ↔
Classical forecast / match / risk methods
    ↓
Retrieval index + structured agricultural data
    ↓
Validation / normalisation / provenance
    ↓
Ingestion (public stats, consented private records, documents, geo/weather)
```

| Component | Status |
|-----------|--------|
| All layers above | Proposed |
| APIs, indexes, trained models | Not in this repository |

Hosting (cloud, private VPC, or on-prem) is undecided and depends on partner security requirements after validation.
