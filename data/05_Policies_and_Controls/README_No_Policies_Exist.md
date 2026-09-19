# Accounting & Finance Policies — Current State

This folder is intentionally close to empty. As of FY2025, Northbridge Collective
and its subsidiaries have **no documented accounting or finance policies**. That
absence is itself part of the dataset — it's the gap a real finance function
(or an AI-driven automation layer) would need to fill.

## What does not exist, anywhere in the company

- **No close checklist or close calendar.** Month-end close happens whenever
  Priya has bandwidth that month. There's no target close date, no standard
  task list, no sign-off process.
- **No revenue recognition policy.** Compare `Deferred_Revenue_Schedule.xlsx`
  (Northbridge Software) to the GL — annual-prepay cash is mostly booked
  straight to revenue instead of being deferred and recognized ratably, because
  nobody wrote down that it should work the other way.
- **No capitalization policy.** There's no documented threshold for
  capitalizing vs. expensing equipment, software, or development costs, and no
  fixed asset register beyond a rough monthly depreciation plug.
- **No expense / T&E policy.** No spending limits, no receipt requirements, no
  approved-vendor list. See `Credit_Card_Statement_Amex_2025.csv` (Verve Supply
  Co.) — every charge is marked `receipt_on_file = N`.
- **No approval matrix.** There's no documented rule for who can approve a
  bill, sign a contract, or book a manual journal entry. In practice, anyone
  with GL access (Priya or Jenna) enters what they think is right.
- **No vendor master / vendor onboarding process.** The same vendor gets
  entered under three or four different spellings because there's no
  standardized vendor list (see `AP_Vendor_Invoices_Log.xlsx` at Verve Supply
  Co., and the tools vendors at Northbridge Software).
- **No chart of accounts standard across entities.** Each subsidiary's chart
  of accounts was set up independently, uses different numbering, and has
  duplicate/overlapping accounts created ad hoc during the year (e.g., "Misc
  Expense" and "Misc Expense 2").
- **No segment/dimension posting policy in NetSuite.** Northbridge Software's
  NetSuite instance supports a Department segment, but there's no rule
  requiring it be filled in — roughly 15% of the transactions that should
  carry one don't, which quietly breaks any department-level report.
- **No intercompany policy.** No documented interest rate, repayment schedule,
  or reconciliation cadence for the intercompany notes between Corporate and
  each subsidiary. See `01_Corporate_Holdco/Intercompany_Tracker.xlsx`.
- **No data retention or backup policy** for any of the manually-maintained
  Excel workbooks that function as this company's accounting system of record
  for two of its four entities.

## What "exists" instead

Tribal knowledge, held almost entirely by Priya (and partially by Jenna), and a
handful of informal notes people have sent each other over email and Slack.
`Scattered_Notes_and_Tribal_Knowledge.md` in this same folder collects a few
of those — read them as evidence of how decisions actually get made today, not
as a substitute for real policy.
