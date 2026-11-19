# AI receipt log -- SCS3.5

Label: AI-assisted, directed by jamani
Tool: Gemini
Spec initialled on (YYYY-MM-DD): 2026-11-19
First prompt sent on (YYYY-MM-DD HH:MM): 2026-11-19 14:25

## The one prompt, word for word

Write a Google Apps Script on Google Sheets with a comment on every line for a kiosk back-office workbook with three functions:

1. checkStock(): Read DASHBOARD range A12:C15 with columns ITEM, CURRENT STOCK, STATUS (for example: ["Milk", 2, "REORDER"], ["Sugar", 15, "OK"]). Filter rows where STATUS is "REORDER", create or clear a sheet named REMINDERS, write headers ["ITEM", "CURRENT STOCK", "STATUS"] in A1:C1, and write matching low-stock rows starting at row 2.
2. generatemonthlyReport(): Read RECORD range A2:F1000 with columns DATE, ITEM, TYPE, QTY, UNIT PRICE, TOTAL (for example: [2026-11-05, "Milk", "OUT", 3, 100, 300]). Filter rows for November 2026 where TYPE is "OUT", sum TOTAL and QTY, create or clear MONTHLY REPORT, write headers ["REPORT MONTHLY", "TOTAL SALES", "UNITS SOLD"] in A1:C1, and write ["NOVEMBER 2026", totalSales, unitSold] in A2:C2.
3. onEdit(e): Trigger on edits to sheet INTAKE in columns A (ITEM) and B (QTY), ignoring header row 1 and blank cells. If column C (DATE) is blank, stamp today's date formatted as dd/MM/yyyy. Validate that QTY is a positive number and write "OK" or "INVALID ENTRY" in column D (STATUS).

## What came back, and what I changed by hand

The tool returned a draft script containing `checkStock()`, `generatemonthlyReport()`, and `onEdit(e)`. By hand, I added the `// AI-assisted, directed by jamani` header comment on line 1, added null-sheet guards (`if (!dashboard) return;` and `if (!record) return;`), fixed the `"RECORDER"` typo to `"REORDER"`, replaced `.toLocaleTimeString()` with `.toLocaleDateString("en", { month: "long" }).toUpperCase()`, changed single quotes `'${NOVEMBER} ${2026}'` to template literal backticks `` `${monthName} ${reportYear}` ``, and fixed the date filter to verify `row[0] instanceof Date && !isNaN(row[0]) && row[0].getMonth() === reportmonth && row[0].getFullYear() === reportYear`.

## Iteration -- only if the draft missed a line of the spec (which line)

## The debug move -- one real error: the message pasted whole, what my trace said first, what the tool said

- **Error message / defect:** `TypeError: row[0].getFullYear is not a function` (and when all cells were dates, `MONTHLY REPORT!A2:C2` output literal `${NOVEMBER} ${2026}`, `0`, `0`).
- **What my trace said first:** Inspecting lines 25–30 in `reading-log.md` showed single quotes around `'${NOVEMBER} ${2026}'` stopped variable interpolation, `typeof row[0].getFullYear() === reportmonth` compared `"number"` to `10`, `.getMonth()` was never called, and text cells in `RECORD!A2:A1000` threw `TypeError` when calling `.getFullYear()`.
- **What the tool said:** Confirmed the single-quote template string bug, the `typeof` comparison bug, and the missing `.getMonth()` check, and recommended guarding with `row[0] instanceof Date && !isNaN(row[0])`.
