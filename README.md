# Crown Agents Bank — Economic Digital Twin

A single self-contained `index.html` — no build step, no internet, no dependencies. Double-click it (or run the open command below) and it works full-screen in any browser, including offline in a boardroom.

> **The pitch in one line:** not a dashboard that *shows* the CEO numbers — a **twin he can push on**. He sees his own bank's engine (flows, corridors, correspondents, nostros, clients), pulls a lever, and watches ROE, economic profit and valuation re-price in real time. Then he asks it a question and it answers from the live model — and drafts the analyst note and board narrative for him.

---

## How to open
```powershell
start C:\Users\raina\crown-agents-digital-twin\index.html
```
Press **F11** for full-screen before the pitch.

---

## The 5-minute demo script (for the CEO room)

1. **Open on the Cockpit.** "This is your bank as a living economic map. Every arc is a payment corridor — green creates economic profit, red destroys it. Width is flow, brightness is intensity. £41.9bn moving through 100 currencies, in one picture." Let the arcs animate.
2. **Pull the FX-margin lever** (right rail) up 1bp. "Watch the whole bank re-price — ROE, economic profit, EBITDA, and what you're worth, live." The KPI strip flashes and moves.
3. **Click a red corridor** on the map (e.g. UK→Sierra Leone). "This lane *destroys* value — compliance load and capital outweigh the spread. The twin tells you to reprice or re-route."
4. **Go to Market & Investor.** Toggle **PRIVATE · HELIOS ↔ IF WE IPO'D** top-right. "Here's the reconciliation you've always wanted: the analysts' model of CAB, line by line, against reality — you beat consensus on every line. And what you'd be worth if you listed: fintech margins on a bank multiple."
5. **Hit "Generate equity research note."** "One click. The twin writes the analyst's initiating-coverage note from your live numbers — and a board narrative in your voice."
6. **Open the Action Centre.** Tick "Automate KYC/AML" and "Reprice frontier tail." "Each move is modelled to ROE and shareholder value. Test the combination before you commit, then challenge your people with it."
7. **Type a question** in the command bar: *"Why did ROE move?"* / *"Which corridors destroy value?"* "Ask it anything. It reads the twin and answers — your digital chief of staff."

---

## What's real vs modelled (data provenance)

Built in, and surfaced in-app via **ⓘ Sources & portability** / "what's real vs modelled":

| Layer | Status | Source |
|---|---|---|
| FY25 income £119m (+12%), adj. EBITDA £35m (29.8%), EPS 6.8p, FX/payment volume £41.9bn (+13%), 592 active clients, NII £30.9m, total assets £1.82bn | **Public** | CAB FY2025 results & 2024 annual report |
| 100% Helios ownership, CEO Bhairav Trivedi, EMpowerFX 100 currencies / 450 pairs, frontier-market footprint | **Public** | CAB / Helios disclosures |
| Published analyst consensus split (FX £45.5m / Payments £28.5m / Other £37.3m / OpEx £78.2m) | **Public** | CAB FY25 results page |
| Peer multiples (Wise, Ebury, Western Union, Standard Chartered) | **Public** | Listed-peer filings / market data |
| ROE, cost of equity, economic profit, cost-income, capital & liquidity ratios, valuation multiples | **Derived** | Modelled from the public figures + peer ratios |
| Corridor / client / correspondent / nostro line items, trade-finance & per-transaction detail | **Illustrative** | Realistic placeholders shaped to CAB's known footprint — not public. Swap in the bank's own ledgers and they become real. |

The point for the CEO: **the engine never changes.** Plug in the real ledgers and every illustrative number turns real — the visuals, the economic-profit maths and the recommendations are already there.

---

## Why it's a portable framework (any bank, any business model)

The architecture is deliberately **modular** so the same twin can be re-skinned for any institution. Each domain is a pluggable data module:

```
ENGINE (bank-agnostic, never changes)
  • Economic-profit calc:  EP = Revenue − DirectCost − Liquidity − Compliance − Ops − Capital×CoE
  • Value-chain spine:     Clients → Products → Flows → Network → Settlement → Recipients
  • Scenario engine:       levers + executable actions → live ROE / EP / valuation re-price
  • Twin console:          natural-language read-out from the live model
  • Generators:            analyst note + board narrative
DATA MODULES (swap per institution)
  • CAB:        corridors, currencies, correspondents, nostros, MTO/DFI/central-bank clients
  • Nationwide: mortgage & savings products, funding/payment rails, member segments
  • <any org>:  re-point the modules; the questions and the engine are identical
```

The questions a CEO asks — *where is value created, where does it leak, which actions lift returns, how do the market and I see the business* — are universal. Only the nouns change. An agent can populate a new institution's modules from its filings and ledgers, and the twin reads out its economics the same way.

---

## Architecture notes (for the "how is it built?" questions)
- **One file, zero dependencies.** All charts (flight-control corridor map, correspondent network graph, waterfalls, ROE bridge, donuts, scatter, heatmaps, Lorenz concentration) are hand-rolled SVG — so it runs anywhere, offline, forever.
- **Reactive core.** A single `compute(scenario, appliedActions)` derives every metric and segment economic profit; every lever/action re-runs it and re-renders. `baseSnapshot()` gives live deltas-vs-baseline.
- **Production path.** Replace the `DATA` blocks with feeds from the GL, payments hub, treasury/nostro system, KYC/AML platform and capital model; keep the engine and UI. The illustrative line items are the integration contract.

*Figures are illustrative and not investment advice; the public figures are sourced as above.*
