# Method note -- SCS3.1

## 1. What I set out to do
Configure users, groups, organizational units, and delegated admin roles for SCS3.1 while logging every step beforehand.

## 2. What I did, in order
Created the change log, added the new starter, set up groups and OUs, tested delegated admin permissions, and executed the rollback.

## 3. What went wrong, and how I fixed it
The unit path in the log initially defaulted to my local Linux username instead of my sandbox unit, so I updated it to match the CSV export.

## 4. How long it took, against the plan
Completed within the scheduled lab session alongside verification checks.

## 5. One lesson for the next person
Always verify your exact sandbox Organizational Unit path from the console before writing log entries.

## 6. What I might be wrong about, and how I would find out
Some group permissions might overlap across OUs; I would verify by signing in as a test user and checking effective access.
