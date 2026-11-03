# Architecture — How the four repositories combine

This document explains the combination plan for the `cabinet-division-bangladesh-before-all` repository: why these four source repositories were chosen, what role each plays, how the data flows between them, and how the whole is greater than the sum of its parts.

## The combination logic

A Cabinet-level reform initiative needs four functions that no single source repository delivered on its own. The combination maps each function to exactly one source repository:

| Function needed | Source repository | Where it lives in the combined repo |
|---|---|---|
| Strategic communications (read-only reform portfolio) | `fertilizer` | `reference-repos/fertilizer/` (9 published documents) |
| Ministerial decision artefact | `fertilizer-reform` | `reference-repos/fertilizer-reform/` (single decision page) |
| Formal project proposal + briefing | `fertilizer-nationalism` | `reference-repos/fertilizer-nationalism/` (briefing + DPP); distilled into `docs/proposal/` |
| Deployable digital governance stack | `e-bill-system` | `reference-repos/e-bill-system/` (Next.js + Prisma + PostgreSQL) |
| Public-facing portal surfacing all of the above | (new) | `index.html` at repo root |
| Formal record for the Cabinet | (new) | `docs/proposal/Cabinet_Division_KIFGP_Proposal.docx` and `.pdf` |

The two new artefacts (the portal `index.html` and the formal proposal) are derived from and reference the four source repositories. Nothing in the source repositories is modified; they are vendored verbatim under `reference-repos/`.

## Why each repository was included

### `fertilizer-nationalism` — the proposal source

This is the flagship. It contains:
- **`index.html`** — the interactive KIFGP landing page (the briefing for the Ministry of Agriculture, September 2026), presenting the four-layer architecture, the seven-signature action plan, and the budget build-up.
- **`dpp.html`** — the full IMED-format Development Project Proforma: Part A (Project Summary), Part B (Project Details, sections 1–25), and Annexures A–H (district profile, char geography, cropping patterns, PARTNER evidence, GPMS alignment, technology pipeline, unit-rate build-up, manifesto alignment matrix).
- **`sbar-age-bangladesh.html`** — a self-contained Bengali poster rendering the slogan সবার আগে বাংলাদেশ.
- **`social/`** — social-preview image gallery.

This is the primary source from which the formal Cabinet proposal (`docs/proposal/Cabinet_Division_KIFGP_Proposal.docx`) is derived. The proposal restructures the DPP's 25 IMED sections into 13 chapters + 6 annexures suitable for Cabinet-level review, preserving every financial figure, beneficiary count, component cost, risk and indicator.

### `fertilizer` — the strategic communications portfolio

A static, GitHub-Pages-hosted reform portfolio site with an inbox-driven site builder (drop a `.pdf` or `.html` into `content/inbox/`, push, and GitHub Actions builds `site/` and deploys it). It publishes 9 documents under `https://moniruzjaman.github.io/fertilizer/<slug>/`:

1. `briefing` — Comprehensive Strategic Report on Fertilizer Distribution Reform
2. `dashboard` — Burden to Bloom interactive dashboard
3. `editorial` — From Abundant Supply to Every Farmer's Hands
4. `fertilizer-decision-memo` — Minister's Decision Memo
5. `minister-email` — The Path to Bloom ministerial action plan
6. `soil-12-parameter` — Soil testing reference
7. `fertilizer-management-path-to-bloom-report` — Full ministerial report
8. `from-fertilizer-security-to-farming-security-validate` — Strategic paper
9. `sar-sarvabhaumer-gobhire-1` — Supporting background document

This is the **strategic communications layer**: the published record of analysis and briefing that supports the reform case. The combined portal's `#portfolio` section catalogues these.

### `fertilizer-reform` — the decision artefact

A single self-contained HTML page (`index.html`, no build step) presenting the Distribution Reform Package to the Minister: the biometric PoS mandate within 90 days, divisional pilots, and subsidy-targeting reform. This is the **ministerial decision artefact** — a one-page "for decision" memo in visual form.

### `e-bill-system` — the operational digital governance stack

A Next.js 16 + Prisma + PostgreSQL application. Its Prisma schema (`prisma/schema.prisma`) is already purpose-built for fertilizer subsidy governance — this is the key insight that makes the combination powerful. The schema contains:

| Model | Purpose | Reform mapping |
|---|---|---|
| `User` | Beneficiary registry with `nationalIdHash`, `kycStatus`, `verificationLevel`, `role` (FARMER/DEALER/ADMIN), `landTitleId`, `cooperativeCertId` | Krishak Card beneficiary master linked to NID |
| `Dealer` | Licensed dealer registry with `licenseNumber`, `lat`/`long`/`serviceRadius` geofencing, `isVerified` | Last-mile integrity + 2026 Dealer Policy enforcement |
| `Fertilizer` | Product master with `FertilizerType`, composition (N-P-K), `pricePerUnit`, `subsidyRate` (%), `maxPerFarmerPerSeason` | Subsidy math + per-season entitlement caps |
| `Transaction` | Subsidy ledger with farmer↔dealer, `transactionHash` (SHA-256 for blockchain), `lat`/`long`/`locationVerified` (geofencing), `subsidyAmount`/`farmerPayment`/`totalAmount`, `blockchainRecorded`, `qrCodeReference`, `TransactionStatus` | The Central Digital Ledger with QR receipts + geofence check |
| `TransactionItem` | Per-line quantity, unitPrice, subsidyRate, totalPrice | Line-item integrity |
| `SoilHealthCard` | N/P/K/pH/organicMatter, `recommendedFertilizers` JSON, district/upazila/union | Soil-test-based recommendation engine (12-parameter card) |
| `InventoryItem` | Dealer↔fertilizer quantity, lastRestocked | Stock visibility |
| `AuditLog` | action, entityType, entityId, userId, oldValues/newValues JSON, ipAddress | Cabinet-grade accountability trail |
| `Customer` / `Bill` / `BillItem` | Generic invoice/billing (the active `/e-bill` UI) | Dealer's commercial invoice; `Bill.blockchainHash` mirrors `Transaction.transactionHash` |

