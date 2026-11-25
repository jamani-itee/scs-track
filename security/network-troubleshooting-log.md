# Network troubleshooting log -- SCS4.1

Date: 2026-11-25
Station: SA isolated kit station

## Fault 1 -- station fault

Symptom (the owner's words): net-look shows PASS on Rung 2 (10.10.51.195/24) and Rung 5 (name lookup), but FAIL on Rung 3 (Gateway 10.10.51.1 did not answer) and Rung 4 (8.8.8.8 did not answer).
My guess (device, cable or network): Network/gateway path or local interface on Rung 3 because address assignment (Rung 2) and name resolution (Rung 5) passed while the gateway did not answer.
The rung I expected to fail: 3

| Step | What I did (one swap or one look) | What changed | Rung |
|---|---|---|---|
| 1 | Checked Wi-Fi on, Airplane mode off, and no active fault card or VPN on DESKTOP-MEV4V8E | nothing | 1 |
| 2 | Checked whether a healthy nearby device also uses gateway 10.10.51.1 and gets a reply | [record whether 10.10.51.1 answered on the nearby device or also failed] | 3 |
| 3 | [record your next single look or swap from your paper log] | [nothing or what changed] | 3 |
| 4 |  |  |  |
| 5 |  |  |  |
| 6 |  |  |  |

The rung that failed: 3
The fault was: [actual fault observed after checking]
Fixed by: [specific check, swap, or setting change that resolved it]
Put back: [checked on the station after put-back]
