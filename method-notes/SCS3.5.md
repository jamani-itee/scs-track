# Method note -- SCS3.5

- **Module:** SCS3.5 -- Kiosk Back-Office Automation (Google Apps Script)
- **Author:** jamani
- **Label:** AI-assisted, directed by jamani
- **Date:** 2026-11-19

## What I built and why

I automated three recurring back-office tasks for a kiosk workbook in Google Sheets using Google Apps Script (`workspace/automation/kiosk-back-office.gs`):

1. **`checkStock()`** scans `DASHBOARD!A12:C15` for items marked `"REORDER"` and writes them into the `REMINDERS` tab.
2. **`generatemonthlyReport()`** filters `"OUT"` sales transactions for November 2026 in `RECORD!A2:F1000`, calculates total sales and total units sold, and writes them to `MONTHLY REPORT!A2:C2`.
3. **`onEdit(e)`** triggers automatically on edits to columns A and B of `INTAKE` (skipping header row 1), stamps today's date (`dd/MM/yyyy`) in column C if blank, and marks column D `"OK"` for positive numbers or `"INVALID ENTRY"` otherwise.

## How I audited, tested, and debugged the AI draft

1. **Privacy & specification first:** Before prompting the AI tool, I wrote the specification using only sheet names, column headings, and made-up sample rows—never real customer names, phone numbers, addresses, or balances.
2. **Pre-run reading log:** I committed the raw AI draft first (`63523a3`) and read every single line into `reading-log.md` (`cb7b60b`) before executing it once, classifying each line as `variable`, `sequence`, `condition`, `loop`, or `trigger`.
3. **Run 1 testing & break tracing:** I worked out expected outputs on paper before running the script on a copy of the spreadsheet. Run 1 exposed four defects:
   - `"RECORDER"` typo instead of `"REORDER"` in `checkStock()`, returning zero reorder items.
   - `toLocaleTimeString()` instead of `toLocaleDateString()` when formatting the month name.
   - Single quotes `'${NOVEMBER} ${2026}'` instead of backticks `` `${monthName} ${reportYear}` ``, printing literal placeholder text.
   - `typeof row[0].getFullYear() === reportmonth` comparing `"number"` to `10` and crashing on non-date text cells in `RECORD!A2:A1000`.
4. **Hand patches & Run 2 verification:** I patched those lines by hand, added null-sheet guards (`if (!dashboard) return;` and `if (!record) return;`), renumbered `reading-log.md` to match every line (`1`–`81`), and verified in Run 2 that all test cases, edge cases, and the nine-breaks audit (`breaks.md`) pass cleanly.
5. **Evidence preservation:** I saved the editor copy of `kiosk-back-office.gs` and the tested `.xlsx` spreadsheet copy in `~/scs/evidence/scs3.5/` outside the Git repository.
