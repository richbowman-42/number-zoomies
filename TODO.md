# Number Zoomies — TODO

## Task-switching statistics

Measure how much switching between kinds of math costs, compared with staying on
the same kind. For example: addition followed by addition, versus addition
followed by subtraction, or addition followed by division.

**What to track**

- For each answer, remember the kind of math of the problem just before it. That
  gives 16 pairs (previous → current), like `add → add`, `add → sub`, `add → div`.
- Keep stats for each pair over time: how many tries, how many right, and the
  typical answer time.
- Same-task pairs (`add → add`) are the baseline. The **switch cost** for a kind of
  math is its typical time (and accuracy) after a different kind, minus its
  typical time after the same kind. Example: "Division is 1.4 s slower and 8%
  less accurate right after multiplication than after division."
- Track the pairs across rounds so a trend shows whether switching gets easier
  with practice.

**Things to decide when building it**

- Leave out the first problem of each round, since it has no previous problem.
- Problems right after a Survival miss break start fresh, so track them
  separately or leave them out.
- Voice answers include recognition lag. Keep them apart from typed times,
  as the fact grid already does.
- Only rounds with two or more kinds of math produce switch pairs, and random
  order won't give every pair equal numbers. Maybe add an option to deliberately
  alternate kinds of math so pairs fill in faster.
- Where it shows: likely the grown-ups page (a 4 × 4 grid of pair times and
  accuracy, plus switch cost for each kind of math), with a simple
  kid-friendly line on the results screen at most.
- Storage: e.g. `player.pairs["add>sub"] = {n, ok, times: [last 30]}`, plus a
  per-round summary for the trend. Needs the backup merge code
  (`mergePlayer`) updated to handle it.
