# Solution concept (PROPOSED)

## One-liner

A **procurement intelligence** system that helps Ghanaian soybean processors turn fragmented supply, market, and document information into grounded answers and planning views—using Mistral open-weight models for language/RAG tasks and classical ML for numerical forecasting and matching.

## What it is

| Capability | Status |
|------------|--------|
| Natural-language procurement queries grounded in retrieved data | PROPOSED |
| Structured views of supply nodes (when consented data exist) | PROPOSED |
| Requirement extraction from processor intake forms / emails | PROPOSED |
| Forecasts of regional availability / price indicators | PROPOSED (ML—not LLM) |
| Match suggestions: requirement ↔ aggregator/producer lots | PROPOSED |
| Risk flags (export competition, quality mismatch, logistics) | PROPOSED |

## What it is not

- Not a live marketplace or escrow  
- Not a credit product  
- Not an agronomy advisory app first  
- Not a claim that beans will appear because a dashboard exists  
- Not deployed software

## User value hypothesis

If processors can see *earlier and more reliably* where suitable beans may be secured—quantity, timing, quality tags, indicative prices, logistics—they can plan purchases, negotiate with aggregators, and allocate working capital better than with phone/WhatsApp-only discovery.

**Falsifiable:** see validation hypotheses H1–H5.

## Design principles

1. **Evidence labels in the UI** (KNOWN vs estimate vs missing).  
2. **Numbers from tables/models; prose from LLMs with citations.**  
3. **Consented private data never trained into public weights without agreement.**  
4. **Low-bandwidth modes** (compact text, cached districts, offline packs).  
5. **Local/sovereign deployment options** via open weights.
