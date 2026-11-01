<!-- Rapider Official App SOW & Specification | App #150: Real Estate Investment Analysis (real-estate-investment-analysis) | Domain: REA -->

# #150 Real Estate Investment Analysis (`real-estate-investment-analysis`) — Scope of Work (SOW)

- **App Number & Name:** `#150` — Real Estate Investment Analysis
- **App Key:** `real-estate-investment-analysis`
- **Rapider Suite / Domain Key:** `REA` (Real Estate, Facilities & Construction Suite)
- **Model Prefix:** `Rea*`
- **Representative Product:** Dealpath (`Dealpath Real Estate Investment Platform`)
- **Top 6 Global Benchmarks:** Dealpath (`P1`), Altus Group ARGUS Intelligence (`P2`), Juniper Square (`P3`), Yardi Investment Suite (`P4`), MRI Investment Modeling (`P5`), SAP S/4HANA Real Estate & Investment Management (`P6`)
- **Companion Combined Feature Set:** [`../combined-features/150-real-estate-investment-analysis-features.md`](../combined-features/150-real-estate-investment-analysis-features.md)

---

## 1. Executive Outcome & Target Audience

**Executive Outcome:**  
`real-estate-investment-analysis` equips Private Equity Real Estate (`PERE`) funds, REITs, Family Offices, Syndicators, Real Estate Developers, and Corporate Acquisitions teams with an institutional operating system spanning initial Offering Memorandum (`OM`) screening to post-acquisition performance tracking. It manages the deal pipeline (`ReaInvestmentDeal`), harvests proprietary sales and lease comparables (`ReaMarketCompRecord`), builds multi-year DCF & rollover pro-formas (`ReaUnderwritingModel`), sizes binding `LTV`/`DSCR`/`Debt-Yield` debt stacks (`ReaDebtTrancheSchedule`), calculates multi-hurdle JV / LP-GP promote waterfalls (`ReaEquityWaterfallModel`), enforces earnest-money due-diligence workstreams (`ReaDueDiligenceChecklist`), records immutable Investment Committee voting ballots (`ReaInvestmentCommitteeMemo`), and executes 1-click onboarding of closed acquisitions directly into `#141` (`property-management`), `#145` (`commercial-lease-administration`), `#142` (`construction-project-administration`), `budgeting` (`FinBudget`), and `acc` (`FinLegalEntity`).

**SME Fast-Path vs. Enterprise Progressive Disclosure:**
- **SME Fast-Path:** Drop in a 24-unit multifamily or industrial warehouse Offering Memorandum, generate a 60-second Back-of-the-Envelope (`BOE`) Tear Sheet (`\$6,800,000.00` price, `6.15%` Going-In Cap, `7.40%` Stabilized Yield-on-Cost), model a 5-year value-add pro-forma with `65% LTV` debt and an `8% Pref + 70/30` LP/GP split, and export a clean IC Memo.
- **Enterprise Depth:** Institutional `ARGUS`-style commercial tenant rollover probability (`Renewal` vs. `Vacate` downtime, `$`/RSF TI, `%` LC), `5x5` 2D Exit-Cap vs. Rent-Growth IRR sensitivity grids, floating `SOFR` forward-curve debt stress tests (`MRI`), 3-hurdle compounded IRR GP catch-up & promote waterfalls (`Juniper Square`), multi-member Investment Committee Home `WorkItem` voting locks (`Dealpath`), and live Post-Acquisition **Actual NOI vs. IC Underwritten Pro-Forma** benchmarking (`Yardi Investment Suite`).

