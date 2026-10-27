# AzureDeck 2.0.0 — Launch reliability overhaul

AzureDeck now coordinates single launches, batches and automatic rejoins through a bounded launch executor. Fifty queued synthetic accounts are covered by the integration suite. Native starts remain exclusive and at least five seconds apart; account-specific startup confirmation can overlap. Adaptive admission begins with one confirmation, grows after confirmed joins, and returns to one on failure or resource pressure. Settings allows a maximum of 1–4 overlapping confirmations, a launch interval and a bounded startup timeout.

Recoverable account failures use exponential backoff up to five minutes. Repeated identical failures stop; expired or mismatched sessions require local sign-in. A failed account does not stop unrelated accounts. Duplicate account ownership spans queueing, startup, retry and repair. Ordinary app/Discord commands use a separate worker. A global installation failure shares one background maintenance operation. If maintenance cannot recover, unattempted accounts remain encrypted and paused rather than all being reported as failed.

## Installation and maintenance

Roblox and Bloxstrap remain selectable with installation checks and icons. Deployment inspection reads the configured Roblox channel, checks Roblox's public client-version metadata, discovers complete installed bundles and refreshes expired/missing selections. Stock protocol registration is inspected for diagnostics; it is never executed as an arbitrary command. Offline metadata is recorded as unavailable, not proof that an installed client is current.

Validated direct Player launch is preferred. On Bloxstrap, idle preparation applies its supported updates/modifications before account ticket issuance; active clients reuse the validated bundle without another preparation pass. A bounded supported-launcher fallback is available for recoverable direct-start failures when no other client is active. No patching, injection, update suppression or security-prompt bypass is used. The Player can still require an update itself.

Maintenance pauses conflicting new launches and waits for active Roblox sessions and existing updater work to finish before changing shared installation files. It uses the supported official signed installer or Bloxstrap update/force-reinstall path, with a persistent two-phase budget. It does not delete the full Roblox folder. Healthy sessions are preserved, and affected accounts resume after successful maintenance. If sessions stay open indefinitely, maintenance deliberately remains queued with an explicit status. AzureDeck cannot promise seamless forced platform updates or coordinate another manager that independently writes the same files.

Installer monitoring uses process creation times and ancestry, retained handles and verified Roblox publisher identity. Correlated fatal installer dialogs close automatically; a name alone or another process's dialog is not permission to terminate it. New launches wait while tracked cancelled/timed-out jobs finish. Existing grace periods, helper handoffs, account-matched join logs and unique-player checks remain in place.

## Recovery and diagnostics

Unfinished queue and single-account destinations are encrypted locally and resume automatically after restart when enabled. Retry counts and completion records prevent restart replay of exhausted or completed work. A corrupt checkpoint is preserved without execution. Recovered live clients are kept; restoring multi-instance compatibility waits for a safe opportunity. This default can be changed in Settings > Launch & recovery.

Crash/Unknown recovery retains cancellation generations, grace periods, access-denial exclusions and per-incident limits. Backoff now increases across repeated crash recovery attempts; offline waits do not consume attempts. Settings, groups, browsers, avatars, graphics controls, macros, Discord commands, hotkeys and config transfer retain their existing UI and routes.

A bounded rotating `launch-diagnostics.jsonl` in AzureDeck's data directory records account IDs, actions/categories, selected executable/version/channel, process IDs/parents, durations, exit codes and attempts. Only explicit diagnostic fields are accepted: authentication data, passwords, raw command lines and private destinations are excluded. Normal encrypted workspace/guard data stays separate from public release artifacts.

## Evidence and limits

Read VALIDATION.md for final test counts and artifact hashes. Tests use synthetic accounts and controlled disposable processes. No real Roblox account, installer or update was executed. Fifty real games, real private-server access, live Discord delivery and the ten-client Roblox Home logout issue are not claimed verified. Hardware, Roblox deployment policy, authentication limits, server permissions and unavailable Windows privileges remain external constraints.

The source package includes build scripts, vendored dependencies, tests, continuation notes and this report. The GitHub distribution publishes only the tested executable, manifest and release notes through its existing workflow.
