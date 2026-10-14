# Changelog

## 1.1.1
- Form 940 line 13: a payment now counts toward the year named in its memo (for example "FUTA 2023"), not the year it was paid. Late payments of earlier years no longer reduce the current year's balance. With no year in the memo, the payment date's year is used.
- Oregon OQ: the TriMet warning now explains that a one-cent gap against the ledger is normal (payroll rounds each payslip, the form rounds the quarter total down).

## 1.1.0
- Due dates that fall on a weekend or US federal holiday move to the next business day (for example the Q3 Oregon OQ is due Nov 2, 2026, not Oct 31).
- Oregon OQ: prepaid boxes (3a, 3b, 8a, 20b) are flagged as "from your ledger – not verified", and you can type the real payment amounts from Revenue Online to replace them.
- Form 132 rebuilt: one line per real employee (names cleaned and merged, agency and payment-ID payees ignored), with whole hours and UI wages marked "enter", and no TriMet column.
- Form 940: the four quarters now add up exactly to line 12, a list shows every payment counted on line 13, and an unfinished current year is flagged as a snapshot.
- Overview note: payments are matched to the oldest unpaid month first, so combined payments recorded without a program split can create false arrears; verify with the agency.

## 1.0.3
- Form 940 shows a "what if state unemployment tax applied" comparison under the form.

## 1.0.2
- TriMet box 6a now uses the official rate by year (0.008237 for 2026) and box 7a = wages × rate rounded down, instead of a rate backed out of the ledger.

## 1.0.1
- Oregon withholding due monthly (15th of next month); statewide transit rate corrected to 0.1%; notes for UI/WBF exemptions and Paid Leave employee-share-only.

## 1.0.0
- Overview, month-by-month detail, Form 941, Form 940 (6.0% FUTA with no state credit) and Oregon Form OQ + Form 132 tabs.
- Oldest-unpaid-first payment matching; colour-coded status.
