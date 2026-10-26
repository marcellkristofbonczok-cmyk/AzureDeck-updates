AzureDeck 1.9.4

- Fix disconnect monitoring for error 769, 278 and 267, including OCR reading OK as 0k.
- Fix a WinRT capture-worker crash; retain account log matching after teleports and support larger batches of fresh logs.
- Keep automatic potato sizing at least 640x360 while detection is on. Show when detection/recovery prerequisites are disabled.
- Randomize each client's Anti-AFK jump/activity interval independently between 1 and 10 minutes, including retries.
- Space native launches at least five seconds apart. Obtain a replacement ticket before closing an existing client; report native Roblox profile/session rejection without deleting saved sessions.
- Keep kick/ban codes 267/600 detectable without automatically rejoining them.
- Include the imported 1.9.3 UI, graphics, clipboard and session-transfer improvements.

535 automated/native regression checks passed, including rendered OCR fixtures for all three requested codes, plus read-only stored-session identity verification. Existing encrypted accounts/settings are preserved.

After updating: Settings > Window Monitoring > Check clients now enables detection. Enable Prevent Minimization for screen checks of minimized clients. Automatic rejoin also requires global recovery and the account's own recovery switch.

Ten-client native Roblox Home logouts/teleports are not proven fixed; pacing, safer replacement and diagnostics are mitigations. Live multi-account joins and in-game Anti-AFK were not tested. Random timing does not guarantee undetectable automation.