**Target Personas:**
1. **Acquisitions Analyst / Associate:** Screens OMs, builds `Base`/`Downside`/`Upside` `ReaUnderwritingModel`s, curates `ReaMarketCompRecord`s, and manages `ReaDueDiligenceChecklist` rooms.
2. **VP / Director of Acquisitions:** Negotiates LOIs, reviews debt sizing & GP/LP waterfalls, presents `ReaInvestmentCommitteeMemo`s, and triggers closed-deal onboarding.
3. **Investment Committee (`IC`) Member / CIO / Managing Partner:** Audits sensitivity matrices, comps, and DD red flags, and casts binding `APPROVE` / `APPROVE_WITH_CONDITIONS` / `DECLINE` votes via Home `WorkItem`s.
4. **Portfolio / Asset Manager:** Monitors post-closing Actual-vs.-Underwritten NOI variance and evaluates `Hold vs. Refi vs. Sell` scenarios.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### In Scope
- `ReaInvestmentDeal` pipeline, 60-second BOE Tear Sheets, proprietary Sales & Lease `ReaMarketCompRecord` harvesting, LOI/bid-round tracking, structured pass reasons, and `#148` capex estimate links (`REI-001`–`REI-006`).
- Versioned `ReaUnderwritingModel` (`3–15 yr` DCF), commercial rollover probability math (`TI`/`LC`/downtime), multifamily unit-renovation schedules, terminal exit cap reversion, `5x5` 2D sensitivity matrices, and version IRR attribution diffs (`REI-007`–`REI-012`).
- Multi-constraint `ReaDebtTrancheSchedule` (`min(LTV, LTC, DSCR, DebtYield)`), SOFR rate-cap stress tests, multi-tier `ReaEquityWaterfallModel` (`Pref`, `Catch-Up`, `IRR Hurdle Promotes`), Hold/Refi/Sell simulation, and fund concentration checks (`REI-013`–`REI-018`).
- `ReaDueDiligenceChecklist` EMD hard-date tracking, immutable `ReaInvestmentCommitteeMemo` voting ballots, 1-click `OnboardClosedAcquisition` handoff to `#141`/`#145`/`#142`/`budgeting`/`acc`, post-acquisition Actual-vs.-Underwritten tracking, and grounded Dealpath-style AI copilots (`REI-019`–`REI-028`).

### Out of Scope
- Ongoing day-to-day rent collection, security deposits, and maintenance work orders after closing (owned by `#141` `property-management` and `maintenance`).
- Post-closing ASC 842 / IFRS 16 ROU amortization schedules (owned by `#145` `commercial-lease-administration`).
- Detailed 2D/3D construction takeoff quantification (owned by `#148` `construction-cost-estimation`, referenced on value-add/development deals).
- Fund investor KYC/AML wire execution and partnership tax K-1 preparation (GL/payments owned by `acc` and `payments`).

### Suite Ownership & Integration Contract Table

| Domain / App | Owns | Integration Contract with `real-estate-investment-analysis` |
| :--- | :--- | :--- |
| **`real-estate-investment-analysis` (`REA`)** | `ReaInvestmentDeal`, `ReaMarketCompRecord`, `ReaUnderwritingModel`, `ReaDebtTrancheSchedule`, `ReaEquityWaterfallModel`, `ReaDueDiligenceChecklist`, `ReaInvestmentCommitteeMemo` | Governs pre-acquisition screening, DCF/debt/waterfall modeling, DD, IC governance, and post-closing UW benchmark comparison. |
| **`crm` (`CRM` — Built)** | `CrmAccount`, `CrmContact`, `CrmOpportunity` | Supplies sell-side brokerages, sellers, lenders, and LP/JV partner entities. |
| **`construction-cost-estimation` (`#148`) & `construction-admin` (`#142`)** | `ReaCostEstimate`, `ReaConstructionJob` | `#148` supplies ROM/DD capex budgets into `ReaUnderwritingModel`; closed value-add/development deals initialize `ReaConstructionJob` in `#142`. |
| **`property-management` (`#141`) & `commercial-lease-admin` (`#145`)** | `ReaProperty`, `ReaUnit`, `ReaTenancyLease`, `ReaCommercialLease` | Created/seeded upon `OnboardClosedAcquisition`; `#141` streams realized monthly property NOI back for Actual-vs.-Underwritten tracking. |
| **`acc`, `budgeting` & `accpayable` (`FIN` — Built)** | `FinLegalEntity`, `FinBudget`, `FinSupplierBill`, `FinJournalEntry` | Receives Year-1 Underwritten `FinBudget` upon closing, EMD wire vouchers (`accpayable`), and actual GL NOI feeds. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture (12 Pages)

