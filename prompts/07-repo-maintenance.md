# 7. Repo maintenance sweep

Triage the backlog you've been ignoring — issues and PRs — and surface the next
high-value moves. Parallel workers make short work of a big backlog.

**Copy-paste:**

```
Do a maintenance sweep of this repo's issues and PRs. If the backlog is large, use
parallel workers on a smaller model and verify their flags yourself.

For issues and open PRs:
  - Identify duplicates and group them.
  - Flag stale items that need a human decision.
  - Rank the still-valid items by value-to-effort.

Output a single triage report with a recommended next 5 actions. Do NOT close,
merge, or comment on anything automatically — just propose. I make the calls.
```

**Notes**
- "Do not close anything automatically" is the guardrail — you review, it proposes.

**Origin**
- GitHub asked 500+ maintainers what they want from AI. Issue triage and duplicate
  detection were at the top. They want AI to propose, not to act.
  [GitHub Blog](https://github.blog/open-source/maintainers/how-github-models-can-help-open-source-maintainers-focus-on-what-matters/)
- Anthropic runs Claude on each new issue in its own repo to find duplicates.
  [Workflow file](https://github.com/anthropics/claude-code/blob/main/.github/workflows/claude-dedupe-issues.yml)
- Limit: we found no source for PR triage.
- Anthropic's repo also closes a duplicate automatically after 3 days with no
  objection. [Script](https://github.com/anthropics/claude-code/blob/main/scripts/auto-close-duplicates.ts)
  This prompt does not. A one-time sweep has no objection period, so you make the call.
