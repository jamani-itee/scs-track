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
| 2 | Checked whether a healthy nearby device also uses gateway 10.10.51.1 and gets a reply | not done: no healthy nearby device check recorded | 3 |
| 3 | Checked Rung 3 gateway reachability on DESKTOP-MEV4V8E | nothing | 3 |
| 4 |  |  |  |
| 5 |  |  |  |
| 6 |  |  |  |

The rung that failed: 3
The fault was: Gateway 10.10.51.1 did not answer during net-look
Fixed by: not done: unresolved during evening check
Put back: not done: not verified on station

## Fault 2 -- station fault

Symptom (the owner's words): Intermittent connectivity observed on station DESKTOP-MEV4V8E
My guess (device, cable or network): network
The rung I expected to fail: 3

| Step | What I did (one swap or one look) | What changed | Rung |
|---|---|---|---|
| 1 | Checked connection state before changing any settings | nothing | 1 |
| 2 | Ran net-look to read interface and rung status | nothing | 3 |
| 3 |  |  |  |
| 4 |  |  |  |
| 5 |  |  |  |
| 6 |  |  |  |

The rung that failed: 3
The fault was: not done: second fault details not completed from paper log
Fixed by: not done: not recorded
Put back: not done: not checked on station

## Fault 3 -- fault card, I was the fixer

Symptom: not done: fault card exercise not completed on station
My guess (device, cable or network): device
The rung I expected to fail: 2
Steps taken: 1. Checked active fault card status (none active). 2. Checked ~/scs-faults for guess file (none found).
The rung that failed: not done: fault card not run
Sealed log fingerprint: not done: no guess file found in ~/scs-faults
Card number (27-30): not done: no reveal recorded
Proved on lab device: not done: not run on lab device
The fault was: not done: fault card not run
Fixed by: not done: no fix performed
Put back: not done: not applicable

## The card I planted

Card number: not done: did not plant a fault card
Step I did by hand: not done: did not plant a fault card
Undo: not done: did not plant a fault card
How I checked it: not done: did not plant a fault card
