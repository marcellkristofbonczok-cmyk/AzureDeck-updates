AzureDeck 1.9.5 — Discord control center and account groups

- Use account names, group:<name>, or all consistently for account actions. Add quoted names, per-user numbered pickers and paginated account/group/resource cards.
- Create persistent account groups, assign selected/multiple accounts, rename groups and delete groups while keeping the accounts. Manage them from the desktop or Discord.
- Add remote saved-destination launch, browser requests, restore/optimize/arrange/inspect, recovery/exclusion/favorite/nickname/destination controls, queue actions, Anti-AFK, themes, preferences and validated non-secret settings.
- Replace plain responses with blue/amber/red Discord cards. Long operations update one progress message while status, selection and queue commands remain responsive. Fall back to text if Embed Links is missing.
- Sync remote changes with desktop controls without overwriting unrelated local drafts. Keep credentials, private setting URLs and screenshot consent local. Preserve silent connection and existing channel/user authorization.

591 regression checks passed, including synthetic Discord transport tests, account/group persistence, native targeted monitoring and updater replacement/restart. Live Discord delivery and live Roblox joins were not tested.

After updating, reconnect the bot and send !help or !select. Examples:
!group create Farm
!group add Farm Alpha Beta
!join group:Farm <Roblox-link>
!launch group:Farm
!stop all
!settings set disconnectDetection on
!afk on

Command guide: https://github.com/marcellkristofbonczok-cmyk/AzureDeck-updates/blob/main/docs/DISCORD-REMOTE.md

The prior ten-client native Roblox Home logout remains unproven fixed.