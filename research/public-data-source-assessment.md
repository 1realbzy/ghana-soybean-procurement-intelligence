# Public data source assessment

**Project stage:** Idea  
**Assessment date:** 2026-09-23 (UTC)  
**Method:** Live HTTP GET (and limited API) checks from a research environment. Numbers below are only those confirmed in downloaded files or API responses on that date. Unreachable sources are labelled as such.  
**Evidence labels:** FACT (verified retrieve) · COMPANY CLAIM · SECONDARY EVIDENCE · ANALYST INTERPRETATION · ASSUMPTION · INSUFFICIENT EVIDENCE  

This note inventories **public** data that could later support desk research or a thin exploratory layer. It does **not** claim a working product, proprietary feeds, partner agreements, or validated willingness to share operational data.

Access vocabulary (do not collapse):

| Term | Meaning |
|------|---------|
| DISCOVERED | A page, report, or dataset listing exists |
| ACCESSIBLE | The actual file/payload can be retrieved without a paid key in this check |
| MACHINE-READABLE | Programmatic consume (CSV/JSON/API/GeoTIFF/GeoPackage), not only PDF narrative |
| SUFFICIENT | Fields and granularity are *potentially* enough for a named capability — not that the capability is built |

**Data availability ≠ data sufficiency.** A source may be discoverable, downloadable, and machine-readable yet still lack the fields or granularity needed for a named product capability (for example national production context versus available soybean lots; a short price snapshot versus multi-year procurement forecasting; weather covariates versus supplier availability).

Companion note: [public-vs-private-data-boundary.md](public-vs-private-data-boundary.md).

---

## Summary table (2026-09-23)

| Source | DISCOVERED | ACCESSIBLE | MACHINE-READABLE | SUFFICIENT (named use) | Notes |
|--------|------------|------------|------------------|------------------------|-------|
| USDA GAIN GH2023-0006 / GH2024-0006 PDFs | Yes | Yes (GET 200) | Semi (PSD tables in PDF) | Partial — national benchmarks / narrative; not lot matching | HEAD often 405; use GET. Classification: primary official government source (US FAS) |
| UN Comtrade public preview API (HS 1201, 2304) | Yes | Yes (rate-limited; 429 if hammered) | Yes (JSON) | Partial — trade / unit-value sketches | Bulk/async needs subscription |
| World Bank WITS HTML | Yes | Yes (HTML UI) | No (no no-login bulk dump verified) | Unverified for CY2023 figure | Older desk CY2023 HS 2304 figure **not re-verified** live |
| FAOSTAT QCL API / bulk ZIP | Yes | **No** at test time (API 521; bulk 403) | Designed yes | No until reachable | Treat as intermittently reachable from this egress |
| OWID FAOSTAT-derived soy production CSV | Yes | Yes | Yes | Proxy only | **Derivative**, not primary FAO |
| MoFA PBB 2024 & 2025 PDFs (mofep.gov.gh) | Yes | Yes | Semi (PDF tables) | Partial — policy / targets context | Targets ≠ realized series |
| MoFA SRID national cropped-area CSV 2019–2023 | Yes | Yes | Yes | Partial — area series / exploratories; not available lots | Soyabean HA by year; ODC-By 1.0 on dataset page |
| MoFA SRID commodity prices CSV | Yes | Yes | Yes | Partial — short 2025 price map; not multi-year forecast | Soya Bean rows; **2025-05-17 to 2025-10-31** only in file tested |
| MoFA Agriculture Facts & Figures 2024 PDF | Yes | Yes | Semi | Partial — district yields exploratory with care | Table 4.17 soy yield by district in extract |
| GCX | Yes | Yes, partially | Yes, for verified last-close snapshot | No — for historical procurement intelligence | See §7; not a stable public API |
| Bank of Ghana FSR 2024 PDF | Yes | Yes | Semi | Partial — annual GCX soy volume/price fact | Primary for GCX soy annual figures cited below |
| GSS StatsBank PxWeb Trade API | Yes | Yes (HS-2) | Yes (CSV/JSON-stat) | Partial — HS chapter 12 aggregate only | HS-10 code list empty in meta tested |
| NASA POWER point API | Yes | Yes | Yes (CSV) | Partial — covariates only | Sample near Tamale |
| CHIRPS monthly GeoTIFF archive | Yes | Yes | Yes | Partial — covariates only | Public-domain style waiver on CHC site |
| GMet WIS2 synop sample | Yes | Yes (sample GET) | Yes (GeoJSON) | Unclear for historical normals | Auth header present; formal request may be needed |
| GADM 4.1 Ghana GeoPackage | Yes | Yes | Yes | Partial — join key; licence limits commercial use | **Non-commercial** without prior permission |
| World Bank Pink Sheet monthly XLSX | Yes | Yes | Yes | Partial — global benchmarks only | Not Ghana domestic |
| ESOKO | Yes (site) | No open historical soy CSV found | No | No (open historical panel) | Commercial / not open in this check |

