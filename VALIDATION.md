# AzureDeck 1.9.4 validation

Built and checked on 2026-10-26 for Windows x64 with MSVC C++20, /O2, static /MT, Windows SDK, version resources, application icon and an asInvoker manifest. The complete final PowerShell build succeeded and propagated test exit status. Two existing unused tray-helper warnings remain in the hotkey test target. CMake version metadata was updated; CMake was not executed.

- Core/integration: **454 passed, 0 failed**.
- ImGui/audio/scroll: **20 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **38 passed, 0 failed**.
- Native window sizing: **2 passed, 0 failed**.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Total regression checks: **535 passed, 0 failed**.

The native probe recognized real rendered fixture dialogs for 769, 278 and 267, as well as existing codes. It exercised covered-window capture, resizing, minimized behavior, restoration exclusions, independent account tracking, consecutive-frame confirmation, incident clearing, worker shutdown and account-matched minimized logs. OCR reading the 769 OK action as 0k was reproduced and corrected. Apartment teardown followed by a new capture worker no longer caused the reproduced access violation.

Initial capture checks on Codex's isolated sandbox desktop returned a zero-sized target or invalid-state HRESULT. The final optimized native checks above ran on the normal interactive desktop and all passed. An intermediate expanded probe exposed the 769 OCR failure before it was fixed. These earlier failures are not counted as successful checks.

Added coverage verifies log association after a teleport changes place, rejection of foreign account identity, batches with twelve new logs, native-profile rejection evidence and rejection of creator/foreign-host lookalikes, transient verification errors, independently varying bounded Anti-AFK times, launch pacing, readable automatic window sizes, and generic-incident error-code enrichment. Existing cookie isolation, encrypted persistence, clipboard/session transfer, Discord and updater checks remain passing.

A separate read-only check matched all ten saved session identities against Roblox. It displayed no credentials, requested no launch tickets and launched no game clients. This confirms the manager's saved sessions at check time; it does not certify native Roblox Home authentication. The Monitoring page was rendered with isolated synthetic app data and visually inspected at 1260x940; the detection-off message, controls, minimum-size note and version label are readable.

Final executable: **2,429,952 bytes**, version **1.9.4.0**.
SHA-256: **3d6d8b9ad5cde906e84d86f80deb28d177cd86f0b27e3b1e732fdafef7019b38**.

Live multi-account launches, in-experience Anti-AFK effectiveness and real server teleports were not tested. The reported ten-client native Home logout is not proven fixed: this version supplies safer ticket replacement, launch pacing, native-session warnings and bounded recovery. Windows capture/OCR requires usable visible rendering or matched log evidence. Detection and per-account recovery remain opt-in. The full three-minute cleanup and WebView2 probes were not rerun because those systems were not changed.

See docs/RELEASE-1.9.4.md. Historical 1.8.3 results are preserved in docs/VALIDATION-1.8.3.md; the 1.9.3 import report is historical as well.