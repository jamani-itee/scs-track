# Method note -- SCS3.2

1. Enforcing 2-Step Verification and restricting external link sharing at the OU level immediately closes the highest-risk gaps for credential theft and accidental public exposure.
2. Keeping business records in Shared Drives rather than personal My Drive folders prevents data loss when staff leave or forget to transfer ownership.
3. Suspending a leaver instead of deleting the account preserves email, Drive ownership transfer options, and audit history without risking permanent data loss after the 20-day deletion window.
4. Writing every change-log row before clicking in the Admin console creates an auditable trail that matches Google's own Admin and Drive log timestamps.
5. Testing restores across four paths (suspended user, shared drive trash, admin data restore, and offline export) proves what metadata and sharing settings do not survive a backup.
6. What I might be wrong about in this client's data, and how I would find out: I might be wrong about which legacy folders or third-party connected apps are still shared publicly via old links or owned by former staff, and I would find out by exporting the full Drive audit log events and checking third-party app access under Security > Access and data control > API controls with the owner.
