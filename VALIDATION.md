# AzureDeck 1.9.13 validation

Checked on 2026-10-27 for Windows x64 with MSVC C++20, /O2, static /MT, Windows SDK and embedded version/icon/asInvoker manifest. The full PowerShell build passed. The final incident bookkeeping/access-denial changes were rebuilt and the core integration suite passed again. The icon lifecycle fix was compiled/relinked and its final UI previews verified. CMake was updated but not executed. Nonfatal warnings remain for unused tray helpers and a test-local shadowed variable.

- Core/integration: **615 passed, 0 failed** (including 28 launcher/policy checks and 8 real watchdog checks with synthetic callbacks).
- ImGui/audio/layout: **29 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Legacy native startup lineage: **8 passed, 0 failed**.
- Disposable clean-root compatibility probe: **14 passed, 0 failed**; not used by production recovery.
- Modern installer UI/autoclose: **17 passed, 0 failed**.
- Launcher process-job/URI/native-maintenance probe: **26 passed, 0 failed**.
- Installer trust/cancellation compatibility: **3 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **41 passed, 0 failed**.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Installed Bloxstrap executable and managed Player bundle inspection: **2 passed**, read-only.
- Total regression/native/inspection checks: **776 passed**.
- Final launcher-selector/icon/settings previews: **8 passed**, covering 100%/150% text scales, wide/narrow layouts and wheel scrolling.

Launcher tests validate the default Bloxstrap selection, backend/grace ranges, disabled/pending/stopped Unknown exclusions, persistence through grace, cancellation on health, stable-health reset, clock rollback, independent global crash/Unknown controls, retry caps and the legacy account gate. Disposable complete/incomplete native bundles exercise metadata discovery without execution. Both persistent guard files and budgets remain independent. Manager selection checks actual installed status and preserves the old value if unavailable.

Watchdog integration uses an owned idle child, synthetic saved account data, injected network availability and an injected rejoin callback. It verifies crash scheduling without legacy per-account opt-in, no offline attempt burn, exactly one saved-account rejoin, no duplicate next tick, Unknown scheduling, cancellation when healthy, a later independent incident and manual cancellation invalidation. TestManager disables real native operations. No authentication ticket or network account session is used.

The shared native job fixture checks official-installer maintenance mode with an auto-opened owned Home client: it closes that client and finishes rather than mistaking Home for a game join. Existing job tests retain helper handoffs, account/private/server URI encoding, unique-child stabilization, fatal dialogs, pending-work pause/release, timeouts, late-cancel cleanup and unrelated-process protection. Actual app icons were extracted as local data. Visual QA caught and fixed the missing GDI+ lifetime; final previews show the real installed Roblox/Bloxstrap icons.

Final executable: **2,739,712 bytes**, version **1.9.13.0**. SHA-256: **ea93c8b9d5cd56938e23fcadf40a2c620a4fed017e37e22bf9f85ac3e9e4a096**.

Neither real launcher, official installer, real-player termination, live account join, private-server access nor live Discord delivery was exercised. Actual platform/account/server behavior remains an environment dependency. Unknown monitoring may reflect capture limitations, so recovery has a grace, cooldown and per-incident cap. In-app stops/queue cancellation suppress recovery until an explicit launch. The ten-account Roblox Home login issue remains unproven fixed. No user sessions, cookies, tokens, browser profiles, raw fixtures or logs enter packages/publication.

Evidence: work/build-v1.9.13-final.log, work/manager-v1.9.13-final.log, work/ui-build-v1.9.13-final.log, work/window-monitor-v1.9.13.log, work/updater-restart-v1.9.13.log, work/bloxstrap-installed-v1.9.13.log and work/ui-v1.9.13-final.log, relative to the original workspace. See CONTINUATION.md and docs/RELEASE-1.9.13.md.
