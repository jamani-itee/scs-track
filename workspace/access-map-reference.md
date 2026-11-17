# Access map -- the reference shop (an invented business) -- SCS3.1

Who should have which access, and why?  One row per person, or per identical job.
Groups are people; units are settings; every person is in one unit and many groups.
Why: the three questions in one line -- what the job needs, what goes wrong with more, who decided.
This map is of an invented business and may be committed.  Your client's map never comes here:
it lives in the client folder (Clients, in your Windows SCS folder).

| Person (job) | What the job needs | OU | Groups | Admin role | Why (one line) |
|---|---|---|---|---|---|
| The owner | Full workspace control and billing | /Trainees/hussink/Management | all-staff@, management@ | Super Admin | Needs full control; others could lock out business; owner decided |
| The accountant (a sandbox user, ticket 4) | Financial records and user read access | /Trainees/hussink/Staff | all-staff@, finance@ | User Management Admin | Needs user/billing visibility; full admin exposes security settings; owner decided |
| The shop manager | Staff scheduling and shared drives | /Trainees/hussink/Management | all-staff@, management@, counter@ | none | Needs team drive access; admin role risks accidental account changes; owner decided |
| Counter staff (four) | POS email and front desk shared drive | /Trainees/hussink/Staff/Front Desk | all-staff@, counter@ | none | Needs customer email; extra access risks financial data leaks; manager decided |
| The new starter (a sandbox user, ticket 1) | Basic email and front desk resources | /Trainees/hussink/Staff/Front Desk | all-staff@, counter@ | none | Needs onboarding tools; extra access risks unapproved changes; manager decided |
| Welders (three) | Workshop announcements and safety docs | /Trainees/hussink/Staff/Workshop | all-staff@, workshop@ | none | Needs safety bulletins; office files risk accidental edits; manager decided |
| Drivers (two) | Delivery schedules and route sheets | /Trainees/hussink/Staff/Logistics | all-staff@, drivers@ | none | Needs dispatch info; internal records are unnecessary; manager decided |
| Me (the admin) | Routine user and group setup | /Trainees/hussink | all-staff@, it-admin@ | Help Desk Admin | Needs daily support tools; Super Admin risks full lockout; owner decided |

## The partner's cold read

Partner: hussink.  One person with more than the job needs, or "none" and why: none, every role matches the minimum job requirement.
