# v2 requirements coverage and investigation

Current behavior is refined in RELEASE-2.0.1.md: fresh validated launcher references and full channel/version checks, stable active cohorts, fatal/healthy updater separation, bounded retry/resume/replay, and account-matched channel diagnostics. The final user brief rejects timestamp-based selection and prioritizes preserving healthy sessions.

| Requested area | Implementation/evidence | Practical limit |
| --- | --- | --- |
| Development autonomy | Implemented, built and tested in the supplied workspace; release workflow publishes verified artifacts. | No OS security prompt bypass or assumed external approval. |
| Installer investigation | Code review found periodic Bloxstrap preparation against shared state, stale version/channel selection and entire-batch replay. Deployment/protocol/lineage diagnostics now identify future events. | No real failing launch was observed during development; these are verified old code paths and cause candidates, not proof of the user's exact failure. |
| Installation/version manager | Complete-bundle validation, per-backend discovery, channel/public version metadata, stale-path refresh, supported update/reinstall, persistent budgets. | Offline metadata cannot prove server compatibility; Bloxstrap itself must be installed at its supported path. |
| Launch orchestration | Keyed bounded workers, adaptive concurrency, native spacing, hardware gates, account-specific confirmation, timeout, retry/backoff and duplicate protection. | Four startup confirmations maximum; the games themselves consume resources outside AzureDeck. |
| Installer conflicts | Timed lineage and publisher checks, owned jobs, fatal-dialog closure, shared maintenance future, pause/resume and retained queue. | Unrelated healthy installers are not force-killed; external writers must finish. |
| Direct launch | Validated Player URI launch, fresh tickets, cache refresh, supported Bloxstrap preparation/fallback. | Player still enforces updates; no compatibility bypass. |
| Self-healing | Existing watchdog plus crash/Unknown/disconnect rules, cancellation generations, exponential recovery and bounded incidents. | Expired sessions, kicks/access denial and exhausted repair budgets need attention. |
| Update scheduling | Exclusive creation gate; active sessions and writers defer shared-file maintenance; affected work resumes. | Maintenance can remain queued while sessions remain active indefinitely. No seamless forced-update guarantee. |
| Structured diagnostics | Rotating JSONL field whitelist, account/path/version/channel/PID/parent/duration/exit/attempt/category/action fields. | Unknown parent/channel values are explicit; raw command lines are excluded. |
| Existing features | Existing account/group/Discord/browser/macro/graphics/config/UI routes retained; regression suite rerun. | Live Discord/private-server behavior was not exercised. |
| Automated verification | Single/sequential/50-account/concurrent/exception/adaptive/cancel/restart tests plus native controlled process, installer, capture and updater probes. | Synthetic account callbacks are not real Roblox game launches. |
| Efficiency | Four fixed workers sleep on a condition variable; retained process handles, incremental logs, bounded caches, five-second installer scans and bounded diagnostics. | Platform UI/OCR and resource monitoring retain bounded polling; no real 50-game performance benchmark. |
| Final delivery | v2.0.0 executable/resource/manifest, source package, release notes and continuation documentation. | Publication is confirmed only after the GitHub workflow and anonymous asset verification. |

Bloxstrap's own documentation explains that current Player builds process launch URIs and may start RobloxPlayerInstaller when an update is required, even when launched directly. See https://github.com/bloxstraplabs/bloxstrap/wiki/A-deep-dive-on-how-the-Roblox-bootstrapper-works and the upstream Bootstrapper implementation at https://github.com/bloxstraplabs/bloxstrap/blob/v2.11.4/Bloxstrap/Bootstrapper.cs. Registration mismatch is inspected but does not select an arbitrary executable in AzureDeck's direct path. Account-specific native Home authentication with many clients remains an unverified separate platform issue.

## 2.0.2 correction to channel/cohort interpretation

Saved engine update-query channels are diagnostic hints, not persistent account assignments. Current launcher/reference selection governs launches. Different installed GUIDs do not alone prove process incompatibility: a separate complete bundle matching current deployment metadata can launch without switching the primary live pin or global channel. Missing/unverified builds still wait for safe maintenance. Real mixed-build gameplay/server compatibility is not guaranteed or claimed tested.
