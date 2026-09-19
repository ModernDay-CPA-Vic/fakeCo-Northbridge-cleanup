# Data Dictionary & Known Issues

FY2025 (Jan–Dec), consolidated revenue ~$14.6M across three operating
subsidiaries, ~96 employees + ~8 contractors. Every "known issue" below was
injected on purpose (seeded random generation) so it reproduces — this list
doubles as a starting backlog for automation initiatives.

---

## 01_Corporate_Holdco/

| File | What it is |
|---|---|
| `Company_Overview.md` | Background on the company, entities, and people |
| `Corporate_Payroll_Register_2025.csv` | Semi-monthly payroll for the 5-person corporate team |
| `Consolidated_Trial_Balance_MANUAL.xlsx` | The entire "consolidation process" — one tab per entity's trial balance, manually re-typed by the Controller each month, plus a naive unmapped/unreviewed stack and a Known Issues tab |
| `Intercompany_Tracker.xlsx` | Corporate's own view of the intercompany note balance with each subsidiary |
| `Journal_Entries_Manual_2025.xlsx` | Corporate's undocumented plug entries |

**Known issues:**
- No shared chart of accounts across entities — the "Consolidated (unreviewed)" tab is
  literally four trial balances stacked with no account mapping or eliminations.
- Northbridge Software already runs on NetSuite with OneWorld (multi-subsidiary
  consolidation) licensed — but the other three entities were never migrated onto
  it, so this manual Excel workbook exists purely because underused infrastructure
  the company already owns was never finished being rolled out.
- Intercompany interest income booked by Corporate does not match intercompany
  interest expense booked by any of the three subsidiaries (different people,
  different months, nobody reconciles). See `Intercompany_Tracker.xlsx`.
