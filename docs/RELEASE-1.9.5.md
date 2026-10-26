# AzureDeck 1.9.5 — Discord control center and account groups

Discord now supports consistent account/group/all targeting, per-user numbered pickers, paginated reports and colored status cards. Long operations update one message while the polling loop remains responsive. Group definitions and memberships persist in the encrypted workspace and can be managed both locally and remotely.

Use `!help` or `!select` after connecting. The complete [Discord guide](DISCORD-REMOTE.md) covers commands, quoting, group assignments, preferences, queue control, permissions and local-only fields.

Examples:

```text
!group create Farm
!group add Farm Alpha Beta
!select group:Farm
!join group:Farm <Roblox-link>
!launch group:Farm
!stop all
!settings set disconnectDetection on
!afk on
```

The desktop **Manage groups** dialog supports selected-account assignment, rename, ungroup, delete and filtering. Account/group metadata created by older versions is preserved; named empty groups survive restart. Each account has one group. Deletes keep accounts and sessions. Group changes validate all accounts before one committed write.

Remote operations reuse the existing launcher, process validation, window services, settings validators, screenshot gate and encrypted persistence. They do not expose arbitrary shell/file access or credentials. Shared FPS behavior remains explicit; browser requests are acknowledged as queued, not falsely reported as opened. Settings and open account forms preserve unrelated remote edits while retaining local drafts.

The bot keeps the existing user/channel authorization and optional everyone switch. Styled embeds require Embed Links; basic text fallback remains available. Connection stays silent. No new library, Gateway service or public server is required. Pending work/users/pages are bounded and the four-second REST poll interval is retained.

Application and manifest versions are 1.9.5. The existing source build scripts include the new inl/header modules through manager.cpp. Vault/workspace version 1 remains compatible; groups are an optional workspace field. The 1.9.4 monitoring, randomized Anti-AFK, cookie isolation, safer ticket replacement and updater protections remain included. Ten-client native Roblox Home logout is still not proven fixed.

See root `VALIDATION.md` for actual checks, binary hash and limits. No real Discord messages or live Roblox launches are required by the synthetic tests.
