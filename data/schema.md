# Data schema (LOGICAL — PROPOSED)

No production database is deployed. Fields illustrate the minimum structured layer.

## `producer_org`
- org_id, name, district, region, contact_ref, consent_flag

## `aggregator`
- aggregator_id, name, operating_districts[], historical_reliability_score (nullable), consent_flag

## `lot_offer` (consented)
- lot_id, aggregator_id, qty_mt, available_from, available_to, quality_grade, moisture_pct, price_indicative_ghs, delivery_point, status

## `processor_requirement`
- req_id, processor_id, qty_mt, window_start, window_end, quality_spec_id, max_price_ghs, delivery_point

## `quality_spec`
- spec_id, protein_min, oil_min, fm_max, process_route (solvent|expeller|any)

## `market_observation`
- obs_id, date, market_name, commodity (bean|sbm|oil), price_ghs, unit, source_id

## `external_stat`
- stat_id, series_name, geo, period, value, unit, source_id, definition_note

## `document`
- doc_id, title, publisher, published_on, uri, licence, trust_tier

## `model_forecast`
- forecast_id, target, geo, period, value, model_version, mae_backtest, created_at

Provenance columns on all facts: `source_id`, `captured_at`, `evidence_label`.
