# Forecasting and matching (PROPOSED — classical ML)

## Forecasting

| Target | Candidate methods | Features (examples) | Success metric |
|--------|-------------------|---------------------|----------------|
| District availability | baselines, gradient boosting, simple hierarchical models | history, rainfall, area, prices | MAE / MAPE on held-out seasons |
| Price indicators | time-series baselines | local quotes, FX, import prices | MAE |
| Processor intake demand | exponential smoothing / regression | historical crush, seasonality | MAE |

LLMs may **narrate** forecast outputs; they do not replace the regressor.

## Matching

Score processor requirements against lot/aggregator records:

`score = w1*quality_fit + w2*quantity_fit + w3*time_fit + w4*logistics + w5*reliability`

Weights set by validation with procurement officers—not guessed as optimal here.

## Status

No trained models or reported accuracies in this repository.
