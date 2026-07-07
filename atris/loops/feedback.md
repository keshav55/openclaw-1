# Loop - Feedback

**Owner:** `team/issue-triage`
**Wiki:** [systems/loops.md](../wiki/systems/loops.md) — loop system overview; issue-triage owner context lives in `team/issue-triage/MEMBER.md`.
**Runner:** `gh issue list` against the upstream GitHub repo (`openclaw/openclaw`) — the real user-facing bug/feature intake for this project.

**Protects:** every user-reported bug or feature request on the upstream repo becomes
a tracked, labeled GitHub issue instead of vanishing into chat/DMs.

**Signal (green =):** the GitHub issue intake is reachable and has at least one open
issue — proof the pipe from users to tracked work is alive. Zero results or a command
failure (auth expired, API down, repo renamed) means the loop is broken, not idle.

**Check:** `gh issue list --repo openclaw/openclaw --state open --limit 1 --json number | jq -e 'length > 0'`

**Cadence:** per tick.

**Feeds:** quality.
**Fed by:** users, support, operators, telemetry.

## Log

- 2026-07-07: Scaffolded via `atris loops init`; owner was a TODO stub and Check was
  the vacuous `true`. Created `team/issue-triage/MEMBER.md` as real owner, replaced
  Check with `gh issue list --repo openclaw/openclaw --state open --limit 1 --json number | jq -e 'length > 0'`
  (verified live: exit 0, `true`, upstream repo has hundreds of open issues e.g. #101451, #101446).
  This check fails if `gh` auth breaks, the network is down, or the repo has zero open
  issues — it is not a static/vacuous probe.
