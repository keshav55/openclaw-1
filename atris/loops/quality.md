# Loop - Quality

**Owner:** `team/quality-gate`
**Wiki:** [systems/loops.md](../wiki/systems/loops.md) — loop system overview; quality-gate owner context lives in `team/quality-gate/MEMBER.md`.
**Runner:** `pnpm lint` (`oxlint --type-aware`) — the project's own type-aware lint gate over `src/`, `extensions/`, and friends.

**Protects:** shipped changes do not introduce lint or type-aware regressions that make
the codebase harder to trust or operate.

**Signal (green =):** `pnpm lint` exits 0 across the whole tracked source tree. A
non-zero exit means a real lint/type-aware violation landed.

**Check:** `pnpm lint`

**Cadence:** per commit / per tick.

**Feeds:** feedback, release confidence, owner trust.
**Fed by:** feedback, reviews, incidents, failed checks.

## Log

- 2026-07-07: Scaffolded via `atris loops init`; owner was a TODO stub and Check was
  the vacuous `true`. Ran `pnpm install --frozen-lockfile` (no `node_modules` existed
  yet, 1m21s), created `team/quality-gate/MEMBER.md` as real owner, and replaced Check
  with `pnpm lint` (verified live: exit 0, "Found 0 warnings and 0 errors. Finished in
  15.7s on 3857 files with 136 rules"). This is oxlint's real type-aware pass over the
  actual source tree — it fails on any real lint/type violation, unlike a static probe.
