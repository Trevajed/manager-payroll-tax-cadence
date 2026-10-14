# Payroll Tax Cadence — a Manager.io extension

A **read-only** extension for [Manager.io](https://www.manager.io) that shows, for each payroll tax, what you have **accrued, paid and still owe** by month, quarter and year, colour-coded so late items stand out. It also fills **on-screen worksheets** of the federal and Oregon payroll forms from your ledger figures.

> **Not tax or legal advice.** The form worksheets are for transcribing figures, not filing. Check every number against your payroll provider and the official forms.

## Features

- **Overview**: attention box (overdue / coming due), a card per tax, and a month-by-quarter heat grid (✓ paid, ◐ part-paid, … not yet due, ! late).
- **Month-by-month detail**: accrued, paid and owed for every month, quarter and year.
- **Form 941 (federal, quarterly)**, including fractions-of-cents reconciliation and monthly liability.
- **Form 940 (FUTA, annual)**: 6.0% with no state credit (line 8 at 0.6% plus line 9 at 5.4%) when no state unemployment tax is paid.
- **Oregon Form OQ + Form 132**: withholding, statewide transit, TriMet and Paid Leave Oregon, with per-employee detail. Unemployment insurance and Workers' Benefit Fund are left for manual entry.
- Nothing is written to your books, except the optional button that creates the saved report described below.

## How it works

Manager extensions get data through a `postMessage` bridge. The page asks Manager for a saved **General Ledger Transactions** report and works everything out in the browser. No data leaves your machine.

Payments (debits) are applied to the oldest unpaid month first. Credits to a payable account count as owed, and debits as paid.

## Requirements

- Manager desktop or server edition (extensions run in both; built with 26.x).
- Payable accounts whose names contain these words:

| Tax | Account name must contain |
|---|---|
| Social Security | `Social Security` and `Payable` |
| Medicare | `Medicare` and `Payable` |
| FUTA | `FUTA` and `Payable` |
| Oregon withholding | `OR` and `Withh…` and `Payable` (due monthly, 15th of next month) |
| Statewide transit | `Statewide` and `Transit` |
| TriMet | `TriMet` |
| Paid Leave Oregon | `Paid Leave` and `Payable` |
| OregonSaves | `Oregon Saves` |

- A wage expense account named exactly **Salary and Wages**. Payslip lines should carry the employee name as the payee.
- Federal income tax withholding is optional. Its account must contain `Federal` and `Withh…` or `Income`, plus `Payable`.

## Install

1. In Manager, create a saved report: **Reports → General Ledger Transactions → New**, description `Payroll cadence - all accounts 2024-2026`, From `2024-01-01`, To `2026-12-31`, account left empty. (The extension's **Create** button can do this for you.)
2. Open **Settings → Custom Buttons → New** (Manager's newer **Extensions** screen also works).
3. Name: `Payroll Tax Cadence`. Placement: **Summary view**.
4. Paste the whole contents of [`payroll_tax_cadence_extension.html`](payroll_tax_cadence_extension.html) into the HTML box and save.
5. Click the new button on the Summary page, pick the report and year, and press **Load**.

## Customising

Everything lives in `payroll_tax_cadence_extension.html`.

- `TAXES` lists the taxes and the account-name tests.
- `dueDate()` holds the due-date rules (`m15` = 15th of next month, `q` = end of month after quarter, `a` = Jan 31 next year).
- Rates and wage caps are in `calc941`, `calc940` and `calcOQ`. Oregon box numbers follow the 2024 Form OQ, so check them against the current form.

## Limitations

- TriMet uses the rate in the `TRIMET_RATE` table in `payroll_tax_cadence_extension.html`; add each new year's rate there.
- Oregon unemployment insurance and Workers' Benefit Fund have no ledger source, so they are manual.
- Form 941 line 3 (federal income tax withheld) needs its own payable account, otherwise it shows $0.00.
- The TriMet worksheet assumes all wages are earned inside the district.

## License

MIT, see [LICENSE](../LICENSE). Copyright (c) 2026 Two Sisters Nightmare, LLC.