---

## Source notes (verified locators)

### 1. USDA FAS GAIN — Oilseeds Voluntary Ghana

| Field | Detail |
|-------|--------|
| Classification | **Primary official government source** (United States Department of Agriculture, Foreign Agricultural Service — GAIN attaché report). Not a multilateral organisation. |
| Locators (GET 200) | `…DownloadReportByFileName?fileName=Ghana+Oilseeds+Voluntary+2023_Accra_Ghana_GH2023-0006.pdf`; same pattern for `…2024_…_GH2024-0006.pdf` |
| FACT (text extract) | “processing capacity of about **172,000 MT** per year… actual production… about **72,000 MT** per year”; “all **13** major soybean processors are operating under-capacity” (GH2023-0006 narrative) |
| Content | Oilseed soybean / meal / oil PSD tables (area, production, trade, crush, etc.) plus policy/feed narrative |
| Geography / time | National Ghana; marketing-year estimates/forecasts (parse Official vs Post columns carefully) |
| MACHINE-READABLE | Semi — tables in PDF |
| SUFFICIENT for | National benchmarks and utilisation narrative context. **Not** sufficient for lot-level matching or supplier availability. |

### 2. UN Comtrade — Ghana HS 1201 / HS 2304

| Field | Detail |
|-------|--------|
| Classification | Multilateral/international source |
| Locator tested | `https://comtradeapi.un.org/public/v1/preview/C/A/HS?reporterCode=288&period=2022&cmdCode=2304&flowCode=M&partnerCode=0&…` → HTTP 200 |
| FACT (World, TOTAL MOT, customs C00, 2022 HS 2304 import) | `primaryValue` **50567510.125** USD CIF; `netWgt` **92868090** kg (~**92.87k MT**). Use this aggregate only — do not sum mode/customs breakdown rows. |
| FACT (HS 1201) | Preview returned World import records; bean import value is small relative to meal under the same filter pattern |
| MACHINE-READABLE | Yes — JSON preview (≤500 records; rate limits). Bulk needs premium key |
| Note on older WITS CY2023 figure | A prior desk figure (~US$44.42m HS 2304, CY **2023**, WITS) was **not re-verified** in this assessment. It is a separate observation (different year and retrieval path), not evidence of a contradiction with the 2022 Comtrade row. |

### 3. FAOSTAT / OWID proxy

| Field | Detail |
|-------|--------|
| Classification | Multilateral (FAO); OWID = secondary derivative |
| Live primary | QCL API **521**; bulk ZIP **403** from this egress on 2026-09-23 |
| Proxy | OWID grapher soy production CSV HTTP 200 (Ghana rows present in download) — label as **proxy**, not MoFA/FAO primary |

### 4. MoFA Programme Based Budget (PBB) 2024 & 2025

| Field | Detail |
|-------|--------|
| Classification | Primary official source (budget/performance PDF) |
| Locators | `https://www.mofep.gov.gh/sites/default/files/pbb-estimates/2024/2024-PBB-MOFA.pdf`; `…/2025/2025-PBB-MOFA.pdf` → HTTP 200 |
| Use | Outcome indicators / targets (production, yield, self-sufficiency, export lines). **Not** a continuous statistical time series |
| Conflict retained | MoFA reported production figures can disagree with USDA MY forecasts — do not average (see [market-evidence.md](market-evidence.md)) |

### 5. MoFA SRID open CSVs

| Dataset | Locator / result | MACHINE-READABLE | SUFFICIENT note |
|---------|------------------|------------------|-----------------|
| National cropped area 2019–2023 | `…/national%20cropped%20area%202019%20to%202023.csv` → 200 | Yes | Supports area context / exploratory comparison. Does **not** reveal available lots. Soyabean HA: 112,472 (2019) … **195,042** (2023) in file |
| Commodity prices | `…/Commodity%20prices%20_04.11.25.csv` → 200 | Yes | Supports a short 2025 retail/wholesale map. Does **not** support robust multi-year procurement price forecasting |

Classification: Primary institutional dataset (MoFA SRID). Licence on cropped-area dataset page cited as ODC-By 1.0 in assessment notes.

### 6. MoFA Agriculture in Ghana Facts & Figures 2024

