GOAL: Test whether a student can visually estimate the standard deviation of a dataset shown as a dotplot, using the rule-of-thumb that roughly two-thirds of data lies within one SD of the mean.

DESCRIPTION: The student sees a dotplot (drawn with JSXGraph as a grid of crosses) showing the heights, in cm, of a randomly generated village population. Below it is a single numeric input box where the student types their estimate of the standard deviation of the plotted heights, in cm.

STRUCTURE: Single part. A JSXGraph dotplot (crosses) displays heights of a randomly generated village population. One numerical input for the student's SD estimate, graded by one PRT (`prt_ans1`) with two nodes checking closeness to the true computed SD of the generated sample.

RANDOMIZATION: mean1 random 100–200; sd1 random 5–9; ds1 (sample size) random 60–100; data points drawn from a normal distribution with that mean/sd, rounded to integers and sorted; true sample mean/SD (mean_real, m1) computed from the generated data and used for grading and display. The dotplot's x-axis bounding box is now `xmin:dorx1[1]-2` to `xmax:dorx1[ds1]+2` — a tight margin of 2 on each side of the actual data range, replacing the old right-hand side formula that added extra empty space for mobile display.

ANSWER TESTS: Node 0 — checks whether the student's answer is within 10% of m1 (the true sample SD) → full marks, stop. Node 1 (if node 0 false) — checks whether the answer is within 25% of m1 → 0.5 marks; otherwise 0 marks, with the single falsepenalty applied at node 0. The teacher answer `mr1` is now computed as `float(round(m1*10)/10)` (rounded to 1 decimal place) rather than via `dispdp`, since `dispdp` produces a display string, not a number, and is rejected by the numerical input.

FEEDBACK: General feedback restates the "2s ≈ middle two-thirds", "4s ≈ middle 95%", "range ≈ 5s–6s" rules of thumb and states the real mean/SD. Node-specific feedback distinguishes "within 10%", "within 25%", and "not close enough".

IMPLEMENTATION NOTES:
- The teacher answer `mr1` must be a plain numeric value (not a display-formatted string) because it's used directly as the correct answer for a `numerical` input type; `dispdp(m1,1)` failed for this reason and was replaced with `float(round(m1*10)/10)`.
- The requested display-only xmax change was applied exactly as planned; no grading logic, PRT structure, or randomization was touched.
- First build attempt was missing the PRT block and qtest cases entirely (structural omissions, not a plan deviation) — these were added in the accepted draft along with standard PRT node attributes (quiet, truenextnode, feedbackstyle, etc.) required for STACK to accept the question.