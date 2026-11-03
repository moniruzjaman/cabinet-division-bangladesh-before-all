# Bangladesh Before All — Cabinet Division Fertilizer Governance Reform Portal

[![Deploy to GitHub Pages](https://github.com/moniruzjaman/cabinet-division-bangladesh-before-all/actions/workflows/deploy.yml/badge.svg)](https://github.com/moniruzjaman/cabinet-division-bangladesh-before-all/actions/workflows/deploy.yml)
[![Live portal](https://img.shields.io/badge/portal-live-brightgreen)](https://moniruzjaman.github.io/cabinet-division-bangladesh-before-all/)

**সবার আগে বাংলাদেশ · Bangladesh Before All**

A unified, professional-grade repository for the **Cabinet Division, Government of the People's Republic of Bangladesh**, combining four source workstreams on fertilizer distribution reform under one Cabinet-level mandate. It hosts the flagship **Kurigram Integrated Fertilizer Governance & Farmer Card Pilot (KIFGP)** — a Tk 3,949.6 lakh, 36-month initiative that converts Bangladesh's ~Tk 17,001 crore annual fertilizer subsidy from a channel of chronic leakage into a verified, auditable, farmer-facing system.

| | |
|---|---|
| **Sponsoring body** | Cabinet Division, in coordination with the Ministry of Agriculture |
| **Implementing agency** | Department of Agricultural Extension (DAE), Kurigram |
| **Total investment** | Tk 3,949.6 lakh (≈ Tk 39.50 crore · ≈ US$ 3.21 million) |
| **Duration** | 36 months · 01 July 2026 – 30 June 2029 |
| **Project code (proposed)** | MoA / DAE / KUR / 2026-27 / 01 |
| **ADP cycle** | FY 2026-27 |
| **Classification** | OFFICIAL |
| **Live portal** | 🔗 https://moniruzjaman.github.io/cabinet-division-bangladesh-before-all/ |

---

## What this repository is

This is **one combined repository** assembled from four earlier workstreams. Each source repository is preserved verbatim under [`reference-repos/`](reference-repos/) so nothing is lost, and the whole is surfaced through a single professional portal (`index.html`), a formal 19-page project proposal, and structured documentation.

| Source repository | Role in the combined Cabinet portal |
|---|---|
| [`reference-repos/fertilizer/`](reference-repos/fertilizer/) | The Ministry of Agriculture's static reform-portfolio site — 9 published pages (briefing, dashboard, decision memo, editorial, 4 reference PDFs) with an inbox-driven site builder (26 tests). **Strategic communications layer.** |
| [`reference-repos/fertilizer-reform/`](reference-repos/fertilizer-reform/) | A single self-contained HTML decision page presenting the Distribution Reform Package to the Minister. **Decision artefact.** |
| [`reference-repos/fertilizer-nationalism/`](reference-repos/fertilizer-nationalism/) | The flagship interactive KIFGP briefing and the full IMED-format Development Project Proforma (`dpp.html`). **Source of the proposal.** |
| [`reference-repos/e-bill-system/`](reference-repos/e-bill-system/) | A Next.js 16 + Prisma + PostgreSQL application whose data model is already purpose-built for fertilizer subsidy governance (User/Dealer/Fertilizer/Transaction/SoilHealthCard/AuditLog with blockchain hash, geofencing, subsidy %). **Operational digital governance stack.** |

The combination is **smart, not mechanical**: the four repos map cleanly to the four functions a Cabinet-level reform needs — *strategic communications*, *ministerial decision*, *formal project proposal*, and *deployable digital infrastructure*. Each fills a gap the others leave open.

---

## Repository structure

```
cabinet-division-bangladesh-before-all/
├── index.html                          # The public GitHub Pages portal (self-contained)
├── README.md                           # This file
├── LICENSE                             # MIT
├── .gitignore
├── .github/workflows/deploy.yml        # GitHub Pages deploy workflow
│
├── docs/
│   ├── proposal/
│   │   ├── Cabinet_Division_KIFGP_Proposal.docx   # Formal 19-page proposal
│   │   ├── Cabinet_Division_KIFGP_Proposal.pdf    # PDF render of the proposal
│   │   └── PROJECT_PROPOSAL.md                    # Markdown summary of the proposal
│   └── architecture/
│       ├── ARCHITECTURE.md             # How the 4 repos combine (combination plan)
│       └── REFORM_PORTFOLIO.md          # Catalog of the 9 reform-portfolio documents
│
├── reference-repos/                    # The 4 source repositories, vendored verbatim
│   ├── e-bill-system/                  # Operational subsidy ledger (Next.js + Prisma)
│   ├── fertilizer/                     # Static reform-portfolio site + site-builder
│   ├── fertilizer-reform/              # Single-page decision package
│   └── fertilizer-nationalism/         # KIFGP briefing + DPP
│
└── scripts/                            # (empty — generation scripts live in the build env)
```

---

## The KIFGP at a glance

The flagship initiative is the **Kurigram Integrated Fertilizer Governance & Farmer Card Pilot**. Its architecture is **four layers, one grid, one package, one char promise**:

| Layer | What it does | Target |
|---|---|---|
| **1. Identity & Land** | 100% enrolment of 566,202 farm families on the Krishak Card, biometrically linked to NID + BDS/EDLMS parcels | 566,202 families |
| **2. Point of Sale** | 116 biometric PoS terminals across 107 outlets + 9 upazila servers + district mirror; offline-first, Bangla voice UI | 116 PoS · uptime ≥ 98% |
| **3. Tracking & Transparency** | Central Digital Ledger (permissioned blockchain), public dashboard, automated leakage alerts | 95% sales authenticated · leakage < 5% |
| **4. Advisory** | Land-based Soil Health Grid: 11,087 composite tests → 436,902 parcel-linked digital Soil Health Cards | 436,902 SHCs · N reduction −30% |
| **Cross-cutting** | Modified One-Must-One-Should (1,314 demos, 56,620 lead farmers) + char promise (107 solar SIPs, 9 speedboats, 9 collection centres) | — |

**Returns:** steady-state ≈ Tk 78.9 crore/yr; 10-yr NPV @12% benefits ≈ Tk 260 Cr vs costs ≈ Tk 36 Cr; **BCR ≈ 6–7:1 · EIRR ≈ 35%**; sensitivity at 50% benefit realisation still BCR ≈ 3:1.

Full details in the [formal proposal](docs/proposal/Cabinet_Division_KIFGP_Proposal.pdf).

---

## The seven signatures

The proposal resolves to **seven signatures requiring no new legislation and a single budget cycle**. Each action unlocks the next.

1. Issue the biometric PoS circular — within 90 days
2. Complete 100% Farmer Card enrolment — within 12 months
3. Link stock allocation to BDS/EDLMS land data — by Boro 2026-27
4. Approve KIFGP at Tk 3,949.6 lakh in ADP FY 2026-27
5. Adopt the land-based Soil Health Grid
6. Launch Modified One-Must-One-Should
7. Sanction the char resilience & market package

---

## Deployment

The portal is **deployed and live** via GitHub Actions, automatically redeployed on every push to `main`.

- **Live URL:** 🔗 https://moniruzjaman.github.io/cabinet-division-bangladesh-before-all/
- **Build workflow:** [.github/workflows/deploy.yml](.github/workflows/deploy.yml)
- **Run history:** [Actions tab](https://github.com/moniruzjaman/cabinet-division-bangladesh-before-all/actions)

The workflow uploads the repository root (the `index.html` portal, the `docs/` deliverables, and the vendored `reference-repos/`) as the Pages artifact and deploys it. The `index.html` portal is fully self-contained — inline CSS and JS, no build step, no CDN — and the proposal PDF/DOCX committed under `docs/proposal/` are directly downloadable from the portal's "The proposal" section.

**If the workflow is ever disabled or Pages is reset**, the `configure-pages` step has `enablement: true`, so the next run will re-enable Pages in GitHub Actions mode automatically. To redeploy on demand without a code change, use *Actions → "Deploy Cabinet Division Portal to GitHub Pages" → Run workflow*.

---

## Why the combination works

A Cabinet-level reform needs four things that no single source repository delivered on its own:

- **A public face** — the `index.html` portal, written in the visual language of the briefing material (deep green + gold, Bengali accents), surfacing the crisis, the architecture, the budget, the seven signatures, and the formal proposal.
- **A formal record** — the 19-page Cabinet Division project proposal in `.docx` and `.pdf`, structured to IMED format with 13 chapters and 6 annexures, derived from the KIFGP Development Project Proforma.
- **A strategic communications portfolio** — the 9-document reform portfolio (briefings, dashboard, decision memo, editorial, reference PDFs) preserved and catalogued.
- **A deployable digital governance stack** — the e-bill system's Prisma data model, which already models User/Dealer/Fertilizer/Transaction with blockchain hash, geofencing, subsidy % and QR references. The integrity layer the proposal mandates already exists as working code.

See [`docs/architecture/ARCHITECTURE.md`](docs/architecture/ARCHITECTURE.md) for the full combination plan and data-flow mapping.

---

## License

MIT — see [`LICENSE`](LICENSE). The vendored source repositories under `reference-repos/` retain their original licenses (the `fertilizer` and `e-bill-system` repos are MIT; the briefing material is Crown / Government of Bangladesh content made available for the reform's public communications).

---

## Attribution

**Cabinet Division, Government of the People's Republic of Bangladesh**, in coordination with the **Ministry of Agriculture**. Implementing agency: **Department of Agricultural Extension (DAE), Kurigram**. Compiled and structured as a combined professional-grade repository from four source workstreams by Moniruz Jaman.

> সবার আগে বাংলাদেশ — _Walking the path towards nationalism for sovereignty, one verified kilogram, one dignified farmer, one reclaimed taka at a time._
