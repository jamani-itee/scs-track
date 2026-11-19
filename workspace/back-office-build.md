# Back office build — SCS3.4
Client: a kiosk (named in the client folder, not here). Sheet: SCS3.4 Kiosk Back Office.

## Overkill test

| # | Question | My client's answer |
| :-: | :-: | :-: |
| 1 | How many people type into it? | One owner, and occasionally one trusted family member at the counter. |
| 2 | How many rows a month? | Around 60 to 120 sales and stock entries per month. |
| 3 | Does it need to talk to anything else? | Nothing automated; M-Pesa messages are checked manually. |
| 4 | What happens if a number is wrong? | The owner spots it on the Dashboard and adds a correcting row. |
| 5 | Who supports it next year? | The owner, using the printed owner's card in their language. |

Verdict: Sheets. Pattern: Inventory. Because: the kiosk has under 200 rows a month, one or two trusted operators, no external integrations, and the owner can maintain it with a simple reference card.

## Validation

| Column | Rule | The garbage I typed | Refused? |
| :-: | :-: | :-: | :-: |
| Records!A2:A (DATE) | Is valid date (after 01/01/2000) | tomorrow | Yes |
| Records!B2:B (ITEM) | Dropdown from Lists!A2:A | sugar 1 kg | Yes |
| Records!C2:C (DIRECTION) | Dropdown (IN, OUT) | SOLD | Yes |
| Records!D2:E (QUANTITY & PRICE) | Number greater than 0 | -3 | Yes |

## Protection

| Range | Who can edit | Warning or restriction | Entry columns still open? |
| :-: | :-: | :-: | :-: |
| Dashboard tab | Only you | Restrict who can edit | Yes (Records entry columns open) |
| Records!F2:F (AMOUNT formula) | Only you | Restrict who can edit | Yes (A2:E open for entry) |

## AI receipts

| # | The ask (headings only) | The formula | What I changed | Hand check (log row) |
| :-: | :-: | :-: | :-: | :-: |
| 1 | Tab Records has Date, Item, Direction, Quantity, Price, Amount. Add Amount for OUT rows dated in the current month. | `=SUMIFS(Records!F:F,Records!C:C,"OUT",Records!A:A,">="&(EOMONTH(TODAY(),-1)+1),Records!A:A,"<="&EOMONTH(TODAY(),0))` | Verified `+1` on `EOMONTH(TODAY(),-1)` so the last day of the prior month is excluded, and matched column letters to Records. | Row 1 |

## Break the books

| # | Attack | I said | What happened | Held / the fix |
| :-: | :-: | :-: | :-: | :-: |
| 1 | Item name not on Lists typed into Records | Refused by dropdown validation | Refused with red error pop-up | Held (validation rule) |
| 2 | Quantity of -3 entered | Refused by >0 rule | Refused with red error pop-up | Held (validation rule) |
| 3 | Date next year entered | Accepted because it is a valid date | Accepted into Records | Expected; noted on owner's card to verify today's date |
| 4 | New row with amount/price left blank | Accepted because rules check typed values | Accepted with 0 amount | Expected; noted on owner's card that every row needs a price |
| 5 | Number typed over a Dashboard formula | Refused by sheet protection | Refused; edit blocked for partner account | Held (Dashboard restricted to owner) |
| 6 | Number typed over AMOUNT formula in Records | Refused by range protection | Refused; edit blocked for partner account | Held (F2:F restricted to owner) |
| 7 | Delete or clear a row in the middle of Records | Protected cells refuse full row delete, entry cells can be cleared | Entry cells cleared; restored via Version History | Held; Version History used to restore cleared cells |
