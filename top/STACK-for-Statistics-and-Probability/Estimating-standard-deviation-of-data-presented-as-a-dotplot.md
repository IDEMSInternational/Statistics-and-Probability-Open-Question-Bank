# Metadata — STACK-for-Statistics-and-Probability/Estimating-standard-deviation-of-data-presented-as-a-dotplot.xml

Running record of every agent (and user) action on this question that
isn't the XML itself: the reasoning, findings, improvement notes, and
reference lookups behind each change. Entries are appended in order,
newest at the bottom. The XML changes themselves are recorded by git —
this file holds the substance and meaning behind them, not the diffs.

## Entry 1 — concierge (2026-09-16T14:42:24)

**Issue:**
- #1

**Closes on merge:**
- yes

**Reference files fetched:**
- (none)

```text
Reserved as part of issue #1.
```

## Entry 2 — planner (2026-09-16T14:50:35)

**Reference files fetched:**
- (none)

**Reference files recommended by Planner:**
- Specialist_tools/JSXGraph/JSXGraph.md

```text
GOAL (non-negotiable): Test whether a student can visually estimate the standard deviation of a dataset shown as a dotplot, using the rule-of-thumb that roughly two-thirds of data lies within one SD of the mean.

STRUCTURE (non-negotiable): Single part. A JSXGraph dotplot (crosses) displays heights of a randomly generated village population. One numerical input for the student's SD estimate, graded by one PRT with two nodes checking closeness to the true computed SD of the generated sample. (Unchanged from the current question.)

CHANGE BEING MADE: In `questionvariables`, replace the x-axis upper bound formula
  xmax:dorx1[ds1]+2+(dorx1[ds1]-dorx1[1])/1.5;
with
  xmax:dorx1[ds1]+2;
This removes a deliberate block of empty space on the right of the plot that was originally added to keep the whole dataset visible on mobile screens — no longer needed. The new xmax simply mirrors the existing left margin (xmin:dorx1[1]-2), giving a tight, sensible x-range around the actual data. No other variable, input, or PRT logic changes.

RANDOMIZATION (unchanged): mean1 random 100–200; sd1 random 5–9; ds1 (sample size) random 60–100; data points drawn from a normal distribution with that mean/sd, rounded to integers and sorted; true sample mean/SD (mean_real, m1) computed from the generated data and used for grading and display.

ANSWER TESTS (unchanged): Node 0 — NumRelative within 10% of m1 → full marks, stop. Node 1 (if node 0 false) — NumRelative within 25% of m1 → 0.5 marks; otherwise 0 marks, with the single falsepenalty applied at node 0.

FEEDBACK (unchanged): General feedback restates the "2s ≈ middle two-thirds", "4s ≈ middle 95%", "range ≈ 5s–6s" rules of thumb and states the real mean/SD. Node-specific feedback distinguishes "within 10%", "within 25%", and "not close enough".

PRT/QTEST SUGGESTIONS: (none) — this is a display-only change to the JSXGraph bounding box; no grading logic is affected.
```

