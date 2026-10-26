# AzureDeck 1.9.9 — Automatic update, fresh reinstall and retry

On an installer/critical-settings launch failure, recovery now runs automatically:

1. Close verified Roblox player instances for the current Windows user/session, including instances outside the selected queue.
2. Temporarily release multi-instance compatibility and wait for or run the official updater.
3. Restore compatibility and retry the failed account with a fresh ticket.
4. If the update fails or the retried client still fails, download a fresh official Roblox installer, verify its Roblox Corporation Windows signature, reinstall, and retry again.
5. If the fresh reinstall or its subsequent retry fails, keep launches blocked instead of repeating forever.

The selected batch is rebuilt after recovery so accounts closed earlier are launched again; prior counts are replaced by final outcomes. Clients outside the selected batch remain closed. AzureDeck's saved accounts, sessions and settings are preserved.

The automatic setting is on by default under Settings > Launch & recovery. Repair now, Recheck installation and Cancel repair are also available. Progress remains visible and status/Discord commands stay responsive. Cancelling stops the wait; a running updater is allowed to finish so its writes are not interrupted.

Recovery allows one update and one fresh reinstall per episode. A confirmed healthy join plus a 30-minute cooldown permits a later independent episode. An explicit manual retry can reset the budget. Failed state writes retain the launch block and exhausted retry budget.

Downloads use the official HTTPS host with no account cookies or redirects, a 64 MB cap and publisher/signature verification before execution. Only AzureDeck's downloaded staging copy is cleaned up. The installed Roblox updater is kept intact so future updates and repairs remain possible.

Roblox describes reinstalling as replacing broken or deleted files in its [official reinstall guide](https://en.help.roblox.com/hc/en-us/articles/203312910-How-Do-I-Reinstall-the-Roblox-Software/). This is an official overwrite reinstall; AzureDeck does not delete its account vault or Roblox's installed updater.

See VALIDATION.md for executed checks. The official download/signature were verified without running the installer. Recovery/queue behavior was tested with injected synthetic operations; no real installation was changed and no live account was launched during validation.
