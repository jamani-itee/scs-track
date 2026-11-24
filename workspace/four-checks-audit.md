# Four-Checks Audit

Run all four on every AI-built piece before a client sees it.  Write what you found, not what you hoped.
'Clean' is allowed only with the evidence beside it: the command you ran and what it printed, or the
page you read and the date you read it.  One section per piece; add a new piece at the bottom each time.

## Piece 1: the stock tool (workspace/stock-tools)

### Auth
Looked for: Hardcoded API keys, tokens, passwords, or insecure HTTP URLs in workspace/stock-tools/*.js.
Found: Hardcoded gateway API key LLDEMO-SMS-5c1e9a07d2b84f63 on line 9 of workspace/stock-tools/send-sms.js sent over HTTP.
Evidence: Command: grep -n "SMS_API_KEY" workspace/stock-tools/send-sms.js -> Printed: 9:const SMS_API_KEY = "LLDEMO-SMS-5c1e9a07d2b84f63"; (in commit e6f6660).

### Edge cases
Ugly inputs, written before trying them: Exact threshold (20 vs 20), blank In stock (""), quoted commas ("Nails, 3 inch"), and apostrophe names (ng'ombe salt lick).
Found: reorderList uses < instead of <=, omitting items at their exact reorder level (grinding discs 115 mm), blank In stock evaluates to NaN, and line.split(",") splits quoted commas.
Evidence: Command: node workspace/stock-tools/reorder.js workspace/stock-tools/stock-export.csv -> Printed output omitted grinding discs 115 mm and Cement 50 kg, and split "Nails, 3 inch" across columns.

### Wrong versions
Looked for: Node.js APIs requiring newer versions than LTS or deprecated calls.
Found: Object.groupBy on line 29 of workspace/stock-tools/reorder.js requires Node 21+ (fails on Node 18/20 LTS).
Evidence: Command: node -v && grep -n "groupBy" workspace/stock-tools/reorder.js -> Printed: v22.22.1 and 29:  return Object.groupBy(list, (r) => r.Supplier);.

### Invented libraries
Looked for: Non-existent modules or unexported helpers in require(...) calls.
Found: fetchWithRetry imported from "node:http" on line 5 of workspace/stock-tools/send-sms.js does not exist in node:http.
Evidence: Command: node -e 'console.log(typeof require("node:http").fetchWithRetry)' -> Printed: undefined.

The one to fix first, and why: Remove the hardcoded SMS_API_KEY from send-sms.js first so secrets are not stored in code, then fix the <= threshold in reorder.js.

## Piece 2: my own SCS3.5 script

### Auth
Looked for: Hardcoded credentials, external URLs, or missing sheet permissions in workspace/automation/kiosk-back-office.gs.
Found: Clean (uses SpreadsheetApp.getActiveSpreadsheet() with no hardcoded keys or external URLs).
Evidence: Command: grep -En "http|key|token|secret|password" workspace/automation/kiosk-back-office.gs || echo "No credentials or URLs found" -> Printed: No credentials or URLs found.

### Edge cases
Ugly inputs, written before trying them: Blank rows, comma-formatted numbers ('1,500'), unknown payment methods ('airtel'), and duplicate runs of summariseToday().
Found: Blank dates produce Invalid Date, Number("1,500") returns NaN, unknown payment methods are dropped, and re-running appends duplicate rows.
Evidence: Command: nl -ba workspace/automation/kiosk-back-office.gs -> Lines 18-36 lack blank-row guards, comma stripping, an Other payment branch, and duplicate-date checks.

### Wrong versions
Looked for: Deprecated SpreadsheetApp calls or incompatible JavaScript syntax in workspace/automation/kiosk-back-office.gs.
Found: Clean (uses standard SpreadsheetApp methods and compatible syntax).
Evidence: Command: grep -n "SpreadsheetApp\|getSheetByName\|appendRow" workspace/automation/kiosk-back-office.gs -> Printed lines 6, 7, 8, 36.

### Invented libraries
Looked for: Non-existent Apps Script classes or invented methods in workspace/automation/kiosk-back-office.gs.
Found: Clean (only standard Apps Script SpreadsheetApp and built-in Date/Number/String methods).
Evidence: Command: grep -Eo "[A-Za-z0-9_]+\.[A-Za-z0-9_]+" workspace/automation/kiosk-back-office.gs -> Printed only valid SpreadsheetApp, sheet, date, and string methods.

What I will do about what I found (a fix on the sheet copy, SCS3.5's test log, or 'clean'): Record the findings in workspace/automation/breaks.md and workspace/automation/test-log.md, and apply the guards on the sheet copy before live use.
