# Public vs private data boundary

**Project stage:** Idea  
**Date:** 2026-09-23  
**Purpose:** Separate what the **public sources verified in this assessment** can presently support from what would need consented processor, aggregator, or other private operational data (or another accessible lot-level source). This is a research boundary note, not a claim that any private partnership exists.

Related: [public-data-source-assessment.md](public-data-source-assessment.md), [../product/data-requirements.md](../product/data-requirements.md).

**Data availability ≠ data sufficiency.** Discoverable, downloadable, or machine-readable public files may still lack the fields or granularity required for a named capability.

---

## A — Capabilities presently supported (partially) by verified public sources

| Capability (idea-stage) | Public inputs (examples) | Limit (availability ≠ sufficiency) |
|-------------------------|--------------------------|-------------------------------------|
| National supply-balance **sketch** | MoFA SRID cropped area; Facts & Figures / GAIN PSD; Comtrade HS 1201/2304 | Production context ≠ available lots; MY vs calendar year; crush assumptions not public |
| Trade & unit-value monitoring | Comtrade preview; GSS HS-12; Pink Sheet globals as external benchmark | GSS HS-12 mixes oilseeds; HS-10 soy not API-friendly in meta tested |
| Short-window domestic price **map** | MoFA SRID commodity prices (2025 window in file tested) | Snapshot ≠ multi-year procurement forecasting |
| Weather–yield **exploratory** | CHIRPS / NASA POWER + GADM + district yields from Facts & Figures PDF | Covariates ≠ supplier availability; GADM commercial licence restriction |
| Policy / programme context | MoFA PBB PDFs | Targets ≠ realized |
| Formal exchange **pulse** | BoG FSR annual GCX soy volume/price; GCX last-close snapshot | Illiquid channel; last-close ≠ farmgate panel or historical OHLCV |

None of the above is implemented as a product in this repository.

---

## B — Capabilities not presently supported by verified public sources

| Capability | Why verified public sources are not presently sufficient |
|------------|----------------------------------------------------------|
| Matching buyers to available lots | Inventories, grades, timing, and counterparty identity were not found in the open sources checked; would need partner/private operational data or another accessible lot-level source |
| Mill demand / crush schedules | Firm offtake calendars and meal inclusion practices are typically private |
| Dense farmgate & assembly-point prices with quality | SRID panel in the file tested is short; GCX snapshot is thin; no open ESOKO historical dump verified |
| Logistics / basis (north ↔ crush) | Contract freight and local basis vs global benchmarks were not found as open series |
| Supplier reliability / reject rates | Would need consented intake histories |
| Credit / offtake / marketplace execution | Out of product scope; also needs private commercial systems |
| Commercial redistribution of some boundary layers | e.g. GADM non-commercial licence without permission |

---

## C — Implication for the product hypothesis

Desk research can document crush under-utilisation, meal imports, thin formal markets, and northern fragmentation using public sources (see [market-evidence.md](market-evidence.md)).

Whether **limited timely visibility / coordination** is a material, addressable constraint remains an **open research hypothesis**. The public sources verified here do not settle that question. Processor, aggregator, and producer-organisation discovery (see [../validation/interview-plan.md](../validation/interview-plan.md)) and any later consented microdata would be needed before claiming product-market fit, adoption, or model performance.

**Maturity:** This repository remains at **Idea stage**. Public accessibility assessment does not upgrade maturity, imply customers, revenue, deployment, or a working prototype.
