# AzureDeck 2.0.0 validation

Checked on 2026-10-27, Windows x64, MSVC C++20 /O2 /MT, Windows SDK, embedded version 2.0.0.0/icon/asInvoker manifest. The full PowerShell build passed. Final shared-file guards and diagnostic-parent bookkeeping were rebuilt/relinked; the complete core suite passed again against that final executable. CMake is maintained but was not executed. Nonfatal existing shadow/unused-helper warnings remain.

- Core/integration: **650 passed, 0 failed** (35 new coordinator/restart/concurrency checks plus the prior 615 checks; final total is taken from the executable's report).
- ImGui/audio/layout: **29 passed**.
- Native hotkeys: **16 passed**.
- Legacy native startup lineage: **8 passed**.
- Disposable clean-root compatibility: **14 passed**; production recovery does not delete that root.
- Modern installer UI/autoclose: **17 passed**.
- Launcher job/URI/native-maintenance probe: **26 passed**.
- Installer trust/cancellation compatibility: **3 passed**.
- Native startup/capture/OCR/restoration/log monitoring: **41 passed**.
- Native updater replacement/restart: **5 passed**.
- Installed Bloxstrap executable/managed bundle read-only checks: **2 passed**.
- Total regression/native/metadata checks: **811 passed**.
- Final UI previews: **8 passed**, Accounts and Launch & recovery at 100%/150% text, wide/narrow layouts and scrolling.
- Public production and configured-channel version endpoints were also verified with read-only requests; no account credentials or installer execution.

The launch executor tests admit fifty requests, enforce keyed duplicate ownership and a four-worker bound, release ownership before future readiness, survive exceptions, adapt admission after confirmed joins/failure/pressure, and drain cancellation even while paused. Actual Manager integration dispatches fifty synthetic accounts exactly once, preserves the other 49 after one expired account, clears terminal intents, excludes secrets/raw account errors from structured diagnostics, and keeps account commands responsive.

Restart integration merges encrypted queue/single-launch checkpoints, resumes eligible work automatically, excludes exhausted attempts and completed tombstones, prevents a second restart replay, and preserves malformed input without execution. Concurrent Manager tests reject deletion/duplicate launch while a launch is held and prevent FPS/graphics writes from racing the native creation/maintenance gate. Existing crash/Unknown watchdog, group, config clipboard, Discord, session-isolation and deployment/discovery tests remain passing. Expired authentication errors no longer consume generic startup retries.

The prior native job/UI probes still verify helper handoffs, unique Player adoption, account/private-server URI encoding, fatal dialog closure, pending job tracking, cancellation/timeout late-child cleanup and unrelated-process protection. Native window monitoring exercises only controlled windows, capture, OCR and restoration. The updater probe replaces/restarts copied fixture executables and preserves a synthetic vault sentinel.

Executable: **2,811,392 bytes**, resource version **2.0.0.0**. SHA-256: **1e37ac3097b8dafb3a86e5e9bc1cee46faf9561781b7004ba810d151551d97aa**.

No real Roblox account, real installer/update/reinstall, real-player termination, live private-server join or live Discord delivery was exercised. Fifty real games and their CPU/RAM/GPU consumption were not benchmarked. Roblox Home authentication at high account counts remains unproven fixed. Direct launch does not bypass required updates; offline deployment checks cannot prove compatibility. Safe maintenance remains explicitly queued while active sessions/writers continue indefinitely. Windows security and account/server access requirements remain external limitations.

Evidence retained privately under work/: build-v2.0.0-final.log, relink-v2.0.0-verified.log, window-monitor-v2.0.0.log, updater-restart-v2.0.0.log, bloxstrap-installed-v2.0.0.log and ui-v2.0.0-final.log. Local installation/channel inspection snapshots are not packaged or published. No vaults, sessions, cookies, bot tokens, browser profiles, raw test logs or machine-local data enter the source/distribution artifacts. See docs/RELEASE-2.0.0.md and docs/V2-REQUIREMENTS.md for coverage and platform limits.
