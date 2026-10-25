# AzureDeck 1.8.3 validation

Built on 2026-10-25 for Windows x64 using MSVC, C++20, /O2, static /MT, Windows SDK 10.0.26100.0, version resources and an embedded asInvoker manifest. The final complete PowerShell build succeeded. CMake version metadata was updated; CMake was not executed. Only the two existing unused tray-helper warnings remain in the hotkey test target.

- Core/integration: **428 passed, 0 failed**.
- ImGui/audio/scroll: **20 passed, 0 failed**.
- Native hotkey routing: **16 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **35 passed, 0 failed**.
- Native window sizing: **2 passed, 0 failed**.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Total regression checks: **506 passed, 0 failed**.

New coverage uses a loopback HTTP server to seed a shared WinHTTP cookie cache, then verifies that isolated account requests send only their explicitly supplied cookie and an anonymous request sends none. Identity checks reject wrong accounts, expired sessions and malformed responses before launch-ticket creation. Clipboard tests verify portable settings/preferences round trips, preservation of private local fields, and rejection of malformed, unsupported or invalid configuration values. Settings save successfully with the account worker deliberately blocked. Discord drafts save without requiring a connection.

Native window fixtures verify that ordinary optimization preserves position and dimensions, while explicit resizing reduces dimensions without moving the window. Existing monitor fixtures verify minimized restoration, exclusions, fresh captures, potato-size OCR and minimized log detection. The updater test preserves a synthetic vault and verifies replacement, backup and restart using disposable executables.

Settings and account pages were rendered with synthetic data at 100% and 150% scaling; config controls and removal of manual settings-save buttons were visually checked. A separate read-only verification of existing account sessions succeeded using the corrected HTTP implementation. It did not launch game clients, request launch tickets, alter account sessions or display credentials.

Final executable: 2,333,696 bytes; version 1.8.3.0.
SHA-256: ddd54ebca7887b629c25ff2bc92aa1caea35a819bc0c5643390bce79faa53600

Live multi-account game launches were not performed. Roblox client behavior, service availability, server access and Windows capture/OCR remain external dependencies. Wrong identities are blocked, unverifiable joins remain unconfirmed, and existing live clients are preserved by ordinary Launch. See docs/RELEASE-1.8.3.md.