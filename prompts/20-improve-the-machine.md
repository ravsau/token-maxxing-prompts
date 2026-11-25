# 20. Improve the machine that improves your projects

The meta prompt for a big agent setup: spend the tokens on what makes every later
run better, not on one more feature.

**Copy-paste:**

```
Analyse my project portfolio, agent setup, past task runs, analytics, skills, and
the corrections I have made to agent output.

Your objective is to maximise the economic output of this system, not the amount
of code shipped.

Find the 10 highest-leverage improvements that would compound across several
projects. For each one:
  - Establish a baseline with evidence.
  - Investigate competing approaches.
  - Implement and test the strongest approach where it is safe to do so.
  - Package repeatable workflows into reusable skills.
  - Define measurable success criteria.
  - Add regression tests or an evaluation harness.
  - List the decisions that still need my judgement.

Use parallel agents and isolated worktrees where they help. Challenge your own
assumptions. A completed task is not the same as a good outcome.

Do not stop at recommendations when a safe, testable change is possible. Keep
production deploys, outside communication, spending, and irreversible changes
behind my approval. Prefer improvements that keep producing value after this
session ends.
```

**Notes**
- Token maxxing: spend 500k tokens redesigning five websites. Outcome maxxing: spend
  500k tokens on a tested method that keeps improving fifty.
- Pair it with [15](15-agent-eval-harness.md) so you can measure whether it worked.

**Origin**
- From an AI assistant's answer to "how should I spend a large budget on my strongest
  model?" (November 2026). The ranking in that answer was its own guess.
- Limit: not yet run and measured by this repo. Open a PR with your result.
