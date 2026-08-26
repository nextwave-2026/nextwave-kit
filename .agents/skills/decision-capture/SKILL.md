---
name: decision-capture
description: "Activate at decision-shaped moments during work: when rejecting a real alternative, cutting scope deliberately, accepting a constraint, taking a time-pressure trade-off, or changing design after a failure."
---

# Decision capture

Log only decisions that changed direction or scope. Routine implementation, naming, ordinary refactors, dependency picks with no real alternative, and facts already obvious in the diff do not earn entries.

When a qualifying moment occurs, ask the human for the rationale before recording it. Append this four-field shape to `DECISIONS.md`:

```text
Time: <ISO 8601 UTC time>
Decision: <what was decided>
Instead of: <the rejected alternative>
Because: <the human's exact words or fragment>
```

The agent writes **what** was decided and **when**. The human supplies **why**, in their own words. Never invent, infer, or reconstruct the `Because` field. Ask for it, accept a fragment, and record that fragment verbatim. If the human has not supplied a rationale, do not fabricate an entry. Append at the bottom; do not rewrite earlier entries. Commit this coordination update straight to `main`, not on a code branch or PR.
