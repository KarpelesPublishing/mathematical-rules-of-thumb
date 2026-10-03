---
name: math-thumb-analysis
description: "Apply Chapter 5 (Analysis: Know When Limits and Proofs Are Safe) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to write the hypotheses that make a convergence or stopping claim defensible."
---

# Chapter 5. Analysis: Know When Limits and Proofs Are Safe

Apply Chapter 5 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [05-analysis.ipynb](../../notebooks/05-analysis.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Domain and metric; quantifiers; convergence notion; uniform bounds; completeness or compactness assumptions.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Is the problem about perturbation or numerical error?** Find a Lipschitz or derivative bound. If an iteration is a verified contraction, translate its last step into a stopping certificate.
- **Are functions converging?** Before moving a limit through continuity, integration, differentiation, or summation, name the governing interchange theorem. Check whether its control is uniform and whether one bound works across the entire domain.
- **Is the object a function series?** Seek a point-independent majorant and try the M-test.
- **Is the limit unknown?** Compare late terms or partial sums with one another. A tail estimate plus completeness may be enough.
- **Does a numerical series change sign?** Test absolute convergence first. If that fails, move to cancellation-sensitive tests.
- **Does a positive term have a recognizable leading scale?** Compare it with a $p$-series, geometric series, or logarithmic benchmark.
- **Is a proof stalled?** Inspect its architecture: use density plus continuity for identity, formal negation for counterexamples, a stronger invariant for induction, compactness for existence, or backward error algebra for epsilon-delta construction.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Finite numerical checks cannot prove a universal quantified assertion. Name the theorem and verify its domain-wide hypotheses.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 5.1.1 | Use a Lipschitz constant as an error amplifier | Independent | guaranteed bound | valid lipschitz constant; inputs in certified domain |
| 5.1.2 | Turn contraction rate into a fixed-point error bound | Workflow | guaranteed bound | contraction factor below one; invariant complete domain |
| 5.1.3 | Demand uniform control before interchanging limits | Workflow | exact under assumptions | uniform convergence or stronger dominating condition |
| 5.2.1 | Use the M-test for uniform convergence of function series | Independent | guaranteed bound | uniform termwise majorant; summable majorant series |
| 5.2.2 | Use the Cauchy criterion when the limit is unknown | Workflow | exact under assumptions | complete metric space |
| 5.2.3 | Test absolute convergence before conditional behavior | Workflow | exact under assumptions | series of real or complex terms |
| 5.2.4 | Compare with a model whose threshold you know | Workflow | exact under assumptions | eventual nonnegativity or absolute values; known model behavior |
| 5.3.1 | Extend equality from a dense set by continuity | Independent | exact under assumptions | both functions continuous; dense agreement set; common domain |
| 5.3.2 | Negate quantified claims mechanically | Workflow | exact | well formed quantified statement |
| 5.3.3 | Strengthen an induction claim when the step lacks leverage | Workflow | empirical heuristic | inductive structure; stronger claim is true |
| 5.3.4 | Use compactness as the signal that escape is impossible | Workflow | exact under assumptions | compact domain; continuous function for extrema |
| 5.3.5 | Choose delta by working backward from epsilon | Specialized | exact under assumptions | target error epsilon positive; controllable input distance |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [05-analysis.ipynb](../../notebooks/05-analysis.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Turn convergence speed into a stopping certificate** (rule 5.1.2). Why does q=.9 need more steps than q=.5? Each step retains a larger fraction of the error. The geometric certificate makes the required step count explicit.
- **Watch a boundary layer defeat uniform convergence** (rule 5.1.3). What is the supremum error to the pointwise limit for finite n? It is 1, approached as x tends to 1 from below. The maximum need not be attained for the supremum to be 1.
- **Control a whole function series at once** (rule 5.2.1). Can the same finite bound be used with q=1? No. Its denominator vanishes and the geometric majorant fails. A different domain or argument is needed.
- **Test absolute convergence before reordering a series** (rule 5.2.3). Can reordering 1−1/2+1/3−... change its sum? Yes. The positive and negative parts each diverge, so any target can be reached. Absolute convergence is what makes order irrelevant.

## Teach and check understanding

Start with 5.1.2, 5.1.3, 5.3.2 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