All visible sidebar groups strictly satisfy Rapider's **Minimum 3 Items per Section Rule** (`Pipeline & Comps`: 3 items, `Underwriting & Waterfalls`: 3 items, `Diligence, IC & Portfolio`: 3 items; 9 visible + 3 hidden detail/drawer routes = 12 total pages).

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | `deal-pipeline` | Acquisitions Pipeline & Funnel | `Pipeline & Comps` | `true` | KPI strip (`Active Pipeline \$`, `Deals in Exclusivity`, `Avg Target Levered IRR %`, `YTD Closed \$`), `<rapider-kanban>` (`Screening` -> `Underwriting` -> `LOI` -> `Exclusivity / DD` -> `IC Approved` -> `Closed`), `#activeFilterTagsBar`. |
| 2 | `deals-register` | Deals & BOE Tear Sheets | `Pipeline & Comps` | `true` | `findSWR` `ReaInvestmentDeal` table with clickable Deal Name (`#/deal-detail`), asset class/strategy pills, Going-In Cap, Levered IRR, AI OM-Upload trigger. |
| 3 | `market-comps-library` | Sales & Lease Comps Library | `Pipeline & Comps` | `true` | Searchable `ReaMarketCompRecord` table (`Sales Comps` & `Lease Comps`), submarket/asset-class filters, `\$`/RSF, `\$`/Unit, Cap Rate, 1-click "Attach to Deal". |
| 4 | `underwriting-proforma` | DCF Pro-Forma & Rollover Studio | `Underwriting & Waterfalls` | `true` | Multi-year `ReaUnderwritingModel` cash-flow grid (`Base`, `Downside`, `Upside`), commercial rollover / unit-reno tabs, Exit Cap reversion, and `5x5` 2D IRR Sensitivity Matrix. |
| 5 | `debt-capital-stack` | Debt Sizing & Rate Stress | `Underwriting & Waterfalls` | `true` | `ReaDebtTrancheSchedule` sizer showing binding constraint (`LTV` vs. `DSCR` vs. `Debt Yield`), IO/Amort table, and `SOFR` forward-curve stress chart. |
| 6 | `equity-waterfalls` | JV & GP/LP Equity Waterfalls | `Underwriting & Waterfalls` | `true` | `ReaEquityWaterfallModel` tier builder (`Return of Capital` -> `Pref %` -> `Catch-Up` -> `Promote Hurdles 1/2/3`), annual cash-distribution split table, `LP Net IRR` vs. `GP IRR`. |
| 7 | `due-diligence-room` | Due Diligence & EMD Tracker | `Diligence, IC & Portfolio` | `true` | `<rapider-kanban>` (`Pending Seller` -> `In Review` -> `Red Flag` -> `Cleared`) for `ReaDueDiligenceChecklist` items (ALTA, Phase I ESA, PCA, Leases), `EMD Hard-Date` countdown. |
| 8 | `ic-memos-approvals` | IC Memos & Voting Governance | `Diligence, IC & Portfolio` | `true` | `ReaInvestmentCommitteeMemo` register, locked underwriting snapshot badge, multi-member Home `WorkItem` ballot tally, and 1-click `OnboardClosedAcquisition` launcher. |
| 9 | `actual-vs-underwriting` | Post-Close Actual vs. Underwriting | `Diligence, IC & Portfolio` | `true` | Closed-portfolio benchmark comparing realized `#141`/`acc` NOI & `#142` capex against frozen IC Pro-Forma, plus `Hold vs. Refi vs. Sell` simulator. |
| 10 | `deal-detail` | Investment Deal 360 Tear Sheet | *(Hidden)* | `false` | Deep-link route (`#/deal-detail?id=...`) with `Back` filter restoration, BOE metrics, LOI bid history, attached comps, DD red flags, and `projectChannelMessage` deal war-room. |
| 11 | `underwriting-model-detail` | Locked Pro-Forma & Waterfall Audit | *(Hidden)* | `false` | Deep-link route (`#/underwriting-model-detail?id=...`) displaying full period `Decimal128` DCF rows, `v1 vs vN` IRR attribution bridge, and downloadable CSV schedule. |
| 12 | `deal-comp-ic-drawer` | OM Extract / Comp / IC Drawer | *(Hidden)* | `false` | Sliding drawer (`<rapider-phone-input>` for broker/seller/lender contacts), cited OM PDF preview, `try...catch...finally` button reset, auto-close, and SWR invalidation. |

---

