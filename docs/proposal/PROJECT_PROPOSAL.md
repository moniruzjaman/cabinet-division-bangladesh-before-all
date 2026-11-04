# Project Proposal — Bangladesh Before All

**Kurigram Integrated Fertilizer Governance & Farmer Card Pilot (KIFGP)**

> সবার আগে বাংলাদেশ · Bangladesh Before All

A formal project proposal for the **Cabinet Division, Government of the People's Republic of Bangladesh**, in coordination with the **Ministry of Agriculture**. This markdown file is a summary; the authoritative version is the 19-page formal document:

- **Word:** [`Cabinet_Division_KIFGP_Proposal.docx`](Cabinet_Division_KIFGP_Proposal.docx)
- **PDF:** [`Cabinet_Division_KIFGP_Proposal.pdf`](Cabinet_Division_KIFGP_Proposal.pdf)

---

## Project summary

| | |
|---|---|
| **Title** | Kurigram Integrated Fertilizer Governance & Farmer Card Pilot (KIFGP) |
| **Sponsoring body** | Cabinet Division (convening) · Ministry of Agriculture (implementing) |
| **Implementing agency** | Department of Agricultural Extension (DAE), Kurigram |
| **Co-implementers** | BADC, SRDI, BARI/BRRI, Union Parishads & LGD, ICT Division, a2i |
| **Location** | Kurigram district — 9 upazilas, 73 unions, 3 paurashavas, 219 blocks, 382 chars |
| **Duration** | 36 months · 01 July 2026 – 30 June 2029 |
| **Total cost** | Tk 3,949.6 lakh (≈ Tk 39.50 crore · ≈ US$ 3.21 million) |
| **Financing** | 60% ADP · 25% PARTNER/World Bank · 10% PPP/private · 5% in-kind |
| **Project code** | MoA / DAE / KUR / 2026-27 / 01 (proposed) |
| **ADP cycle** | FY 2026-27 |
| **Classification** | OFFICIAL |

## The problem

Bangladesh spends ~Tk 17,001 crore per year on fertilizer subsidy — close to 80% of public agricultural spending — yet the bottom 40% of farmers receive only ~15% of the benefit (World Bank). The warehouse is full; the farmer's hand is not. Between them stands leakage: unrecorded dealer sales, premiums over MRP (+33% to +100% observed), diversion, and allocation negotiated through dealers rather than tied to land and crop. In Kurigram, 95.2% of surveyed mustard farmers over-apply urea; only 9.2% consult a specialist.

## Objectives

1. Eliminate subsidy leakage via fingerprint-match authentication at every fertilizer sale (PoS + upazila local server), with crop-declaration and land-parcel validation.
2. Complete 100% Farmer Card enrolment of 566,202 farm families (508,493 families + 57,709 sharecroppers), linked to NID and BDS/EDLMS parcels.
3. Replace blanket soil-card targets with a land-based Soil Health Grid: 11,087 composite tests → 436,902 parcel-linked digital Soil Health Cards.
4. Raise nutrient-use efficiency via Modified One-Must-One-Should (certified seed + soil-test-based entitlement; five crop-specific reductions).
5. Secure char agriculture: solar irrigation, extension by water, fair-price collection centres, stress-tolerant seed.
6. Institutionalise real-time and performance audit, open e-GP tendering, union-level single-window service, and independent oversight.

## Solution architecture

Four layers, one grid, one package, one char promise *(updated per FC Signed Guidelines dated 20 September 2026)*:

