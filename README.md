# Token Maxxing: the prompt to run before your AI usage resets

You pay a flat monthly fee for Codex, ChatGPT, Claude Code, Claude, Gemini or Cursor.
The tokens don't roll over. When a reset lands, the leftover capacity is gone.

**This repo is one prompt.** Paste it into the tool that holds your context, and it
tells you what is worth building with the tokens you are about to lose.

## The TokenMaxxing meta prompt

```
I have a lot of AI tokens left before my usage resets, and I want to spend them on
high-leverage work instead of wasting them.

Based on what you know about me — my recent work, projects, notes, files, logs and
goals — give me 10-15 substantial tasks that would genuinely benefit from a lot of
tokens and a large context window.

Think along these lines:
  - mine old or unfinished projects for valuable ideas or assets
  - analyse past work or content and find patterns, opportunities, things worth reviving
  - evaluate whether an existing workflow or "factory" actually produces good results,
    before I optimise it
  - audit my recurring systems, agents, automations and processes; find what is broken,
    duplicated, or produces output nobody uses
  - synthesise scattered notes and logs into reusable knowledge, decisions, or
    source-of-truth documents
  - find recurring mistakes, bottlenecks, and things I keep relearning
  - stress-test an important project or plan
  - turn repeated manual work into a system
  - find contradictions or neglected opportunities across everything I am working on
  - take something partly built and do the heavy work needed to get it near finished

Do not give me generic productivity tasks or random brainstorming. Favour work where
you can read a lot, compare a lot, synthesise deeply, and leave me with something
reusable or actionable.

For each idea, say briefly what you would actually do and what output I would get.

Prioritise ideas that turn things I already have into more leverage.
```

If the short one returns shallow ideas, use the
[longer version](prompts/00-token-maxxing-meta-prompt.md).

## How to run it

1. Run the prompt where your history lives: ChatGPT web, Claude web, or a local agent
   in your project folder. In a fresh chat with no context you get generic output.
2. Hand the ideas to a coding agent on your machine (Codex CLI, Claude Code, Cowork)
   and build them before the reset.

## The rule

Only spend leftover tokens on work that leaves a **durable artifact**: something
committed, documented, decided, or reusable after the reset.

## Ready-made prompts

The meta prompt often points at a repo. These are the jobs it usually names. Each
file cites where the method originated and states the limit of that evidence.

| # | Prompt | What you get back |
|---|--------|-------------------|
| 1 | [Parallel read-only repo audit](prompts/01-parallel-repo-audit.md) | A ranked bug/risk report from specialist reviewers |
| 2 | [Fix one bounded bug category](prompts/02-fix-bug-category.md) | A clean PR with a definition of done + verification |
| 3 | [Test-debt pass](prompts/03-test-debt.md) | Missing tests written, flaky tests isolated |
| 4 | [Code archaeology](prompts/04-code-archaeology.md) | A module map + evidence-backed cleanup candidates |
| 5 | [ADRs from real code](prompts/05-adrs-from-code.md) | Decision records with cited files and commits |
| 6 | [Mine sessions into a reusable skill](prompts/06-mine-into-skill.md) | The smallest reusable skill/CLI/subagent |
| 7 | [Repo maintenance sweep](prompts/07-repo-maintenance.md) | Triaged issues/PRs + next high-value actions |
| 8 | [Large legacy refactor](prompts/08-large-refactor.md) | A phased plan, then verified steps with a commit each |
| 9 | [Benchmark optimization loop](prompts/09-benchmark-optimization-loop.md) | Measured speed gains + a ledger of every variant |
| 10 | [Mutation-guided test hardening](prompts/10-mutation-test-hardening.md) | Tests proven to catch one class of bug |

## Rules for big and unattended runs

- **Write the plan first.** Most plans have a rolling ~5-hour cap and a weekly cap. A
  cap can stop a job mid-run. A `PLAN.md` lets you resume instead of restart.
- **Use a worktree or a branch.** Unattended changes never land in your working tree.
- **Allowlist tools.** A job scoped to read, edit and test cannot delete things.
- **Open PRs, don't merge.** The review is the point.
- **Run the tests between phases** and stop on failure.
- **Use smaller subagents.** Run the grunt work (search, per-file edits, first-pass
  review) on a smaller model with fast mode off. Keep the large model for the plan,
  the verification of findings, and the final report.
- **Cap parallel subagents at ~6.** More mostly duplicates.

Further reading on overnight runs:
[playbook](https://trystandby.com/guides/run-claude-code-overnight) ·
[what breaks](https://medium.com/@evekhm/running-claude-code-autonomously-overnight-what-breaks-and-how-to-fix-it-3bee3bd958b5) ·
[60 PRs in one night](https://www.developersdigest.tech/blog/12-tools-in-one-night-with-claude-code) ·
[spec-queue runner](https://github.com/igdutra/claude-overnight)

## Contribute

Ran it and got a job worth stealing? Open a PR with a new file under `prompts/`, or an
issue with the prompt, the tool, and the result. The job must leave a durable artifact.

## Sources

- r/codex — [ideas on what to do with resets](https://www.reddit.com/r/codex/comments/1up0622/)
- r/codex — [how do you use resets](https://www.reddit.com/r/codex/comments/1uh20ru/)

Video walkthrough coming on [CloudYeti](https://www.youtube.com/@CloudYeti).
Write-up: [cloudyeti.io/blog](https://cloudyeti.io/blog).

## License

MIT — see [LICENSE](LICENSE).