## 4. Canonical Data Models (`Rea*` — 7 Models)

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`ReaInvestmentDeal`** | `dealCode` (`String`, e.g., `DL-2026-104`), `dealName` (`String`), `strategy` (`CORE`, `CORE_PLUS`, `VALUE_ADD`, `OPPORTUNISTIC`, `DEVELOPMENT`), `assetClass` (`MULTIFAMILY`, `INDUSTRIAL`, `OFFICE`, `RETAIL`, `LIFE_SCIENCES`, `MIXED_USE`), `marketSubmarket` (`String`), `unitCount` (`Integer`), `rentableSqFt` (`Decimal128`), `askingPrice` (`Decimal128`), `targetPurchasePrice` (`Decimal128`), `goingInCapRatePct` (`Decimal128`), `emdAmount` (`Decimal128`), `emdHardDate` (`Date`), `passReasonCode` (`String`), `stage` (`SCREENING`, `UNDERWRITING`, `LOI_SUBMITTED`, `EXCLUSIVITY_DD`, `IC_APPROVED`, `CLOSED_ACQUIRED`, `PASSED_DEAD`), `version` (`Integer`) | `brokerAccountRef` -> `CrmAccount`, `brokerContactRef` -> `CrmContact`, `sellerAccountRef` -> `CrmAccount`, `capexEstimateId` -> `ReaCostEstimate` (`#148`, nullable), `onboardedPropertyId` -> `ReaProperty` (`#141`, nullable), `omFileRef` -> Rapider Drive | Transitioning to `PASSED_DEAD` requires non-empty `passReasonCode`; transitioning to `CLOSED_ACQUIRED` requires an `APPROVED` `ReaInvestmentCommitteeMemo`. |
| **`ReaMarketCompRecord`** | `compType` (`SALES_COMP`, `LEASE_COMP`), `propertyName` (`String`), `assetClass` (`String`), `submarket` (`String`), `transactionDate` (`Date`), `rentableSqFt` (`Decimal128`), `unitCount` (`Integer`), `salePrice` (`Decimal128`), `pricePerSqFt` (`Decimal128`), `pricePerUnit` (`Decimal128`), `capRatePct` (`Decimal128`), `startingRentPerSqFt` (`Decimal128`), `tiPerSqFt` (`Decimal128`), `freeRentMonths` (`Decimal128`), `isVerified` (`Boolean`), `version` (`Integer`) | `sourceDealId` -> `ReaInvestmentDeal` (nullable), `attachedDealIds[]` -> `ReaInvestmentDeal` | `pricePerSqFt = salePrice / rentableSqFt` (`Decimal128` when `rentableSqFt > 0`). |
| **`ReaUnderwritingModel`** | `modelName` (`String`), `scenarioType` (`BASE_CASE`, `DOWNSIDE`, `UPSIDE`, `REFI_HOLD_SELL`), `revisionNumber` (`Integer`), `holdPeriodYears` (`Integer`, `1..20`), `purchasePrice` (`Decimal128`), `closingCostsAmount` (`Decimal128`), `totalCapexRenovation` (`Decimal128`), `exitCapRatePct` (`Decimal128`), `sellingCostPct` (`Decimal128`), `discountRatePct` (`Decimal128`), `annualCashFlows` (`Object[]`: `year`, `gpr`, `vacancyLoss`, `egi`, `opex`, `noi`, `tiLcCapex`, `unleveredCf`, `debtService`, `leveredCf`), `netExitProceeds` (`Decimal128`), `unleveredIrrPct` (`Decimal128`), `leveredIrrPct` (`Decimal128`), `equityMultipleX` (`Decimal128`), `npvAmount` (`Decimal128`), `isIcLockedBaseline` (`Boolean`), `version` (`Integer`) | `dealId` -> `ReaInvestmentDeal` | Once `isIcLockedBaseline == true`, model is strictly immutable (`409` on edit—new analyses clone `revisionNumber + 1`); `exitCapRatePct > 0`. |
| **`ReaDebtTrancheSchedule`** | `trancheType` (`SENIOR_LOAN`, `MEZZANINE`, `CONSTRUCTION_DRAW`), `maxLtvPct` (`Decimal128`), `minDscrX` (`Decimal128`), `minDebtYieldPct` (`Decimal128`), `bindingConstraint` (`LTV`, `LTC`, `DSCR`, `DEBT_YIELD`), `sizedLoanAmount` (`Decimal128`), `rateMode` (`FIXED`, `FLOATING_SOFR`), `interestRatePct` (`Decimal128`), `ioMonths` (`Integer`), `amortizationYears` (`Integer`), `annualSchedule` (`Object[]`), `version` (`Integer`) | `underwritingModelId` -> `ReaUnderwritingModel`, `lenderAccountRef` -> `CrmAccount` (nullable) | `sizedLoanAmount == min(loanByLtv, loanByLtc, loanByDscr, loanByDebtYield)` in exact `Decimal128`. |
| **`ReaEquityWaterfallModel`** | `lpEquitySharePct` (`Decimal128`), `gpEquitySharePct` (`Decimal128`), `prefReturnIrrPct` (`Decimal128`), `gpCatchUpPct` (`Decimal128`), `promoteTiers` (`Object[]`: `upToIrrPct`, `lpSplitPct`, `gpSplitPct`), `tierDistributions` (`Object[]`), `lpNetIrrPct` (`Decimal128`), `lpEquityMultipleX` (`Decimal128`), `gpTotalIrrPct` (`Decimal128`), `gpPromoteEarned` (`Decimal128`), `version` (`Integer`) | `underwritingModelId` -> `ReaUnderwritingModel` | `lpEquitySharePct + gpEquitySharePct == 100.0000%`, and every `promoteTiers[i]` satisfies `lpSplitPct + gpSplitPct == 100.0000%`; total LP + GP distributions across all periods MUST equal `100.00%` of total distributable levered cash flow (`\$0.00` leakage). |
| **`ReaDueDiligenceChecklist`** | `category` (`TITLE_SURVEY`, `ENVIRONMENTAL_ESA`, `PHYSICAL_PCA`, `ZONING`, `LEASE_RENT_ROLL_AUDIT`, `TAX_UTILITY_T12`, `INSURANCE`, `DEBT_LEGAL`), `itemTitle` (`String`), `severity` (`BLOCkER`, `MATERIAL_PRICE_ADJUST`, `STANDARD`), `dueDate` (`Date`), `findingSummary` (`String`), `status` (`PENDING`, `IN_REVIEW`, `RED_FLAG`, `CLEARED`, `WAIVED_BY_IC`), `version` (`Integer`) | `dealId` -> `ReaInvestmentDeal`, `ownerEmployeeRef` -> `HrEmployee`, `evidenceFileRefs[]` -> Rapider Drive | Deal cannot execute `OnboardClosedAcquisition` while any `BLOCKER` checklist item remains in `PENDING` or `RED_FLAG` state (unless `WAIVED_BY_IC`). |
| **`ReaInvestmentCommitteeMemo`** | `memoCode` (`String`), `executiveThesis` (`String`), `keyRisksAndMitigants` (`Object[]`), `requiredQuorumVotes` (`Integer`), `votes` (`Object[]`: `voterEmployeeRef`, `decision`, `conditions`, `votedAt`), `status` (`DRAFT`, `VOTING_OPEN`, `APPROVED`, `APPROVED_WITH_CONDITIONS`, `DECLINED`), `decidedAt` (`DateTime`), `version` (`Integer`) | `dealId` -> `ReaInvestmentDeal`, `lockedModelId` -> `ReaUnderwritingModel`, `compIds[]` -> `ReaMarketCompRecord`, `votingWorkItemIds[]` -> Home `WorkItem` | Opening voting (`FreezeUnderwritingForIc`) atomically sets `lockedModel.isIcLockedBaseline = true`; recorded `votes` and `APPROVED` memos are append-only immutable. |

