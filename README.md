# Token Maxxing: the prompt to run before your AI usage resets

You pay a flat monthly fee for Codex, ChatGPT, Claude Code, Claude, Gemini or Cursor.
The tokens don't roll over. When a reset lands, the leftover capacity evaporates —
you paid for it and got nothing back.

**This repo is one prompt.** Paste it into the tool that holds your context, and it
tells you what is actually worth building with the tokens you are about to lose.

---

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

There is also a [longer, more structured version](prompts/00-token-maxxing-meta-prompt.md)
for when the short one returns shallow ideas.

## How to run it

It works best if two things are true:

1. You have a lot of chat history about your projects in one place — ChatGPT web,
   Claude web, or a local agent that can read your folders. That history is what the
   prompt mines. In a fresh chat with no context you get generic output.
2. You also run a coding agent on your machine — Codex CLI, ChatGPT desktop, Claude
   Code, Cowork. That is what implements the ideas.

Use the chat tool to surface the ideas out of all your context. Then hand them to the
coding agent and build them before the reset.

## The rule

Only spend leftover tokens on work that leaves a **durable artifact** — something
committed, documented, decided, or reusable after the reset.

Good use of spare tokens = existing information x synthesis x reusable output x a
decision at the end. Bad use = more words, more brainstorming, more documents nobody
opens.

## See when your tokens actually expire

Most tools don't show this clearly. For Codex there's an unofficial endpoint the
community found — ask Codex or ChatGPT to query it for you:

```bash
curl -sS 'https://chatgpt.com/backend-api/wham/rate-limit-reset-credits'
```

Unofficial, and it needs your authenticated session. Treat it as a rough gauge. The
point is to know whether you have hours or days.

---

## If the answer is "work on this codebase"

The meta prompt often points at a repo. These seven are the ready-made versions of
the jobs it usually names, so you don't have to write the prompt again.

| # | Prompt | What you get back |
|---|--------|-------------------|
| 1 | [Parallel read-only repo audit](prompts/01-parallel-repo-audit.md) | A ranked bug/risk report from specialist reviewers |
| 2 | [Fix one bounded bug category](prompts/02-fix-bug-category.md) | A clean PR with a definition of done + verification |
| 3 | [Test-debt pass](prompts/03-test-debt.md) | Missing tests written, flaky tests isolated |
| 4 | [Code archaeology](prompts/04-code-archaeology.md) | A module map + evidence-backed cleanup candidates |
| 5 | [Documentation pass](prompts/05-documentation.md) | ADRs, runbooks, user flows built from the real code |
| 6 | [Mine sessions into a reusable skill](prompts/06-mine-into-skill.md) | The smallest reusable skill/CLI/subagent |
| 7 | [Repo maintenance sweep](prompts/07-repo-maintenance.md) | Triaged issues/PRs + next high-value actions |

Plus [bonus jobs](prompts/08-bonus.md): large legacy refactor, disk cleanup, and how
to conserve usage while you spend.

**Watch the caps.** Big parallel jobs burn fast. Most plans have a rolling ~5-hour cap
that can stop a job mid-run, plus a weekly cap. Write the plan first, then run.

---

## If you're not in a rush: unattended runs

A reset that is days away is a different job from one that is hours away. With time
to spare, the community pattern is to queue work and walk away, then review a pile of
pull requests in the morning. Three shapes show up again and again.

### Overnight batch jobs

