# AzureDeck 1.9.10 validation

Built and checked on 2026-10-26 for Windows x64 with MSVC C++20, /O2, static /MT, Windows SDK, version resources, icon and asInvoker manifest. The complete PowerShell build passed. CMake targets were updated but CMake was not executed. Nonfatal warnings remain for existing unused tray helpers and repair-module/test local-variable shadowing.

- Core/integration: **574 passed, 0 failed**.
- ImGui/audio/scroll/layout: **29 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Native installer/player process-tree startup probe: **9 passed, 0 failed**.
- Native full-root cleanup probe: **14 passed, 0 failed**.
- Native repair trust/cancellation probe: **3 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **41 passed, 0 failed**.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Official Roblox download/signature verification: **1 passed; installer not executed**.
- Total compiled/native/download checks: **692 passed**.
- Final installation-recovery UI previews: **8 passed**, at 100%/150% text scales and wide/narrow layouts including editor wheel scrolling.

Startup tests verify that helper presence does not immediately fail a new/live player, a live player receives the full timeout, matching join evidence wins, a persistent exited handoff needs startup/exit/helper grace, and helper name alone cannot fail a live player even at timeout. A real disposable process fixture retains its exited parent, waits at least 15 seconds before classifying its installer child, rejects unsigned hidden-helper preflight classification, and confirms a replacement Beta player child from fresh matching account/place replication logs despite a sibling installer helper. No Roblox binary is used in those fixtures.

Cleanup tests operate only under a new disposable temporary tree. They reject parent/wrong-child/traversal targets and protected-data overlap, preserve files when cancelled before deletion, stop on a held file lock, delete read-only files and synthetic Studio installation files, remove nested junctions without following outside targets, preserve a sibling synthetic vault, reject a root junction, and handle an already missing root. External and vault sentinels are verified afterwards. Production uses Windows' native LocalAppData known folder and protects the manager executable/data paths.

Injected Manager operations cover one persistent clean-reinstall budget, no elapsed-time-only retry, healthy-join/cooldown gating, manual retry, fail-closed state writes, shared concurrent repair, responsive status commands, queue rebuilding/counts, cancellation and multi-instance release/restoration. Tests inject recovery/native launch callbacks; they do not execute production cleanup or a real installer. Final selected queue outcomes replace pre-repair counts.

Final executable: **2,717,184 bytes**, version **1.9.10.0**. SHA-256: **77e6268a5681e1347180f6979f9beed2b7af8841c2122ec9256d0942ed6085db**.

The real %LOCALAPPDATA%\Roblox folder was NOT deleted, real players were NOT closed by repair, and the official installer was NOT executed during validation. Actual installer UI, connectivity, live account joins and platform policies remain environment dependencies. Full production cleanup intentionally includes Studio and all other local data inside that exact folder; Player alone is reinstalled. Cancel cannot restore removed files. The ten-client native Roblox Home logout remains unproven fixed. Live Discord delivery, real browser sign-in and in-game Anti-AFK were not exercised.

Local evidence relative to the original workspace: work/build-v1.9.10-tests.log, work/window-monitor-v1.9.10.log, work/updater-restart-v1.9.10.log, work/repair-download-v1.9.10.log and work/ui-v1.9.10.log. Raw logs, downloaded installers, local fixtures, account data and screenshots are excluded from source/release archives. Read CONTINUATION.md and docs/RELEASE-1.9.10.md.
