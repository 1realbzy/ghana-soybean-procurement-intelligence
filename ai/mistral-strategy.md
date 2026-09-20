# Mistral strategy (PROPOSED)

## Role of Mistral open-weight models

| Task | Use Mistral? | Why |
|------|--------------|-----|
| Natural-language query understanding | Yes | Flexible intent parsing |
| RAG answers with citations | Yes | Grounded synthesis over docs/tables |
| Requirement extraction from text | Yes | Semi-structured intake |
| Multilingual prompts (e.g. English + local languages) | Conditional | Only if evaluation passes |
| Forecasting tonnage/price | **No** | Numerical calibration needed |
| Match ranking | **No (primary)** | Use interpretable scorers; LLM may explain |
| Inventing missing statistics | **Never** | Hallucination risk |

## Why open weights

- Deployable under local control (sovereignty narrative aligned with African accelerator goals).  
- Cost/latency tuning on modest GPUs.  
- Auditability of prompts, retrieval, and refusal behaviour.

## What is not claimed

- That any Mistral model is already fine-tuned on Ghana soy data.  
- That multilingual African-language performance is proven for this domain.  
- That Mistral alone solves forecasting.

## Model selection (to be evaluated, not pre-announced as final)

Evaluate instruction-tuned open weights appropriate to licence and hardware (e.g. small/medium Mistral family checkpoints current at prototype time). Selection criterion: grounded-answer accuracy and latency on a Ghana soy eval set—not marketing names.
