# Language model strategy

The language model layer is **model-agnostic**. No vendor is selected in this repository.

## Intended roles

Natural-language interaction; information extraction; document understanding; retrieval-grounded responses; requirement extraction; summarisation; multilingual prompts only if evaluation supports it.

## Not intended roles

Primary calculator for forecasts, match scores, or risk numbers. Those belong to classical statistical or ML methods with measurable error.

## Evaluation criteria (future)

Inference efficiency; model size; context length; multilingual capability; performance on relevant language tasks; quantisation support; hardware requirements; latency; retrieval-grounded generation quality; information extraction accuracy; deployment flexibility; licensing; data governance fit.

## Principle

This is not “an LLM for farmers” or “a chatbot for agriculture.” The core hypothesis is agricultural procurement intelligence. The language model is an interface and reasoning component inside a broader data and decision system.

No fine-tuning, benchmarks, or production inference exist here yet.
