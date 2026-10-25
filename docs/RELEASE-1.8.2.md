# AzureDeck 1.8.2

## Launches and Discord results

Creating a process no longer counts as a successful launch. Each queued account waits for a responsive client window and a new Roblox engine log containing the requested account and place followed by a connection/replication record. Existing logs and logs for other accounts cannot confirm a join. Ambiguous matches remain unconfirmed. This check is sequential, so later clients do not overlap the earlier client's startup verification.

The native “Failed to download or apply critical settings” dialog is detected by its Windows controls, including owned dialogs, without relying on OCR. Only that new failed process is closed. AzureDeck obtains a fresh ticket and retries after 3 and 6 seconds, for at most three attempts per launch request. Persistent network/settings errors remain failures; this cannot repair a Roblox service outage.

A live client without verifiable join evidence after 90 seconds remains open and is reported as **unconfirmed**. It is not counted as successful or automatically relaunched. Discord and the Instances page distinguish confirmed joins, failed accounts, unconfirmed accounts, and skipped accounts. Earlier successes are checked again at batch completion. Confirmation describes evidence observed during startup, not a guarantee that the connection remains live indefinitely.

## Monitoring and restoration

Prevent Minimization and Disconnect Detection apply and save immediately. Turning prevention on restores existing minimized managed windows without requesting focus, except accounts explicitly excluded. A timestamp check prevents delayed minimize notifications from duplicating restoration requests.

Detection suppresses automatic low-resource minimization; manually minimized windows stay minimized unless prevention is enabled. For clients launched in this app session, an account-matched log can detect a connection ending without screen capture. This includes deliberately leaving a game. A missing, changed, ambiguous or unsupported log cannot prove a connection. Recovered clients without a matched log require a visible window for OCR.

Screen inspection captures the full window so small graphics windows retain their dialog headings and buttons, scales small captures for OCR, and falls back to installed user-profile OCR languages when en-US is unavailable. English dialog recognition remains heuristic. Two corroborating checks are required; a suspected dialog gets a second check after two seconds, then normal interval polling resumes. Captures and log text are not uploaded or written into diagnostics.

**Check clients now** enables detection and schedules fresh checks. Expand **Current account inspections** to see the last attempt, total checks, screen attempts, last fresh screen, and availability/error details. A minimized window with no matched log is explicitly unavailable; an alive process or a popup-free capture never implies Connected.

## Compatibility and verification

Client log formats are not a stable Roblox API. The engine markers were cross-checked against the publicly maintained [Bloxstrap activity watcher](https://github.com/bloxstraplabs/bloxstrap/blob/main/Bloxstrap/Integrations/ActivityWatcher.cs). AzureDeck's implementation is independent and fails to unconfirmed when it cannot obtain the expected evidence. No Roblox binaries, memory, security protections, or private APIs were patched.

Regression checks use isolated synthetic logs/windows and disposable updater executables. Live authenticated multi-account joins and live Roblox disconnect screens still depend on Roblox, the network, installed OCR languages and Windows capture support; they were not exercised against the user's accounts.

Updates are published to [AzureDeck releases](https://github.com/marcellkristofbonczok-cmyk/AzureDeck-updates/releases). Install through **Settings > App updates > Check for updates > Download > Install and restart**. Existing sessions and settings stay in the app data directory.
