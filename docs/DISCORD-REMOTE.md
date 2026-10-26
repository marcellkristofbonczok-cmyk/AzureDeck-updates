# Discord control guide — AzureDeck 1.9.5

Connect the bot in AzureDeck's Discord tab. Connection stays silent. Send `!help` for the command dashboard or `!select` for a numbered picker. If ordinary commands have no readable content, enable Message Content Intent in Discord Developer Portal or mention your bot before the command.

## Pick accounts and groups

```text
!select
!pick 2
!accounts all 2
!select group:Farm
!join group:Farm https://www.roblox.com/games/123456
!stop all
```

Account actions take an account name/ID, `group:<name>`, or `all`. Bare group names work when unambiguous. Prefix with `account:` or `group:` when a group has the same name as an account. `a:` and `g:` are short aliases. Local nicknames work when unique. Exact account IDs take precedence over nicknames.

Quote names containing spaces: `!select "group:Farm Two"`. You can use single or double quotes; escape the active quote with a backslash.

`!select`, `!accounts` and `!groups` show up to ten numbered items per page. Type `!pick 3` or `!select #3` to choose item 3 on **your latest** picker card. Pickers store stable identifiers and expire after ten minutes. Each Discord user has a separate picker and selection. Selecting a group keeps that group selected as its membership changes; a launched batch snapshots its member IDs when queued.

| Command | Purpose |
| --- | --- |
| `!select` / `!select page 2` | Open a picker page. |
| `!select <target>` | Save your account, group or all selection. |
| `!pick <number>` | Select a numbered item on your latest card. |
| `!accounts [target] [page]` | Show accounts; defaults to all. |
| `!status [target]` | Show your selection, or all if nothing is selected. |
| `!resources [target] [page]` | Show client memory/CPU totals and account states. Missing metrics are omitted. |
| `!groups [page]` | Show group membership/running counts. |

## Manage groups

```text
!group create Farm
!group add Farm Alpha Beta
!group add Farm group:OtherGroup
!group remove Alpha Beta
!group rename Farm "Farm Two"
!group delete "Farm Two"
```

Each account belongs to one group. Assignment moves accounts from their previous group. Empty named groups persist. Renaming updates member records; deletion clears membership and **keeps the accounts and sessions**. Multi-target assignment validates every target before saving. Commands accept up to eight arguments, so one add command can name up to six selectors. A selector may itself name a group or all accounts.

On the desktop, select account checkboxes and open **Accounts > Manage groups**. Create/choose a group, then assign the selected accounts. Rename, ungroup and delete controls are in the same dialog. Existing group text fields and group filters keep working.

## Launch and control clients

Commands with an optional target use your saved selection when the target is omitted.

| Command | Behavior |
| --- | --- |
| `!join <target> <Roblox-link-or-placeId>` | Launch the target into a public/private server it can access. |
| `!join <link>` | Launch your current selection. |
| `!launch [target]` | Launch using each account's preferred destination, then last game, then the app default. |
| `!rejoin [target]` | Explicitly replace clients using each account's last game. Every target needs one. |
| `!stop [target]` | Cancel pending starts for those accounts and queue stop actions for their clients. |
| `!focus [target]` | Bring managed windows forward. |
| `!minimize [target]` | Minimize managed windows. Prevention may restore them unless they are excluded. |
| `!restore [target]` | Restore minimized managed windows without requesting focus. |
| `!eco [target]` / `!normal [target]` | Change owned-client process priority. |
| `!optimize [target]` | Apply existing process/window optimization to the selected managed clients. |
| `!arrange <target> <layout> [monitor]` | Use grid, horizontal, vertical, cascade or focus layout; monitor numbers start at 1. |
| `!browser [target]` | Queue authenticated account browser requests on the PC. The UI processes them as available; failures appear in app Logs. |
| `!inspect [target]` | Enable detection globally if needed and request an immediate check of those targets. Other accounts retain normal scheduled checks. |

Aliases: `!launch <target> <link>` works like join, `!kill` like stop, `!list` like accounts, `!sel` like select, and `!resource` like resources. Normal Launch preserves an existing live client; use Rejoin to replace it. The bot reports actual results and unconfirmed joins rather than treating process creation as success.

