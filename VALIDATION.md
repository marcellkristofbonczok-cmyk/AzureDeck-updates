# AzureDeck 1.9.5 validation

Built and checked on 2026-10-26 for Windows x64 using MSVC C++20, /O2, static /MT, Windows SDK, version resources, application icon and an asInvoker manifest. The complete final PowerShell build succeeded. Only the two existing unused tray-helper warnings remain in the hotkey target. CMake version metadata was updated; CMake was not executed.

- Core/integration: **507 passed, 0 failed**.
- ImGui/audio/scroll: **20 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **41 passed, 0 failed**.
- Native window sizing: **2 passed, 0 failed**.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Total: **591 passed, 0 failed**.

Remote-control coverage uses synthetic encrypted accounts, isolated data directories and the real Discord polling thread with a deterministic fake transport. No real bot token, Discord delivery, live game launch or account authentication is used. Tests cover account/group/all resolution, name collisions, quoted names/JSON, multi-target atomic membership, rename/delete and empty-group persistence, scoped recovery/destination changes, private-field rejection, validated settings/preferences, saved-destination launch queueing and cancellation, browser request queue consumption, paginated stable pickers, expiry and per-user isolation, UTF-8 embed limits, suppressed mentions, text fallback when embeds are denied, reply association/order and updating a pending card while the command worker is deliberately blocked. Existing owner/everyone authorization, bot/webhook/channel filtering and silent startup remain passing.

An intermediate run exposed a compatibility regression where unknown commands threw before returning their error result; it was corrected and the full suite above passed afterward. Earlier partial runs are not counted as release verification.

Desktop settings/preferences/account forms use field-only atomic saves and a three-way merge so unrelated remote edits do not overwrite local drafts, and local saves do not restore stale remote fields. Synthetic tests cover stale settings/preference snapshots and a local account edit deliberately queued behind a blocked worker while a remote group change commits. Patches merge against current values under storage locks; multi-account metadata failures leave all rows unchanged. The Manage groups dialog was rendered with synthetic accounts at 100% and 150% UI scale and visually checked; its dimensions scale to keep the controls readable.

Native checks ran separately on the normal interactive desktop because the isolated sandbox desktop cannot supply Windows capture frames. They include rendered OCR fixtures for 769/278/267, capture/restoration lifecycle, minimized matched-log detection, new targeted inspection requests that leave other schedules unchanged, and global immediate inspection. The updater fixture verifies replacement, previous-binary backup, restart and preservation of synthetic encrypted data.

Final executable: **2,580,480 bytes**, version **1.9.5.0**.
SHA-256: **8c449a2a1144ae4c81eb5031cff915c0b37b76d973c1fc2d0e5b23a80cad228e**.

Live Discord delivery, actual role/channel permissions, browser-window delivery, in-game Anti-AFK effectiveness and live multi-account game joins were not exercised in this release session. Discord cards use documented message/embed fields; real channel setup remains an external dependency. Existing local screenshot consent and credential isolation remain enforced. The ten-client native Roblox Home logout remains unproven fixed. WebView2 and the full three-minute cleanup probe were not rerun because their implementations were not changed.

Local logs relative to the original workspace root: work/build-v1.9.5-release-final.log, work/window-monitor-v1.9.5.log, work/window-sizing-v1.9.5.log and work/updater-restart-v1.9.5.log. Those local logs and preview data are excluded from source/release archives. Historical 1.9.4 results remain in docs/VALIDATION-1.9.4.md. See docs/RELEASE-1.9.5.md and docs/DISCORD-REMOTE.md.