# 6. Mine your history into a reusable skill

Turn the work you've already done into a tool you can reuse. This compounds — every
future session gets cheaper.

**Copy-paste:**

```
Look back over my recent sessions, saved memories, and the corrections I've made
to you in this project. Find the workflow I repeat most often — the thing I keep
re-explaining or re-typing.

Then build the SMALLEST reusable version of it: a skill, a subagent definition, a
CLI script, or a saved prompt — whatever fits. Requirements:
  - It captures the pattern, not one specific instance.
  - It's documented well enough that I (or another agent) can use it cold.
  - It's the minimum that works. No framework, no config sprawl.

Show me the workflow you identified and why, then the artifact.
```

**Notes**
- The best token sink there is: it makes every later run cheaper.
- Ask for the *smallest* version — otherwise you get an over-engineered framework.
- Bigger version: mine failed attempts, PR review comments and human corrections
  too, and give each skill a few test cases with known good output so you can tell
  when an edit makes it worse. Measure with [prompt 15](15-agent-eval-harness.md).

**Origin**
- Anthropic: ask the agent to capture its successful approaches and common mistakes
  in a skill.
  [Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)
- OpenAI: "Keep each skill focused on one job."
  [Skills in ChatGPT and Codex](https://learn.chatgpt.com/docs/build-skills)
- Limit: no source measures the benefit, and no source describes a pass over many old
  sessions.