---

## 5. Core End-to-End User Journeys (6 Journeys)

### Journey 1: AI OM Extraction -> 60-Second BOE Tear Sheet -> Comps Harvest
1. Broker emails an Offering Memorandum PDF + Rent Roll for `Sunbelt Logistics Park` (`240,000 RSF` industrial, `\$31,200,000.00` ask). Analyst uploads the PDF via `deal-comp-ic-drawer` and runs **AI OM Extractor**.
2. Analyst verifies cited fields (`\$130.00/RSF`, Year-1 NOI `\$1,965,600.00` -> `6.30%` Going-In Cap) and runs **AI Comps Recommender**, attaching 4 submarket industrial `ReaMarketCompRecord`s (`avg \$142.00/RSF`, `5.95%` cap). Deal advances to `UNDERWRITING`.

### Journey 2: Institutional 10-Year DCF, Binding Debt Sizer & 3-Tier GP/LP Waterfall
1. On `underwriting-proforma`, Analyst models 4 commercial NNN tenant suites (`75%` renewal probability, `6 mo` vacant downtime, `\$8.00/RSF` TI, `4.5%` LC, `3.5%` market rent growth) and links a `\$950,000.00` roof/dock upgrade `ReaCostEstimate` from `#148`, yielding `Unlevered IRR = 9.84%` at a `6.00%` Exit Cap.
2. On `debt-capital-stack`, Analyst enters lender terms (`Max 65% LTV = \$20,280,000`, `Min 1.30x DSCR = \$18,940,000`, `Min 8.75% Debt Yield = \$22,464,000` @ `5.85%` fixed `24m IO`): engine highlights `DSCR` as the binding constraint (`sizedLoanAmount = \$18,940,000.00`), lifting `Levered IRR = 15.12%` (`1.94x EMx`).
3. On `equity-waterfalls`, Analyst models `90% LP / 10% GP` co-invest with an `8.00%` Pref, `80/20` split to `12.00%` IRR, and `65/35` above `12.00%`, outputting `LP Net IRR = 13.88%` and `GP Promote = \$1,412,500.00`.

