---
name: math-thumb-trigonometry
description: "Apply Chapter 3 (Trigonometry: Control Angles, Directions, and Oscillations) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to choose angle representations that preserve quadrants and quantify a small-angle approximation."
---

# Chapter 3. Trigonometry: Control Angles, Directions, and Oscillations

Apply Chapter 3 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [03-trigonometry.ipynb](../../notebooks/03-trigonometry.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Angle units; signed coordinates; oscillation frequency; triangle data type; tolerance near zero.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Is the angle small?** Convert to radians. Use sine or tangent as $x$ only after checking the cubic correction; use $1-x^2/2$ when cosine's small departure from one matters.
- **Are two signed components defining a direction or phase?** Preserve both with `atan2`. If they multiply same-frequency cosine and sine terms, convert the coefficient pair to amplitude and phase.
- **Is the angle large or outside a familiar interval?** Reduce it modulo the function's period before using a reference angle or numerical routine.
- **Is the triangle given by SAS or SSS?** Start with the law of cosines. If it is given by SSA, use the law of sines and test both inverse-sine branches.
- **Does the formula subtract nearly equal trigonometric values?** Search for an exact identity such as $1-\cos x=2\sin^2(x/2)$ before evaluating.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Use radians for local models. Keep signed components for direction; check both inverse-sine branches for SSA triangle data.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 3.1.1 | Replace sine by the angle at small scale | Independent | first-order approximation | small angle; radian measure |
| 3.1.2 | Keep the quadratic correction for cosine near zero | Independent | first-order approximation | small angle; radian measure |
| 3.1.3 | Use tangent approximately equal to angle only away from poles | Independent | first-order approximation | small angle; radian measure; far from tangent pole |
| 3.2.1 | Use atan2, not a plain arctangent, for direction | Independent | exact under assumptions | nonzero vector; documented argument order; consistent angle units |
| 3.2.2 | Combine a sine-cosine pair into one shifted sinusoid | Independent | exact | same frequency and argument; real coefficients |
| 3.2.3 | Reduce large angles before evaluating trigonometric functions | Workflow | exact under assumptions | known period; angle reduction done with sufficient precision |
| 3.3.1 | View the law of cosines as corrected Pythagoras | Independent | exact under assumptions | euclidean triangle; included angle matches two known sides; consistent angle units |
| 3.3.2 | Check both branches in the sine-law ambiguous case | Workflow | exact under assumptions | side side angle data; known angle opposite known side |
| 3.3.3 | Use radians whenever angles enter calculus or approximation | Workflow | exact | angular quantity; local change or calculus formula |
| 3.3.4 | Use a half-angle identity for one minus cosine | Workflow | exact | consistent angle units |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [03-trigonometry.ipynb](../../notebooks/03-trigonometry.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Put an error budget on a small angle** (rule 3.1.1). Can you substitute 5 directly for a five-degree angle? No. Five degrees equals 5π/180 radians. Substituting 5 would change both the angle and the approximation regime.
- **Keep direction when a ratio loses the quadrant** (rule 3.2.1). Why is atan(y/x) wrong for the vector (−1,1)? The ratio is −1, whose principal arctangent is −45°. The vector is in quadrant II, so atan2 gives 135°.
- **Avoid subtracting nearly equal floating numbers** (rule 3.3.4). If direct subtraction returns zero, must the exact quantity be zero? No. Rounding can make cos(x) indistinguishable from one even though 2 sin²(x/2) retains the small positive quantity.
- **Count the triangles in the sine-law ambiguous case** (rule 3.3.2). Why can arcsin give a wrong answer when a=7? Arcsin returns only the acute angle B. With h<a<b, the obtuse angle 180° minus B also fits, so there are two triangles.

## Teach and check understanding

Start with 3.1.1, 3.2.1, 3.3.4 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
