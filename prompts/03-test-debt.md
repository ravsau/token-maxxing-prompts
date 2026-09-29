# 3. Test-debt pass

Testing is the ideal token sink: high value, low risk, produces artifacts you keep.

**Copy-paste:**

```
Do a test-debt pass on this repo. In order:

  1. Map coverage: which critical paths have no tests? Rank by blast radius
     (what breaks in production if this function is wrong).
  2. Write missing tests for the top untested critical paths. Real assertions,
     not smoke tests. Cover the edge cases, not just the happy path.
  3. Find flaky tests: run the suite a few times, flag any test that passes and
     fails non-deterministically, and diagnose why (timing, shared state, order
     dependence).
  4. Leave a prioritized report: what you added, what's still uncovered and why
     it matters, and which flaky tests need a human decision.

Run the suite at the end and paste the result.
```

**Notes**
- "Rank by blast radius" stops it from testing trivial getters to pad numbers.
- Flaky-test isolation alone is often worth the whole run.
- Keep a new test only if it builds, passes on repeated runs, and adds coverage.
  These are the filters that Meta's TestGen-LLM uses.

**Origin**
- Meta, TestGen-LLM: LLM-written tests that pass filters before engineers see them.
  [Paper](https://arxiv.org/abs/2402.09171)
- Google Testing Blog: causes of flaky tests and how to triage them.
  [2016](https://testing.googleblog.com/2016/05/flaky-tests-at-google-and-how-we.html) ·
  [2021](https://testing.googleblog.com/2021/03/test-flakiness-one-of-main-challenges.html)
- Limit: no source supports "rank by blast radius". That part is our own rule.
