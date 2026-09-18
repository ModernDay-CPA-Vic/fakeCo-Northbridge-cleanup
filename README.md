# Messy Books to Clean Books — a finance automation case study (in progress)

> **This is a portfolio project, not a real client engagement.** Northbridge
> Collective, its three subsidiaries, every person, vendor, dollar figure, and
> file in this repo is **synthetic** — generated to look and behave like a real
> mid-market company's books, so the automation work here can be demonstrated
> against something realistic. Nothing here describes an actual company.

**The premise:** Northbridge Collective is a fictional, post-Series B holding
company that grew fast and never invested in its finance function. It's now
three years into operating with no shared systems, no policies, and no way to
produce a clean consolidated financial picture — and that's about to become a
serious problem. This repo documents, step by step, what a finance
transformation project looks like: diagnosing the mess, scoping the fix with
the CFO, building the automation, and handing it off.

**Status:** 🟡 In progress. Section 1 (the diagnostic) is complete. Sections
2–5 will fill in as the actual scoping, build, and handoff work happens —
see the status flags below.

---

## Table of contents

1. [The mess — what's broken and why it matters now](#1-the-mess--whats-broken-and-why-it-matters-now) ✅ complete
2. [Scoping it with the CFO](#2-scoping-it-with-the-cfo) 🟡 in progress
3. [Building the automation](#3-building-the-automation) 🟡 in progress
4. [Results and handoff](#4-results-and-handoff) ⬜ not started
5. [Summary](#5-summary) ⬜ not started

---

## 1. The mess — what's broken and why it matters now

### The company

Northbridge Collective is a holding company with three operating
subsidiaries, ~96 employees + ~8 contractors, and ~$14.6M in consolidated
FY2025 revenue:

| Entity | Business | System of record | FY25 Revenue |
|---|---|---|---|
| Northbridge Software, Inc. | B2B SaaS (construction/trades project management) | QuickBooks Online + Stripe | ~$5.1M |
| Verve Supply Co. | DTC + wholesale kitchenware | Xero + Shopify/Amazon | ~$4.8M |
| Northbridge Advisory Group, LLC | Ops/supply-chain consulting | **No accounting software — raw Excel** | ~$4.7M |
| Northbridge Collective, Inc. | Corporate/holdco | Excel (the "consolidation system") | G&A only |

One fractional Controller (3 days/week, split across all four entities) and
one offshore contract bookkeeper are the entire finance function. No CFO, no
accounting manager, no FP&A.

### Why it matters right now

Northbridge is fielding early acquisition interest, and its board has asked
finance to be "diligence-ready" within two quarters. A buyer's first
diligence request list will ask for a clean trial balance, a documented close
process, and reconciled subledgers across all four entities — none of which
currently exist. That gap, not tidiness for its own sake, is what's driving
this project.

### What's actually wrong

- **No data warehouse or consolidation tool.** Four entities, four
  unconnected systems (two real, two Excel), no shared schema.
- **No shared chart of accounts.** Every entity numbers and names accounts
  differently; the same kind of expense lands in different accounts month to
  month depending on who typed it in.
- **Manual, undocumented journal entries everywhere.** Every entity has a
  log of plug/reclass entries with memos like *"TO ADJUST"* or *"per Sarah"*
  and no attached support.
- **Reconciliation gaps across the board.** AR subledgers, a deferred
  revenue schedule, inventory valuation, work-in-progress, and intercompany
  balances that all fail to tie back to the general ledger — by amounts large
  enough that an acquirer's diligence team would flag every one of them.
- **No documented policies, anywhere.** No close checklist, no revenue
  recognition policy, no capitalization policy, no expense policy, no
  approval matrix, no vendor master.

### The files

The [`data/`](./data) folder holds the actual synthetic books — general
ledger exports, subledgers, payroll registers, bank statements, and the
manual journal entry logs — for all four entities, plus a folder documenting
the complete absence of finance policy. Start with
[`data/DATA_DICTIONARY_AND_KNOWN_ISSUES.md`](./data/DATA_DICTIONARY_AND_KNOWN_ISSUES.md),
which maps every file and lists every specific, reproducible break — that
list is also the backlog for Section 3.

```
data/
├── 01_Corporate_Holdco/              consolidation workbook, intercompany tracker
├── 02_Northbridge_Software_SaaS/     GL, billing, payroll, AR aging, deferred revenue
├── 03_Verve_Supply_Co_Ecommerce/     GL, sales, inventory, AP, bank & card statements
├── 04_Northbridge_Advisory_Services/ GL (Excel only), time & billing, AR, contractor pay
├── 05_Policies_and_Controls/         what's missing, and how decisions actually get made
└── DATA_DICTIONARY_AND_KNOWN_ISSUES.md
```

All GL exports balance (debits = credits, proper double-entry) — the mess is
in categorization, documentation, and reconciliation, the same way it would
be at a real company. Nothing here is "broken" in a way that couldn't have
happened by accident.

---

## 2. Scoping it with the CFO

🟡 **In progress — this section will document:**

- The initial scoping conversation: what the CFO/board actually asked for,
  and how that got translated into a project brief
- Proposed timeline and phasing (discovery → design → build → handoff)
- The tech stack and access requested to do the work (data warehouse
  choice, orchestration/automation tooling, AI/LLM tooling, and why)
- Constraints: budget, existing headcount (Priya + Jenna), what could and
  couldn't change in the interim

*Check back once the scoping work is done — or follow the repo for updates.*

---

## 3. Building the automation

🟡 **In progress — this section will document:**

- The prioritized list of automation initiatives, pulled directly from the
  "Known Issues" backlog in Section 1 (vendor de-duplication, GL
  categorization, subledger-to-GL reconciliation, consolidated reporting,
  intercompany elimination, policy-as-code guardrails)
- For each initiative: the **buy vs. build** decision and why (off-the-shelf
  tools evaluated vs. what got custom-built with AI agents)
- Architecture of what got built

---

## 4. Results and handoff

⬜ **Not started — this section will document:**

- Before/after metrics (close time, number of unreconciled items, manual JE
  volume, etc.)
- The handoff plan: a recorded Loom walkthrough training someone else to
  run the new process, and/or an AI agent built to own parts of it going
  forward — plus what I'd do differently
- What worked, what didn't, and what I'd change if I did this again

---

## 5. Summary

⬜ **Not started.** A short TL;DR of the whole project will go here once
Sections 2–4 are done, for anyone who just wants the headline.

---

## About this project

Built by [Vic](https://github.com/) as a self-directed learning project to
practice scoping and shipping AI-driven finance automation end to end, using
a synthetic company so the messy-books problem, the constraints, and the
before/after are all fully reproducible and shareable. See
[`data/DATA_DICTIONARY_AND_KNOWN_ISSUES.md`](./data/DATA_DICTIONARY_AND_KNOWN_ISSUES.md)
for exactly how the dataset was constructed and what's intentionally broken
in it.
