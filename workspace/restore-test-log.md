# Restore test log -- the practice business (2026-11-19)

A backup nobody has restored from is a hope.  'It worked' is not an entry: say what did not come back,
or what you checked to be sure nothing is missing.

| # | Restore | What I deleted or suspended | How I restored it | How long | What came back | What did not come back |
|---|---|---|---|---|---|---|
| 1 | The suspended user, restored whole | Suspended practice leaver account in /Trainees/hussink | Admin console > Directory > Users > Select suspended user > Reactivate | 2 minutes | User account, email address, OU placement, and existing Drive files came back intact | Active sign-in session cookies and prior group memberships did not come back automatically and had to be re-added |
| 2 | A file from the shared drive's trash | Deleted `price-list.csv` from BusinessFiles shared drive | Opened BusinessFiles Shared Drive > Trash > Right-click file > Restore | 1 minute | File content, version history, and Shared Drive folder placement came back intact | Custom external share links were not active because link sharing remained restricted |
| 3 | A user's deleted file, restored by the admin | Permanently deleted `customer-list.csv` from practice user's Drive trash | Admin console > Directory > Users > Select user > Restore data (selected 24-hour date range) | 4 minutes | File `customer-list.csv` and its folder location reappeared in the user's Drive | Previous per-file sharing permissions and public link settings did not come back |
| 4 | One file from the export | Extracted `customer-list.csv` from the Takeout / backup archive into `restore-test/` | Downloaded Takeout zip / `company-backup.tar.gz`, extracted `customer-list.csv`, and verified row count and headers | 5 minutes | All CSV columns, customer rows, and data values came back readable and intact | Google Docs native comment threads, live sharing permissions, and original Drive file IDs did not come back in the static export |
