# AzureDeck 2.0.1

Fixes recurring installer/recovery loops and deployment selection:
- Fresh launcher-reference, full Player-version and channel metadata validation before starts. Folder timestamps do not choose the build; active accounts retain a validated cohort. CDN/origin conflicts do not force channel churn or blind downgrades.
- Account-matched engine logs record observed channels. Incompatible account channels preserve healthy clients. Selection reasons now appear in structured diagnostics and Export diagnostic JSON.
- Fatal installer closure still requires real supported repair. Compatibility releases only for safe exclusive maintenance and restores before retrying accounts. Studio installers and genuine system console bookkeeping do not block Player maintenance.
- Shared dependency waits consume no account attempts and resume saved work automatically. Started timeouts retain their budget. Three identical startup failures stop that account, later accounts continue, and maintenance replay is bounded. Retry logs include the actual reason/count/delay.
- Wrong-installation Player handoffs are detected promptly. File settling avoids redundant reinstalls. Existing fatal guards receive one fresh bounded recovery episode during this upgrade, without silently clearing protection.

Existing account/group/browser/Discord/macros/graphics/config/UI features remain available. Update through Settings > App updates.

Validation uses synthetic accounts and controlled processes. No real installer or account launch was executed. Roblox can require updates/end sessions; healthy-session maintenance may wait for a safe idle period. Per-account channel assignment is observed when identity-matched logs expose it, and future server compatibility cannot be guaranteed. Read VALIDATION.md and docs/RELEASE-2.0.1.md.
