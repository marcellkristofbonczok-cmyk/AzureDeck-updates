# AzureDeck updates

[Download the latest AzureDeck executable](https://github.com/marcellkristofbonczok-cmyk/AzureDeck-updates/releases/latest/download/AzureDeck.exe) · [Release history](https://github.com/marcellkristofbonczok-cmyk/AzureDeck-updates/releases)

AzureDeck is a Windows x64 account manager. This repository distributes tested executables, manifests, release notes and dependency license texts. It contains no account vaults, browser profiles or Discord credentials.

## In-app updates

AzureDeck 1.8.1 and later ship with this update source configured:

```text
https://github.com/marcellkristofbonczok-cmyk/AzureDeck-updates/releases/latest/download/update.json
```

For AzureDeck 1.8, paste that URL into **Settings > App updates > Update manifest**, then **Save settings** and **Check for updates**. Use **Download update** and **Install update and restart**. Close Roblox before installation. The updater keeps account data, verifies the downloaded executable, and retains a previous-version backup.

Updates are checked on startup and every six hours when enabled. A new version is published only after it is built and tested; connecting GitHub does not generate app changes automatically.

## 2.0.1 changes

Fresh Player selection validates launcher references, full executable versions and channel deployment metadata without using folder timestamps as the selection rule. Complete-bundle/reference changes invalidate stale metadata immediately, and active accounts keep a validated cohort. Account-matched channel observations and detailed selection reasons are included in diagnostic export. Fatal installer errors require supported repair; compatibility restores before retrying, Studio/console bookkeeping is excluded, dependency waits retain the queue, and repeated startup/timeout/maintenance replay is bounded. **875 regression/native/inspection checks and eight final UI previews passed.** Tests use synthetic accounts and controlled processes; real account/installer execution and guaranteed uninterrupted platform operation are not claimed. See [release details](docs/RELEASE-2.0.1.md) and [validation](VALIDATION.md).

## 2.0.0 changes

Major launch reliability overhaul: a bounded account coordinator, adaptive overlapping startup confirmations, serialized native creation, deployment/channel checks, supported safe-idle maintenance, independent retries/backoff and encrypted restart recovery with attempt/completion records. Healthy sessions are preserved; unfinished accounts remain saved after unrecoverable installation failures. Launch & recovery exposes concurrency, direct launch, timeout and resume controls. Structured rotating diagnostics exclude credentials and command lines. **811 regression/native/metadata checks and eight final UI previews passed**, including fifty queued synthetic accounts, concurrent admission and actual restart integration. No real installer or account launch was executed; real 30–50-client performance and Roblox Home authentication limits remain unverified. See [release details](docs/RELEASE-2.0.0.md), [requirements coverage](docs/V2-REQUIREMENTS.md) and [validation](VALIDATION.md).

## 1.9.13 changes

Choose **Roblox** or **Bloxstrap** in Accounts > Launch center or Settings > Launch & recovery. Both show actual installed-app icons and installed/missing status; an unavailable choice cannot overwrite the current selection. The choice saves automatically, and each backend has independent repair protection. New default-on global switches rejoin unexpected crashes and persistent Unknown clients with a grace period, cooldown and per-incident retry cap. Stable health resets that cap; offline waits do not burn attempts. In-app stops and queue cancellation invalidate recovery. **776 regression/native/inspection checks and eight final UI previews passed**, including real watchdog tests with synthetic accounts/launch callbacks. No live account or real installer was executed during validation. See [release details](docs/RELEASE-1.9.13.md) and [validation](VALIDATION.md).

## 1.9.12 changes

Launching/rejoining and recovery now use **%LOCALAPPDATA%\Bloxstrap\Bloxstrap.exe** for the current Windows user. Install and finish Bloxstrap setup first. AzureDeck prepares updates before requesting fresh account tickets, sends account-specific public/private-server launch URIs, and tracks the actual player through an owned process job and matching join logs. Cancelled/timed-out jobs remain tracked to prevent duplicates. Recovery asks Bloxstrap to update, then force-reinstall its managed Player if needed; AzureDeck no longer deletes the Roblox folder or uses its stock installer. Settings includes launcher setup links, and potato flags use Bloxstrap's persistent modifications folder. **740 regression/inspection/artifact checks and eight UI previews passed.** Real Bloxstrap/game launches were not executed during validation. See [release details](docs/RELEASE-1.9.12.md) and [validation](VALIDATION.md).

## 1.9.11 changes

Modern installer Critical Error dialogs and temporary helper errors are now detected. Failed installers close automatically, with verified forced closure after ten seconds if graceful exit fails. Recovery reruns a fresh official launcher to update first; if that update or its next client launch still fails, it performs the full clean reinstall and retries. Failure after both attempts completes the waiting launch and shows a clear needs-attention status. The clean fallback still removes Studio/local Roblox data and reinstalls Player only. **711 compiled/native checks and eight UI previews passed**, including modern TaskDialog, stubborn-installer termination and unrelated healthy-updater protection. Real installers were not run or closed during validation. See [release details](docs/RELEASE-1.9.11.md) and [validation](VALIDATION.md).

## 1.9.10 changes

Startup now waits for the player and matching join evidence before classifying installer handoffs. A normal helper name cannot fail a live startup; replacement player children are tracked. Automatic recovery prepares a signed official installer, deletes the entire native **%LOCALAPPDATA%\\Roblox** folder, reinstalls Player, waits, and retries the selected batch. **This removes Studio's installation/settings/cache and all other data in that folder; Player alone is reinstalled. Close Studio first.** AzureDeck data outside Roblox is protected. One clean attempt is allowed per episode; failed cleanup/reinstall keeps launches blocked. **692 compiled/native/download checks and eight UI previews passed.** Tests used temporary cleanup folders; real Roblox was not deleted and the real installer was not run. See [release details](docs/RELEASE-1.9.10.md) and [validation](VALIDATION.md).

## 1.9.9 changes

Automatic recovery now closes verified Roblox players, releases compatibility, updates and retries. If updating fails or the retried client still fails, it downloads and verifies a fresh official Roblox installer, reinstalls, and retries again. The selected batch is rebuilt after recovery. Saved AzureDeck data stays intact; failed fresh reinstall leaves launches blocked. Recovery runs in the background with progress, cancellation and a persistent two-phase limit. The automatic setting is on by default under **Settings > Launch & recovery**. **668 compiled/native/download checks and eight final UI previews passed.** The real installer was not executed during validation. See [release details](docs/RELEASE-1.9.9.md) and [validation](VALIDATION.md).

## 1.9.8 changes

Roblox installer/critical-settings failures now stop further account launches and preserve unattempted queued accounts. Startup follows installer child processes after the player exits; discovery prefers the newest complete installed player over stale registration. The installation block survives restarts. After finishing or repairing Roblox, use **Settings > Launch & recovery > Recheck installation** and retry selected accounts. This protects AzureDeck from repeated attempts; it does not repair Roblox or bypass required updates. **636 compiled/native checks and eight final UI previews passed.** See [release details](docs/RELEASE-1.9.8.md) and [validation](VALIDATION.md).

## 1.9.7 changes

Group management now has its own searchable tick/untick account selector, aligned name/ID rows and a header X. Settings is organized into nine categories with a responsive rail/dropdown and independent editors. Config transfer is under **Settings > Data & config**. **568 compiled/native checks and 42 final app preview/interaction cases passed.** See [release details](docs/RELEASE-1.9.7.md) and [validation](VALIDATION.md).

## 1.9.6 changes

Accounts retain multiple group memberships. Use Accounts > Manage groups to remove selected or individual members from just one group. Add account and scrollbars now stay within padded content; controls wrap and layouts adapt at smaller window sizes and larger text. Copy config uses verified native Unicode clipboard writes and transfers all app settings, private URLs and layouts; account sessions and Discord sign-in stay separate. **606 compiled/native checks passed**, plus 32 final layout/scroll preview cases. See [release details](docs/RELEASE-1.9.6.md) and [validation](VALIDATION.md).

## 1.9.5 changes

Discord now has account/group/all targets, independent numbered pickers, persistent account groups, broader non-secret app controls and colored cards. Long operations update one pending message while other commands remain available. Start with `!help` or `!select`; read the [command guide](docs/DISCORD-REMOTE.md). **591 regression checks passed.** See [release details](docs/RELEASE-1.9.5.md) and [validation](VALIDATION.md).

## 1.9.4 changes

Disconnect monitoring now covers 769, 278 and 267, Anti-AFK uses independent random 1–10 minute intervals, and launch/session handling is more defensive. 535 regression checks passed. Ten-client native Roblox Home authentication remains unproven; see [release details](docs/RELEASE-1.9.4.md) and [validation](VALIDATION.md).

## Publishing the next version

1. Build and test a version newer than the current release.
2. Generate its matching files with the source project's `tools/prepare-update.ps1 -Repository 'marcellkristofbonczok-cmyk/AzureDeck-updates'`.
3. Commit the generated `AzureDeck.exe`, `update.json`, and `release-notes.md` together under `dist/` on `main`.
4. **Publish AzureDeck update** validates the size, hash, product/version and repository URL, then publishes the GitHub release as latest. Existing versions are never overwritten.

The checked-in workflow also supports manual dispatch for retrying a failed initial publication. Only upload release artifacts; never upload account data or tokens.

## Licenses

See [LICENSE](LICENSE), [third-party notices](THIRD-PARTY-NOTICES.md), and [dependency licenses](licenses/).
