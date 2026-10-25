AzureDeck 1.8.2 fixes multi-account startup reporting and monitoring.

- Wait for account-matched server-join evidence before advancing the launch queue; show confirmed, failed, unconfirmed and skipped counts in Discord and the app.
- Detect critical-settings errors and retry only the failed new client, with fresh tickets and bounded backoff. Unverified live clients remain open.
- Apply monitoring switches immediately and restore already-minimized managed windows when Prevent Minimization is enabled, respecting exclusions.
- Fix duplicate restoration caused by delayed minimize events.
- Improve small-window OCR, use matched client logs for minimized disconnects, and show inspection/capture counters plus Check clients now.

Roblox network outages cannot be repaired by the manager. Unsupported log formats remain unconfirmed rather than being reported as successful. Install through Settings > App updates; account data is preserved.