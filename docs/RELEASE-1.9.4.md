# AzureDeck 1.9.4 — disconnect monitoring and randomized activity

## Disconnect detection

- Added explicit coverage for **769, 278 and 267**. Windows OCR can read the short OK action as `0k` or spaced letters; these variants now qualify only with the existing corroborating dialog evidence.
- Fixed a WinRT apartment/factory lifetime crash that could terminate the monitoring worker/app after a prior capture object was disposed. Cached factories release before apartment teardown.
- Added a validated window-bounds fallback for an initially zero capture size and bounded resampling coordinates.
- Kept account log association across legitimate teleports to a different place. A later foreign account identity invalidates the association.
- Increased the bounded fresh-log candidate limit from 8 to 128, so larger batches do not disable matching before the correct log is selected.
- Prefer a readable screen error code over generic log evidence. A confirmed generic incident gains its code after two consistent fresh screen checks.
- Automatically resized potato windows stay at least **640x360 while detection is enabled**. Preserve-size remains unchanged.
- Codes **267/600** are reported but do not initiate automatic rejoin. A later recognized kick/ban code cancels queued live recovery.

Detection remains opt-in. In Settings or Window manager, turn on **Disconnect Detection**, or press **Check clients now** to enable it immediately. The UI explicitly explains when detection is off. Enable **Prevent Minimization** for screen inspection of clients that would otherwise stay minimized. Matched logs can detect an ended connection while minimized; they may not supply its screen error code. Unavailable captures remain Unknown rather than being reported as connected.

Automatic rejoin requires **both** global bounded recovery and **Allow automatic recovery for this account** in each account's details. Recovery uses a fresh verified ticket and the saved destination, with the existing cooldown and attempt limit. It does not resume a game's internal teleport destination or progression.

## Randomized Anti-AFK

Each managed client receives its own independently sampled interval of **60-600 seconds**. The first due time, later pulses, manual-pulse rescheduling and failed-delivery retries use fresh intervals. The fixed-interval UI is replaced with the actual range; older interval fields remain accepted for config compatibility.

Pulses use the existing verified foreground Space scan-code tap and small mouse activity pulse, then restore foreground/minimized state. This remains opt-in. Timing randomness does not guarantee that an experience cannot recognize automation or that every experience accepts Space as a jump.

## Larger batches and native Roblox Home sessions

Native client starts are at least five seconds apart, including retries and recovery. Longer configured spacing is retained. Account identity is still checked before tickets. A currently running client is preserved if verification or ticket issuance fails; it is closed only after a replacement ticket has been issued. HTTP 429 and server failures during verification are distinguished from invalid credentials.

Account-matched Roblox logs can flag a rejected native user-profile request (HTTP 401). AzureDeck surfaces a per-account warning and records a single event for that client; it does not erase or rotate the saved cookie. Use explicit Rejoin with a valid session when needed.

**The reported ten-account native Home logout/teleport problem has not been proven fixed.** The observed native-profile rejections establish a symptom, not its cause. Roblox's [web Account Switcher documentation](https://en.help.roblox.com/hc/en-us/articles/21037888001044-Account-Switching) describes a five-account web feature; it does not establish a native-client concurrency limit. AzureDeck therefore does not impose an invented five-account cap. It also does not reinstate the APPDATA redirection removed in 1.8.6, which previously blocked launches, or modify Roblox process memory. Native Home sessions under one Windows user are not independently virtualized.

Roblox [teleport security and destination access rules](https://create.roblox.com/docs/projects/teleport) remain controlled by Roblox and the experience. Detection/rejoin cannot override server access restrictions, bans, or service failures.

## Build and update

The imported 1.9.3 updater fixtures mislabeled the current and future binaries with the same version. The disposable future fixture now stays ahead of the app, and a mismatch test uses deliberately different metadata. The PowerShell build propagates all nonzero exits, including native crash codes.

See root `VALIDATION.md` for the actual checks, artifact hash and limitations. The GitHub distribution workflow publishes the tested executable and manifest under a new tag without overwriting an existing release. Settings and saved accounts retain their existing encrypted formats.
