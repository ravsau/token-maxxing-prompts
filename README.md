# Token Maxxing: prompts to run before your AI usage resets

You pay a flat monthly fee for Codex, Claude Code, or a Max/Pro plan. The tokens
don't roll over. When a weekly reset is about to expire, the leftover capacity
just evaporates — you paid for it and got nothing back.

This is a small pack of prompts that turn that expiring capacity into something
that's still useful next week: a bug list, missing tests, real docs, a reusable
skill. Copy-paste, point at your repo, walk away.

Works with Codex CLI and Claude Code (the prompts are model-agnostic).

> A video walkthrough is coming on [CloudYeti](https://www.youtube.com/@CloudYeti).
> Write-up: [cloudyeti.io/blog](https://cloudyeti.io/blog).

## First: see when your tokens actually expire

Most tools don't show this clearly. For Codex there's an unofficial endpoint the
community found — ask Codex/ChatGPT to query it for you:

```bash
curl -sS 'https://chatgpt.com/backend-api/wham/rate-limit-reset-credits'
```

Unofficial and requires your authenticated session; treat it as a rough gauge,
not a guarantee. The point is to know whether you have hours or days before a
reset drops.

## The rule

Only spend leftover tokens on work that leaves a **durable artifact** — something
committed, documented, or reusable after the reset. Burning tokens for the sake
of burning them is not productivity.

## The prompts

| # | Prompt | What you get back |
|---|--------|-------------------|
| 1 | [Parallel read-only repo audit](prompts/01-parallel-repo-audit.md) | A ranked bug/risk report from specialist reviewers |
| 2 | [Fix one bounded bug category](prompts/02-fix-bug-category.md) | A clean PR with a definition of done + verification |
| 3 | [Test-debt pass](prompts/03-test-debt.md) | Missing tests written, flaky tests isolated |
| 4 | [Code archaeology](prompts/04-code-archaeology.md) | A module map + evidence-backed cleanup candidates |
| 5 | [Documentation pass](prompts/05-documentation.md) | ADRs, runbooks, user flows built from the real code |
| 6 | [Mine sessions into a reusable skill](prompts/06-mine-into-skill.md) | The smallest reusable skill/CLI/subagent |
| 7 | [Repo maintenance sweep](prompts/07-repo-maintenance.md) | Triaged issues/PRs + next high-value actions |

Plus [bonus jobs](prompts/08-bonus.md): large legacy refactor, disk cleanup, and
how to conserve usage while you spend (smaller subagent models, non-fast mode).

## Watch the caps

Big parallel jobs burn fast. On most plans there's a rolling ~5-hour cap that can
stop a job mid-run *and* a weekly cap. Write the plan first, then run — don't let
a 6-subagent review die halfway because you hit the 5-hour wall.

## Sources

Built from real community discussion, not invented:
- r/codex — [ideas on what to do with resets](https://www.reddit.com/r/codex/comments/1up0622/)
- r/codex — [how do you use resets](https://www.reddit.com/r/codex/comments/1uh20ru/)

## License

MIT — see [LICENSE](LICENSE). Take them, change them, ship them.
