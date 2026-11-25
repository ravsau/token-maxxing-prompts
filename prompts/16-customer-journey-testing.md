# 16. Customer journey testing

Have browser agents act as real prospects with real goals, and fix where they get stuck.

**Copy-paste:**

```
Write 5 to 8 prospective customer personas for my site, each with a concrete goal
(compare prices, buy the cheapest plan, find a free resource, contact sales).

For each persona, use a browser to complete the goal on my site, in a test
environment or with test payment details. Record every step, every point of
confusion, every error, and the time taken. Save screenshots of each friction point.

For each friction point, find the root cause in the code or content. Fix the ones
with a clear cause on a branch and open a PR with before and after screenshots.
Where I have real user data (analytics, session recordings, support mail), check
that the friction you found matches real behaviour.
```

**Notes**
- Never use real payment details or submit real forms on production.
- Agent friction and human friction overlap but are not the same. Check against real data.

**Origin**
- From an AI assistant's answer to "how should I spend a large budget on my strongest
  model?" (November 2026). The ranking in that answer was its own guess.
- Limit: not yet run and measured by this repo. Open a PR with your result.
