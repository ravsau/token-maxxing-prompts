# 5. Documentation pass

Docs written from the actual code, not a generic template. This is the artifact
that keeps paying off long after the reset.

**Copy-paste:**

```
Write documentation for this repo, derived from the real code — not boilerplate.

Produce, where the code justifies it:
  - ADRs (architecture decision records) for the non-obvious choices already made,
    reverse-engineered from the code and commit history.
  - A runbook: how to deploy, roll back, and handle the top 3 failure modes.
  - The main user flows, described step by step from entry point to result.
  - UAT scenarios: concrete acceptance checks a human can run before a release.

Cite the files each doc is based on. If something is ambiguous, write the question
down instead of guessing.
```

**Notes**
- "Cite the files" and "write the question down" keep it honest instead of fluent-but-wrong.
- ADRs from existing code are surprisingly good — the decisions are already there, just undocumented.
