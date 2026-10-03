---
name: math-thumb-measurement
description: "Apply Chapter 16 (Measurement and Uncertainty: Building Trustworthy Results) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to build a measurement uncertainty budget and report a result without hiding covariance or bias."
---

# Chapter 16. Measurement and Uncertainty: Building Trustworthy Results

Apply Chapter 16 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [16-measurement.ipynb](../../notebooks/16-measurement.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Measurand and measurement equation; corrections; input standard uncertainties; sensitivities and covariance; coverage convention; units.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

1. Define the measurand and write \(y=f(x_1,\ldots,x_m)\), including corrections.
2. List every uncertainty source and possible shared cause. Label its evaluation Type A or Type B without treating the label as a rank.
3. Convert each source to a standard uncertainty, retaining its units, distribution, divisor, and evidence.
4. Calculate sensitivity coefficients and covariance terms. Use relative shortcuts only when their assumptions match the model.
5. Inspect variance contributions and improve the components with genuine leverage.
6. Challenge the linear approximation with scale, curvature, bounds, and limiting cases. Switch to Monte Carlo if it bends.
7. Choose a coverage convention, round the uncertainty first, align the result, and report enough method detail to reproduce the claim.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** The ± symbol must be defined: standard uncertainty, expanded uncertainty, interval, or tolerance. Keep covariance and correction uncertainty in the measurement model.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 16.1.1 | Repetition reduces random scatter, not fixed bias | Independent | exact under assumptions | shared fixed bias across repeats |
| 16.1.2 | Type A and Type B describe evaluation methods, not importance | Workflow | conventional threshold | identifiable uncertainty sources |
| 16.1.3 | Keep guard digits until the final reported result | Workflow | empirical heuristic | finite precision calculation |
| 16.1.4 | Round the uncertainty first, then align the result | Workflow | conventional threshold | uncertainty already estimated |
| 16.1.5 | Mean-squared error is variance plus squared bias | Independent | exact under assumptions | fixed target; finite second moment |
| 16.2.1 | A power multiplies relative uncertainty by its exponent | Independent | first-order approximation | small relative uncertainty; differentiable power law; nonzero input |
| 16.2.2 | Products and quotients combine relative uncertainties | Workflow | first-order approximation | small relative uncertainties; independent factors; nonzero factors |
| 16.2.3 | Scale every input uncertainty by its sensitivity coefficient | Workflow | first-order approximation | differentiable measurement model; small input uncertainties; local linearity |
| 16.2.4 | Build an uncertainty budget with sensitivity-scaled RSS terms | Workflow | exact under assumptions | uncorrelated inputs; first order linearization; finite variances |
| 16.3.1 | Keep covariance terms for correlated uncertainties | Workflow | exact under assumptions | known covariance structure; first order linearization |
| 16.3.2 | Convert a uniform half-width to standard uncertainty with $\sqrt{3}$ | Workflow | guaranteed bound | uniform error distribution; symmetric hard bounds |
| 16.3.3 | Coverage factor two is an approximate 95% convention | Workflow | conventional threshold | approximately normal output; adequate degrees of freedom; combined standard uncertainty available |
| 16.3.4 | Improve the dominant uncertainty contributors first | Workflow | exact under assumptions | complete uncertainty budget; comparable variance contributions |
| 16.3.5 | Use Monte Carlo propagation when linear uncertainty rules bend | Workflow | empirical heuristic | specified input distributions; computable measurement model |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [16-measurement.ipynb](../../notebooks/16-measurement.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Keep the covariance in an uncertainty budget** (rule 16.3.1). Does perfect negative correlation make the exact product uncertainty zero? No. It cancels these first-order contributions; higher-order product terms can remain.
- **Watch repetition meet a bias floor** (rule 16.1.1). Can more repetitions remove the bias? No. Bias correction requires calibration or a better measurement model.
- **Propagate a nonlinear transformation by simulation** (rule 16.3.5). Is E[X²] equal to E[X]²? Not with nonzero variance. E[X²]=Var(X)+E[X]².
- **Spend effort on the biggest contributor** (rule 16.3.4). Which halving cuts the total most? Halving the 4 mm term: 4.58 mm drops to 3 mm. Halving the 1 mm term saves under 2%.
- **See when k=2 really means 95%** (rule 16.3.3). Does ±2u from three repeat readings give 95% coverage? No. With ν=2 or 3 it covers only about 82% to 86%; a factor near 3.2 is needed for 95% at ν=3 (about 3.3 to match the 95.45% normal coverage of k=2).

## Teach and check understanding

Start with 16.2.2, 16.3.1, 16.3.3 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
