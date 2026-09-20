# Ghana Soybean Procurement Intelligence

**An early-stage research and technical concept for an AI-powered procurement intelligence system designed to help Ghanaian soybean processors improve visibility into fragmented local soybean supply.**

> **Project stage: VALIDATION.** This repository documents problem research and a technical hypothesis. It is **not** an operational product, MVP, production deployment, or revenue-generating venture. No stakeholder interviews claimed here have been completed unless explicitly marked otherwise (currently: none completed).

---

## One-sentence description

A research-to-venture concept that combines structured agricultural data with Mistral open-weight language models (for retrieval, extraction, and natural-language interaction) and conventional ML (for forecasting and matching) to support soybean processor procurement planning in Ghana.

## Problem

Ghana has material soybean crushing capacity that is repeatedly described as underutilised, while the country continues to import substantial soybean meal and sometimes exports beans. Production is geographically concentrated in the north among fragmented smallholders; formal exchange volumes are tiny relative to national output; and processors face structural constraints around grain availability, quality (solvent vs expeller meal), working capital, logistics, and trade policy.

**Hypothesis (requires validation):** A material part of processor procurement difficulty is limited, timely visibility into where suitable local supply exists, expected volumes and harvest timing, quality characteristics, prices, aggregator networks, and logistics constraints—not only a shortage of physical production or capital.

This repository separates:
- **KNOWN / EVIDENCE-SUPPORTED** structural facts from primary and authoritative secondary sources
- **HYPOTHESIS** about information/coordination failure as a binding constraint
- **PROPOSED** system design
- **REQUIRES VALIDATION** items (especially primary interviews with processors and aggregators)

## Target users (proposed)

| User | Role in concept | Status |
|------|-----------------|--------|
| Soybean crushers / oilseed processors | Primary beneficiary — procurement planning | Proposed; not yet interviewed |
| Aggregators / licensed buyers | Supply-side information providers | Proposed |
| Producer organisations / outgrower schemes | Supply visibility partners | Proposed |
| Feed millers (secondary) | Downstream demand signal | Out of initial scope |

## Evidence for the problem (selected)

| Claim | Label | Source (period) |
|-------|-------|-----------------|
| Large-scale crushers: ~13 firms; ~172,000 MT/year installed grain capacity; ~72,000 MT/year actual (<50%) | KNOWN | USDA GAIN GH2023-0006 (Oilseeds Voluntary, 2023 survey cited) |
| Processors operating below ~70% capacity due to insufficient grain (narrative) | KNOWN (USDA industry narrative) | USDA GAIN GH2024-0006 (7 Jun 2024) |
| >85% of soybean use goes to animal feed (poultry + aquaculture) | KNOWN | MoFA PFJ 2.0 via USDA GH2024-0006 |
| Soybean meal imports ~57–60k MT (USDA Post MY2022/23–2024/25); WITS HS 2304 value **US$44.42m** (CY 2023) | KNOWN | USDA GH2024-0006; World Bank WITS |
| Soybean grain duty 10% CIF; SBM duty often waived in practice → preference for importing meal | KNOWN | USDA Oilseeds 2023 & 2024 |
| MoFA production 291k MT (2023) vs 193k MT (2024); USDA Post 250k (MY2023/24) / 290k forecast (MY2024/25) — **series conflict flagged** | KNOWN with conflict | MoFA PBB 2024/2025; USDA GH2024-0006 |
| Production predominantly northern Ghana; many farms <1 ha | KNOWN | USDA GH2024-0006 |
| GCX soybean trade **512 MT** in 2024 (tiny vs national crop) | KNOWN | Citinewsroom citing 2024 Financial Stability Review (Aug 2025 article) |
| Local beans ~GH¢5,250/t (Apr 2024); domestic SBM GH¢415/50kg vs imported GH¢480/50kg — poultry still prefer imports | KNOWN | USDA GH2024-0006 |
| “Processors lack a usable digital procurement visibility layer” | **HYPOTHESIS — REQUIRES VALIDATION** | Not yet tested via interviews |
| System will raise utilisation by X% / cut losses by Y% / raise farmer income by Z% | **NOT CLAIMED** | No evidence |

Full write-ups: [`research/`](research/).

## Proposed solution

A **procurement intelligence** layer (not a marketplace that moves beans by itself) that helps processors:

1. Express procurement requirements in natural language or structured forms  
2. Retrieve and ground answers from trusted documents and structured supply data  
3. View indicative supply maps (location, timing, quantity, quality tags) where data exist  
4. Explore forecast and risk views produced by non-LLM models  
5. Match against aggregator/producer network records when consented data are available  

**Out of scope for validation stage:** executing trades, credit underwriting, guaranteeing prices, or replacing field agronomy services.

Details: [`product/solution-concept.md`](product/solution-concept.md).

