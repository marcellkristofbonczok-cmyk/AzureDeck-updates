# AzureDeck 1.9.12 validation

Checked on 2026-10-26 for Windows x64 using MSVC C++20, /O2, static /MT, Windows SDK, embedded version/icon and asInvoker manifest. A full PowerShell build passed; final platform/main/bootstrapper-fixture changes were rebuilt and all targets relinked and checked. The final Manager identity/expected-exit ordering was then rebuilt/relinked and its core integration suite passed again. CMake was updated but not executed. Nonfatal warnings remain for unused tray helpers and a test-local shadowed variable.

- Core/integration: **579 passed, 0 failed**.
- ImGui/audio/scroll/layout: **29 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Legacy native startup lineage: **8 passed, 0 failed**.
- Disposable clean-root compatibility probe: **14 passed, 0 failed** (production no longer calls folder deletion).
- Modern installer UI/autoclose: **17 passed, 0 failed**.
- New offline Bloxstrap/job/URI probe: **25 passed, 0 failed**.
- Compatibility download trust/cancellation: **3 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **41 passed, 0 failed**.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Installed Bloxstrap executable and managed Player bundle inspection: **2 passed**, read-only; no program executed.
- Official Bloxstrap release artifact digest/version verification: **1 passed**, download only; no program executed.
- Total final regression/inspection/artifact checks: **740 passed**.
- Final Bloxstrap recovery UI previews: **8 passed**, covering 100%/150% text scales, wide/narrow editors and wheel scrolling.

The Bloxstrap probe creates disposable fake bootstrapper/player executables in a unique temporary tree. It exercises escaped tickets, public/private/specific-instance destinations, one intact Windows argument, no-launch preparation, adopting a player while its parent stays open, helper handoff after root exit, account/place log confirmation, nonzero exit codes, modern critical/exception/connectivity dialogs, cancellation, duplicate-launch blocking, late-child cleanup, healthy timeout completion, pending-work compatibility pause/release, multiple-child rejection and protection of unrelated clients. An unrelated synthetic stock installer cannot pause the new Bloxstrap flow. The first fixture exposed a child-enumeration race; the final implementation requires a unique stable player before adoption and its final checks pass.

Core tests verify migration from the retired native-installer latch/budget, persistence of new Bloxstrap failures, update-then-force recovery limits, cancellation, queue rebuilding/counts, concurrent recovery, responsive status commands, portable config and existing account/group behavior. TestManager explicitly disables real native launch and repair unless callbacks are injected. No real session is used for game launches.

The supported interface was checked against official Bloxstrap 2.11.4 source. The official Bloxstrap-v2.11.4.exe was downloaded into work/ only: 12,589,224 bytes; Windows ProductName Bloxstrap; file version 2.11.4; SHA-256 9ad7758093a356fe5bd9d49911aaacf766dbb9289b6f3662a8ed3242230f46b2, matching its GitHub release asset digest. The actual installed Bloxstrap launcher and its managed bundle were inspected read-only after installation became available. This task did not run or install that reference executable. The reference is excluded from release/source packages.

Final AzureDeck executable: **2,705,920 bytes**, version **1.9.12.0**. SHA-256: **eff2ae9da6de8ae8fae78947a1930767bc7ef7c8cc649c3c91bff75b69d0608a**.

No real Bloxstrap/Roblox installer, game launch, update, reinstall, private-server join or real-player termination was exercised during validation. Actual account access, connectivity, platform behavior and future Bloxstrap compatibility remain live-environment dependencies. Bloxstrap itself can close older clients when updating; Manager tracks expected exits during its operations and rebuilds selected work. AzureDeck does not perform the former whole-folder Roblox deletion. The ten-client native Home logout is not proven fixed. Live Discord delivery, real browser sign-in and in-game Anti-AFK remain unverified. Bloxstrap's own integrations/activity tracking control additional launcher overhead.

Evidence relative to the workspace: work/build-v1.9.12-final.log, work/relink-v1.9.12-verified.log, work/manager-v1.9.12-verified.log, work/window-monitor-v1.9.12.log, work/updater-restart-v1.9.12.log, work/bloxstrap-installed-v1.9.12-final.log, work/bloxstrap-reference-verification.json and work/ui-v1.9.12.log. Raw fixtures/logs/screenshots, third-party reference executables and all local account/session data are excluded from packages. Read docs/RELEASE-1.9.12.md and CONTINUATION.md.
