# System architecture (CONCEPT ONLY)

```
┌─────────────────────────────────────────────────────────┐
│                     User interface                       │
│            (web / USSD-lite / WhatsApp later)            │
└───────────────────────────┬─────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────┐
│              Procurement intelligence layer              │
│     (answers, shortlists, alerts, uncertainty flags)     │
└───────────────┬─────────────────────────┬───────────────┘
                │                         │
┌───────────────▼──────────┐   ┌──────────▼───────────────┐
│ Mistral LM layer (PROPOSED)│   │ Classical ML layer       │
│ - NL understanding         │   │ - supply/demand forecast │
│ - RAG grounded answers     │   │ - price indicators       │
│ - requirement extraction   │   │ - match scoring          │
│ - doc summarisation        │   │ - risk heuristics        │
└───────────────┬──────────┘   └──────────┬───────────────┘
                │                         │
┌───────────────▼─────────────────────────▼───────────────┐
│     Retrieval index + structured agricultural data       │
└───────────────────────────┬─────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────┐
│        Validation / normalisation / provenance           │
└───────────────────────────┬─────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────┐
│ Ingestion: public stats, consented ERP/CSV, docs, GIS,   │
│ weather, price feeds (each with licence & consent tags)  │
└─────────────────────────────────────────────────────────┘
```

## Implementation status

| Layer | Status |
|-------|--------|
| All boxes above | **PROPOSED** — not implemented in this repository |
| Fake services / stub APIs | **Intentionally omitted** (no theatre code) |

## Deployment options (PROPOSED)

- **Controlled cloud** in-region with encryption and access logs  
- **On-prem / private VPC** for processor data  
- **Edge-light clients** caching district packs  

Choice depends on partner security requirements—not decided.