- **Layer 1 (§4.1) — Identity & Land:** 566,202 families on the Krishak Card, biometric + parcel-linked via UP single-window desks. Mandatory **e-KYC** — NID biometric verification must pass *before* any card is issued. Adopts the FC household (**খানা**) definition: one khana = one Farmer Card. Khana classified by FC land thresholds: **Marginal ≤50 শতাংশ · Small 50–500 · Medium 500–1,500 · Large >1,500**. Field capture via **Kobo Toolbox/ODK**; **four-tier validation workflow: UP → Upazila → District → National**.
- **Layer 2 (§4.2) — Point of Sale:** 116 biometric PoS terminals across 107 outlets + 9 upazila servers + district mirror; offline-first, Bangla voice UI. Every PoS transaction prints a **farmer-facing QR-code receipt** (transaction hash, quantity, MRP vs paid price, subsidy share); every outlet is **GPS geo-tagged** with geofence checks rejecting off-site transactions.
- **Layer 3 (§4.3) — Tracking & Transparency:** Central Digital Ledger (permissioned blockchain) with explicit **backward traceability (import → warehouse → dealer)** and **forward traceability (dealer → application → yield)**, public dashboard, automated leakage alerts, quarterly public reports.
- **Layer 4 — Advisory:** Land-based Soil Health Grid (11,087 tests → 436,902 digital SHCs); SRDI full-profile @ Tk 1,500; USSD/SMS Bangla advisory.
- **Cross-cutting:** Modified One-Must-One-Should (1,314 demos, 56,620 lead farmers ≥50% women, 187 SAAOs retrained) + char promise (107 solar SIPs, 9 speedboats, 9 collection centres, 100,000 saplings, BRRI dhan 111/114).

The proposed journey: Import/BADC → local server + biometric PoS → farmer's hands. Subsidy releases only on a verified sale (India DBT-PoS model). Every kilogram traced on a permissioned blockchain ledger.

## Budget

**Total: Tk 3,949.6 lakh** (subtotal Tk 3,590.5L + 10% contingency Tk 359.1L). Capital share 20.6%; balance recurrent. Annual phasing: Y1 Tk 1,777.3L (45%, Gate 1) · Y2 Tk 1,303.4L (33%, Gate 2) · Y3 Tk 868.9L (22%).

| Component | Tk lakh |
|---|---:|
| C3 Farmer Card enrolment (566,202 × Tk 100) | 566.2 |
| C5 Capacity building (56,620 lead farmers + 187 SAAO + 214 dealers) | 535.3 |
| C8 Char resilience (107 solar SIP + 9 speedboats + 100k saplings) | 524.5 |
| C12 PMU & logistics (14 staff × 36 mo) | 331.0 |
| C4 Soil Health Grid (11,087 tests + 436,902 SHCs) | 341.1 |
| C6 One-Must-One-Should demos (1,314 × Tk 25,000) | 328.5 |
| C9 Collection centres (9 × Tk 25 lakh) | 225.0 |
| C2 Software + 2-yr O&M | 220.0 |
| C11 Governance & audit (incl. 3rd-party performance audit) | 191.0 |
| C10 e-Voucher — crop-specific, land-linked digital instrument redeemable only at verified PoS (MFS gateway) | 131.1 |
| C1 Digital infrastructure (116 PoS + 9+1 servers) | 101.7 |
| C7 Advisory comms (27.2M SMS/USSD) | 95.1 |
| **Subtotal** | **3,590.5** |
| Contingency 10% | 359.1 |
| **TOTAL** | **3,949.6** |

## Returns

Steady-state (Year 4+): **≈ Tk 78.9 crore/yr** — leakage recovery Tk 36.0 Cr + input-cost saving Tk 32.4 Cr + post-harvest loss cut Tk 9.1 Cr + diesel displaced Tk 1.4 Cr. 10-yr NPV @12%: benefits ≈ Tk 260 Cr vs costs ≈ Tk 36 Cr. **BCR ≈ 6–7:1 · EIRR ≈ 35%**. Sensitivity at 50% benefit realisation: BCR ≈ 3:1 (decision-robust). Payback < 2 steady-state years. Per farm family: Tk 697 over 3 years (≈ US$ 5.67) vs documented per-bigha savings of Tk 1,052.35/yr — a 9.4× savings-to-cost ratio.

## Decision gates

- **Gate 1 (end Y1, Jul 2027):** 100% Farmer Card enrolment verified + ≥95% transaction capture at live outlets → releases Y2 tranche.
- **Gate 2 (end Y2, Jun 2028):** leakage-detection alerts operational + ≥50% parcel-SHC linkage + ≥60% PoS sales share → releases Y3 tranche.

