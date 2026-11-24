# Name: weekly-stock-reorder

## When to use
Run every week when preparing the stock reorder list and checking SMS dry-run output from the CSV export.

## Steps
1. Verify workspace/stock-tools/stock-export.csv has the expected header columns.
2. Run node --test workspace/stock-tools/reorder.test.js to confirm tests pass.
3. Run node workspace/stock-tools/reorder.js workspace/stock-tools/stock-export.csv to inspect items to reorder.
4. Run SMS_API_KEY="$SMS_API_KEY" node workspace/stock-tools/send-sms.js workspace/stock-tools/stock-export.csv --dry-run.

## How you know it worked
Tests pass with 0 failures and the reorder output lists items at or below their reorder level without errors.

Ran: 2026-11-24 — Passed (7 tests ok)
