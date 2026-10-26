# AzureDeck 1.9.8 validation

Built and checked on 2026-10-26 for Windows x64 with MSVC C++20, /O2, static /MT, Windows SDK, version resources, application icon and an asInvoker manifest. The complete final PowerShell build passed. CMake was updated but not executed. Only the two existing unused tray-helper warnings remain in the hotkey target.

- Core/integration: **539 passed, 0 failed**.
- ImGui/audio/scroll/layout: **29 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Native installer process-tree probe: **6 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **41 passed, 0 failed** on repeat.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Total final executed compiled/native checks: **636 passed, 0 failed**.
- Final installation-protection UI previews: **8 passed**.

Installation tests cover newest complete version selection over stale registration, equal-version registry preference, partial/missing bundle rejection, direct/grandchild installer lineage, unrelated processes, creation-time checks, reused root PIDs, children created after root exit and unknown identities. The persistent latch blocks before player discovery or account authentication, survives restart and fails closed on corrupt state. A three-account synthetic batch with retry limit five stops after one nonretryable result, preserves two unattempted accounts in memory/on disk, and remains paused. Repeating it returns promptly instead of hanging behind that automatic pause. No real Roblox ticket or client is used.

The native installer probe copies its own disposable executable to RobloxPlayerInstaller.exe, starts it through a synthetic parent that exits, and verifies that retained process identity still associates the child. Startup reports an installation problem rather than a successful join or generic player exit. Global preflight sees the open installer; recheck cannot clear a latched failure while it runs. The fixture exits naturally. No real installer is started or terminated.

Native monitoring regressions verify critical-settings dialogs, startup join evidence, 769/278/267 OCR, capture, targeted inspections, restoration and minimized account-matched logs. An initial run passed 40/41 but failed the foreground-preservation observation on the active desktop; the complete repeat passed 41/41 without changes to the restoration code. Final counts above use that repeat. The updater fixture verifies replacement, previous-binary backup, restart and independent synthetic account data.

Final app previews use isolated encrypted fixtures with 18 synthetic accounts and a latched installation reason. Launch & recovery and the blocked Accounts launch center render at 1260x940 at 100% and 150% scale. The installation editor also renders and scrolls at 1000x700 at both scales. Frame/editor bounds, native HTCLIENT hit testing and actual wheel scrolling pass. The final installation/recheck layouts were visually reviewed. The final UI executable hash matches the release payload.

Final executable: **2,627,072 bytes**, version **1.9.8.0**.
SHA-256: **9705e234b0f0dfb2db6bbcc683af112b9d7ffc14d02ae17055c2bee3906c37ee**.

The actual user's critical installer error was not reproduced by running a real installer or joining with a live account. These changes protect AzureDeck from repeated attempts and stale/incomplete local player selection; local checks do not prove every asset is intact, repair Roblox or bypass required Roblox updates. A remaining official-installer failure needs the repair/recheck workflow described in docs/RELEASE-1.9.8.md. Live Discord delivery, real browser sign-in, in-game Anti-AFK and live multi-account joins were not exercised. The ten-client native Roblox Home logout remains unproven fixed. WebView2 and the full cleanup probe were not rerun because their implementations were not changed.

Local evidence relative to the original workspace: work/build-v1.9.8-complete.log, work/ui-v1.9.8-final.log, work/window-monitor-v1.9.8-repeat.log and work/updater-restart-v1.9.8.log. Initial run: work/window-monitor-v1.9.8.log. Raw logs, fixture data and screenshots are excluded from source/release archives. Source/native-probe details are in CONTINUATION.md.