## Governance

Five tiers, no parallel bureaucracy: (1) Steering Committee chaired by Secretary MoA; (2) PMU at DAE Kurigram (14 staff, Deputy Director as PD); (3) Union Parishad single-window desks; (4) Oversight Committee (farmers, civil society, UP chairs, experts → quarterly public reports to the Manifesto Implementation Committee); (5) Technical partners (SRDI, BARI/BRRI, BADC, a2i/ICT). Three-layer audit: real-time ledger, annual C&AG, annual independent performance audit (C11, outcome-based). **Funds flow (§7):** ADP release → PMU designated account over **iBAS++** rails; subsidy disbursements route through **NPSB TakaPay** as the interoperable national switch (banks + MFS wallets on one rail), per FC Signed Guidelines dated 20 September 2026.

### Data governance (§10.5 — NEW)

Four-tier data classification: **Public** (aggregate dashboards, transparency reports) · **Internal** (operational MIS, procurement) · **Confidential** (farmer PII, NID hashes, parcel ownership, accounts) · **Restricted** (biometric templates, keys, ledger signing material). **Data Breach Notification Protocol:** containment within **6 hours** → notification to the **PD (Personal Data Protection) authority within 24 hours** → full incident report to **ICT Division/a2i within 72 hours**, remediation report to Steering Committee next quarter.

## The seven signatures

Seven signatures, no new legislation, one budget cycle. Each action unlocks the next:

1. Issue the biometric PoS circular — within 90 days
2. Complete 100% Farmer Card enrolment — within 12 months
3. Link stock allocation to BDS/EDLMS land data — by Boro 2026-27
4. Approve KIFGP at Tk 3,949.6 lakh in ADP FY 2026-27 — in full compliance with the FC Signed Guidelines dated 20 September 2026 (খানা definition, land thresholds, e-KYC; see §4.1, §7).
5. Adopt the land-based Soil Health Grid
6. Launch Modified One-Must-One-Should
7. Sanction the char resilience & market package

## The digital governance stack

The integrity layer is **not on the critical path of new development.** The companion `e-bill-system` repository (vendored at `reference-repos/e-bill-system/`) carries a Prisma data model already purpose-built for fertilizer subsidy governance: `User` (NID hash, **e-KYC status tiers PENDING → VERIFIED → ACTIVE → SUSPENDED** — only ACTIVE users may draw subsidised fertilizer), `Dealer` (geofencing + GPS geo-tagged outlet), `Fertilizer` (subsidy %, season cap), `Transaction` (SHA-256 hash, blockchain flag, geofence; the **QR-code reference generates the farmer-facing scannable receipt printed at every PoS transaction**), `SoilHealthCard` (N/P/K/pH/OM), `AuditLog` (who/what/when/IP). The reform's Central Digital Ledger, public dashboard, leakage alerts and QR receipts all map to fields that already exist in working code.

## Beneficiary targeting — FC land thresholds (Annex B)

| Category | Count | Land threshold (শতাংশ) | Targeting weight |
|---|---:|---|---:|
| Marginal | 182,319 | ≤50 শতাংশ (≤0.20 acre) | 35.85% |
| Small | 206,382 | 50–500 শতাংশ (0.20–2.00 acre) | 40.58% |
| Medium | 45,708 | 500–1,500 শতাংশ (2.00–6.05 acre) | 9.00% |
| Large | 2,493 | >1,500 শতাংশ (>6.05 acre) | 0.49% |

Marginal + small khana (খানা, per FC household definition) together carry 76.4% of targeting weight.

---

_Full detail: see the 19-page formal proposal — [`Cabinet_Division_KIFGP_Proposal.pdf`](Cabinet_Division_KIFGP_Proposal.pdf) or [`Cabinet_Division_KIFGP_Proposal.docx`](Cabinet_Division_KIFGP_Proposal.docx). Source material: `reference-repos/fertilizer-nationalism/` (KIFGP briefing + DPP)._
