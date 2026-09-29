# 0. The TokenMaxxing meta prompt (long version)

The short version is in the [README](../README.md). Use this one when the short one
returns shallow ideas, or when you want an answer that you can act on directly.

**Copy-paste:**

```
You have a large context window and a generous token budget. Work out the
highest-leverage way to spend it on what I am currently doing.

First, inspect whatever context you can reach: recent work, notes, files,
repositories, task lists, project folders, logs, documents, conversations,
unfinished drafts, research, plans, goals and recurring problems. Do not assume I
use any particular system. Find the equivalent of each thing in whatever I do use.

Do not give me generic productivity advice or small tasks I could do myself. Find
work that suits a model that can read many sources, compare at scale, classify,
critique, reconcile, and produce large finished outputs.

Look especially for chances to:
  - synthesise scattered information into one reusable artifact
  - mine old work for assets worth reviving, combining, repackaging or finishing
  - find recurring mistakes, bottlenecks and failure modes, and write drills against them
  - convert repeated manual work into a system
  - compare or classify dozens of items against consistent criteria
  - turn raw information into decision-ready material, not summaries
  - build a source of truth: knowledge map, evidence library, glossary, canonical brief
  - stress-test a plan: one case for it, one case against it, then reconcile
  - build practice material from my real weaknesses
  - finish substantial work that is already part done
  - audit my existing systems for duplication, stale projects and unused output
  - find contradictions where two plans need the same time, money or attention
  - build evaluation mechanisms: tests, rubrics, scorecards, feedback loops
  - compress thinking I keep repeating into a reference
  - move work from "AI researches" to "human only approves"

For each task tell me: what it is, why it is high leverage, what information it
should inspect, the final deliverable, what you do, the small part I still do, and
why a large context window matters for it.

Group the tasks as QUICK WINS, DEEP WORK, SYSTEMS and EXPERIMENTS.

Start by naming what looks most important in my current work, and where unfinished
work is piling up. Then give me the 10-20 best tasks, ranked by the downstream work
they unlock — not by how interesting they are. Say plainly if some of my apparent
projects are a poor use of tokens. Prefer "turn what exists into leverage" over
"make another new thing".

Finish with: the top 3 tasks to start with, one underrated task, one place I am
wasting AI capacity, one large task I can hand off almost entirely to an agent, and
one meta-level change that would make all my future AI work more effective.
```

## Notes

- The quality of the answer depends on the context the model can see. In a fresh
  chat with no history you get generic output.
- Good use of spare tokens = existing information x synthesis x reusable output x a
  decision or action at the end.
- Bad use = more words, more brainstorming, more documents nobody opens.
- When you build the ideas, run the search and per-file work in subagents on a smaller
  model. Keep the large model for the plan and the final check.
- A rule worth putting in your `CLAUDE.md` or `AGENTS.md`: *when the token budget is
  abundant, spend it compressing accumulated information into reusable systems,
  evidence, tests or decisions — not on generating more ideas.*