## Why AI

- Procurement information is fragmented across documents, messages, spreadsheets, and oral networks — suited to **retrieval + extraction**, not only dashboards.  
- Numerical tasks (forecasting volumes/prices, ranking matches, risk scores) are better handled by **conventional ML/statistics** with measurable error.  
- Separating LLM and ML workloads reduces hallucination risk on numbers and keeps inference costs manageable.

## Why Mistral

- **Open-weight** models support local or controlled-cloud deployment consistent with data-sovereignty preferences.  
- Suitable for NL interaction, RAG, requirement extraction, and (where evaluated) multilingual prompts.  
- Efficient inference options matter for low-bandwidth Ghanaian deployment constraints.  
- **Status:** Mistral is **proposed**, not integrated. No model performance claims.

See [`ai/mistral-strategy.md`](ai/mistral-strategy.md).

## Proposed system architecture (concept only)

```
Data ingestion
    ↓
Validation & normalisation
    ↓
Structured agricultural data layer
    ↓
Document / data retrieval (RAG index)
    ↓
Mistral language-model layer  ←→  Forecasting / matching / risk models (classical ML)
    ↓
Procurement intelligence layer
    ↓
User interface (low-bandwidth-aware)
```

No component above is claimed as deployed. See [`product/system-architecture.md`](product/system-architecture.md).

## Data requirements

See [`product/data-requirements.md`](product/data-requirements.md) and [`data/schema.md`](data/schema.md). Initial sources are expected to mix processor historical procurement (private, consented), aggregator records, public MoFA/USDA/GEPA/GCX statistics, weather, and geospatial layers. **No private datasets are stored in this repository.**

## African / Ghanaian context

- Designed around northern production → southern/middle-belt processing logistics.  
- Assumes intermittent connectivity and preference for efficient open-weight inference.  
- Emphasises **local data control** and clear provenance for government and commercial data.  
- Local-language interaction is a **goal contingent on adequate language data and evaluation**, not a present capability.

## Validation plan

Explicit hypotheses H1–H5, falsifiers, and metrics: [`validation/`](validation/).  
**No hypothesis is marked validated.** Interview plan is prepared but not executed in this repo.

## Current project stage

| Stage | Status |
|-------|--------|
| Desk research on Ghana soybean / feed complex | Completed (sourced notes in `research/`) |
| Problem framing for processor procurement | Completed as hypothesis |
| Technical concept (Mistral + ML split) | Completed as proposal |
| Stakeholder interviews | **Not started** |
| Data partnerships | **Not started** |
| Prototype / RAG demo | **Not built** |
| Model training / evaluation runs | **Not run** |
| Deployment | **None** |

## What has already been completed

- Extraction of soybean-relevant evidence from broader Ghana real-economy research (Wave 2, Sep 2026).  
- Structured problem definition with evidence labels.  
- Proposed product, architecture, AI strategy, evaluation framework, and validation plan.  
- Research gaps and assumptions documented (not hidden).

## What has not yet been validated

- Whether information visibility is a *binding* constraint vs working capital, tariffs, quality, or export competition.  
- Willingness of processors/aggregators to share data.  
- Whether RAG answers are trusted enough for procurement decisions.  
- Any quantitative impact on utilisation, lead time, or cost.  
- Multilingual performance.  
- Unit economics of deployment.

## Roadmap (indicative)

1. **Validation** — processor & aggregator interviews; falsify/refine H1–H5  
2. **Data** — consented pilot dataset + public stats pipeline  
3. **Thin prototype** — RAG over curated docs + structured tables (no fake accuracy claims)  
4. **ML baselines** — simple forecast/match models with reported error  
5. **Evaluation** — against metrics in `ai/evaluation-framework.md`  
6. **Only then** — limited pilot UI  

## Research sources

Primary table: [`research/sources.md`](research/sources.md).

## Accelerator fit (honest self-check)

| Criterion | Current strength | Still required |
|-----------|------------------|----------------|
| Problem relevance | Strong desk evidence of crush underuse, meal imports, fragmented supply | Interview confirmation that *visibility* is the right wedge |
| Innovation | Credible LLM+ML split for procurement intelligence | Working prototype |
| Technical potential | Clear architecture and eval plan | Benchmarks on Ghanaian data |
| Local context | Ghana-specific soy/feed facts and geography | Field validation |
| Scalability | Conceptually transferable to other oilseeds/grains | Not demonstrated |
| Team strength | Documented research discipline | Not evidenced in this repo (add separately in application) |

## Disclaimer

This is a **research and validation** repository for prior-work documentation (including use in applications such as the Mistral AI Africa Accelerator Bootcamp). It must not be read as proof of a live product, customers, revenue, or model accuracy.

## License

Documentation in this repository is shared for transparency of research. Add an SPDX license of your choice before wide redistribution if required.
