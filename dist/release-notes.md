# AzureDeck 1.9.8 — Stop repeated Roblox installer failures

An installer/critical-settings failure now blocks further native launch attempts instead of repeating that failure for every account. The queue stops with honest confirmed/failed/unattempted counts, keeps unattempted accounts queued, and remembers the installation block across app restarts. Automatic recovery also waits. Repeating a blocked batch returns promptly.

The manager chooses the newest complete installed player by executable version; an older registered path no longer overrides a newer complete bundle. Launch preflight checks for required player files, open installers and files still being written before obtaining tickets or replacing a client. Normal direct-player launching remains in use.

Startup follows installer child processes even when the original player exits. Such a handoff is not counted as a game launch. Critical-settings errors no longer trigger repeated automatic restarts. Only the failed new player uses the existing owned-process cleanup; installer processes and other working clients are not globally terminated.

If blocked, finish or repair Roblox and close the installer/error windows. Open Settings > Launch & recovery > Recheck installation, or use the same button in the Launch center. A successful recheck clears the installation pause so you can retry selected accounts. It checks local readiness; it does not repair missing assets, bypass Roblox's required updates or confirm an online join.

If the official installer still fails independently of AzureDeck, follow [Roblox's desktop troubleshooting guide](https://en.help.roblox.com/hc/en-us/articles/203312870-General-Desktop-Roblox-Issues). Roblox also documents the [infinite installation loop](https://en.help.roblox.com/hc/en-us/articles/203312940-Infinite-Getting-Latest-Roblox-Loop) as an installation problem.

See VALIDATION.md for executed synthetic process, batch, native monitoring, updater and UI checks. No live account was launched and the user's failing installer was not reproduced by running a real installer during validation.
