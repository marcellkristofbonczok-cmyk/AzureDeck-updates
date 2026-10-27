# AzureDeck 2.0.2 validation

Checked on 2026-10-27, Windows x64, MSVC C++20 /O2 /MT, Windows SDK. The complete build.ps1 application/test/probe pipeline succeeded. The executable embeds the 2.0.2.0 resource, icon and asInvoker manifest. CMake is maintained but was not run. Existing nonfatal shadow/unused-helper warnings remain.

- Core/integration: **715 passed, 0 failed** (7 more than 2.0.1).
- Native hotkeys: **16 passed**.
- ImGui/audio/layout: **29 passed**.
- Native startup lineage: **8 passed**.
- Disposable clean-root compatibility: **14 passed**.
- Installer UI/autoclose: **17 passed**.
- Launcher jobs/URI/maintenance/Studio/wrong-installation probe: **30 passed**.
- Installer trust/cancellation: **3 passed**.
- Native updater replacement/restart: **5 passed**.
- Native Roblox/Bloxstrap deployment read-only inspection, including obsolete channel hints: **4 passed**.

Total this release: **841 checks passed**. No new UI preview or capture/OCR run was required for this launch-policy correction; the previous 2.0.1 evidence remains historical, not counted again here.

New controlled tests exercise the actual Manager with retained test-owned child processes and a test-only image resolver. They verify independent complete metadata-matching builds without terminating healthy clients, diagnostics identifying both builds, preservation of the primary pin, already mixed validated bundles, missing/mismatched deployment rejection, normalized configured channels and offline historical-hint behavior. The native read-only probe checks both actual installed backends with and without an obsolete channel hint: the executable, current channel, required GUID and update requirement must stay identical. No Player or installer is executed by that inspection.

The full core suite also covers queue/retry/dependency/repair lifecycles, account identity/session isolation, groups, Discord protocol/pickers/remote settings, clipboard config, resource policy and existing launch/watchdog features through controlled callbacks. The updater fixture verifies helper readiness, replacement hash, exact previous-executable backup, restart and synthetic vault preservation in an isolated directory. Native fixture probes close only their retained test-owned processes.

Executable: **2,881,024 bytes**, resource version **2.0.2.0**. SHA-256: **2e5202b5e146ce183a30d93a6ee6baaefb316eaaa3298c939d95cf33c64edc60**.

No real Roblox account launch, live Discord delivery, real installer/update/reinstall or real-player termination was performed. Mixed-build gameplay and future server/channel acceptance are not proven. Structural bundle and public metadata checks cannot verify every asset or guarantee uninterrupted sessions. Required shared-file maintenance still waits for healthy sessions/external writers to finish. Windows security and Roblox update enforcement are not bypassed. The older native Home logout issue remains unproven fixed.

Private evidence: work/build-v2.0.2.log, work/updater-restart-v2.0.2.log and work/deployment-inspection-v2.0.2.log. Raw local logs, diagnostics, account vaults, cookies, bot tokens, browser profiles and machine state are excluded from source/distribution packages. Read docs/RELEASE-2.0.2.md and CONTINUATION.md.
