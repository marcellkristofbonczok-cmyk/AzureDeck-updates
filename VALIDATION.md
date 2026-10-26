# AzureDeck 1.9.6 validation

Built and checked on 2026-10-26 for Windows x64 using MSVC C++20, /O2, static /MT, Windows SDK, version resources, application icon and asInvoker manifest. The full build and all compiled suites passed. A final UI-only numeric-label adjustment was rebuilt successfully and the final executable was checked with the layout previews. CMake version metadata was updated; CMake was not executed. Only the two existing unused tray-helper warnings remain in the hotkey target.

- Core/integration: **518 passed, 0 failed**.
- ImGui/audio/scroll/layout: **24 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **41 passed, 0 failed**.
- Native window sizing: **2 passed, 0 failed**.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Total compiled/native checks: **606 passed, 0 failed**.

The group tests cover automatic legacy migration, case-insensitive deduplication, additive memberships, preserving existing selectors, idempotent additions, named removal, rename/delete without losing other memberships, validation-before-write, concurrent field edits and persistence after reopening. A fixture stores 300 memberships for one account and more than 300 catalog groups, beyond the former 256-group limit. Account sessions are synthetic and no live Roblox joins occur.

Configuration tests compare every settings key and every portable preference through schema-2 export/import, retain schema-1 compatibility, reject invalid FPS/ranges/unknown credential fields before application, and persist an import into a second empty encrypted device profile before reopening it. Native Windows clipboard tests verify owner-window writes, Unicode readback and a 150,000-character payload beyond the old 128 KB ceiling. Unterminated text is rejected using allocation bounds. Clipboard tests run on the isolated test desktop, not the user's interactive clipboard. The export intentionally includes private URLs but no account sessions or bot sign-in.

ImGui geometry tests exercise buttons, switches, checkboxes, inputs and combos in a narrow panel at 100% and 150% text scale. Long labels wrap into taller controls. Final app previews use 18 synthetic accounts across all 13 navigation pages and the group manager at 1000x700 at both scales. The 28 page cases assert padded content bounds and native HTCLIENT hit testing over the scrollbar; the two Settings wheel cases verify actual scrolling to lower content. The Accounts Add account bounds are checked explicitly. Default-size Accounts previews are checked separately. Screenshots of account/group/settings layouts were visually reviewed. Extra bottom space and nested wheel chaining remain enabled.

Native capture/OCR/window checks use disposable rendered windows on the normal Windows desktop because capture is unavailable on the sandbox desktop. They cover error codes 769/278/267, minimized matched-log detection, targeted inspection and restoration. The updater verifies replacement, previous-binary backup, restart and preservation of separate synthetic encrypted data. No real Discord messages were sent.

Final executable: **2,586,112 bytes**, version **1.9.6.0**.
SHA-256: **9215917a7c9518d955c69f467a5bb26be2cc78f609fd197c27d4df772c5fa231**.

Live Discord delivery, actual channel permissions, real browser sign-in, in-game Anti-AFK effectiveness and live multi-account joins were not exercised. The existing ten-client native Roblox Home logout remains unproven fixed. WebView2 and the full three-minute cleanup probe were not rerun because their implementations were not changed. Configuration transfer deliberately excludes account metadata/group memberships and bot sign-in; use the existing metadata/session tools separately. Layouts require matching account IDs on the destination device.

Local logs relative to the original workspace: work/build-v1.9.6-release-final.log, work/build-v1.9.6-ui-final.log, work/ui-v1.9.6-final.log, work/window-monitor-v1.9.6.log, work/window-sizing-v1.9.6.log and work/updater-restart-v1.9.6.log. Raw logs, test profiles and screenshots are excluded from source/release archives. Historical validation remains in docs/VALIDATION-1.9.5.md. See docs/RELEASE-1.9.6.md for user-facing behavior.
