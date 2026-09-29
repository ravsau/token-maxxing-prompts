# 8. Large legacy refactor

A big token budget is one of the few times a legacy refactor is realistic.

**Copy-paste:**

```
This is a large legacy codebase (<N> lines). Propose a future-proof structure.
First write PLAN.md: target module boundaries, the migration order, and the
risks — before touching anything. Then, only if I approve the plan, execute it in
a separate branch or worktree, in small verifiable steps. Run the test suite after
each step and commit after each green step. Stop and report if anything fails.
```

**Notes**
- A usage cap can stop a big refactor mid-run. The plan and the per-step commits let
  you resume.

**Origin**
- OpenAI: a plan file with small milestones and a validation command for each.
  [Long horizon tasks with Codex](https://developers.openai.com/blog/run-long-horizon-tasks-with-codex) ·
  [PLANS.md](https://developers.openai.com/cookbook/articles/codex_exec_plans)
- Anthropic: a progress file and a git commit for each unit of work.
  [Harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents)
- Google: [Software Engineering at Google, ch. 22](https://abseil.io/resources/swe-book/html/ch22.html)