### Journey 3: Due Diligence Red-Flag Price Retrade & Investment Committee (`IC`) Ballot
1. During exclusivity on `due-diligence-room` (`14 days` to `emdHardDate`), the `PHYSICAL_PCA` report flags an unplanned `\$380,000.00` asphalt truck-court replacement (`RED_FLAG`).
2. VP Acquisitions negotiates a `\$350,000.00` purchase-price reduction (`\$30,850,000.00` in `Model v3`), clears the PCA item, and executes `FreezeUnderwritingForIc`, locking `Model v3` (`isIcLockedBaseline = true`) and dispatching 4 Investment Committee Home `WorkItem` voting ballots.
3. All 4 IC Partners cast `APPROVE` votes (`RecordIcVote`), locking `IC-2026-019` immutably.

### Journey 4: 1-Click Closed-Acquisition Onboarding into `#141`, `#145`, `#142` & `budgeting`
1. Upon wire closing, VP Acquisitions clicks **Onboard Closed Acquisition** on `ic-memos-approvals`.
2. `OnboardClosedAcquisition` links SPV `FinLegalEntity` (`acc`), creates `Sunbelt Logistics Park` (`ReaProperty` + 4 `ReaUnit` bays) in `#141`, seeds the 4 NNN leases into `#145` (`commercial-lease-administration`), initializes the `\$950,000.00` capex `ReaConstructionJob` in `#142`, and writes Year-1 monthly underwritten NOI lines into `budgeting` (`FinBudget`).

### Journey 5: Post-Acquisition Actual NOI vs. IC Underwriting & Refi-vs.-Sell Simulation
1. Six quarters post-closing on `actual-vs-underwriting`, Asset Manager compares realized `#141`/`acc` NOI (`+4.8%` ahead of `IC Model v3`) and runs a `REFI_HOLD_SELL` clone scenario evaluating a Year-3 cash-out refinance vs. Year-5 disposition.

### Journey 6: Click-Through Navigation & Filter State Restoration
1. User filters `deals-register` by `Asset Class: "INDUSTRIAL"` and `Strategy: "VALUE_ADD"`, verifying `#activeFilterTagsBar` chips and `[Clear all]`, clicks `Sunbelt Logistics Park` to open `#/deal-detail?id=...` cleanly, and clicks `Back` to restore filter state.

---

## 6. Consolidated Feature Priorities & Work Packages (`P0`, `P1`, `P2`)

### `P0` Foundation Work Packages (11 Capabilities)
- **WP-P0-1 — Deal Pipeline, BOE Tear Sheets & Proprietary Comps DB (`REI-001`–`REI-003`):** `ReaInvestmentDeal` `<rapider-kanban>`/register and `ReaMarketCompRecord` library (`deal-pipeline`, `deals-register`, `market-comps-library`, `deal-detail`).
- **WP-P0-2 — Institutional DCF, Commercial Rollover, Unit Reno & Reversion (`REI-007`–`REI-010`):** `ReaUnderwritingModel` cash-flow/XIRR/NPV engine (`underwriting-proforma`, `underwriting-model-detail`).
- **WP-P0-3 — Multi-Constraint Debt Sizer & Multi-Tier GP/LP Waterfalls (`REI-013`, `REI-015`):** `ReaDebtTrancheSchedule` (`min(LTV, LTC, DSCR, DebtYield)`) and `ReaEquityWaterfallModel` (`debt-capital-stack`, `equity-waterfalls`).
- **WP-P0-4 — Due Diligence, Immutable IC Ballots & Closed-Deal Onboarding (`REI-019`–`REI-021`):** `ReaDueDiligenceChecklist`, `ReaInvestmentCommitteeMemo` Home `WorkItem` ballots, and `OnboardClosedAcquisition` -> `#141`/`#145`/`#142`/`budgeting`/`acc` (`due-diligence-room`, `ic-memos-approvals`).

### `P1` Scale & Enterprise Work Packages (11 Capabilities)
- **WP-P1-1 — LOI Tracking, Pass Taxonomy, `#148` Capex Link, `5x5` Sensitivity & Version Diff (`REI-004`–`REI-006`, `REI-011`, `REI-012`):** Bid rounds, pass analytics, `#148` ROM capex sync, 2D IRR sensitivity tables, and `v1 vs vN` IRR attribution bridges.
- **WP-P1-2 — SOFR Forward Stress, Hold/Refi/Sell, Mandate Guards, EMD Vouchers & Actual-vs-UW (`REI-014`, `REI-016`, `REI-017`, `REI-022`, `REI-023`):** Floating-rate DSCR stress, Refi/Sell simulator, fund concentration checks, `accpayable` EMD wires, and realized `#141` NOI vs. IC baseline tracking (`actual-vs-underwriting`).

