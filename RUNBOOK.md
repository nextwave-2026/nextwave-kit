# Hackathon runbook — shared operating context

Single starting point for every operator and every agent instance working this event. Read this
before doing anything else; it is deliberately short. Where it disagrees with an older note,
this file wins.

**Source of truth for competition facts:** <https://nextwave-hackathon-2026.vercel.app/>.
Re-check it Friday night — the schedule has already been revised once, and Luma's event metadata
still carries the superseded Friday start.

## 1. Event facts (Bogotá)

| When | What |
| --- | --- |
| Sat 29 Aug 09:00 | Check-in, doors open |
| Sat 29 Aug 09:30 | Opening talk |
| Sat 29 Aug 10:00 | Challenges announced |
| **Sat 29 Aug 10:30** | **T-ZERO — 24 hours on the clock** |
| **Sun 30 Aug 10:30** | **Code freeze — submissions locked** |
| Sun 30 Aug 11:00–13:00 | Pitches, 10 minutes per team |
| Sun 30 Aug 13:30 | City champions announced |
| Sun 30 Aug 14:30 | Champions' final pitch, 15 min (10 pitch + 5 Q&A) |

All times local to each site. Four challenges, sealed until kickoff. **Each team takes exactly one,
and the pick is final.** No restriction on framework, protocol or language; invented data, flows,
APIs and databases are explicitly allowed, but every choice must be defensible.

## 2. How we are judged — read this before choosing scope

Three standing directives: **depth over difficulty**, **working beats promised**, **judgment beats
spectacle**.

Five lenses, in weight order:

1. **Functionality** — runs end to end and withstands live modification *without team intervention*
2. **Depth & judgment** — defensible architecture; the team can articulate decisions, rejected
   alternatives and trade-offs
3. **Problem-solving** — addresses the challenge objective including edge cases
4. **Originality** — beyond the standard solution
5. **Experience & clarity** — usable interface; pitch, demo and docs legible to outsiders

**Does not score:** feature count, code volume, framework name-dropping, a polished video without
live function, visible rubric-chasing.

Format per team: short pitch → live demo → **trial by fire** → technical Q&A, 10 minutes total.
Trial by fire means *judges operate our system live with unrehearsed input*. Build for that.

**Required deliverables:** slides, live demo, public GitHub repo with README, architecture diagram,
and a **decision log**. The decision log is written by humans — judges ask us, not the code.

Organisers' own advice, and it matches the rubric: get the thinnest possible version working end to
end in the first hours, then deepen. Do not front-load polish.

## 3. Rules that constrain how we work

- **Event IP (5.1–5.4):** economic rights in work developed *during* the event transfer to the
  organisers.
- **Pre-existing IP (5.7):** stays ours, but must be authored beforehand, live in its own
  repository, and be declared. **This kit must never share git history with the entry repository** —
  copy files in, never merge. The entry's first commit and README declare the provenance; never
  remove either.
- **No substantially-finished projects (4.2):** declared scaffolding and tooling are fine, a working
  solution is not. The kit stays infrastructure — no domain logic.
- **Strong copyleft banned (5.8):** no GPL/AGPL. Every third-party component must be identified in
  the documentation. Run `make licences` before submission.
- **AI tooling permitted (4.2, 5.9)**, with no disclosure obligation.
- **Confidentiality, 5 years (6.2):** sealed briefs, credentials, non-public information. Keep any
  public posting integrations inert during the event.
- **No guaranteed connectivity or backup (10.1):** two full clones on two machines is the backup.

## 4. Operating model

**Two independent operators; the git repository is the only coordination bus.** There is no peer
messaging channel between the two sides and none will be improvised during the event.

- `DECISIONS.md` — append-only, newest at the bottom, union-merged so simultaneous appends survive.
- `INTERFACES.md` — edited in place, deliberately *not* union-merged. A conflict here means stop and
  reconcile the boundary; two contradictory "current" interfaces is worse than a conflict.
- Crew size is settled: we compete as two. Not revisited. If organisers *assign* additional members
  at check-in, absorb it as news — it is not a decision to prepare for.
- Separate credentials on each side, so model allowances are independent rather than one shared
  ceiling.

## 5. Unattended work (`gnhf`) — conditional, one job only

`gnhf` runs a coding agent in a loop unattended, committing each successful iteration. Assessed
2026-08-26. **Verdict: conditional go, gated on a timed validation run before the event.** If that
run does not pass, we drop it rather than debug it.

**Use it for exactly one thing:** overnight adversarial test-hardening of an already-working thin
slice — generate edge-case tests, fix what breaks. That buys robustness under trial by fire, the
highest-weighted lens.

**Do not use it for** new features. Code volume does not score, and code nobody can explain is a
liability in the technical Q&A. It also cannot write the decision log.

Hard bounds when it runs:

- Isolated worktree, side branch, **never the demo branch, never auto-push**.
- Bound the run by **iteration count**, never by the token cap — the token counter is known to
  under-report badly, so it will not stop a runaway.
- Our provider windows **do not reset before the pitch**. A run that burns the budget overnight
  leaves us dry at freeze time, which is the most expensive hour to lose.
- A human reviews every commit before anything merges. Nothing lands unattended.

## 6. Staying in sync

This repository is the shared context. Pull before starting a session; push operating changes here,
not into private notes. Record cross-side decisions in `DECISIONS.md` and interface boundaries in
`INTERFACES.md`. Keep this runbook operational — decisions and current state, not discussion history.
