# AzureDeck 1.8.3

## Correct account launches

The shared HTTP session previously allowed automatic cookie handling alongside explicitly supplied account cookies. Windows can append cached cookies to later requests. Every request now disables automatic cookie handling and uses only its explicitly provided credentials. This follows Microsoft's [WinHTTP cookie-handling guidance](https://learn.microsoft.com/en-us/windows/win32/winhttp/cookie-handling-in-winhttp).

Before obtaining a launch ticket, AzureDeck verifies that the session resolves to the selected account. A wrong, expired or unverifiable identity stops that launch before starting Roblox. Identity errors are not retried. Ordinary Launch preserves an existing live client; explicit Rejoin remains available for replacing it. Recovery checks the launch generation and current process again before dispatch and reserves the account while starting, so an old queued recovery cannot replace a newer manual launch.

Confirmed joins still require matching engine evidence. Missing evidence is reported as unconfirmed rather than successful. Supported Roblox client behavior and external network/service availability remain dependencies; no client security protections were changed.

## Window sizing

Low-resource mode no longer automatically shrinks a window. **Settings > Launching and recovery > Resize clients to 640 x 360** is a separate opt-in. When sizing is requested, the existing position is preserved. Windows that were resized by a prior version retain that size until resized through Windows or the Window manager.

## Automatic settings

General settings, monitoring, hotkeys, appearance, performance preferences, Discord fields and FPS save without a Save button. Writes do not wait for the launch worker. Typing and dragging are coalesced for about 200 milliseconds rather than generating a disk write for every frame; outstanding edits flush when closing the app. Invalid fields remain visible as unfinished drafts while other valid changes can save.

Discord drafts remain in the encrypted local vault. Connecting still requires valid credentials and IDs; edits do not connect the bot or send a startup message. Disconnect/reconnect is required to change a connected bot's access settings. Session-only screenshot sharing remains session-only.

Hotkey changes register automatically; **Retry shortcut conflicts** retries registration after another application releases a key. The FPS cap saves automatically and applies at the next launch when no Roblox client is running. Existing clients are not restarted just to apply an FPS change.

## Clipboard configuration

**Settings > Copy config** copies a versioned JSON configuration. **Import config from clipboard** validates it before applying and saving. It includes theme, low-resource preferences, FPS, portable application settings, monitoring and hotkeys. Account sessions, usernames/passwords, bot tokens/access IDs, webhook URLs, private game links, the trusted update source and account-specific layouts are excluded and remain local. Imported webhook notifications are disabled if this computer has no configured webhook.

Unknown versions, unsupported/private fields, invalid types, out-of-range values and payloads larger than 128 KB are rejected. Config text does not execute commands or import credentials.

## Validation

Tests include a loopback HTTP server that seeds the shared WinHTTP cookie jar, then verifies isolated requests for two synthetic users and an anonymous request. Additional checks cover account identity, clipboard round trips and rejection, saving while the launch worker is blocked, and preserving/reducing native window dimensions. Existing monitoring and updater-restart fixtures are also run. A separate read-only check of stored sessions succeeded without launching game clients or exposing credentials.

Install from **Settings > App updates > Check for updates**, or download from [GitHub releases](https://github.com/marcellkristofbonczok-cmyk/AzureDeck-updates/releases).
