# AzureDeck 1.9.11 validation

Checked on 2026-10-26 for Windows x64 using MSVC C++20, /O2, static /MT, Windows SDK, embedded version/icon and asInvoker manifest. The full PowerShell build passed; changed platform/manager/main/core-test units were then rebuilt and every executable relinked for the final update-first sequence, followed by the final checks below. CMake targets were updated but CMake was not executed. Nonfatal warnings remain for unused tray helpers and local-variable shadowing.

- Core/integration: **577 passed, 0 failed**.
- ImGui/audio/scroll/layout: **29 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Native installer/player startup process-tree probe: **9 passed, 0 failed**.
- Native full-root cleanup probe: **14 passed, 0 failed**.
- Native modern installer dialog/autoclose probe: **17 passed, 0 failed**.
- Native repair trust/cancellation probe: **3 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **41 passed, 0 failed**.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Total final compiled/native checks: **711 passed**.
- Final installation-recovery UI previews: **8 passed**, covering 100%/150% text scales and wide/narrow editors, including wheel scrolling.

The new native probe creates real modern TaskDialogs in disposable child processes, including one executable with a temporary bootstrap filename. It verifies the exact reported critical message, a fatal heading, nonfatal update text, failure under the old Static-only reader, process isolation, healthy progress, graceful acknowledgement/exit, and a stubborn dialog that refuses normal closure. The stubborn fixture is terminated automatically after the test's shortened grace interval; its exit code proves the forced-closure path. An unrelated healthy updater remains open, unconfirmed failures cannot trigger closure, and cancellation preserves the healthy process. No real Roblox installer is started or closed.

Core/Manager tests cover a fatal error completing the launch future and clearing repairRunning, a visible/persisted failure reason, concurrent requests sharing one repair, responsive status commands, update-first then clean-reinstall escalation, the case where an update completes but its client retry still fails, cancellation, queue rebuilding and final counts, persistence failures, two-phase retry budgets and healthy/cooldown gating. A failed update and clean reinstall cannot trigger a third attempt. Recovery/launch callbacks are injected, so these checks do not execute production installers or delete real installation data.

The temporary cleanup fixture covers exact-path restrictions, traversal/protected-data rejection, cancellation before deletion, locked files, read-only files, synthetic Studio files, root/nested junctions, external and sibling vault sentinels, and absent-root no-op behavior. Native startup tests preserve the 15-second exited handoff grace and confirm unique replacement players using new matching logs. Window-monitor regression covers disconnect codes and restoration/minimized-client behavior.

Final executable: **2,735,104 bytes**, version **1.9.11.0**. SHA-256: **0546a1fe884bcca1ba2263a9b9860d2982aaaf7b725e51fc9bb70a105be0829b**.

Real %LOCALAPPDATA%\Roblox was NOT deleted; real Roblox installers/players were NOT executed or closed during validation. Actual update/reinstall success, internet conditions and live account joins remain environment dependencies. The official download/publisher check passed in 1.9.10 without executing the installer; the unchanged download routine was not downloaded again for this release. Healthy installers are not force-terminated. Confirmed fatal installers may be terminated after graceful closure fails, as requested. Full clean reinstall still deletes Studio/local data and reinstalls Player only. The ten-client Home logout, live Discord delivery, real sign-in and in-game Anti-AFK remain unverified.

Evidence relative to the original workspace: work/build-v1.9.11-final.log, work/relink-sequence-v1.9.11.log, work/window-monitor-v1.9.11.log, work/updater-restart-v1.9.11.log and work/ui-v1.9.11.log. Raw logs, fixture data, screenshots and local account data are excluded from packages. See docs/RELEASE-1.9.11.md and CONTINUATION.md.
