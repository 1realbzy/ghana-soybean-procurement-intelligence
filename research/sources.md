# Sources

| ID | Source | Year | Used for | Locator | Classification |
|----|--------|------|----------|---------|----------------|
| S1 | USDA FAS GAIN Oilseeds Voluntary Ghana GH2024-0006 | 2024-06-07 | Production, crush narrative, trade, prices, duties, feed share | USDA FAS GAIN report ID GH2024-0006 (PDF GET verified 2026-09-23) | Primary official government source (US) |
| S2 | USDA FAS GAIN Oilseeds GH2023-0006 | 2023 | Crush capacity survey (~13 / ~172k MT installed / ~72k MT actual) | USDA FAS GAIN report ID GH2023-0006 (PDF GET verified 2026-09-23) | Primary official government source (US) |
| S3 | MoFA Programme Based Budget Estimates | 2024; 2025 | Official production indicators; 2022 bean export value; self-sufficiency KPI | `mofep.gov.gh` PBB-MOFA PDFs (GET verified 2026-09-23) | Primary official |
| S4a | UN Comtrade public preview API | 2022 (live pull) | HS 2304 import World TOTAL MOT: ~US$50.57m CIF; ~92.9k MT net weight | `comtradeapi.un.org/public/v1/preview/...` reporter 288, cmd 2304, flow M, period 2022 (HTTP 200 on 2026-09-23) | Multilateral/international |
| S4b | World Bank WITS / Comtrade mirror | 2023 (prior desk) | HS 2304 import value ~US$44.42m — **not re-verified** in 2026-09-23 live check | https://wits.worldbank.org/ | Multilateral/international; prior desk observation only |
| S5 | Bank of Ghana Financial Stability Review 2024 | 2024 (PDF hosted 2025-07 path) | GCX soy **511.65 MT** (2024) vs 176.39 MT; price **GH₵8,311/MT** | `bog.gov.gh/.../2024-Financial-Stability-Review.pdf` (GET verified; figure on printed p.29 in extract) | Primary official |
| S5b | Financial Stability Review 2024 coverage (Citinewsroom) | 2025-08 article | Rounded GCX soy “512 MT” — prefer S5 | citinewsroom.com | Secondary reporting |
| S6 | MoFA PFJ 2.0 via USDA | Policy via S1 | Feed share; aspirational demand path | Via S1 | Secondary (policy via attaché) |
| S7 | Ghana Nuts company materials | desk access | Named crusher identity (claims only) | ghananuts.com | COMPANY CLAIM |
| S8 | MoFA SRID national cropped area CSV | 2019–2023 | Soyabean harvested area (HA) by year | `srid.mofa.gov.gh/.../national cropped area 2019 to 2023.csv` (GET verified) | Primary institutional dataset |
| S9 | MoFA SRID commodity prices CSV | 2025-05 to 2025-10 (file tested) | Short-window soya bean market prices | `srid.mofa.gov.gh/.../Commodity prices _04.11.25.csv` (GET verified) | Primary institutional dataset |
| S10 | MoFA Agriculture in Ghana Facts & Figures 2024 | 2024 | District soy yields; agri structure | `srid.mofa.gov.gh/.../Facts & Figures 2024.pdf` (GET verified) | Primary institutional publication |
| S11 | GSS StatsBank PxWeb Trade | 2021–2025 meta | HS-2 chapter 12 trade aggregates | `statsbank.statsghana.gov.gh` API (HS-2 OK; HS-10 codes not exposed in meta tested) | Primary institutional dataset |

Conflicting production figures (S1 vs S3) are retained without averaging. Prefer **S5 (BoG PDF)** over S5b press for GCX soy volume. Prefer **S4a (Comtrade 2022 live)** when citing a verified meal-import magnitude for calendar 2022. **S4b** (WITS CY2023 ~US$44.42m) remains on file as a prior desk observation that was **not re-verified**; it is a different year and retrieval path from S4a, not evidence of a contradiction with S4a.

Accessibility inventory: [public-data-source-assessment.md](public-data-source-assessment.md). Public vs private boundary: [public-vs-private-data-boundary.md](public-vs-private-data-boundary.md).