Many small, independent, verifiable jobs across many repos. Nothing auto-merges — you
wake up to PRs and read them over coffee. One reported night produced 60 open PRs
across 21 repos: 12 repos scaffolded, 817 pages given metadata and JSON-LD, a
database migration in five sequential PRs, error monitoring added to four apps, and
four written cross-repo audits.
[Write-up](https://www.developersdigest.tech/blog/12-tools-in-one-night-with-claude-code)

Jobs that suit this shape:

- Add structured data or metadata to every page of a content site.
- Add error monitoring or logging to every service that lacks it.
- Write the missing README for every package in a monorepo.
- Backfill type annotations file by file.
- Generate a changelog from the real commit history, per release.
- Run the same audit across every repo you own and write one report each.
- Convert a directory of scripts into a tested CLI, one script per PR.
- Normalise dependency versions across repos and open one bump PR per repo.

### Large refactors, phased

The one job a big budget makes realistic. The recipe people converge on: write a
`PLAN.md` first, isolate the work in a git worktree, allowlist only the tools the job
needs, run the test suite between phases, and commit after each green phase. Reported
outcome is roughly 70% clean, 20% partial, 10% failed — so a resumable plan matters
more than a clever prompt.
[Playbook](https://trystandby.com/guides/run-claude-code-overnight) ·
[What breaks](https://medium.com/@evekhm/running-claude-code-autonomously-overnight-what-breaks-and-how-to-fix-it-3bee3bd958b5)

Refactors that survive an unattended run:

- Extract shared hooks or helpers into one module and migrate every caller.
- Deduplicate utility functions that drifted into four copies.
- Split one oversized module along a boundary you name in the plan.
- Migrate a database or ORM layer, one table per phase.
- Replace a deprecated library call across the codebase.
- Move from one test framework to another, directory by directory.
- Introduce a type layer into an untyped codebase, module by module.

### Spec-queue runners

Instead of one prompt, you hand the agent a queue of small specs and it works down the
list: implement, test, review, open a PR, next. By morning you get working branches
and one page saying what was built and what needs you.
[Example runner](https://github.com/igdutra/claude-overnight)

Queues worth filling:

- Ten bug reports, each written as a failing test plus the expected behaviour.
- Fifteen small features, each one screen or one endpoint.
- Twenty exercises with tests but no solution, for your own practice later.
- Every open issue labelled `good-first-issue` in your own repo.
- One spec per integration you keep meaning to add.

### Rules people learn the hard way

- Write the plan before the run. A rolling cap can stop a job mid-way; you want to
  resume, not restart.
- Use a worktree or a branch. Overnight changes should never land in your working tree.
- Allowlist tools. A job scoped to read, edit and test cannot start deleting things.
- Open PRs, don't merge. The review is the point.
- Run the tests between phases and stop on failure, rather than at the end.

### A note on the name

"Tokenmaxxing" now gets used two ways. One is a status game — burning tokens to prove
you are serious about AI, internal leaderboards and all.
[IBM's take](https://www.ibm.com/think/insights/tokenmaxxing-dead-long-live-valuemaxxing) ·
[origin of the term](https://mrprompts.substack.com/p/tokenmaxxing)

That is not this. This repo only means: you already paid for capacity that is about to
expire, so point it at something you will still have next week.

> Video walkthrough coming on [CloudYeti](https://www.youtube.com/@CloudYeti).
> Write-up: [cloudyeti.io/blog](https://cloudyeti.io/blog).

## Contribute your own

The meta prompt is only as good as the ideas people feed back into it. If you ran it
and got a job worth stealing, send it here.

- **A new job type** — open a PR that adds a bullet to the meta prompt's list, or a new
  file under `prompts/` in the same format as the existing ones.
- **A result** — open an issue with the prompt you ran, the tool you ran it in, and what
  it gave you back. Real examples help more than theory.
- **A better wording** — if a line in the prompt makes your model go generic, say so.

Keep the bar the same as the rule above: the job has to leave a durable artifact.

## Sources

Built from real community discussion, not invented:
- r/codex — [ideas on what to do with resets](https://www.reddit.com/r/codex/comments/1up0622/)
- r/codex — [how do you use resets](https://www.reddit.com/r/codex/comments/1uh20ru/)

More sources welcome — see above.

## License

MIT — see [LICENSE](LICENSE). Take them, change them, ship them.
