# AzureDeck 1.9.11 — Detect and automatically close fatal installer dialogs

Roblox's modern Critical Error dialog ("Installer encountered a critical error.") is now read through bounded Windows accessibility queries and native control text. It no longer depends on Static controls. Detection is scoped to visible windows of the retained installer process. Normal update text and unrelated windows are excluded.

Repair follows verified existing installer families and checks every installer process in its own tracked job, including temporary helper filenames. Player/Home and WebView descendants are excluded from installer-job error scanning. An installer handing off to a helper cannot hide the helper's fatal dialog just because its filename differs.

A detected fatal installer is closed automatically: AzureDeck acknowledges its error, requests a normal exit and allows ten seconds for it to finish. If that failed installer family refuses to exit, AzureDeck reopens only the retained processes, verifies their creation identities, terminates that family and waits up to three seconds for exit. Independent healthy installers are left to finish normally. Cancellation and healthy updating never trigger forced termination. If Windows denies closure, repair stops with an explicit error instead of waiting indefinitely.

Recovery follows this order automatically:

1. Close the failed installer family and verified Roblox players, then release multi-instance compatibility.
2. Download and verify a fresh official launcher, rerun it to update Roblox without deleting the local Roblox folder, wait for its helpers, and retry the interrupted launch with a fresh ticket.
3. If that update fails, or the retried client still has an installation failure, prepare another verified installer and perform the full clean reinstall. Wait, restore compatibility and retry the selected batch.
4. If the clean reinstall or its next launch still fails, automatically close its fatal installer and stop with a persistent error. No third automatic attempt or repeated deletion is allowed.

Settings and Launch center distinguish an active repair from a blocked launch needing attention. Repair now becomes available after failure. The update-clean-v2 strategy persists both attempt phases across restart and migrates the earlier strategy once. A later automatic episode still requires a confirmed healthy join and the 30-minute cooldown; an explicit Repair now resets the budget.

The full-folder cleanup policy from 1.9.10 is unchanged: the entire native %LOCALAPPDATA%\Roblox folder, including Studio and local data, is removed only in the authorized clean-reinstall flow; only Player is reinstalled. AzureDeck data outside that folder is protected.

Native tests reproduce the modern TaskDialog without Static error controls, including a temporary helper name, graceful acknowledgement, an installer that refuses to close, cancellation and an unrelated healthy window. Manager tests verify that a fatal error completes launch futures, clears active repair state, persists the reason and does not start an unbounded third attempt. Real Roblox installers were not executed or terminated during validation. See VALIDATION.md.
