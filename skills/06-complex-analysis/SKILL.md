---
name: math-thumb-complex-analysis
description: "Apply Chapter 6 (Complex Analysis: Turn Analytic Structure into Bounds and Counts) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to use complex structure to obtain a valid bound or zero count before seeking exact values."
---

# Chapter 6. Complex Analysis: Turn Analytic Structure into Bounds and Counts

Apply Chapter 6 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [06-complex-analysis.ipynb](../../notebooks/06-complex-analysis.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Complex function and analytic domain; contour and orientation; singularities; branch choices; target bound or count.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Is the main operation multiplication or exponentiation?** Move to polar form. If a logarithm, root, or fractional power appears, state the branch before simplifying.
- **Are you about to invoke an analytic theorem?** Write $f=u+iv$, screen with Cauchy-Riemann, and verify the required neighborhood and regularity.
- **Do you need a bound rather than an exact integral?** Estimate maximum integrand magnitude and contour length. Split the path if one maximum is too crude.
- **Do you know a boundary magnitude on an analytic disk?** Use Cauchy's estimate for derivatives; use the maximum-modulus principle for the function's largest modulus.
- **Does a quotient have simple poles?** Compute each needed residue by numerator value over denominator derivative.
- **Is the contour integral closed?** List and classify enclosed poles, check orientation, and use the residue theorem.
- **Is the real question a zero count?** Try Rouché when one term dominates on the boundary. Use the argument principle when $f'/f$ or boundary winding is more accessible.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Do not infer analyticity from Cauchy-Riemann equations at one point, and do not ignore poles, branch cuts, boundary zeros, or contour orientation.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 6.1.1 | Use polar form for complex products and powers | Independent | exact under assumptions | consistent angle units |
| 6.1.2 | Treat the principal argument as branch-dependent | Workflow | exact under assumptions | declared branch interval; path avoids branch cut when continuity needed |
| 6.1.3 | Use Cauchy-Riemann equations as a quick analyticity screen | Workflow | exact under assumptions | real partial derivatives exist for test |
| 6.2.1 | Bound a contour integral by maximum times length | Independent | guaranteed bound | rectifiable contour; valid uniform modulus bound |
| 6.2.2 | Use Cauchy's estimate to bound derivative scale | Independent | guaranteed bound | analytic inside and on circle; known boundary modulus bound |
| 6.2.3 | Look on the boundary for analytic maxima | Independent | exact under assumptions | analytic on connected interior; continuous on compact closure |
| 6.3.1 | Compute a simple-pole residue by division of derivatives | Workflow | exact under assumptions | isolated simple pole |
| 6.3.2 | Turn a contour integral into a sum of enclosed residues | Workflow | exact under assumptions | meromorphic inside contour; closed positively oriented contour; no pole on contour |
| 6.3.3 | Use Rouché when one boundary term dominates | Independent | exact under assumptions | analytic functions inside contour; strict boundary dominance |
| 6.3.4 | Count zeros minus poles with the argument principle | Workflow | exact under assumptions | meromorphic function; no zeros or poles on contour; positively oriented closed contour |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [06-complex-analysis.ipynb](../../notebooks/06-complex-analysis.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **See powers multiply complex arguments** (rule 6.1.1). Does a principal angle record every complete turn? No. It wraps into its branch interval; the unwrapped argument and winding retain the turn count.
- **Use an analytic disk to bound derivatives** (rule 6.2.2). Can you apply the disk bound to 1/z on a disk containing zero? No. The function has a pole at zero, violating the analytic hypothesis.
- **Check strict boundary domination before counting zeros** (rule 6.3.3). What fails when a=1? All three roots lie on the unit circle and strict domination fails. The interior conclusion cannot be carried through unchanged.
- **Count only the poles the contour encloses** (rule 6.3.2). Why is the integral zero again at R=2, even though two poles are inside? The residues −1 and +1 cancel. Enclosing poles does not guarantee a nonzero integral; their residues must not sum to zero.

## Teach and check understanding

Start with 6.2.1, 6.2.2, 6.3.3 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
