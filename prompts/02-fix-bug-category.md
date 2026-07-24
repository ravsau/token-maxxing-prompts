# 2. Fix one bounded category of bugs

Don't say "fix bugs." Pick one category, give it a definition of done and a command
that proves it worked. Bounded scope is what makes this safe to run unattended.

**Copy-paste:**

```
Fix one bounded category of bugs in this repo: <e.g. all unhandled promise
rejections / all missing null checks on API responses / all incorrect error
status codes>.

Rules:
  - Only touch that category. Do not refactor unrelated code.
  - Definition of done: every instance of this category is fixed or explicitly
    listed as "left alone, because <reason>".
  - After the changes, run <verification command, e.g. `npm test`, `pytest -q`,
    the linter> and paste the output. If it doesn't pass, keep going.
  - Produce a summary: what you changed, file by file, and what you deliberately
    skipped.

Open the work as a single focused commit/PR I can review in one sitting.
```

**Notes**
- The verification command is the whole point — no "done" claim without a passing run.
- Good categories: one lint rule, one exception type, one deprecated API call.
