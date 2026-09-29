# 9. Make it faster (benchmark loop)

Many measure-change-measure cycles. Each cycle is cheap to check and expensive to
run, which is what spare capacity is for.

**Copy-paste:**

```
Make <target, e.g. the /search endpoint, the build, this function> faster.

Before you change anything, write down and freeze:
  - the benchmark command and the metric
  - the correctness gate: <test command> must pass
  - counter-metrics you may not make worse: <e.g. peak memory, test count>
  - the baseline, measured 3 times, with the noise between runs

Then loop, on a separate branch:
  1. State one hypothesis.
  2. Make one change for it.
  3. Run the correctness gate, then the benchmark.
  4. Keep the change only if the metric improves by more than twice the noise
     and the gate passes. Otherwise revert it.

Stop after <N> rounds, or after 3 rounds with no gain. Give me a ledger of every
variant: hypothesis, result, kept or reverted. Commit each kept change separately.
```

**Notes**
- The frozen benchmark is the guardrail. An agent that can edit the benchmark will
  improve the number and not the code.
- The reverted variants in the ledger are useful. They tell you what not to try again.

**Field report**
- DHH converted Campfire from Rails to Rust on a personal subscription, for less than
  $10 in tokens. His tuning prompt was "Make it go faster". His benchmarks show 20 to
  95 times more requests per second. He also says the code is ugly and 6 times as
  verbose. [Post](https://x.com/dhh/status/2104811922348450056)
- The short prompt worked because the benchmarks already existed. This prompt makes
  you write them first.

**Origin**
- Andrej Karpathy's autoresearch: a fixed budget, one metric, keep the change or
  discard it. [autoresearch](https://github.com/karpathy/autoresearch)
- Google DeepMind's AlphaEvolve is the earlier loop with automated evaluators.
  [AlphaEvolve](https://deepmind.google/discover/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/)
- A general-purpose version for code: [autoloop](https://github.com/sweekuh/autoloop)
- Limit: the reported results for code are from the authors' own runs. There is no
  controlled comparison.
