# 1. Parallel read-only repo audit

The single best use of a big token budget: many read-only reviewers, each with its
own context window, each looking for one class of problem. They find far more than
one agent reading the whole repo does.

**Copy-paste:**

```
Audit this repository using parallel read-only subagents. Spawn one specialist
reviewer per area, each in its own context window, on a smaller model, and do NOT
let any of them modify files:

  - Security (secrets, injection, auth gaps, unsafe deserialization)
  - Correctness / business logic (wrong behavior, edge cases, off-by-one)
  - Regressions (recent changes that break existing behavior)
  - Architecture (coupling, boundary violations, dead layers)
  - Performance (N+1s, needless allocation, blocking calls)
  - Test coverage (untested critical paths)

Each reviewer reports findings to the main thread. The main thread verifies each
finding against the actual code (drop anything it can't reproduce), dedupes, and
returns ONE ranked report: severity, file:line, why it's a problem, and the
smallest fix. Do not change any code — this pass is read-only.
```

**Notes**
- Cap at ~6 reviewers. More than that mostly duplicates.
- Ask it to verify each finding before reporting — kills the plausible-but-wrong noise.
- The main thread stays on the large model. It does the verification, which is where
  a smaller model makes mistakes.

**Origin**
- Anthropic's Code Review for Claude Code uses the same shape: parallel agents, one
  class of issue each, then a verification step that removes false positives.
  [Code Review docs](https://code.claude.com/docs/en/code-review) ·
  [Subagents docs](https://code.claude.com/docs/en/sub-agents)
- OpenAI's Codex docs show a "one agent per point" review example.
  [Codex subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents)
- Limit: a reviewer that you tell to find problems usually reports some, even in good
  code. Ask for findings that change behaviour only.
  [Best practices](https://code.claude.com/docs/en/best-practices)
