---
name: math-thumb-calculus
description: "Apply Chapter 4 (Calculus: Turn Local Change into Global Control) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to turn a local model into a checked estimate and distinguish an error scale from a proved bound."
---

# Chapter 4. Calculus: Turn Local Change into Global Control

Apply Chapter 4 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [04-calculus.ipynb](../../notebooks/04-calculus.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Function and domain; expansion point; perturbation; derivative information; desired bound or estimate.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Is the input near a value you understand?** Linearize. If you are solving $f(x)=0$, interpret that linear model’s root as a Newton step.
- **Is the question about sensitivity or guaranteed change?** Use relative differentials for small percentage response; use a derivative supremum when a hard interval-wide bound is required.
- **Is the question about graph shape?** Partition at critical, nondifferentiable, and endpoint values. Use derivative signs for monotonicity and convexity for tangent-secant bounds.
- **Is a thin layer being added?** Multiply boundary measure by thickness, then compare the curvature correction with the tolerance.
- **Before integrating, can structure finish the problem?** Check range, parity, and moving endpoints before seeking an antiderivative.
- **Is the issue improper accumulation?** Identify the troublesome endpoint, recall the $p=1$ threshold, compare positive integrands in the correct direction, and use adjacent integrals when a decreasing series remainder is needed.
- **Do you need an integration method?** Search first for an inner function with its derivative, then consider whether parts transfers complexity profitably.
- **Do you need a limit or approximation?** Verify an indeterminate quotient before L’Hôpital, and verify a remainder condition before treating the next Taylor term as a bound.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** A next Taylor term is not automatically an error bound. Establish an appropriate remainder condition or compare with a verified exact result.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 4.1.1 | Linearize near a point you already understand | Independent | first-order approximation | differentiability; nearby input; small increment |
| 4.1.2 | Interpret a Newton step as the tangent-line root | Workflow | first-order approximation | nonzero derivative; sufficiently near simple root |
| 4.1.3 | Use relative differentials for power-law sensitivity | Independent | first-order approximation | small relative change; nonzero positive reference for real log form |
| 4.1.4 | Turn a derivative bound into a change bound | Independent | guaranteed bound | derivative exists or function absolutely continuous; valid uniform derivative bound |
| 4.2.1 | Use the derivative sign before solving for extrema | Independent | exact under assumptions | differentiability on interval |
| 4.2.2 | Bracket a convex function between tangents and secants | Independent | guaranteed bound | convex function; points within convex domain |
| 4.2.3 | Estimate a thin shell as boundary measure times thickness | Independent | first-order approximation | thickness small relative to curvature radius; regular boundary |
| 4.3.1 | Check an integral average against the function's range | Independent | guaranteed bound | continuous or integrable bounded function; finite interval |
| 4.3.2 | Exploit even and odd symmetry before integrating | Independent | exact under assumptions | symmetric domain; verified function symmetry |
| 4.3.3 | Differentiate an accumulated integral at its moving endpoint | Independent | exact under assumptions | continuous integrand near evaluation point; differentiable limit function |
| 4.3.4 | Memorize the p-integral convergence threshold | Independent | exact under assumptions | positive power law tail; infinite upper limit or zero endpoint as specified |
| 4.3.5 | Compare positive integrands with a known benchmark | Independent | guaranteed bound | pointwise order on common domain; integrability |
| 4.3.6 | Bracket a decreasing series tail with integrals | Workflow | guaranteed bound | positive decreasing summand; matching continuous extension |
| 4.3.7 | Look for an inner function and its derivative | Workflow | exact under assumptions | composition structure; matching derivative factor |
| 4.3.8 | Choose integration by parts to move complexity | Workflow | empirical heuristic | product structure; differentiation simplifies one factor |
| 4.3.9 | Use L'Hôpital only after confirming an indeterminate form | Workflow | exact under assumptions | zero over zero or infinity over infinity; differentiability near limit |
| 4.3.10 | Use the first omitted Taylor term as an error scale | Workflow | first-order approximation | sufficient smoothness; next derivative control; near expansion point |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [04-calculus.ipynb](../../notebooks/04-calculus.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Check a tangent estimate against a remainder** (rule 4.1.1). Why is the tangent estimate above the square-root curve? Square root is concave on the positive domain, so its tangent is an upper bound.
- **Read a Newton step from its tangent** (rule 4.1.2). What happens if you start at x=0? The derivative vanishes and the Newton quotient is undefined. A different start or a bracketed method is needed.
- **Distinguish a finite sum from an infinite tail** (rule 4.3.6). Does a finite 100-term sum prove convergence? No. Every finite partial sum exists here. Infinite convergence depends on the tail; p≤1 diverges.
- **Use the first omitted Taylor term as an error scale** (rule 4.3.10). How many terms of 1+1+1/2+1/6+... give e to three decimals? Degree 6: the first omitted term 1/7! ≈ 0.000198 and the actual error is 0.000226, both below 0.0005.
- **Confirm 0/0 before using L'Hôpital** (rule 4.3.9). What is the limit when a=1? There is no finite limit. The numerator tends to 1 and the denominator to 0, so the ratio grows without bound (to +∞ from the right and −∞ from the left). L'Hôpital's 1 is wrong.

## Teach and check understanding

Start with 4.1.1, 4.1.4, 4.3.10 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
