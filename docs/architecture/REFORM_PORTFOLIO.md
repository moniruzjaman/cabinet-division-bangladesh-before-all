# Reform Portfolio — Document Catalog

This catalogues the published documents across the three communication- and decision-focused source repositories. The operational stack (`e-bill-system`) is documented separately in [`ARCHITECTURE.md`](ARCHITECTURE.md).

## 1. `fertilizer` — Strategic reform portfolio (9 published documents)

A static GitHub Pages site with an inbox-driven site builder. Drop a `.pdf` or `.html` into `content/inbox/`, push, and GitHub Actions builds `site/` and deploys it. Each page gets a 1200×630 social preview and a PDF download where applicable.

Base URL (original deployment): `https://moniruzjaman.github.io/fertilizer/`

| # | Document | Slug | Type | Source file |
|---|---|---|---|---|
| 1 | Comprehensive Strategic Report — Fertilizer Distribution Reform | `briefing` | rich-html | `content/inbox/briefing.html` |
| 2 | Fertilizer Management — Burden to Bloom (interactive dashboard) | `dashboard` | rich-html | `content/inbox/dashboard.html` |
| 3 | From Abundant Supply to Every Farmer's Hands (op-ed) | `editorial` | rich-html | `content/inbox/editorial.html` |
| 4 | Fertilizer Reform — Minister's Decision Memo | `fertilizer-decision-memo` | rich-html | `content/inbox/fertilizer-decision-memo.html` |
| 5 | The Path to Bloom — Ministerial Action Plan | `minister-email` | rich-html | `content/inbox/minister-email.html` |
| 6 | Soil Testing — 12-Parameter Report | `soil-12-parameter` | pdf | `content/inbox/soil-12-parameter.pdf` |
| 7 | Fertilizer Management: The Path to Bloom — Ministerial Report | `fertilizer-management-path-to-bloom-report` | pdf | `content/inbox/Fertilizer_Management_Path_to_Bloom_Report.pdf` |
| 8 | From Fertilizer Security to Farming Security | `from-fertilizer-security-to-farming-security-validate` | pdf | `content/inbox/From_Fertilizer_Security_to_Farming_Security-validate.pdf` |
| 9 | Sar-Sarvabhaumer-Gobhire (শর-সর্বভৌমের-গভীরে) | `sar-sarvabhaumer-gobhire-1` | pdf | `content/inbox/Sar-Sarvabhaumer-Gobhire-1.pdf` |

**Legacy redirect:** `fertilizer-distribution-reform-report-ministerial-briefing/` → `briefing/`.

**Build pipeline** (`tools/site-builder/`): config → scan inbox → collect pages (two-pass for slug reservation) → classify (pdf / rich-html / fragment) → emit site (PDF.js reader for PDFs, head-injected SEO/nav for rich-html, wrapped template for fragments) → OG cards via sharp → `index.html` catalog, `404.html`, `sitemap.xml`, `robots.txt`, redirect stubs. 26 tests.

## 2. `fertilizer-reform` — Ministerial decision artefact

A single self-contained HTML page presenting the Distribution Reform Package to the Minister for decision. No build step, no CDN.

| File | Purpose |
|---|---|
| `index.html` | The Distribution Reform Package decision page (biometric PoS mandate within 90 days, divisional pilots, subsidy-targeting reform) |
| `decision.html` | Decision-detail companion page |
| `favicon.png` | Brand favicon |

This is the **ministerial "for decision" artefact** — a one-page visual memo.

## 3. `fertilizer-nationalism` — Flagship KIFGP briefing + DPP

The flagship interactive landing page for the Ministry of Agriculture briefing (September 2026), plus the full IMED-format Development Project Proforma.

| File | Purpose |
|---|---|
| `index.html` | KIFGP interactive briefing — four-layer architecture, seven-signature action plan, budget build-up, the "Bangladesh Before All" framing |
| `dpp.html` | Full IMED-format Development Project Proforma — Part A (Project Summary), Part B (Project Details, 25 sections), Annexures A–H |
| `sbar-age-bangladesh.html` | Bengali slogan poster: সবার আগে বাংলাদেশ |
| `og-image.png` | 1200×630 social preview |
| `twitter-card.png` | 1200×600 Twitter card |
| `social/index.html` | Social-preview image gallery (og, twitter, square, pinterest, story) |
| `.github/workflows/deploy.yml` | GitHub Pages deploy workflow (uploads repo root) |

**DPP structure** (the source for the formal Cabinet proposal in `docs/proposal/`):

- **Part A — Project Summary:** project title; sponsoring ministry/division/implementing agency; location (Kurigram: 9 upazilas, 73 unions, 3 paurashavas, 219 blocks, 382 chars, AEZs 2/3/7/8/9/22, 107 outlets); duration (36 months, two gates); estimated cost & financing (Tk 3,949.6 lakh, 60/25/10/5 mix); 6 objectives; expected outputs & outcomes (10-row table); alignment with 8 national frameworks; priority justification.
- **Part B — Project Details (sections 1–25):** background & rationale; problem & needs analysis (5 categories); climate change & disaster risk screening; environmental & social safeguards, gender & inclusion; target group & beneficiaries; components & activities (C1–C12); implementation arrangement; procurement plan; financial management, disbursement & gates; ADP phasing; logical framework & MEL results framework; economic & financial analysis; sustainability & exit strategy; risk register (8 risks); monitoring, evaluation, audit & reporting; certification & submission.
- **Annexures A–H:** district profile; char geography by upazila; principal cropping patterns; PARTNER evidence base (2023-26); GPMS 2026-27 alignment; technology pipeline; unit-rate build-up (15 rows); manifesto alignment matrix (Korbo Kaj, Gorbo Desh).

## How the portfolio maps to the Cabinet proposal

The formal Cabinet proposal (`docs/proposal/Cabinet_Division_KIFGP_Proposal.docx`) is **derived from** `fertilizer-nationalism/dpp.html`, restructuring its 25 IMED sections into 13 chapters + 6 annexures for Cabinet-level review, while preserving every financial figure, beneficiary count, component cost, risk and indicator. The supporting reform portfolio (the 9 documents in `fertilizer/` and the decision page in `fertilizer-reform/`) provides the strategic-communications and ministerial-decision context that surrounds the formal proposal.