- Northbridge Advisory books its intercompany balance as a receivable ("Due
  from Collective") while Software and Verve book it as a payable ("Due to
  Collective") — opposite sign conventions, never reconciled against each other.
- Prior versions of the consolidation workbook were overwritten each month;
  there's no version history or audit trail.

---

## 02_Northbridge_Software_SaaS/ (NetSuite, single-subsidiary instance, + Stripe)

| File | What it is |
|---|---|
| `GL_Export_NetSuite_Jan-Dec2025.csv` | Full general ledger export in NetSuite's transaction-list shape (Subsidiary, TxnType, DocNum, Account, Department, Debit/Credit) — revenue, COGS, payroll, AP bills, commissions, depreciation, intercompany interest, and manual JEs, 672 lines |
| `Stripe_Billing_Export_2025.csv` | Transaction-level subscription billing for 340 customers across 4 plan tiers |
| `Payroll_Register_ADP_2025.csv` | Semi-monthly payroll for 45 employees across Engineering, Sales & Marketing, Customer Support, G&A |
| `AR_Aging_Subledger.xlsx` | Open invoice aging by customer, with a tie-out tab comparing to the GL AR balance |
| `Deferred_Revenue_Schedule.xlsx` | Manually maintained schedule for annual-prepay customers, with a tie-out tab |
| `Bank_Statement_Chase_Checking.csv` | Reconstructed cash activity plus a handful of uncleared/unrecorded items |
| `Journal_Entries_Manual_2025.xlsx` | Undocumented plug/reclass entries, no attachments |

**Known issues:**
- NetSuite's OneWorld multi-subsidiary consolidation was never turned on for
  the other three entities, so the one real ERP in this company still requires
  a manual re-key into the group consolidation workbook every month.
- The NetSuite Department segment exists and is used on payroll-driving
  accounts, but is missing on ~15% of the transactions that should carry one
  — there's no posting policy enforcing it, so department-level reporting has
  gaps.
- GL revenue is a manually re-keyed monthly summary of the Stripe export, not
  a system integration — it drifts ~0.5–3% from the actual Stripe total every month.
- AR subledger total does not tie to the GL AR balance (a real, if smaller,
  reconciling gap — see the workbook's "Tie-Out (broken)" tab).
- Annual-prepay customers should generate deferred revenue, but most of that
  cash was booked straight to revenue instead — the GL's deferred revenue
  account (2200) is nearly empty while the manually-built schedule shows a
  real remaining balance.
- The same kind of software subscription spend is coded inconsistently
  between account 6400 (Dues & Subscriptions) and 6410 (Computer & Internet
  Expense) — same vendor, different months, different accounts.
- Vendor name inconsistency: "Amazon Web Services" / "AWS" / "aws" all appear
  as separate vendor strings.
- A duplicate expense account (6901 "Misc Expense 2") was created mid-year
  alongside the original 6900 "Misc Expense".
- The bank statement includes a few uncleared items that were never recorded
  in the GL at all.

---

## 03_Verve_Supply_Co_Ecommerce/ (Xero + Shopify/Amazon/Wholesale)

| File | What it is |
|---|---|
| `GL_Export_Xero_Jan-Dec2025.csv` | Full GL export — sales by channel, COGS, payroll, AP bills, depreciation, intercompany, manual JEs, 570 lines. Uses a completely different account-numbering scheme than the SaaS entity's NetSuite instance. |
| `Shopify_Sales_Export_2025.csv` | Order/line-item level sales across Shopify, Amazon, and Wholesale channels, ~23k lines |
| `Payroll_Register_Gusto_2025.csv` | Semi-monthly payroll for 26 employees |
| `Inventory_Valuation_Manual.xlsx` | Manually maintained inventory-on-hand and valuation by SKU, with a tie-out tab |
| `AP_Vendor_Invoices_Log.xlsx` | Vendor bill log, plus a "Vendor Summary (not deduped)" tab showing the same vendors under multiple spellings |
| `Credit_Card_Statement_Amex_2025.csv` | Company card activity, no receipts on file for any charge |
| `Bank_Statement_Mercury_Checking.csv` | Reconstructed cash activity plus unrecorded debit items |
| `Journal_Entries_Manual_2025.xlsx` | Undocumented plug/reclass entries |

**Known issues:**
- COGS is booked monthly as a flat 34%-of-revenue rule of thumb, not tied to
  actual units sold or landed cost — the inventory asset account only ever
  gets credited (never debited for purchases), so it drifts sharply negative
  over the year. This is the single biggest reconciliation gap in the dataset,
  and it's real: nobody ties inventory purchases to the balance sheet.
- Two SKUs show negative on-hand quantity because receiving was never logged.
- The same three vendors (a contract manufacturer, a 3PL, a packaging
  supplier) each appear under 3-4 different name spellings/capitalizations —
  see the "Vendor Summary (not deduped)" tab for the exact list.
- Same chart-of-accounts overlap issue as the SaaS entity: software spend
  split inconsistently between accounts 660 and 661.
- Every Amex charge is coded to an account with no receipt on file.
- Wholesale AR is only ~75-95% collected in the month billed — a real, modest
  aging balance, not a fabricated one.

---

## 04_Northbridge_Advisory_Services/ (no accounting software — Excel only)

| File | What it is |
|---|---|
| `GL_Export_Excel_Only_2025.xlsx` | The entire "general ledger," kept as an Excel tab with loosely-typed account labels (no real chart of accounts), plus a second tab showing a trial balance built with formulas whose ranges never got extended when rows were inserted later in the year — so the "formula" total silently misses recent entries |
| `Time_and_Billing_Log.xlsx` | Consultant hours by client/month, billed vs. unbilled (WIP), with a tie-out tab |
| `AR_Invoices_Sent.xlsx` | Client invoices generated from billed time, with payment status |
| `Contractor_1099_Payments.csv` | Payments to 8 independent contractors |
| `Bank_Statement_BofA_Checking.csv` | Reconstructed cash activity plus unrecorded items |
| `Journal_Entries_Manual_2025.xlsx` | Undocumented plug/reclass entries |

**Known issues:**
- This entity has no accounting software at all — the "GL" is a spreadsheet
  the Controller maintains directly, with all the usual Excel failure modes.
- The trial balance tab's formulas were built against a fixed row range; when
  new entries were inserted later in the year, the range was never extended,
  so the "formula" total quietly excludes recent activity — compare the
  `true_*` columns to the `formula_*_BROKEN` columns on that tab.
- Unbilled revenue (WIP) accrual is skipped in roughly a quarter of months —
  the time & billing log's unbilled total does not match the GL's WIP balance.
- Contractor payments are coded inconsistently between "Contractor Costs" and
  "Contractor Payments - 1099" — same kind of spend, two different accounts.
- Two near-duplicate expense accounts exist ("Software Expense" and "Software
  Expense - Other"; "Misc." and "Misc Expense"), created at different points
  in the year.
- The intercompany balance with Corporate uses the opposite sign convention
  from the other two subsidiaries (see Corporate section above).

---

## 05_Policies_and_Controls/

No accounting or finance policies are documented anywhere in the company.
`README_No_Policies_Exist.md` lists everything that's missing (close
checklist, revenue recognition policy, capitalization policy, expense policy,
approval matrix, vendor master, standardized chart of accounts, NetSuite
segment posting policy, intercompany policy). `Scattered_Notes_and_Tribal_Knowledge.md`
collects a handful of informal emails/Slack messages that function as the
only "policy" that actually exists today.

---

## Cross-cutting patterns worth knowing before you build automation on this

- **No data warehouse — and the one real ERP in the building is underused.**
  Northbridge Software's NetSuite instance has OneWorld multi-subsidiary
  consolidation available and unused; the other three entities were never
  onboarded to it. Extending NetSuite to the group, rather than building a
  separate warehouse from scratch, is worth evaluating as part of any
  automation roadmap.
- **Manual journal entries** appear in every entity's `Journal_Entries_Manual_2025.xlsx`
  with memos like "TO ADJUST", "per Sarah", or "reverse prior entry" and no
  attached support — these are good candidates for an anomaly-detection or
  documentation-enforcement automation.
- **Every "Tie-Out (broken)" tab** in this dataset is a real, computed gap
  between two things that should agree and don't — they're reproducible from
  the underlying data, not hand-typed numbers, so they make good test cases
  for reconciliation automation.
- **Vendor name normalization** is needed in at least three places (AWS/Google/etc.
  at Software, and the manufacturer/3PL/packaging vendors at Verve Supply).
- **Segment/dimension hygiene** (NetSuite Department tagging) is a smaller but
  real gap worth flagging alongside the chart-of-accounts issues.
- **Chart-of-accounts mapping** across all four entities is the single biggest
  prerequisite for any real consolidation or FP&A automation here.
