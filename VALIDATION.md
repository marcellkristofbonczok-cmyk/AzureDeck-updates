# AzureDeck 1.8.2 validation

Built on 2026-10-25 for Windows x64 using MSVC, C++20, /O2, static /MT, Windows SDK 10.0.26100.0, version resources and the embedded asInvoker manifest. Application and all test/probe targets compiled. CMake version metadata was updated but CMake was not executed. The two pre-existing unused tray-helper warnings remain in the standalone hotkey tests.

- Core/integration: **408 passed, 0 failed**.
- ImGui/audio/scroll: **20 passed, 0 failed**.
- Native hotkey registration/routing: **16 passed, 0 failed**.
- Native startup, capture/OCR, minimization and log fallback: **35 passed, 0 failed**.
- Native executable replacement/restart: **5 passed, 0 failed**.
- Total: **484 passed, 0 failed**.

The first native run exposed a delayed-minimize-event race. The restoration logic was corrected, and the complete native probe passed on the final build. A Windows macro collision in a probe variable was corrected; test-target compilation resumed successfully with the same final application/object files. The cancellation expectation now asserts that a skipped account cannot produce an all-success result.

New regression coverage includes account/place log identity, stale logs, partial records, creator text, ambiguity, truncation, connection transitions, native critical-settings failure detection, false-success prevention, cancellation, 640x360 OCR, restoration without focus, per-account exclusions, rapid minimize events, and minimized log detection with zero screen captures. Immediate monitoring settings were tested with a blocked command worker and an older queued settings save.

Monitoring and account pages were rendered with 100 synthetic accounts at 100% and 150% UI scaling. No account data was included in the preview. The updater probe used disposable old/new executables, preserved a synthetic vault sentinel, and verified backup, replacement, restart, and paths containing spaces.

Final executable: 2,301,952 bytes, version 1.8.2.0.
SHA-256: 8df208404bab01665347ee8da7819a517a7820d6b298fea4dd653ee9e517198a

Live authenticated Roblox launches and real disconnect dialogs were not exercised against the user's accounts. Roblox log formats, network behavior, Windows capture support and installed OCR languages remain external dependencies. Missing verification evidence is reported as unconfirmed, never success. See docs/RELEASE-1.8.2.md.