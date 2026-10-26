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
