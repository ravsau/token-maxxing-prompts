# 5. ADRs from real code

The decisions are already in your code. They are just not written down. This job
writes them as architecture decision records (ADRs).

**Copy-paste:**

```
Write ADRs (architecture decision records) for the non-obvious choices already made
in this repo. Reverse-engineer them from the real code and the commit history.

For each ADR give: title, context, decision, status, consequences.

Rules:
  - Cite the files and commits each ADR is based on.
  - If the code and commits do not give the reason for a decision, write
    "rationale unknown". Do not invent a reason.
  - Keep each ADR short. Describe the decision, not the implementation.
```

**Notes**
- Code shows what was done, not why. The "rationale unknown" list is your list of
  questions for the people who know.

**Origin**
- Michael Nygard defined the ADR format in 2011.
  [Documenting Architecture Decisions](https://www.cognitect.com/blog/2011/11/15/documenting-architecture-decisions)
- Research on ADRs that an LLM writes from repositories and commits:
  [AgenticAKM](https://arxiv.org/abs/2602.04445) ·
  [ADRs from commits](https://arxiv.org/abs/2609.03721)
- Limit: in one study, reviewers found the ADRs too long and too near the
  implementation. The rules above are there for that reason.
