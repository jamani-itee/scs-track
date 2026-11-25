# Network troubleshooting log -- SCS4.1

Date: 2026-11-25
Station: SA isolated kit station

## Fault 1 -- station fault

Symptom (the owner's words): net-look shows PASS on Rung 2 (10.10.51.195/24) and Rung 5 (name lookup), but FAIL on Rung 3 (Gateway 10.10.51.1 did not answer) and Rung 4 (8.8.8.8 did not answer).
My guess (device, cable or network): network
The rung I expected to fail: 3

| Step | What I did (one swap or one look) | What changed | Rung |
|---|---|---|---|
| 1 | Checked Wi-Fi on, Airplane mode off, and no active fault card or VPN on DESKTOP-MEV4V8E | nothing | 1 |
| 2 | Checked whether a healthy nearby device also uses gateway 10.10.51.1 and gets a reply | [record what you saw on the nearby device] | 3 |
| 3 | [record your next single look or swap from your paper log] | nothing | 3 |
| 4 |  |  |  |
| 5 |  |  |  |
| 6 |  |  |  |

The rung that failed: 3
The fault was: [actual fault observed]
Fixed by: [specific check, swap, or setting change]
Put back: [checked on the station after put-back]

## Fault 2 -- station fault

Symptom (the owner's words): [symptom from your paper log for the second station fault]
My guess (device, cable or network): network
The rung I expected to fail: [expected rung number]

| Step | What I did (one swap or one look) | What changed | Rung |
|---|---|---|---|
| 1 | [first single look or swap before changing anything] | nothing | [rung] |
| 2 | [second single look or swap] | [what changed or nothing] | [rung] |
| 3 |  |  |  |
| 4 |  |  |  |
| 5 |  |  |  |
| 6 |  |  |  |

The rung that failed: [rung number]
The fault was: [actual fault observed]
Fixed by: [what fixed it]
Put back: [checked on the station after put-back]

## Fault 3 -- fault card, I was the fixer

Symptom: [fault card symptom or not done: reason]
My guess (device, cable or network): device
The rung I expected to fail: [rung number]
Steps taken: [single checks/swaps or not done: reason]
The rung that failed: [rung number or not done]
The fault was: [fault or not done: reason]
Fixed by: [fix or not done: reason]
Put back: [checked on station or not done: reason]

## The card I planted

Card number: [card number or not done: reason]
Step I did by hand: [manual fault step or not done: reason]
Undo: [how it is undone or not done: reason]
How I checked it: [verification check or not done: reason]
