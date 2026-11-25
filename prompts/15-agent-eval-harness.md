# 15. Evaluation harness for your agents

Find out from your own data which tasks need your most expensive model and which
run fine on a cheaper one.

**Copy-paste:**

```
Collect 30 to 50 tasks my agents have already done, where we know the right
outcome (merged PRs, accepted drafts, fixed bugs, rejected attempts).

Build a small harness that replays each task in an isolated worktree with
different setups: model, prompt, skills loaded, harness config. For each run,
record correctness against the known outcome, cost, wall-clock time, and how much
human correction it needed.

Report a table of task type x setup. Name the cheapest setup that passes each task
type. Save the harness and the task set in the repo so I can re-run it when models
or prompts change.
```

**Notes**
- The task set with known answers is the expensive part. Keep it and reuse it.
- Run it on your subscription harness. A script that calls a paid API can burn a lot
  of money fast; decide that before you start.

**Origin**
- From an AI assistant's answer to "how should I spend a large budget on my strongest
  model?" (November 2026). The ranking in that answer was its own guess.
- Limit: not yet run and measured by this repo. Open a PR with your result.