## Account options

```text
!recovery group:Farm on
!exclude group:Farm off
!favorite account:Alpha on
!nickname account:Alpha "Main account"
!destination group:Farm <Roblox-link>
!launch group:Farm
```

Recovery also requires global recovery and disconnect detection to be enabled. The existing cooldown, attempt limit and kick/ban exclusions still apply. `!exclude` controls Prevent Minimization exclusions. Destination changes are saved without echoing the private invite back into the bot response; the command you send still appears in your Discord channel. Rejoin uses the last game, while Launch can use the preferred destination.

## Change app settings

```text
!settings list
!settings list 2
!settings get disconnectInterval
!settings set disconnectDetection on
!set disconnectInterval 5
!set recoveryEnabled on
!get recoveryCooldown
!prefs
!prefs potatoFps 15
!prefs autoCleanup on
!theme 2
!potato on
!afk on
!afk pulse group:Farm
```

Settings cover monitoring, recovery, launch pacing/gates, notifications, appearance, sound, resource alerts, backup preferences and hotkeys. Use on/off for switches, integers for numbers, and quoted JSON for complex fields. All changes pass the existing type/range validators and save through the same encrypted storage. `!settings get` shows a setting's current type/value. `!set` and `!get` are aliases. A JSON setting replaces its complete value; use `!settings get hotkeys` first when keeping existing shortcuts.

Example of one quoted JSON value:

```text
!settings set hotkeys '{"0":{"key":79,"mods":3,"global":true}}'
```

`!prefs <key> <value>` supports theme (0-4), potatoFps (1-240), lowResource, minimize and autoCleanup. `!theme` and `!potato` are shortcuts. `!afk on/off` controls the existing independently randomized 1-10 minute scheduler; `!afk pulse [target]` requests a manual pulse.

`!fps all 60` applies the **shared** FPS setting only with all Roblox clients closed. Legacy `!fps 60` still works. Use `!prefs potatoFps 60` to save for a future launch. Per-account FPS injection is not provided. Graphics/FPS preferences take effect on a future native launch after existing clients close.

Remote changes sync into desktop controls. Pending local edits to other fields are preserved. Credentials, session transfer, private setting URLs, update source and screenshot consent remain local. Legacy fixed Anti-AFK interval/background fields remain accepted in old configs but are not offered as active remote controls.

## Queue, cleanup and screenshots

| Command | Behavior |
| --- | --- |
| `!queue status` | Show actual launch counts and queue pause state. |
| `!queue pause` / `!queue resume` | Pause future starts or resume the queue. The current launch may finish. |
| `!queue cancel [target]` | Cancel pending/in-progress starts; defaults to all. Use Stop for already-running clients. |
| `!cleanup [all]` | Run the existing verified leftover cleanup; active visible clients stay protected. |
| `!screen` | Share the primary monitor only if screen sharing was enabled locally for this app session. |
| `!ping` | Verify the connection responds. |

## Cards, permissions and access

Responses use Discord's native embed cards, with blue completion/info states, amber pending/attention states and red errors. Long operations update their initial pending message with progress and final results; the bot continues accepting status/selection/queue controls. Account/group pickers are typed numbered commands, not Gateway buttons or slash commands. Paging avoids truncating large account lists. Card text uses conservative limits and preserves UTF-8; mentions are disabled.

Allow **View Channel**, **Read Message History**, **Send Messages**, **Embed Links**, and **Attach Files** in the monitored channel (Send Messages in Threads for a thread). Without Embed Links, the bot tries a text fallback. If basic sending is denied too, the app shows the specific Discord permission error. Connecting sends no startup message. The REST poller checks every four seconds; Discord presence may still show offline.

Owner-only mode accepts your configured personal user ID. **Accept commands from everyone** gives human users in the monitored channel the same account/group/non-secret app controls. Bots, webhooks, other channels and unauthorized users are ignored. It does not remove the local screenshot gate or expose credentials. Only enable this mode for a channel whose users should have those controls.

Protocol reference: Discord's [message/embeds API](https://github.com/discord/discord-api-docs/blob/main/developers/resources/message.mdx). Live Discord delivery/permissions remain external dependencies; synthetic transport tests do not replace testing your own channel configuration.
