# AzureDeck 2.0.1 validation

Checked on 2026-10-27, Windows x64, MSVC C++20 /O2 /MT, Windows SDK, embedded 2.0.1.0 version/icon/asInvoker manifest. The PowerShell pipeline compiled the application and test/probe targets. Native testing caught a Studio console-host completion bug, which was fixed and its launcher probe rerun successfully. Final deployment inventory invalidation changes were rebuilt; all application/test/probe targets were relinked and the complete core suite passed against the final executable. CMake is maintained but was not executed. Existing nonfatal shadow/unused-helper warnings remain.

- Core/integration: **708 passed, 0 failed** (58 more than 2.0.0).
- ImGui/audio/layout: **29 passed**.
- Native hotkeys: **16 passed**.
- Native startup lineage: **8 passed**.
- Disposable clean-root compatibility: **14 passed**; production does not delete this root.
- Modern installer UI/autoclose: **17 passed**.
- Launcher jobs/URI/maintenance/Studio/wrong-installation probe: **30 passed**.
- Installer trust/cancellation compatibility: **3 passed**.
- Native capture/OCR/disconnect/restoration/log monitoring: **41 passed**.
- Native updater replacement/restart: **5 passed**.
- Installed Bloxstrap executable/Player bundle read-only inspection: **2 passed**.
- Actual native/Bloxstrap reference/deployment inspection: **2 passed**, read-only.
- Total regression/native/inspection checks: **875 passed**.
- Final UI previews: **8 passed**, Accounts and Launch & recovery at 100%/150% text, wide/narrow layouts and scrolling.

Controlled recovery tests verify three identical failures stop one account while the next runs, detailed retry reasons/counts/delays, zero-attempt dependency waits, automatic live resume, cancellation of already-saved intents, persisted budgets for started timeouts, and bounded maintenance replay. The actual Manager repair future is exercised with synthetic repair/launch callbacks and a real test-owned compatibility mutex: queued maintenance keeps it, fatal update proceeds to reinstall, validation clears protection, compatibility restores, then affected launches resume. The one-time repair-strategy migration retains the fatal latch and cannot reset again on app restart.

Deployment tests compare complete GUID/full executable versions and launcher references rather than timestamps; cover ahead-of-metadata references, CDN/origin conflicts, malformed/partial/ambiguous bundles, offline limits and fresh inventory/reference invalidation. Synthetic metadata files plus retained idle children exercise actual Manager cohort decisions with an explicit test image resolver: equivalent references keep the pin, genuine incompatible updates defer new starts, channel conflicts preserve healthy clients, and idle cohorts refresh. New identity-matched engine logs record different account channels; creator output cannot forge them. Observations survive restart. Diagnostic export includes a bounded field whitelist and excludes injected synthetic secret fields. File settling is bounded/cancellable and does not initiate installers.

Native job tests retain helper handoffs, unique Player adoption, URI/private-server encoding, fatal-dialog closure, cancellation/timeout cleanup and unrelated-process protection. New cases leave a Studio installer running without blocking Player maintenance and immediately close/reject only the owned Player from the wrong installation. Genuine system console hosts are ignored as bookkeeping while actual writers remain tracked. The updater fixture replaces/restarts copied test executables, verifies its backup and preserves a synthetic vault sentinel.

Executable: **2,879,488 bytes**, resource version **2.0.1.0**. SHA-256: **cce85b1d2d8f59e33a68f17484c183bcb211f30f2838b9ede1d92e8b19131c1c**.

No real Roblox account, actual installer/update/reinstall, real-player termination, live private-server join or live Discord delivery was exercised. Fifty-account tests are synthetic; real fifty-game CPU/RAM/GPU behavior and the earlier Roblox Home logout issue remain unproven fixed. Roblox may enforce updates/end sessions. No stable supported API predicting every account's future prelaunch A/B channel assignment was verified; actual channel observations require identity-matched engine evidence. Complete-bundle/metadata checks cannot prove every asset or guarantee future server compatibility. Offline/ahead-of-metadata references carry explicit uncertainty. Safe maintenance can wait while healthy sessions or genuine external writers remain active; Windows security/permission constraints are not bypassed.

Evidence retained privately under work/: build-v2.0.1-selection-verified.log, relink-selection-201-verified.log, probe-selection-verified-201.log, window-monitor-v2.0.1.log, updater-restart-v2.0.1.log, bloxstrap-installed-v2.0.1.log, deployment-inspection-v2.0.1.log and ui-v2.0.1-final.log. Raw local snapshots, logs, account vaults, sessions, cookies, bot tokens and browser profiles are excluded from source/distribution packages and publication. See docs/RELEASE-2.0.1.md and CONTINUATION.md.
