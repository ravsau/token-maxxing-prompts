# 13. Revenue leak investigation

Find where traffic you already have fails to turn into money, then fix the worst leak.

**Copy-paste:**

```
Across every website I own, find where existing traffic is failing to become
revenue. Use the analytics and search data I can give you access to (GA4, Search
Console, payment dashboards, email tool exports).

For each site, map the path: landing page -> main call to action -> pricing or
offer -> checkout or sign-up -> email capture. For each step, record the number
you can measure and the source of the number. Mark anything you cannot measure.

Rank the leaks by money lost per month, using conservative numbers. For the top 3,
propose competing fixes, implement the strongest one on a branch, and say how we
will know it worked (metric, baseline, date to check). Missing tracking counts as a
leak: fix it first when it blocks the measurement.

Do not change pricing, send email, or deploy without my approval.
```

**Notes**
- Every number needs a source. A leak estimate without one is a guess.
- Broken or missing tracking is usually the first real finding.

**Origin**
- From an AI assistant's answer to "how should I spend a large budget on my strongest
  model?" (November 2026). The ranking in that answer was its own guess.
- Limit: not yet run and measured by this repo. Open a PR with your result.