### `P2` Adjacent & Grounded AI Work Packages (6 Capabilities)
- **WP-P2-1 — Lender/Appraiser CSV I/O & Vintage Funnel Scorecard (`REI-018`, `REI-028`):** Standardized cash-flow schedule export/import and vintage underwriting accuracy metrics.
- **WP-P2-2 — Grounded Dealpath-Style Investment AI Copilots (`REI-024`–`REI-027`):** PDF-cited OM/Rent-Roll/T-12 extractor, comps recommender, DD red-flag & `#141` assumption sanity-checker, and conversational pipeline query assistant.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **IC Voting Member / CIO / Partner** | Reviews all deals/models/DD rooms, casts binding `RecordIcVote` decisions via Home `WorkItem`s, authorizes `WAIVED_BY_IC` DD overrides and closed-deal onboarding. | Cannot retroactively alter `isIcLockedBaseline == true` underwriting models or already-cast IC ballot timestamps. |
| **VP / Director of Acquisitions** | Full CRUD on `ReaInvestmentDeal`s, LOIs, `ReaInvestmentCommitteeMemo` drafts, triggers `FreezeUnderwritingForIc` and `OnboardClosedAcquisition`. | Cannot cast IC votes on own sponsored deal if governance policy enforces independent quorum. |
| **Acquisitions Analyst / Associate** | Builds `ReaUnderwritingModel`s, `ReaDebtTrancheSchedule`s, `ReaEquityWaterfallModel`s, curates `ReaMarketCompRecord`s, manages `ReaDueDiligenceChecklist`s. | Cannot unlock IC-frozen models or onboard closed assets into `#141`/`acc`. |
| **External JV Partner / Lender (Scoped Deal Room)** | Views shared Base-Case pro-forma and cleared `ReaDueDiligenceChecklist` documents on a single invited `dealId`. | Strictly isolated to single `dealId`; masked from internal GP promote sensitivity notes, competitor pipeline deals, and internal IC dissent comments! |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### Guarded Domain Commands
Every command requires `{ idempotencyKey, correlationId, expectedVersion }`:
1. `CalculateUnderwritingAndWaterfall({ underwritingModelId })` — Deterministically computes `Decimal128` multi-year NOI, binding debt schedule, Unlevered/Levered IRR & EMx, `5x5` sensitivity matrix, and LP/GP waterfall tiers.
2. `FreezeUnderwritingForIc({ dealId, underwritingModelId, memoPayload, icVoterRefs[] })` — Locks `isIcLockedBaseline = true` and opens Home `WorkItem` ballots for every IC voter.
3. `RecordIcVote({ memoId, voterEmployeeRef, decision, conditions, workItemId })` — Appends immutable signed vote and transitions memo to `APPROVED` / `DECLINED` once quorum completes.
4. `OnboardClosedAcquisition({ dealId, memoId, legalEntityRef })` — Verifies `memo.status IN (APPROVED, APPROVED_WITH_CONDITIONS)` and zero unresolved `BLOCKER` DD items, then provisions `#141` `ReaProperty`/`ReaUnit`, `#145` commercial leases, `#142` capex job, and `budgeting` `FinBudget`.

### Domain Events Published & Consumed (Kafka)
- **Published:** `rea.investment_deal.created`, `rea.investment_deal.passed`, `rea.ic_memo.voting_opened`, `rea.ic_memo.approved`, `rea.acquisition.onboarded`.
- **Consumed:** `rea.cost_estimate.submitted` (from `#148` for development/reno capex), `rea.owner_distribution.posted` & `fin.journal_entry.posted` (from `#141` & `acc` for Actual-vs.-Underwritten NOI feeds).

### `requiredWorkflows` (in `app.manifest.json`)
- `wf-rea-emd-hard-date-countdown`: Escalates urgent Home `WorkItem`s at `T-7d`, `T-3d`, and `T-24h` prior to `emdHardDate` while open `BLOCKER` DD items remain.
- `wf-rea-ic-quorum-orchestrator`: Manages multi-partner IC voting SLAs and locks final committee resolutions.
- `wf-rea-monthly-actual-vs-uw-sync`: Pulls monthly realized `#141`/`acc` property NOI against frozen `isIcLockedBaseline` models.

