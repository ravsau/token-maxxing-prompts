# 7. Repo maintenance sweep

Triage the backlog you've been ignoring — issues and PRs — and surface the next
high-value moves. Parallel workers make short work of a big backlog.

**Copy-paste:**

```
Do a maintenance sweep of this repo's issues and PRs (use parallel workers if the
backlog is large).

For issues and open PRs:
  - Identify duplicates and group them.
  - Flag anything that looks already-fixed in the current code (cite the code).
  - Flag stale items that need a human decision.
  - Rank the still-valid items by value-to-effort.

Output a single triage report with a recommended next 5 actions. Do NOT close,
merge, or comment on anything automatically — just propose. I make the calls.
```

**Notes**
- "Do not close anything automatically" is the guardrail — you review, it proposes.
- Finding already-fixed issues alone can clear a lot of noise.
