# Ghana Soybean Procurement Intelligence

Validation-stage research on whether an information and coordination layer can help Ghanaian soybean processors source suitable local beans more effectively.

## Status

**Validation stage.** Desk research on Ghana’s soybean crush, trade, and supply structure is complete. A falsifiable product hypothesis and technical sketch exist. No stakeholder interviews have been run, no production system is deployed, and no model has been integrated or evaluated on Ghanaian procurement data.

## Problem

Ghanaian soybean processors operate crushing capacity that industry surveys have reported as underused relative to installed capacity, with insufficient grain cited as a constraint ([USDA GAIN GH2023-0006](https://www.fas.usda.gov/data); [GH2024-0006](https://www.fas.usda.gov/data/ghana-oilseeds-and-products-voluntary-2), June 2024). Production is concentrated in northern Ghana and described as largely smallholder ([GH2024-0006](https://www.fas.usda.gov/data/ghana-oilseeds-and-products-voluntary-2)). Formal exchange volumes for soybeans are small versus the crop (GCX soy traded 512 MT in 2024, per Financial Stability Review coverage). Ghana has imported soybean meal at material scale while also exporting beans ([WITS](https://wits.worldbank.org/) HS 2304; MoFA PBB export values; USDA oilseeds notes). Quality differences (including solvent-extracted versus expeller meal) and trade-policy asymmetries affect the economics of crushing versus importing meal ([GH2024-0006](https://www.fas.usda.gov/data/ghana-oilseeds-and-products-voluntary-2)).

Desk research therefore supports a **processor-side challenge in securing sufficient suitable local beans and running plants consistently against available capacity**. It does **not** establish which constraint binds most for which firms: grain scarcity, working capital, quality, logistics, export competition, trade policy, information, or some mix.

## Why soybean procurement?

1. **Crush underuse.** USDA’s 2023 industry survey cites about 13 large processors with roughly 172,000 MT/year installed grain capacity and about 72,000 MT/year actual throughput ([GH2023-0006](https://www.fas.usda.gov/data)).
2. **Grain cited as a constraint.** Later USDA oilseeds notes describe utilisation below about 70% with insufficient grain as the industry narrative ([GH2024-0006](https://www.fas.usda.gov/data/ghana-oilseeds-and-products-voluntary-2)).
3. **Meal imports persist.** Soybean meal imports on the order of 60,000 MT in recent marketing years; WITS reports about US$44.4 million of HS 2304 imports in calendar 2023 ([GH2024-0006](https://www.fas.usda.gov/data/ghana-oilseeds-and-products-voluntary-2); [WITS](https://wits.worldbank.org/)).
4. **Policy and quality frictions.** Grain import duty versus practical treatment of meal imports, and buyer preference for higher-protein solvent meal, shape crush economics ([GH2024-0006](https://www.fas.usda.gov/data/ghana-oilseeds-and-products-voluntary-2)).
5. **Thin formal markets.** GCX soybean trade of 512 MT in 2024 is negligible relative to national production (FSR 2024 summary via press).

MoFA calendar-year production for 2024 (193,000 MT in PBB 2025) differs from USDA’s MY2024/25 production forecast (290,000 MT). Those series are not interchangeable; this repo does not average them. Details: [research/evidence.md](research/evidence.md).

## The hypothesis

**We are investigating whether** a material share of processors’ difficulty securing suitable local beans arises from fragmented supply information, limited visibility into available quantities and timing, quality uncertainty, and weak coordination among processors, aggregators, and producer networks.

That hypothesis is open. Competing explanations (working capital, tariffs, quality technology, export offtake, logistics) remain live. Primary research must rank them.

## What we are exploring

If primary research supports the hypothesis, a useful product would be a **procurement intelligence** workflow: help a processor state requirements; surface relevant supply, market, and document context; flag uncertainty; and support shortlisting of sourcing options. It would not execute trades, extend credit, or guarantee offtake.

Product concept (still a hypothesis): [product/solution-concept.md](product/solution-concept.md).

## Technical direction

Proposed pipeline (nothing below is claimed as implemented):

```
ingestion (public stats, consented private records, documents, geo/weather)
    → validation / normalisation / provenance
    → structured data layer + retrieval index
    → language / model layer (candidate)  ↔  forecasting / matching (classical methods)
    → procurement intelligence interface
```

Language models are a **candidate** for natural-language queries, extraction, and document interfaces—not a predetermined requirement. Volume, price, and match scores should come from transparent statistical or ML methods with measurable error. Detail: [ai/technical-direction.md](ai/technical-direction.md), [product/system-architecture.md](product/system-architecture.md).

## Why Mistral could fit

If validation shows a language/RAG workflow is needed, efficient open-weight models (including Mistral family checkpoints) are candidates for:

- natural-language interaction with procurement staff  
- information extraction from unstructured notes or documents  
- retrieval-grounded answers with citations  
- multilingual prompts **only if** evaluation supports it  

Numerical forecasting and ranking would not rely on an LLM as the primary calculator. Model choice depends on later evaluation (accuracy, latency, cost, deployment constraints)—not on this README. See [ai/mistral-strategy.md](ai/mistral-strategy.md).

## Current work

- Ghana soybean value-chain desk research ([research/ghana-soybean-value-chain.md](research/ghana-soybean-value-chain.md))
- Evidence audit with confidence labels ([research/evidence.md](research/evidence.md))
- Procurement constraint map ([research/procurement-constraints.md](research/procurement-constraints.md))
- Problem definition separating observation from hypothesis ([research/problem-definition.md](research/problem-definition.md))
- Product hypothesis and workflows ([product/](product/))
- Data requirements and logical schema ([product/data-requirements.md](product/data-requirements.md))
- Technical direction and evaluation plan ([ai/](ai/))
- Falsifiable hypotheses and interview guides ([validation/](validation/))

No runnable prototype is in this repository yet ([prototype/README.md](prototype/README.md)).

## What we do not know yet

- Relative importance of information/visibility versus capital, quality, policy, logistics, and export competition  
- Actual end-to-end procurement workflows inside crushers  
- Availability and reliability of lot-level or network-level supply data  
- Willingness of processors, aggregators, and producer organisations to share data  
- Whether better information changes purchase decisions  
- Competitive tools already in use  
- Willingness to adopt or pay for an intelligence workflow  

## Validation plan

Next stage is primary discovery with processors, aggregators, and producer organisations using falsifiable hypotheses H1–H5 and the interview guides in [validation/](validation/). No interviews in this repo’s evidence base have been completed.

## Research gaps

Named firm-level capacity and utilisation for recent seasons; reconciled official trade series; solvent versus expeller meal share; export-permit enforcement detail; crushing margins; national soy post-harvest loss rates; competitor landscape; primary user evidence on constraint ranking. Full list: [research/evidence.md](research/evidence.md).

## Roadmap

1. Primary stakeholder discovery  
2. Validate procurement workflow and constraint ranking  
3. Obtain representative consented data (if justified)  
4. Build a narrow prototype only after workflow clarity  
5. Test with users  
6. Evaluate technical and commercial viability  
7. Proceed, pivot, or stop  

## Research sources

Primary table: [research/sources.md](research/sources.md). Key anchors: USDA GAIN GH2023-0006 and GH2024-0006; MoFA Programme Based Budget production/export series; World Bank WITS HS 2304 (2023); GCX volumes via Financial Stability Review coverage.

## Disclaimer

This repository documents early-stage research and technical exploration. It does not represent a deployed commercial product or validated production system.
