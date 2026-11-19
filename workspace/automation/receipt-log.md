# AI receipt log -- SCS3.5

Label: AI-assisted, directed by jamani
Tool: Gemini
Spec initialled on (YYYY-MM-DD): 2026-11-19
First prompt sent on (YYYY-MM-DD HH:MM): 2026-11-19 14:25

## The one prompt, word for word

[Paste the exact prompt you sent to the AI tool to generate the Apps Script draft—with your spec, column headings, and sample rows, and zero real client data]

## What came back, and what I changed by hand

The tool returned an 88-line Google Apps Script containing three functions (`checkStock`, `generatemonthlyReport`, and `onEdit`).
By hand, I made five targeted fixes after reviewing the code and running Run 1:

1. Added null-sheet guards (`if (!dashboard) return;` and `if (!record) return;`) so missing tabs fail safely.
2. Fixed the typo `"RECORDER"` -> `"REORDER"` in `checkStock()` so low-stock items match the dashboard status.
3. Replaced `.toLocaleTimeString()` with `.toLocaleDateString("en", { month: "long" }).toUpperCase()` in `generatemonthlyReport()`.
4. Replaced single quotes `'${NOVEMBER} ${2026}'` with template literal backticks `` `${monthName} ${reportYear}` `` so the cell renders `NOVEMBER 2026`.
5. Replaced `typeof row[0].getFullYear() === reportmonth && row[0].getFullYear() === reportYear` with `row[0] instanceof Date && !isNaN(row[0]) && row[0].getMonth() === reportmonth && row[0].getFullYear() === reportYear` so November 2026 `"OUT"` rows filter accurately without crashing on non-date cells.

## Iteration -- only if the draft missed a line of the spec (which line)

None (or list any specific line of your initialled spec that was missing from the first draft).

## The debug move -- one real error: the message pasted whole, what my trace said first, what the tool said

- **Error / Defect observed:** In `generatemonthlyReport()`, cell `A2:C2` output literal `${NOVEMBER} ${2026}` with `0` sales and `0` units sold (and threw `TypeError: row[0].getFullYear is not a function` when non-date text existed in `RECORD!A2:A1000`).
- **What my trace said first:** Reading lines 25–30 in `reading-log.md` showed single quotes around `'${NOVEMBER} ${2026}'` prevented variable interpolation, `typeof row[0].getFullYear()` evaluated to the string `"number"` rather than `10`, and `.getMonth()` was never called.
- **What the tool said:** Confirmed the single-quote template string bug, the `typeof` comparison against `reportmonth`, the missing `.getMonth()` check, and recommended guarding with `row[0] instanceof Date && !isNaN(row[0])`.
