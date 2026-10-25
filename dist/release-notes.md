AzureDeck 1.8.3

- Fix cross-account cookie reuse: isolate every HTTP request and verify account identity before requesting a launch ticket.
- Preserve live clients on ordinary Launch; protect recovery against stale or duplicate requests. Use Rejoin explicitly to replace a client.
- Stop automatic window shrinking by default; make 640x360 resizing optional.
- Autosave settings, hotkeys, encrypted Discord fields and FPS without Save buttons. FPS applies at the next launch after all clients close.
- Add Copy config and Import config from clipboard in Settings. Credentials, account sessions, private links and the update source remain local.

506 regression checks passed, plus read-only stored-session identity verification. Install through Settings > App updates; existing account data is preserved.