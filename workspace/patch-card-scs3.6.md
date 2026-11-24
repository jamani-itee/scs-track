# Patch Card -- SCS3.6

One real bug from the audit.  The fix, not a rewrite.  The spec and the test come before the prompt.

The bug, in one sentence: reorderList in workspace/stock-tools/reorder.js uses < instead of <=, omitting items whose In stock value equals their Reorder at level.
Which check found it (auth, edge case, wrong version, invented library): edge case
The spec for the fix, one thing: Change the reorderList filter comparison from < to <= so items at or below their reorder threshold are included.
The test that shows the bug (input -> expected): grinding discs 115 mm with In stock 20 and Reorder at 20 -> included in reorderList output instead of omitted.
The prompt, word for word: In workspace/stock-tools/reorder.js, change reorderList so items with In stock at or below Reorder at (<=) are included, matching the comment on line 22, without changing any other function.

## The Diff, Read Whole

Every line the patch changed.  A line the spec did not ask for is marked BEYOND in the second column.

| Line | What the patch changed | In the spec? | My adjustment |
|---|---|---|---|
| 24 | Changed parseInt(r["In stock"], 10) < parseInt(r["Reorder at"], 10) to <= | Yes | Kept <= and handled blank In stock cells as 0 |
| 24-27 | Added const stock = r["In stock"] === "" ? 0 : parseInt(r["In stock"], 10); | BEYOND | Added in commit 3 so blank In stock cells do not evaluate to NaN |

Tests before the patch: 5 ok, 1 not ok (includes items AT their reorder level failed on starting state).
Tests after the patch: 6 ok, 0 not ok.
Tests after my adjustment: 7 ok, 0 not ok.
Commits on scs3.6-patch (the test, the patch, the adjustment):
1. Add failing test for items at exact reorder level
2. Patch reorderList to include items at reorder threshold
3. Adjust reorderList to treat blank In stock as 0

## Receipt

1. Label: SCS3.6 reorderList threshold patch
2. Tool and tier: Gemini CLI (free tier) + manual adjustment
3. Spec and prompt: above, word for word
4. Tests or checks: node --test workspace/stock-tools/reorder.test.js (7 ok)
5. Rights line: not checked
6. Cost: 0
