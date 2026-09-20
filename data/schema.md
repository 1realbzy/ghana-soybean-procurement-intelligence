# Logical data schema

Design sketch only. No database is provisioned.

## Entities

**ProcessorRequirement** — quantity_mt, window_start, window_end, quality_spec_id, delivery_location, max_price (optional), notes.

**SupplyLot** (aggregator / PO) — quantity_mt, location, available_from, quality_attributes, asking_price (optional), reliability_notes, consent_flags.

**ProducerOrgForecast** — org_id, district, expected_mt, harvest_window, confidence, as_of_date.

**PriceObservation** — commodity, location, date, unit, price, source.

**TradeStat** — hs_code, flow, period, quantity, value, source.

**DocumentChunk** — doc_id, text, provenance_url, licence, embedding_ref (future).

**Recommendation** — requirement_id, candidate_refs, score_components, evidence_refs, uncertainty_flags.

## Provenance

Every numeric field should carry source_id and observed_at (or estimated_by_model + method_id). Prefer refusing over inventing missing quantities.
