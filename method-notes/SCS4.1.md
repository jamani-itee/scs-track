# Method note -- SCS4.1

## 1. What I set out to do
Complete the SCS4.1 network checks, diagnose gateway 10.10.51.1 on Rung 3 using the troubleshooting ladder, and record honest notes without private data.

## 2. What I did, in order
Ran net-look, wrote one pre-action prompt in network-diagnosis-receipt.md before changing settings, checked Rung 1 connection state and Rung 3 gateway reachability against a nearby device, and started updating the SCS4.1 logs and hardening record.

## 3. How I checked it worked
Verified net-look receipt output, checked saved files with cat and ls -la, committed changes in git, and ran check-scs4.1 to see which checks passed or remained open.

## 4. What went wrong and what I did about it
Pasting Markdown directly into bash caused shell command errors, and my router screenshot was still on the Windows side rather than in ~/scs/evidence/scs4.1; I switched to cat << 'EOF' for file writes and planned to copy the sanitized screenshot via File Explorer.

## 5. What I would do differently next time
Write Markdown files through an editor or single-quoted heredoc rather than pasting raw lines into bash, and copy sanitized screenshots into ~/scs/evidence/scs4.1 before running check-scs4.1.

## 6. What I might be wrong about, and how I would find out
Gateway 10.10.51.1 not answering could be a local interface or ping/firewall filter rather than a dead router; I would test a known-good device on the same network and check interface and router status directly.