The critical point: **the integrity layer the proposal mandates already exists as working code.** The reform's "Central Digital Ledger with permissioned blockchain" corresponds to `Transaction.transactionHash` and `blockchainRecorded`; the "public dashboard" corresponds to the existing `/api/dashboard` route; the "automated leakage alerts" correspond to the `AuditLog` anomaly layer; the "QR-code receipt" corresponds to `qrCodeReference`. This is why the project can credibly target 95% PoS-authenticated sales by Year 3 — the integrity layer is not on the critical path of new development.

## Data flow

```
                    ┌─────────────────────────────────────────────────────┐
                    │            CABINET DIVISION MANDATE                 │
                    │  (convenes MoA, Finance, Planning, IMED, ICT, LGD)  │
                    └───────────────────────────┬─────────────────────────┘
                                                │
              ┌─────────────────────────────────┼─────────────────────────────────┐
              │                                 │                                 │
              ▼                                 ▼                                 ▼
   ┌────────────────────┐         ┌─────────────────────────┐         ┌──────────────────────┐
   │  PUBLIC PORTAL     │         │  FORMAL PROPOSAL         │         │  REFORM PORTFOLIO     │
   │  index.html        │         │  docs/proposal/*.docx    │         │  reference-repos/     │
   │  (GitHub Pages)    │◄────────┤  docs/proposal/*.pdf     │────────►│  fertilizer/          │
   │  surfaces all 4    │         │  19 pages · 13 chapters  │         │  fertilizer-reform/   │
   └─────────┬──────────┘         │  6 annexures · 11 tables │         │  fertilizer-          │
             │                    └───────────┬─────────────┘         │  nationalism/         │
             │                                │                        └──────────────────────┘
             │                    derived from │
             │                                ▼
             │                    ┌─────────────────────────┐
             │                    │  fertilizer-nationalism │
             │                    │  (KIFGP briefing + DPP)│
             │                    └───────────┬─────────────┘
             │                                │  references
             │                                ▼
             ▼                    ┌─────────────────────────────────────┐
   ┌────────────────────┐         │  OPERATIONAL DIGITAL GOVERNANCE STACK│
   │  e-bill-system     │◄────────┤  reference-repos/e-bill-system/      │
   │  Prisma schema:    │         │  Next.js 16 + Prisma + PostgreSQL    │
   │  User, Dealer,     │         │  Models already map 1:1 to the       │
   │  Fertilizer,       │         │  reform's integrity layer           │
   │  Transaction,      │         └─────────────────────────────────────┘
   │  SoilHealthCard,  │
   │  AuditLog         │
   └────────────────────┘
```

The portal and proposal are the **derived artefacts** (the public face and the formal record). The four source repositories are the **inputs** (communications, decision, briefing/DPP, operational stack). The vendoring under `reference-repos/` preserves provenance; the new artefacts make the whole Cabinet-ready.

## What was added vs. preserved

| Added (new artefacts in the combined repo) | Preserved (vendored verbatim under `reference-repos/`) |
|---|---|
| `index.html` — the public portal | `fertilizer/` — full site-builder pipeline, 9 content pages, 26 tests |
| `docs/proposal/Cabinet_Division_KIFGP_Proposal.docx` — formal proposal | `fertilizer-reform/` — decision page HTML + assets |
| `docs/proposal/Cabinet_Division_KIFGP_Proposal.pdf` — PDF render | `fertilizer-nationalism/` — briefing, DPP, social assets |
| `docs/proposal/PROJECT_PROPOSAL.md` — markdown summary | `e-bill-system/` — full Next.js app, Prisma schema, API routes |
| `docs/architecture/ARCHITECTURE.md` — this document | |
| `docs/architecture/REFORM_PORTFOLIO.md` — document catalog | |
| `README.md` — repo overview | |
| `.github/workflows/deploy.yml` — GitHub Pages workflow | |
| `.gitignore`, `LICENSE` | |

## Deployment topology

The combined repo is designed for a single GitHub Pages deployment:

- **Portal** (`index.html`) — served at the repo root, fully self-contained.
- **Proposal** (`docs/proposal/*.pdf`, `*.docx`) — committed binary files, directly downloadable from the portal's `#proposal` section.
- **Reference repos** (`reference-repos/`) — committed source, browsable on GitHub and linkable from the portal.
- **GitHub Actions** (`.github/workflows/deploy.yml`) — uploads the repo root as the Pages artifact; deploys to the `github-pages` environment on every push to `main`.

For the operational e-bill system (which needs Node + PostgreSQL), deployment is separate (Vercel or equivalent) and out of scope for the Pages deployment. The portal links to the schema and documentation; production deployment of the subsidy ledger is a downstream activity gated by Cabinet approval of the proposal.