### Grounded Rapider AI Contract
AI tools (`REI-024`–`REI-027`) cite exact OM PDF pages/tables and `ReaMarketCompRecord` IDs, never expose confidential deals outside user ACLs, and NEVER cast IC votes, wire EMD funds, or onboard legal entities without explicit human authorization.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **MNPI, NDA & Deal-Room Confidentiality (SEC / AIFMD / SOC 2):** Acquisition targets under NDA (especially public-REIT or corporate sale-leaseback deals containing Material Non-Public Information `MNPI`) support Ethical-Wall deal-level ACLs restricting visibility strictly to named deal-team members.
- **Institutional Financial Auditability:** Frozen `isIcLockedBaseline` models, `Decimal128` IRR/waterfall calculations, and signed `ReaInvestmentCommitteeMemo` vote logs are append-only immutable for SEC/LP fiduciary examinations (`10+ years`).
- **Accessibility & Responsive UX:** WCAG 2.2 AA contrast (`#ffffff !important` on primary/danger buttons), wide-table financial keyboard navigation on `1440px`, tablet IC memo reading on `768px`, and `390px` mobile IC `WorkItem` voting & pipeline tear-sheet review.

---

## 10. Deterministic Acceptance Criteria (15 Testable Criteria)

1. **Sidebar Section 3+ Item Compliance:** `Pipeline & Comps` (3 items), `Underwriting & Waterfalls` (3 items), and `Diligence, IC & Portfolio` (3 items) each contain `>= 3` visible pages; `deal-detail`, `underwriting-model-detail`, and `deal-comp-ic-drawer` set `displayOnMenu: false`.
2. **Binding Debt Constraint Invariant (`Decimal128`):** `ReaDebtTrancheSchedule` deterministically sets `sizedLoanAmount == min(loanByLtv, loanByLtc, loanByDscr, loanByDebtYield)` and labels the exact `bindingConstraint`.
3. **Zero-Leakage GP/LP Equity Waterfall Conservation:** Across every period and exit reversion in `ReaEquityWaterfallModel`, `sum(lpDistributions) + sum(gpDistributions) == totalDistributableLeveredCashFlow` to the exact `Decimal128` cent (`\$0.01`), and `lpEquitySharePct + gpEquitySharePct == 100.0000%`.
4. **Immutable IC Baseline Model Lock:** Once `FreezeUnderwritingForIc` sets `isIcLockedBaseline == true`, any direct edit/delete on that `ReaUnderwritingModel` rejects with `409 IC_BASELINE_LOCKED`.
5. **IC Approval & Blocker-DD Gate on Acquisition Onboarding:** `OnboardClosedAcquisition` rejects deterministically (`422 ACQUISITION_GATE_UNMET`) if `ReaInvestmentCommitteeMemo` is not `APPROVED`/`APPROVED_WITH_CONDITIONS` or if any `BLOCKER` `ReaDueDiligenceChecklist` item is unresolved (`PENDING`/`RED_FLAG`).
6. **Structured Pass-Reason Requirement:** Transitioning a `ReaInvestmentDeal` to `PASSED_DEAD` without a `passReasonCode` fails with `422 PASS_REASON_REQUIRED`.
7. **Idempotent Cross-App Acquisition Onboarding:** Running `OnboardClosedAcquisition` creates canonical `#141` `ReaProperty`, `#145` commercial leases (if applicable), `#142` capex job (if applicable), and `budgeting` Year-1 `FinBudget` with zero duplicate records on retry.
8. **Ethical-Wall Deal Isolation:** External JV/Lender or non-team users cannot query MNPI-restricted `ReaInvestmentDeal` records (`403` enforced).
9. **SWR Reads & Active Filter Tags:** Every pipeline/list view uses `findSWR`/`countSWR` with zero manual `isDeleted` `where` filters, filters `item.isDeleted !== true` in memory, and renders `#activeFilterTagsBar` with escaped chips and `[Clear all]`.
10. **Table Actions & Real Click-Through Navigation:** Zero standalone "View" buttons in `Actions`; clicking `dealName` or `memoCode` navigates cleanly to detail routes without `<base href>` 404 diversion, and `Back` restores filter state.
11. **Custom Elements & Drawer Lifecycle:** Uses `<rapider-kanban>` on `deal-pipeline` and `due-diligence-room`, `<rapider-phone-input>` in `deal-comp-ic-drawer`, `finally` button reset, and auto-close on save/cancel.
12. **2D Sensitivity Determinism:** Every cell in the `5x5` Exit-Cap vs. Rent-Growth matrix matches standalone `ReaUnderwritingModel` evaluation for those exact coordinates within `0.01 bps`.
13. **Zero `projectId` Field:** No `Rea*` model defines `projectId`.
14. **Literal Dollar Escaping & Markdown Integrity:** All prose pricing/currency figures render cleanly without unescaped inline math collisions.
15. **Theme & Contrast Validation:** All 12 pages pass deterministic dark/light `validate_theme` checks with `#ffffff !important` on primary/danger buttons and zero `window.alert`/`confirm`/`prompt`.
