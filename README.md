# Ghana Soybean Procurement Intelligence

Early-stage research and technical design for an AI-based procurement intelligence system aimed at Ghanaian soybean processors.

## Overview

This project investigates whether combining structured agricultural data, retrieval, an efficient open-weight language model, and conventional machine learning can help processors source suitable local soybeans more effectively.

Desk research documents a processor-side challenge around crush utilisation, fragmented northern supply, thin formal markets, and meal imports alongside bean exports. Whether limited information and coordination are a material, addressable part of that challenge is still an open question. The work is at idea stage, supported by desk research and an initial technical design. The core problem hypothesis has not yet been validated with processors or other supply chain participants.

## Problem

Soybean processors in Ghana have been reported to run well below installed crushing capacity, with insufficient grain cited as a constraint (USDA GAIN GH2023-0006; GH2024-0006). Production is concentrated in the north and described as largely smallholder. Formal exchange volumes for soybeans are tiny relative to the crop. Soybean meal continues to be imported at material scale while beans are also exported. Quality differences (for example solvent-extracted versus expeller meal) and trade-policy asymmetries affect whether crushing local beans beats importing meal.

What remains unclear is how much of any given plant’s shortfall comes from absolute scarcity, working capital, quality rejects, export competition, logistics, policy, or late/incomplete information about available supply. This project focuses on the last class of explanations without assuming it is primary.

The working product hypothesis is that processors often lack timely, trustworthy visibility into where supply exists, expected production, harvest timing, available quantities, quality, prices, producer and aggregator networks, geography, logistics, emerging gaps, and procurement risk — and that a better information layer could help if those factors matter enough in practice.

## Why soybean?

Soybean is a useful first commodity because the crush and feed complex is large enough to matter, utilisation and meal-import patterns are documented in public attaché and trade sources, and the supply base is geographically concentrated and fragmented. MoFA and USDA production series disagree for recent periods (for example MoFA 193k MT for 2024 versus USDA’s MY2024/25 forecast of 290k MT); those figures are not averaged here. Detail sits in [research/](research/).

## Target users

**Primary:** Ghanaian soybean processors (procurement and operations staff).

**Secondary (if data-sharing proves viable):** aggregators, producer organisations, farmer networks/cooperatives, and logistics actors who sit between farm and plant.

No organisation named in this repository is a customer or partner.

## Evidence

Strongest desk anchors (not a claim that information failure is proven):

1. Large crushers: roughly 172k MT/yr installed grain capacity versus about 72k MT/yr actual throughput in a 2023 industry survey (USDA GAIN GH2023-0006).
2. Utilisation narrative below about 70%, with insufficient grain cited (USDA GAIN GH2024-0006).
3. Soybean meal imports on the order of 60k MT in recent marketing years; HS 2304 imports about US$44.4m in calendar 2023 (USDA; World Bank WITS).
4. Grain import duty versus practical treatment of meal imports, plus preference for higher-protein solvent meal (USDA GH2024-0006).
5. GCX soybean trade of 512 MT in 2024 — negligible formal liquidity (Financial Stability Review coverage).
6. Northern smallholder geography versus southern/central crush locations (USDA qualitative structure).

Full notes and conflicting series: [research/market-evidence.md](research/market-evidence.md), [research/sources.md](research/sources.md).

## Proposed system

If validation supports the information hypothesis, the product would be a **procurement intelligence** layer: take a processor’s requirements, retrieve relevant supply and market context with provenance, flag uncertainty, and support shortlisting of sourcing options.

It would not execute trades, extend credit, or guarantee offtake. It is not “a chatbot for farmers.” The language model, if used, is an interface and extraction component inside a broader data and decision system.

Intended questions to help answer later (not claimed as working today): what supply may be available; where and when; whether it matches requirements; what quality information exists; what gaps or risks to investigate; what evidence supports a recommendation.

## Technical architecture

Proposed pipeline. Nothing below is implemented in this repository.

```
Agricultural data
        ↓
Data ingestion
        ↓
Validation / normalisation / provenance
        ↓
Structured agricultural data layer
        ↓
Retrieval / knowledge layer
        ↓
Language model layer (open-weight candidates)
        ↔
Forecasting / matching / risk models (classical ML / stats)
        ↓
Procurement intelligence
        ↓
User interface
```

See [product/system-architecture.md](product/system-architecture.md).

## AI strategy

Language models are for natural-language interaction, requirement and document extraction, retrieval-grounded answers, summarisation, and multilingual prompts only if evaluation supports it.

Forecasting, price analysis, matching, ranking, and risk scores should use conventional statistical or ML methods with measurable error. The model layer is **model-agnostic**: candidate open-weight models are chosen later by evaluation, not by brand preference. See [ai/language-model-strategy.md](ai/language-model-strategy.md).

## Data requirements

Public production and trade stats, price panels, geography/weather, quality specs, and — if partners consent — processor purchase histories and aggregator or producer-organisation lot data. Without consented operational data, public PDFs alone are unlikely to beat existing buyer networks. See [product/data-requirements.md](product/data-requirements.md) and [data/schema.md](data/schema.md).

## African / Ghanaian context

Technical implications specific to this setting, not slogans:

- **Fragmented supply:** many small northern farms and trader networks; formal exchange covers almost none of the crop.
- **Local data:** MoFA, trade, and attaché series exist but conflict or lag; firm-level intake data are private.
- **Connectivity:** interfaces must tolerate intermittent links and low bandwidth; heavy cloud-only demos are a poor fit until proven otherwise.
- **Data governance:** processor and aggregator records are commercially sensitive; consent and on-prem or private hosting may be required.
- **Language:** English dominates formal procurement; local-language support is an evaluation question, not a default claim.
- **Deployment:** model size, quantisation, and offline or edge-light options matter more than leaderboard scores.

## Current stage

**Idea stage.**

Completed: desk research on the Ghana soybean chain, constraint mapping, a product hypothesis, architecture sketch, data requirements, falsifiable hypotheses, and a validation plan.

Not completed: stakeholder interviews, consented procurement datasets, any model training or evaluation, user testing, commercial validation, or a runnable prototype.

## What has been done

- Ghana soybean value-chain desk research
- Procurement bottleneck and constraint analysis
- Market evidence notes with source labels
- Problem definition separating observation from hypothesis
- Solution concept and user workflows
- System architecture and data schema
- Language-model, retrieval, and forecasting strategy (design only)
- Falsifiable hypotheses, interview plan, and metrics

## What has not been validated

- Processor and aggregator interviews
- Producer-organisation interviews
- Real procurement microdata
- Model performance of any kind
- User adoption
- Willingness to pay
- Production deployment
- That information/visibility is a primary binding constraint

## Validation plan

Test hypotheses H1–H5 with processors, aggregators, and producer organisations using the interview plan in [validation/](validation/). Advance only if discovery shows information and coordination matter enough, and a data path exists. Otherwise pivot or stop.

## Roadmap

1. Stakeholder discovery  
2. Data acquisition (consented)  
3. Data preparation  
4. Initial prototype  
5. Model evaluation  
6. User testing  
7. Iteration  
8. Commercial validation  

## Research

- [Problem definition](research/problem-definition.md)
- [Value chain](research/ghana-soybean-value-chain.md)
- [Procurement bottlenecks](research/procurement-bottlenecks.md)
- [Market evidence](research/market-evidence.md)
- [Sources](research/sources.md)

## License

MIT — see [LICENSE](LICENSE).

---

This repository documents early research and technical exploration. It is not a deployed commercial product.
