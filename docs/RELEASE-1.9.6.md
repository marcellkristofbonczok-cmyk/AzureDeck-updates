# AzureDeck 1.9.6 — Multiple groups, fitted UI and working config copying

Accounts retain all their groups when added to another. Open Accounts > Manage groups to remove selected accounts from just the chosen group or remove one member beside its name. Existing single-group records migrate automatically. There is no fixed membership/catalog count limit; names and overall workspace storage retain their validation bounds.

Discord examples:

```text
!group add Farm Alpha Beta
!group add Trading Alpha
!group remove Farm Alpha
!group clear account:Beta
```

Adding Alpha to Trading keeps Farm. Removing Alpha from Farm keeps Trading. Clear explicitly removes every membership for its targets. Rename/delete, selectors, counts, search, sorting and account labels handle multiple memberships. Group management does not delete accounts or their sessions.

The Accounts header and content panels now honor their padding. Add account and scrollbars sit clear of the native resize border. Wider scrollbars, wrapped controls and labels, adaptive metric columns/launch panels, scroll chaining and extra bottom space improve navigation at smaller window sizes and 150% text scale.

Copy config creates and verifies a native Unicode clipboard payload using an owner window. Version 2 includes every app setting and appearance/performance preference, including private server/webhook URLs, update source, selections, hotkeys and saved layouts. Keep this JSON private. Imports validate everything before applying and support old version-1 exports. Account sessions, account metadata/group memberships and Discord bot sign-in are separate. Sign in on the destination device or use the existing account/session transfer tools. Stored window layouts apply to matching account IDs.

See root VALIDATION.md for the executed checks. Live Discord delivery and live Roblox game joins were not exercised. The existing ten-client native Roblox Home logout remains unproven fixed.
