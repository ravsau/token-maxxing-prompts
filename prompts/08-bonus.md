# Bonus jobs

Three more good uses, plus how to spend without blowing your caps.

## Large legacy refactor

A big enough token budget is one of the few times a legacy refactor is realistic.

```
This is a large legacy codebase (<N> lines). Propose a future-proof structure.
First produce a plan: target module boundaries, the migration order, and the
risks — before touching anything. Then, only if I approve the plan, execute it in
small verifiable steps, running the test suite after each step. Stop and report if
anything fails.
```

Plan first. A rolling ~5-hour cap can kill a big refactor mid-run — you want a
resumable plan, not a half-migrated repo.

## Disk / workspace cleanup

```
Scan this project (or my dev workspace) for stale and idle files: build artifacts,
old logs, orphaned branches' leftovers, dependency caches, large files nobody
references. Produce a list with sizes and a reason each is safe to remove. Do not
delete anything — I'll confirm the list.
```

Read-only. It proposes, you delete.

## How to conserve usage while you spend

Spending leftover tokens doesn't mean burning them recklessly:

- Run subagents on a **smaller model** (e.g. a mini variant) for the grunt work.
- Turn **off fast mode** for background jobs — you're not waiting on them.
- Set a **lower reasoning level** for mechanical passes.
- **Cap subagent count** at ~6; more mostly duplicates and drains faster.
- **Plan before you run** so a job survives the 5-hour wall.
