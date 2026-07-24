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
