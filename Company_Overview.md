# Northbridge Collective, Inc. — Company Overview (fictional)

*Everything in this dataset is synthetic — invented for building and testing finance
automation, not real financial data.*

## Snapshot

- **Structure:** Holding company with three operating subsidiaries, HQ in Austin, TX
- **Stage:** Post-Series B, high growth, ~14 months removed from its last raise
- **FY2025 consolidated revenue:** ~$14.6M across the three operating entities
- **Headcount:** ~96 employees + ~8 1099 contractors across the group
- **Finance team:** One fractional Controller (3 days/week, spread across all four
  entities) and one offshore contract bookkeeper. No CFO, no accounting manager,
  no FP&A function. No dedicated accounting system tying the entities together.

## The entities

| Entity | Business | System of record | Revenue (FY25) | Headcount |
|---|---|---|---|---|
| **Northbridge Collective, Inc.** | Holding company / corporate | Excel workbook | n/a (G&A only) | 5 |
| **Northbridge Software, Inc.** | B2B SaaS — "BuildFlow" project management software for construction & trades companies | QuickBooks Online + Stripe | ~$5.1M | 45 |
| **Verve Supply Co.** | DTC + wholesale premium kitchenware brand | Xero + Shopify/Amazon/PayPal | ~$4.8M | 26 |
| **Northbridge Advisory Group, LLC** | Ops/supply-chain consulting for mid-market manufacturers | No software — Excel only | ~$4.7M | 20 + 8 contractors |

## People

- **Marcus Doyle** — CEO
- **Priya Natarajan** — Controller (fractional, 3 days/week, shared across all four
  entities — this is the entire "finance function")
- **Jenna Ruiz** — Staff Accountant / Bookkeeper (offshore contractor, does most of
  the day-to-day data entry across all four books)
- **Tom Alvarez** — HR & Ops Manager
- **Chloe Park** — Executive Assistant

## Why this company needs a finance upgrade

Northbridge Collective raised a Series B on the strength of its growth, not its
back office. Each subsidiary grew up independently — one is an acquired-then-
integrated SaaS company, one is a scrappy DTC brand, one is a services firm that
never adopted accounting software at all — and nobody has ever unified them. The
result, deliberately reproduced in this dataset:

1. **No data warehouse or consolidation tool.** Four different systems (QBO,
   Xero, Excel, Excel) feed one manually-rebuilt Excel workbook every month-end.
2. **No shared chart of accounts.** The same kind of expense is coded to
   different, inconsistently-named accounts depending on which entity and which
   month you're looking at.
3. **Manual, undocumented journal entries everywhere.** Plugs, reclasses, and
   "per Sarah"-style memos with no attached support.
4. **Reconciliation gaps across the board.** AR subledgers, deferred revenue,
   inventory, intercompany balances, and bank accounts that don't tie to the GL.
5. **No documented policies.** See `05_Policies_and_Controls/` — there isn't a
   close checklist, a revenue recognition policy, a capitalization policy, an
   expense policy, or an approval matrix anywhere in the company.

See `DATA_DICTIONARY_AND_KNOWN_ISSUES.md` at the root of this folder for a
file-by-file map of what's in this dataset and exactly what's broken in each
file — that list is meant to double as a backlog for automation initiatives.
