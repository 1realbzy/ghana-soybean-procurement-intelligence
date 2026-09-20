# Data requirements

## Classes of data

| Class | Examples | Access path | Status |
|-------|----------|-------------|--------|
| Public official | MoFA production, trade stats, GCX bulletins | Download / scrape under ToS | Desk-used; not piped |
| Attache / multilateral | USDA GAIN, FAO, WITS | Public | Desk-used |
| Processor private | Historical purchases, specs, suppliers | DPA + consent | **Not collected** |
| Aggregator private | Lot lists, farmer groups | Consent | **Not collected** |
| Geospatial / weather | District boundaries, rainfall | Public APIs | Planned |
| Documents | Contracts templates, quality standards, policy PDFs | Licence-aware | Curated list TBD |

## Minimum viable pilot dataset (PROPOSED)

1. One processor’s 2–3 seasons of purchase records (anonymised suppliers if required)  
2. District-level production estimates  
3. Weekly price panel (even informal market quotes)  
4. Quality specification library  
5. Aggregator directory for pilot geography  

Without (1) and (5), RAG over public PDFs alone is unlikely to beat existing buyer networks—**validation risk**.

## Sovereignty & privacy

- Tag every record with `source`, `licence`, `pii_flag`, `retention`.  
- No training of third-party closed models on consented private data without contract.  
- Prefer open-weight inference under processor control for sensitive corpora.
