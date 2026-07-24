# 4. Code archaeology

Point it at the parts of the repo nobody understands anymore. It has the patience
to read every old PR and neglected module; you don't.

**Copy-paste:**

```
Do code archaeology on this repo. Investigate the neglected and least-understood
parts: modules with the oldest last-touched dates, code with no tests and no
recent commits, and closed/merged PRs that changed core behavior.

Produce:
  1. A module map — what each major module does, its dependencies, and its role.
  2. Evidence-backed cleanup candidates: dead code, duplicated logic, abandoned
     experiments, config nobody reads. For each, cite the file and the evidence
     (no callers, superseded by X, last touched <date>).
  3. Anything surprising or risky you found along the way.

Do not delete or change anything. This is a mapping pass — I decide what to cut.
```

**Notes**
- Explicitly read-only. The value is the map, not premature deletion.
- Great for a codebase you inherited or haven't touched in months.
