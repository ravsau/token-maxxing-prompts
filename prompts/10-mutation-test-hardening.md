# 10. Mutation-guided test hardening

Coverage says a line ran. It does not say a test would fail if the line was wrong.
This job finds the bugs your tests would miss, then writes the tests that catch them.

**Copy-paste:**

```
Harden the tests for <module> against one class of bug: <e.g. wrong boundary
checks / missing permission checks / currency rounding>.

  1. Write realistic mutants of the code for that class only. One small change each.
  2. Drop any mutant that behaves the same as the original.
  3. Run the existing test suite against each mutant. List the mutants that survive.
  4. For each survivor, write a test that fails on the mutant and passes on the
     original. Run both to prove it.
  5. Keep only the tests that you proved. Never leave a mutant in the code.

Work in a separate branch. Report: mutants made, mutants that survived, tests added,
and survivors you could not kill, with the reason.
```

**Notes**
- Name one bug class. "All bugs" gives you hundreds of trivial mutants.
- Step 4 is the verification. A test that was not run against its mutant proves nothing.
- If you use subagents, a smaller model can write the mutants. Keep the large model
  for step 2 and step 4.

**Origin**
- Meta, ACH (FSE 2025). Engineers name a bug class, the system writes mutants and
  then the tests that catch them.
  [Paper](https://arxiv.org/abs/2501.12862) ·
  [Engineering at Meta](https://engineering.fb.com/2025/02/05/security/revolutionizing-software-testing-llm-powered-bug-catchers-meta-ach/)
- Limit: the evidence is for one bug class (privacy) in Kotlin. The paper reports that
  a plain LLM filter misses many equivalent mutants, so examine the survivors yourself.
