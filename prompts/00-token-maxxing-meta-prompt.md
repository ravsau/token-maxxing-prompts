# 0. The TokenMaxxing meta prompt

Start here. The other prompts each do one job. This one asks the model to look at
your actual world and tell you which jobs are worth the tokens.

It works best when the model already has context about you: a long chat history,
a project folder, notes, a repo, a task board, logs. Run the short version in the
tool that holds your context (ChatGPT web, Claude with memory, a local agent in
your project folder). Then take the ideas it returns into your coding agent and
build them before the reset.

## Short version

**Copy-paste:**

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

## Long version

Use this when you want the answer structured well enough to act on directly.

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

- The short version is usually enough. Reach for the long one when the model keeps
  returning shallow ideas.
- The quality of the answer depends on the context the model can see. In a fresh
  chat with no history you get generic output.
- Good use of spare tokens = existing information x synthesis x reusable output x a
  decision or action at the end.
- Bad use = more words, more brainstorming, more documents nobody opens.
- A rule worth putting in your `CLAUDE.md` or `AGENTS.md`: *when the token budget is
  abundant, spend it compressing accumulated information into reusable systems,
  evidence, tests or decisions — not on generating more ideas.*