| Field | Detail |
|-------|--------|
| Classification | Primary institutional publication (PDF) |
| Locator | `https://srid.mofa.gov.gh/sites/default/files/2025-12/AGRICULTURE%20IN%20GHANA%20%28Facts%20%26%20Figures%29%202024.pdf` → 200 |
| Content (extract) | District soyabean yields (Table 4.17 in text extract), regional/national appendices |
| MACHINE-READABLE | Semi |

### 7. Ghana Commodity Exchange (GCX)

| Field | Detail |
|-------|--------|
| Classification | Primary institutional market operator (exchange) |
| DISCOVERED | Yes — public market-intelligence page exists |
| ACCESSIBLE | Yes, partially — page reachable; a Firebase `marketdata.json` payload embedded in public site JS was retrievable (HTTP 200) in this check |
| MACHINE-READABLE | Yes, for the verified **last-close** snapshot (small number of soybean-related symbols with closing/high/low/opening-style fields) |
| SUFFICIENT | **No** for historical procurement intelligence — no research-grade historical OHLCV series or lot-level procurement feed was verified |
| Site | `https://www.gcx.com.gh/market_intelligence/` returned a thin SPA shell; data loaded client-side |
| Stability / terms | The Firebase endpoint is an **implementation detail** of the public website, not a documented stable public API; it may change or require auth later. Licensing and commercial reuse conditions were **not** established by this check |

### 8. Bank of Ghana Financial Stability Review 2024

| Field | Detail |
|-------|--------|
| Classification | Primary official source |
| Locator | `https://www.bog.gov.gh/wp-content/uploads/2025/07/2024-Financial-Stability-Review.pdf` → 200 |
| FACT (PDF body; printed page marker **29** in extract) | Soybean GCX volume “surging by 190.1 per cent to **511.65** metric tonnes from **176.39**”; price “to **GH₵8,311.00** per metric tonne” |
| Interpretation | Press roundings to “512 MT” are secondary; prefer **511.65** from BoG PDF |

### 9. Ghana Statistical Service StatsBank (PxWeb)

| Field | Detail |
|-------|--------|
| Classification | Primary institutional dataset |
| API | `https://statsbank.statsghana.gov.gh/api/v1/en/Trade/` → 200 |
| FACT | `trade_detail_hs2.px` returns CSV for HS chapter **12** (oil seeds aggregate). `trade_detail_hs10.px` metadata exposed **empty** HS-10 value list in this check — soy-specific 10-digit not enumerable via that meta response |
| SUFFICIENT | Chapter-12 trade context only — **not** HS 1201/2304 alone |

### 10. Weather / boundaries / global prices

| Source | Class | Access snapshot | Product caution |
|--------|-------|-----------------|-----------------|
| NASA POWER | Multilateral/international | Point CSV 200 (sample northern coords) | Useful covariates; does not reveal supplier availability |
| CHIRPS 2.0 | Research/academic / open archive | Monthly tifs 200 | Zonal stats need district polygons |
| GMet WIS2 | Primary official | Sample GeoJSON 200 | Confirm licence/auth for production pulls |
| GADM 4.1 GHA | Other (third-party boundaries) | gpkg ~15 MB 200; 16 regions / 260 districts verified | **Non-commercial** without prior permission |
| Pink Sheet | Multilateral/international | Monthly XLSX 200 | Global benchmarks ≠ Ghana farmgate |
| ESOKO | Other / commercial | No open historical soy CSV found | INSUFFICIENT EVIDENCE for open use |

---

## What the verified public sources presently support (idea-stage)

**Presently supported (desk / exploratory sketches) by sources verified in this assessment:** national area/production cross-checks; trade and unit-value monitoring (Comtrade HS 1201/2304; GSS HS-12); short-window 2025 domestic price maps (SRID); weather–yield exploratories if PDF district yields are carefully extracted; thin GCX annual pulse (BoG); policy context (PBB).

**Not presently supported by the public sources verified in this assessment** (would require partner/private operational data or another accessible lot-level source): processor intake matching; dense farmgate/grade series; mill demand calendars; logistics basis; supplier reliability; consented lot registries; robust multi-year Ghana domestic price forecasting (SRID history too short in the file tested; GCX snapshot too thin for that use).

A concrete **future exploratory option** (not executed in this repository): compare MoFA SRID soyabean harvested area 2019–2023 to USDA GAIN PSD area estimates — labelled comparison only, not a product feature. No notebook or charts are included here.

---

## Verification caveats

- Access results are point-in-time (2026-09-23 UTC) and egress-dependent.  
- FAOSTAT primary hosts failed in this environment; re-test before design lock.  
- Comtrade anonymous preview is rate-limited.  
- GCX Firebase URL is an implementation detail of the public website, not a stable public API.  
- Do not treat PDF extracts as continuously updated APIs.  
- No stakeholder interviews, prototypes, or model results are claimed here.
