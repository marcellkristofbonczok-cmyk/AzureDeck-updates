# AzureDeck 2.0.2 — Accounts blocked by channel compatibility

Version 2.0.1 could skip accounts with “This account's observed channel requires a different Player deployment” even though a usable Player was installed. It promoted a historical engine UpdateController query URL into an authoritative per-account deployment requirement, then treated differing running builds as incompatible without sufficient evidence.

Selection now uses the current launcher configuration, installation reference and fresh local inventory. Saved engine-query channels remain diagnostic hints only; they cannot switch channels, select another build or request an installation. This does not claim that the configured channel predicts every future server-side account assignment.

Healthy processes keep running. Their complete bundles are validated independently instead of rejecting differing GUIDs outright. An already-installed additional build may be selected only when its complete bundle, GUID and full executable version agree with current public deployment metadata, after file settling. The existing cohort's primary pin stays intact. This direct launch does not mutate global registration/channel state, change shared graphics settings while clients run, or start an updater. Existing adopted-process verification and installer guards remain active.

Missing, incomplete, changing or version-mismatched targets still require safe supported maintenance. Diagnostics identify running and required GUIDs/versions and the selected channel. Unavailable targets are not blindly launched, and shared files are not reinstalled beneath healthy sessions.

Update using Settings > App updates, or download the new executable from the release. Retry the skipped accounts after updating; no account deletion or cookie re-entry is required for this particular regression. The existing app updater may require Roblox to be closed before application replacement.

See VALIDATION.md for actual test counts and executable hash. Real Roblox account gameplay, mixed-build server acceptance and genuine installer recovery were not exercised. Roblox can enforce updates or end sessions, and future server/channel compatibility cannot be guaranteed. A required maintenance operation can still wait for healthy sessions/external installation writers to finish. No injection, binary patching, registry modifications or anti-cheat bypass was added.
