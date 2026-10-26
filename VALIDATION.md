# AzureDeck 1.9.7 validation

Built and checked on 2026-10-26 for Windows x64 using MSVC C++20, /O2, static /MT, Windows SDK, version resources, application icon and asInvoker manifest. The complete build and compiled suites passed. The final UI padding/label adjustment was rebuilt successfully and all final preview cases use that exact executable. CMake metadata was updated; CMake was not executed. Only the two existing unused tray-helper warnings remain in the hotkey target.

- Core/integration: **518 passed, 0 failed**.
- ImGui/audio/scroll/layout: **29 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Total compiled/native checks executed for this release: **568 passed, 0 failed**.
- Final app previews/interactions: **42 passed**.

The new widget checks verify clicking a membership row to add/remove, disabled-row behavior, and room for the aligned name/ID block at 100% and 150% text scale. Existing custom button, slider, checkbox, combo, animation, audio and scrolling checks remain passing. Existing group migration, additive membership, named removal, unrelated-membership preservation, atomic validation and encrypted persistence tests remain in the core suite.

The final app uses 18 synthetic accounts in isolated encrypted data directories. At both 100% and 150% scale, previews exercise all nine Settings categories and group management at 1000x700, scrolling through Launch & recovery, Window monitoring and Data & config, clicking the first membership twice to remove then re-add just Farm while retaining Trading, and clicking the modal header X. The main-library selection is checked after the group interactions and stays unchanged. General, Launch & recovery, Data & config, group management and Accounts also render at 1260x940 at each scale. Bounds checks keep editors, group rows, list and footer within the window; native hit testing remains HTCLIENT inside the content area. Screenshots of the final small and wide layouts and aligned group rows were visually reviewed.

A source review against the prior packaged source confirms all 38 prior toggle/numeric Settings fields plus destination/default-group/webhook/default-page controls, monitoring, hotkeys, config transfer, update and backup actions remain reachable. The normal Settings root has no extra outer scrolling canvas; each category editor handles its own scrolling. Configuration clipboard behavior and all automatic saving/storage implementations are retained.

The native updater fixture verifies replacement by a strictly newer payload, previous-binary backup, restart, paths with spaces and preservation of separate synthetic account data. No real Roblox client or account is started by that fixture.

Final executable: **2,604,032 bytes**, version **1.9.7.0**.
SHA-256: **ce965fe6915223c44fe260ac5f79b73977c84a835e45798a6e8b0cf5bdcce5cd**.

Live Discord delivery, actual channel permissions, real browser sign-in, in-game Anti-AFK and live multi-account joins were not exercised. The existing ten-client native Roblox Home logout remains unproven fixed. Window capture/OCR/restoration, window sizing, WebView2 and the three-minute cleanup probes were not rerun because their implementations were not changed. The separate 41 monitoring and two sizing checks last passed in 1.9.6; see docs/VALIDATION-1.9.6.md. Those prior counts are not included above.

Local logs relative to the original workspace: work/build-v1.9.7.log, work/build-v1.9.7-ui-final.log, work/ui-v1.9.7-final.log and work/updater-restart-v1.9.7.log. Raw logs, synthetic test data and screenshots are excluded from source/release archives. Smoke page/action instructions are in CONTINUATION.md. See docs/RELEASE-1.9.7.md for user-facing changes.
