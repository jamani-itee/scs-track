# Project Rules

## Stack
- Node.js v22.22.1 with built-in node:test and node:assert in workspace/stock-tools
- Google Apps Script V8 in workspace/automation/kiosk-back-office.gs

## Tests
- Run node --test workspace/stock-tools/reorder.test.js before committing changes to workspace/stock-tools.
- Write a failing test reproducing the exact bug input before applying a patch.

## Never
- Never hardcode API keys or secrets in source files; read from process.env and fail if missing.
- Never commit .env files; keep .env in .gitignore.
- Never apply changes outside workspace/stock-tools when running scoped tool tasks.
