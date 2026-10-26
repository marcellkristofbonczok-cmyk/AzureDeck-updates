# AzureDeck 1.9.9 validation

Built and checked on 2026-10-26 for Windows x64 with MSVC C++20, /O2, static /MT, Windows SDK, version resources, application icon and asInvoker manifest. The complete final build passed. CMake was updated but not executed. Nonfatal warnings include the two existing unused tray helpers and local-variable shadowing in the repair module/test fixture.

- Core/integration: **567 passed, 0 failed**.
- ImGui/audio/scroll/layout: **29 passed, 0 failed**.
- Native hotkeys: **16 passed, 0 failed**.
- Native installer process-tree probe: **6 passed, 0 failed**.
- Native repair trust/cancellation probe: **3 passed, 0 failed**.
- Native startup/capture/OCR/restoration/log monitoring: **41 passed, 0 failed** with the corrected activation-event observation.
- Native updater replacement/restart: **5 passed, 0 failed**.
- Official Roblox download/signature verification: **1 passed; installer not executed**.
- Total compiled/native/download checks: **668 passed**.
- Final installation-recovery UI previews: **8 passed**.

Repair tests exercise update then fresh-reinstall escalation, the case where updating completes but the subsequent client still fails, persistent retry budgets across restart, no unbounded retries, healthy-join/cooldown gating, explicit manual reset, fail-closed state writes, helper-process waiting and auto-opened player/WebView descendants. Multi-instance tests preserve a deferred request, release a unique synthetic compatibility lock on its owning thread and restore it before launching.

Injected Manager operations verify that concurrent failures share one update/reinstall, account commands remain responsive while recovery is blocked, both failures leave waiting launches blocked, cancellation does not fall through into reinstall, and a recovered batch requeues accounts closed earlier. The exact synthetic launch sequence and final counts are checked so pre-repair results are not double-counted. TestManager disables native recovery by default and uses a non-native stub; these tests cannot close real Roblox clients or execute an installer.

The repair probe rejects unsigned/missing installer files and cancels before connection/file creation. Its optional download-only mode streamed the official HTTPS installer and verified the Windows trust chain plus exact Roblox Corporation signer without executing the downloaded file. Downloads have no account cookies, no redirects, bounded streaming and a 64 MB cap. The real installed Roblox signature was inspected read-only during implementation; no real update/reinstall was performed.

Native installer/monitor checks cover retained process ancestry after root exit, installer detection, protected recheck behavior, critical-settings startup failure, confirmed joins from synthetic account-matched logs, capture/OCR including 769/278/267, targeted inspection and minimized-log monitoring. An initial foreground-window equality assertion was unreliable on the active desktop. The fixture now observes foreground activation events and verifies that the restored target never activates, allowing unrelated desktop focus changes. The updated probe passed all 41 checks; restoration production code was unchanged. The updater verifies replacement, backup, restart and preservation of separate synthetic data.

Final UI previews use 18 synthetic accounts in isolated encrypted directories and a latched installation reason. Launch & recovery and the blocked Accounts launch center render at 1260x940 at 100% and 150% text scale. The settings editor also renders and scrolls at 1000x700 at both scales. Frame/editor bounds, native HTCLIENT hit testing and wheel scrolling pass. Layouts were visually reviewed; the preview executable matches the release hash.

Final executable: **2,694,656 bytes**, version **1.9.9.0**.
SHA-256: **f6723b94443a6011fe8a357c79803001699974cd005928f16e36ab318b2ebe6e**.

The full real Roblox updater/reinstaller was not run, real players were not closed by repair, and no live account was joined during validation. Production installer UI, platform policies, connectivity and actual game joins remain live-environment dependencies. An installer that fails after both automatic phases leaves launches blocked. Installed Roblox updater files are never deleted. AzureDeck data is outside the installer staging folder. The ten-client native Roblox Home logout remains unproven fixed. Live Discord delivery, real browser sign-in and in-game Anti-AFK were not exercised; the full cleanup probe was not rerun.

Local evidence: work/build-v1.9.9-final.log, work/rebuild-monitor-v1.9.9.log, work/window-monitor-v1.9.9-verified.log, work/updater-restart-v1.9.9.log, work/repair-download-v1.9.9-final.log and work/ui-v1.9.9.log, relative to the original workspace. Raw logs, downloaded test installers, fixture data and screenshots are excluded from source/release archives. See CONTINUATION.md and docs/RELEASE-1.9.9.md.
