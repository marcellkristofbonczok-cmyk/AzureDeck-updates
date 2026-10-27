# AzureDeck 2.0.1 — Validated deployment selection and bounded recovery

This update fixes the recurring installer/recovery paths while preserving the existing account, group, browser, macro, Discord, graphics, config-transfer and UI features.

## Investigation and selection

Verified code defects included a two-minute executable-path cache, deployment-GUID mismatch forcing a potentially older installation, fatal installer closure being mistaken for healthy updater completion, compatibility being released before maintenance was safe, generic retries for shared prerequisites, and unbounded batch replay after repeated maintenance exits. A Player handed off into another installation could also remain classified as an updater helper. These are verified implementation paths; no real failing account was launched during validation.

Before each native start AzureDeck now freshly reads complete Player bundles and active installation references. Native references come from the Player protocol/uninstall registration and must match a discovered installation beneath the supported roots. Bloxstrap uses its PlayerState.json VersionGuid. Neither reference text nor arbitrary registry arguments are executed. Studio installers and Studio clients are excluded from Player maintenance.

Selection compares the full deployment GUID and executable version. Roblox's public deployment metadata is cached by backend/channel/reference-and-inventory fingerprint, while local executable/reference discovery is fresh. New complete bundles invalidate old metadata immediately, even when protocol registration is unchanged. A mismatch checks the public origin as well as the CDN. Conflicting metadata preserves a validated reference rather than causing channel churn. A valid launcher reference ahead of public metadata is retained with an explicit reason rather than forcibly downgraded. Missing, incomplete or ambiguous installations require supported verification; multiple offline folders without a reference are never guessed from timestamps. A unique complete offline fallback is explicitly marked as server-unverified.

Folder creation/modification timestamps do not determine the launch build. Write times are used only to wait for the selected EXE/DLL to settle and to invalidate cached metadata. New files get a cancellable settling window rather than immediately triggering another reinstall. The adopted Player is checked again; an unexpected different installation/build closes only that newly owned client and enters supported verification.

## Cohort and channel handling

Active accounts retain a validated cohort executable. An equivalent reference/path change keeps the existing pin. A genuine incompatible update queues safe maintenance while healthy sessions continue; the pin refreshes after validated maintenance or when no affected clients remain. Different account channels requiring incompatible deployments fail that account clearly and let compatible queued work continue without switching the global channel or restarting healthy clients.

Channel observations come from new account-matched engine logs. Hints are not attributed before identity matches, creator output cannot forge them, and per-account observations persist as diagnostic events. AzureDeck reads the configured channel and relevant installation references; it does not patch the registry. Selected paths, full versions, channels and selection reasons are written to rotating structured diagnostics. The existing Export diagnostic JSON button now includes the latest 256 whitelisted launch records.

## Installer recovery and retry limits

Fatal installer failures always retain the need for real supported repair, even when the deployment GUID still matches. Only explicitly healthy updater completion can use the metadata-validated completion shortcut. Recovery updates first and uses the bounded reinstall phase if necessary. Compatibility is released only for exclusive safe maintenance and restored before the shared repair future completes. A pending safe-maintenance wait does not release an already-active compatibility mutex.

Shared compatibility/helper waits do not burn account attempts. After a bounded wait the exact account and remaining queue are saved and paused, then resume automatically when ready. A started operation that times out retains its consumed attempt across resumes. Three identical startup failures stop that account; the next account continues. Startup retry waits are capped at 60 seconds, with a hard overall attempt/cycle bound. Maintenance-driven account replay is limited to once per batch. Logs include the actual error, attempt count and delay instead of only “recoverable launch failure.” Cancellation also removes already-paused saved intents.

The old coordinator's persistent guard format migrates once to a fresh bounded repair episode while retaining an existing fatal block. Application restarts cannot repeatedly reset that new budget. Graphics overrides retain backups and apply to the validated direct Player as well as Bloxstrap's persistent modifications, only while clients are closed.

## Verification and limits

Read VALIDATION.md for final counts, hashes and evidence. New controlled tests cover repeated failures, following-account progress, compatibility waits with zero attempts, live queue resume, fatal update/reinstall/compatibility handoff, persisted timeout budgets, repeated maintenance replay, saved-intent cancellation, selection references, conflicting metadata, partial/mismatched builds, file settling, cohort pinning, account-specific channel observations, diagnostic export, Studio exclusion and wrong-installation child cleanup.

No real Roblox account, actual installer/update/reinstall, live private-server access or live Discord delivery was exercised. Fifty-account tests remain synthetic. Roblox can require a new build or end sessions server-side. No stable supported prelaunch API for every account's future A/B deployment assignment was verified; account-specific observations become available when identity-matched engine logs expose them. Structural/metadata validation cannot prove every asset or guarantee future server compatibility. Offline/ahead-of-metadata references are reported honestly. Safe maintenance can stay queued while healthy sessions or another genuine writer remain active. Unmanaged clients and Windows security/permission constraints are not bypassed.

Primary implementation references examined: Bloxstrap 2.11.4 Bootstrapper.cs, LaunchSettings.cs, Models/Persistable/DistributionState.cs, RobloxInterfaces/Deployment.cs and Utility/WindowsRegistry.cs at https://github.com/bloxstraplabs/bloxstrap/tree/v2.11.4/Bloxstrap. They document its launch/channel parsing, selected VersionGuid, public metadata/origin fallback and protocol registration. No upstream code was injected into Roblox, and no Player binaries or anti-cheat mechanisms are patched.
