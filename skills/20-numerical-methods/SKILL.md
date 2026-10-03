---
name: math-thumb-numerical-methods
description: "Apply Chapter 20 (Numerical Methods: Approximation You Can Trust) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to budget a numerical computation and verify its accuracy with an independent check."
---

# Chapter 20. Numerical Methods: Approximation You Can Trust

Apply Chapter 20 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [20-numerical-methods.ipynb](../../notebooks/20-numerical-methods.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Function or data; domain; root bracket or integration interval; smoothness; conditioning; precision and tolerance; coupled error sources.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Does a small residual support the claimed answer?** Normalize it, estimate conditioning, and check the quantity of interest before inferring forward accuracy.
- **Is the algorithm itself stable?** Compute a backward error in a structure and scale that represent scientifically acceptable input perturbations.
- **Is arithmetic representation losing information?** Use compensated reduction, Horner nesting, or barycentric interpolation before increasing precision.
- **Is a numerical derivative needed?** Scale the input, choose forward or centered differences from domain access, sweep nearby steps, and use complex-step only through analytic code.
- **Are interpolation samples selectable?** Use Chebyshev-like nodes for a global polynomial; otherwise prefer a representation suited to fixed, noisy, or nonsmooth data.
- **Is an integral smooth and freely sampled?** Use an appropriate Gaussian family; split at known nonsmooth locations and audit adaptive error estimates.
- **Is a convergence order advertised?** Run at least three resolutions with controlled coupled errors and estimate the observed rate before extrapolating.
- **Is a scalar root bracketed?** Budget bisection first, then permit secant or Newton acceleration without surrendering containment.
- **Can a root solver stop safely?** Require a meaningful residual plus location, correction, or bracket evidence, with condition checks near singular roots.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Convergence order, residual size, and solver success flags require interpretation. Establish continuity before treating a sign change as a root bracket.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 20.1.1 | Interpret a residual through conditioning | Workflow | guaranteed bound | compatible condition measure; scale aware residual; local linear error model |
| 20.1.2 | Use backward error to distinguish stability from conditioning | Workflow | exact under assumptions | meaningful nearby problem; compatible condition measure; scale aware perturbation |
| 20.1.3 | Use compensated summation for long mixed-scale sums | Workflow | empirical heuristic | floating point model; finite nonoverflowing terms |
| 20.1.4 | Use Horner's rule for polynomial evaluation | Workflow | exact under assumptions | floating point model; well scaled inputs |
| 20.1.5 | Evaluate interpolating polynomials in barycentric form | Workflow | empirical heuristic | floating point model; well scaled inputs |
| 20.2.1 | Use a square-root-epsilon step for forward differences | Workflow | asymptotic | floating point model; well scaled inputs |
| 20.2.2 | Use a cube-root-epsilon step for centered differences | Workflow | asymptotic | floating point model; well scaled inputs; smoothness |
| 20.2.3 | Use complex-step differentiation when the code is analytic | Workflow | empirical heuristic | floating point model; well scaled inputs; analyticity; small parameter |
| 20.2.4 | Use Chebyshev-like nodes for high-degree global interpolation | Workflow | empirical heuristic | floating point model; well scaled inputs; smoothness |
| 20.2.5 | An n-point Gauss rule integrates degree 2n-1 polynomials exactly | Independent | exact under assumptions | floating point model; well scaled inputs |
| 20.2.6 | Split adaptive quadrature where the integrand is difficult | Specialized | empirical heuristic | floating point model; well scaled inputs |
| 20.3.1 | Expect a factor of four from halving trapezoid spacing | Workflow | asymptotic | floating point model; well scaled inputs; smoothness |
| 20.3.2 | Expect a factor of sixteen from halving Simpson spacing | Workflow | asymptotic | floating point model; well scaled inputs; smoothness |
| 20.3.3 | Use step halving to extrapolate away leading error | Workflow | asymptotic | floating point model; well scaled inputs |
| 20.3.4 | Verify a claimed discretization order on three resolutions | Workflow | exact under assumptions | floating point model; well scaled inputs |
| 20.3.5 | Budget bisection iterations from the bracket width | Independent | guaranteed bound | floating point model; well scaled inputs; continuous sign changing bracket |
| 20.3.6 | Expect secant convergence of order about 1.62 | Independent | asymptotic | floating point model; well scaled inputs; smoothness |
| 20.3.7 | Safeguard Newton with a bracket | Specialized | empirical heuristic | floating point model; well scaled inputs |
| 20.3.8 | Stop Newton using the correction as well as the residual | Workflow | empirical heuristic | reliable newton correction; scale aware residual; simple nonsingular root |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [20-numerical-methods.ipynb](../../notebooks/20-numerical-methods.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Turn a bracket into a numerical certificate** (rule 20.3.5). What does one extra halving buy? It halves the bracket width and the midpoint error ceiling.
- **Find where a smaller derivative step stops helping** (rule 20.2.2). Why does extremely tiny h fail? The nearby function values round before subtraction, so dividing by tiny h amplifies rounding error.
- **Measure trapezoid convergence** (rule 20.3.1). What error ratio should step halving approach? About four in the second-order regime, before roundoff dominates.
- **Watch equal spacing blow up** (rule 20.2.4). Does raising the degree always help? Not with equal spacing: worst error grows from .62 to 29. Chebyshev nodes shrink it from .26 to .022.
- **Recover small terms with compensated summation** (rule 20.1.3). Does adding a million copies of 1e-16 to 1 in plain floating point change the total? No. Each addition rounds back to exactly 1, losing the whole 1e-10. Kahan summation recovers it.

## Teach and check understanding

Start with 20.3.4, 20.3.5, 20.3.7 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
