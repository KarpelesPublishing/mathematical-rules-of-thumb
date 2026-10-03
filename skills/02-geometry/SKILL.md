---
name: math-thumb-geometry
description: "Apply Chapter 2 (Geometry: Estimate Shape Before Measuring It) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to use scaling and feasibility checks before committing to a geometric calculation."
---

# Chapter 2. Geometry: Estimate Shape Before Measuring It

Apply Chapter 2 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [02-geometry.ipynb](../../notebooks/02-geometry.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Lengths with units; evidence of similarity; vertex order or perpendicular height; permitted error.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Are two figures scaled copies?** Find the linear factor first. Raise it to the second power for area and the third for volume; subtract powers when forming ratios such as perimeter over area.
- **Is the change small?** Express it as a dimensionless fraction. For circle area, double the fractional radius change and compare its square with the required accuracy.
- **Could the data be impossible?** Test the triangle inequality before any three-side formula and check units before interpreting coordinates or lengths.
- **Do you need only a plausibility range?** Enclose the shape in a box or bracket a Euclidean diagonal before performing the exact computation.
- **Is the boundary circular or polygonal?** Use chord-radius geometry for shallow sagitta, a full turn for regular-polygon angles, and the $1/n^2$ law to predict the effect of refinement.
- **Is area encoded in coordinates?** Keep vertices in cyclic order and use shoelace. If a perpendicular height is already known, $bh/2$ is usually the shorter route.
- **Is the result a weighted location?** With nonnegative weights, require the centroid to remain inside the convex hull.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Do not apply square-cube laws to shape changes that are not similar, or use a necessary geometric bound as a sufficient construction test.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 2.1.1 | Remember the square-cube laws for similar shapes | Independent | exact under assumptions | geometric similarity; uniform linear scale factor |
| 2.1.2 | Expect boundary-to-area ratio to shrink like inverse size | Independent | exact under assumptions | geometrically similar shapes; uniform length scaling |
| 2.1.3 | Double the fractional radius change to estimate circle-area change | Independent | first-order approximation | small relative radius change; positive reference radius |
| 2.2.1 | Check the triangle inequality before doing triangle algebra | Independent | guaranteed bound | metric or normed distance; nonnegative lengths |
| 2.2.2 | Use a bounding box for a fast area or volume ceiling | Independent | guaranteed bound | object contained in box; box dimensions known |
| 2.2.3 | Bracket a right-triangle diagonal before taking a square root | Independent | guaranteed bound | nonnegative component lengths; euclidean diagonal |
| 2.3.1 | Estimate shallow-arc sagitta by chord squared over radius | Independent | first-order approximation | sagitta small relative to radius; circular arc |
| 2.3.2 | Estimate regular-polygon angles from the exterior turn | Independent | exact under assumptions | simple planar polygon; interior angles counted consistently |
| 2.3.3 | Expect regular-polygon circle error to fall quadratically | Independent | asymptotic | regular inscribed or circumscribed polygon; large side count |
| 2.3.4 | Use the shoelace formula for polygon area from coordinates | Independent | exact under assumptions | simple planar polygon; vertices in cyclic order |
| 2.3.5 | Prefer base times perpendicular height when height is available | Workflow | empirical heuristic | triangle or decomposable shape; known perpendicular height |
| 2.3.6 | Use the convex hull as a centroid sanity check | Workflow | guaranteed bound | nonnegative weights; weights sum to one |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [02-geometry.ipynb](../../notebooks/02-geometry.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Separate length, area, and volume scaling** (rule 2.1.1). If every dimension doubles, does volume double? No. Similar volume multiplies by 2³=8, while area multiplies by 2²=4.
- **Check whether an arc is shallow enough** (rule 2.3.1). Why does the chord-to-radius ratio matter? The omitted terms grow with c/R. A formula that works for a shallow arc need not meet the same tolerance for a wide chord.
- **Refine a polygon toward a circle** (rule 2.3.3). Does doubling the sides make the area error exactly one quarter? Only asymptotically. The exact sine formula should be checked at finite side counts.
- **Check the triangle inequality before triangle algebra** (rule 2.2.1). Can sides 3, 4 and 8 form a triangle? No. 3 + 4 = 7 is shorter than 8, so the free ends cannot meet. Any area or angle computed from these numbers is meaningless.

## Teach and check understanding

Start with 2.1.1, 2.1.3, 2.2.1 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
