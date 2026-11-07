# 11. Find the implicit state machines

A whole-repo read. The agent traces every place where state changes (booleans,
timestamps, nullable fields, `if` checks) and rebuilds the lifecycles your app
actually has. It needs a large context and a lot of reading, which is what spare
capacity is for.

**Copy-paste (short):**

```
find all of the implicit state machines in my app
```

**Copy-paste (a report you can act on):**

```
Audit this codebase for implicit state machines.

Find workflows where states and transitions are encoded indirectly through
booleans, enums, timestamps, status fields, conditionals, or async events.

For each workflow:
1. List the states and the valid transitions.
2. Point to the relevant files and lines.
3. List invalid or contradictory states the current code allows.
4. Look for race conditions, missing transitions, and inconsistent state handling.
5. Rank the findings by real bug risk.
6. Say whether an explicit state machine would help, or whether simple conditionals are enough.

Do not modify code. Put concrete issues before theoretical ones.
```

**Notes**
- An implicit state machine is a lifecycle that nobody wrote down. There is no status
  enum and no list of allowed moves. The state lives in flags and timestamps spread
  across many files, so the app can reach combinations nobody planned, such as a
  cancelled user who still has access.
- Run the short one first. Use the long one when you want file and line references
  and a ranked list.
- Keep the audit read-only. Fix the top few findings on a branch: one enum, one
  `canTransition(from, to)` check, and one test for each transition.
- To stop new ones, add a "no implicit state machines" rule to `CLAUDE.md` or
  `AGENTS.md`. The rule text is on the
  [full page](https://github.com/ravsau/god-tier-prompts/blob/main/prompts/01-implicit-state-machines.md#keep-new-ones-out).

**Field report**
- Lars Trieloff (Adobe) ran it on helix-opspile. Only one table had a real status
  column. The rest of the state lived in nullable timestamps, leases and in-memory
  flags. The first known defect: a reply can post twice on Retry.
  [Post](https://x.com/trieloff/status/2116867892797165660) ·
  [Issue](https://github.com/adobe/helix-opspile/issues/233)
- Daniel Lockyer posted his agent's summary: "I found about 70 implicit state machines."
- More receipts, and the refactors that followed (Foundry, Alloy, Hyperlane):
  [god-tier-prompts](https://github.com/ravsau/god-tier-prompts/blob/main/prompts/01-implicit-state-machines.md#who-vouched-for-it)

**Origin**
- Steve Ruiz posted the short prompt on X on Oct 31, 2026 with the words "good prompt".
  [Post](https://x.com/steveruizok/status/2116552016218710389)
- Limit: the evidence is posts and PRs from people who ran it on their own code. There
  is no controlled comparison against a plain "find bugs" prompt, and the number of
  findings depends on the repo.
