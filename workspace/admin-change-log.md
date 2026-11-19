# Admin change log -- SCS3.1

Date: 2026-11-17
Sandbox admin sign-in: jamani@your-actual-domain.com
My unit: /Trainees/hussink
Naming convention: first.last

One row per admin action, written BEFORE the click. A ticket may take several rows; add them as you go.
Logged at: the time on the laptop clock when you wrote the row.
Console path: where you expect to click, with ">" between the steps; correct it after if the console differs.
Audit log: filled in SGL/Lab -- the time the console's audit log shows for this change, or "gap:" and why.
Never write a password here. The first password is handed over by voice.

| #   | Ticket           | Logged at | What I am about to change (console path)                                      | Who or what it affects                                                 | Why (the three questions, one line)                                                                           | How I checked it                                                                | Audit log |
| --- | ---------------- | --------- | ----------------------------------------------------------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | --------- |
| 1   | 1 New starter    | 10:50     | Admin console > Directory > Users > Add new user                              | amina.otieno, new Front Desk starter                                   | The job needs counter email and calendar, extra access risks financial records, the owner decided             | Verified user appears active in users list and signed in via private window     | 10:52     |
| 2   | 2 Groups         | 10:55     | Admin console > Directory > Groups > Create group                             | counter@your-actual-domain.com, counter staff                          | Staff need one shared address for shift rotas, wider access exposes management mail, the shop manager decided | Verified group page lists all counter members                                   | 10:57     |
| 3   | 3 Units          | 11:00     | Admin console > Directory > Organizational units > Create organizational unit | Front Desk under /Trainees/hussink/Staff                                | Chat must be turned off for counter staff only while other staff keep it, the owner decided                   | Verified Front Desk OU appears in tree and moved new starter into it            | 11:02     |
| 4   | 4 Delegated role | 11:05     | Admin console > Account > Admin roles > Assign users                          | Accountant user in /Trainees/hussink/Staff, Password Reset Admin        | The job needs password resets for staff only, full admin risks billing and data deletion, the owner decided   | Signed in as accountant and tested three actions to confirm role limits         | 11:07     |
| 5   | 5 Rollback       | 11:10     | Admin console > Account > Admin roles > Unassign users                        | Accountant user in /Trainees/hussink/Staff, remove Password Reset Admin | The role test is complete and elevated privileges are no longer needed, the trainer decided                   | Confirmed Password Reset Admin role is removed from the accountant user profile | 11:12     |

## Gaps

One line per gap between this log and the console's audit log: "row 3: ..." for a row, "no row: ..." for an event.

## Audit match

Rows matched: 5 of 5. Gaps explained: 0.

## SCS3.2 -- sharing, security, backups, offboarding (2026-11-19)

Practice OU only.  Every row written before the click; the check column filled after it.

| # | Time | What I am about to change (console path) | Who or what it affects | Why, in one line | How I checked it | Undo |
|---|---|---|---|---|---|---|
| 1 | 17:47 | Admin console > Security > Authentication > 2-step verification | /Trainees/hussink (practice user) | Enforce 2-step verification to prevent credential-only account takeover | Enrolled practice user in 2SV, verified on Security screen and captured screenshot | Set Enforcement back to Off / Inherit on /Trainees/hussink |
| 2 | 17:56 | Admin console > Apps > Google Workspace > Drive and Docs > Sharing settings | /Trainees/hussink | Restrict external sharing to warn or block outside sharing and prevent data leaks | Tested outside-share attempt from partner account and verified warning/block | Reset external sharing to Inherit on /Trainees/hussink |
| 3 | 18:05 | Admin console > Apps > Google Workspace > Drive and Docs > Sharing settings > Link sharing default | /Trainees/hussink | Set default link access to Restricted so new files are not exposed by link | Created test file in practice user Drive and confirmed General access defaults to Restricted | Reset link default to Inherit on /Trainees/hussink |
| 4 | 18:12 | Admin console > Apps > Google Workspace > Drive and Docs > Manage shared drives > Create shared drive | /Trainees/hussink (BusinessFiles shared drive) | Create shared drive so business files live under company ownership rather than personal Drive | Verified shared drive appears in Drive and moved business files into it | Remove test files and delete shared drive if needed at reset |
| 5 | 18:18 | Admin console > Apps > Google Workspace > Drive and Docs > Manage shared drives > Settings | BusinessFiles shared drive members | Block non-member access and restrict external sharing on the shared drive | Checked shared drive settings panel and tested external share restriction | Reset shared drive external sharing toggle |
| 6 | 18:25 | Admin console > Devices > Mobile and endpoints > Settings > Universal settings > Password settings | /Trainees/hussink | Require device screen lock and strong passcode to protect company data on mobile endpoints | Verified device screen lock policy shows active on /Trainees/hussink OU | Set device screen lock policy back to Inherit |
| 7 | 18:32 | Admin console > Directory > Users > Select user > Security > Reset sign-in cookies / 2-step backup codes | Practice user in /Trainees/hussink | Generate paper backup codes for account recovery and verify active session controls | Wrote backup codes on paper only and confirmed 2SV status on user Security card | Revoke unused backup codes at reset |
| 8 | 18:40 | Admin console > Directory > Users > Select leaver > Suspend user | Practice leaver in /Trainees/hussink | Suspend leaver account immediately upon departure to block sign-in while preserving data | Attempted sign-in as leaver in private window and confirmed access refused | Un-suspend user at end of lab reset |
| 9 | 18:48 | Admin console > Apps > Google Workspace > Drive and Docs > Transfer ownership | Practice leaver to manager in /Trainees/hussink | Transfer ownership of leaver Drive files to manager so business records are retained | Confirmed files appear in manager Drive and ownership transfer logged in Drive audit events | Transfer ownership back if needed during reset |
| 10 | 18:55 | Admin console > Directory > Groups > Remove leaver from staff groups | Practice leaver in /Trainees/hussink | Remove leaver from shared mailing lists and shared drive access groups | Verified group membership list no longer shows the suspended leaver | Re-add user to groups after un-suspend |
| 11 | 19:30 | Admin console > Directory > Users > Select leaver > Reactivate (un-suspend) user | Practice leaver in /Trainees/hussink | Un-suspend practice user at end of lab so the practice OU is left whole | Verified user status shows Active in Directory and exported final Users CSV | N/A (this is the reset step) |
