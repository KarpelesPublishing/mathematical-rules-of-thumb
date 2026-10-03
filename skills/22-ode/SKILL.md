---
name: math-thumb-ode
description: "Apply Chapter 22 (Ordinary Differential Equations: Choosing and Checking Time Integrators) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to separate time-integrator stability from accuracy and verify the quantities the application needs."
---

# Chapter 22. Ordinary Differential Equations: Choosing and Checking Time Integrators

Apply Chapter 22 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [22-ode.ipynb](../../notebooks/22-ode.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: ODE and initial state; state/time units; shortest important timescale; stiffness clues; component tolerances; events and invariants.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Are accepted explicit steps far smaller than output accuracy seems to require?** Inspect Jacobian scales and solver statistics; test a stiff method at the same tolerances.
- **Is the system strongly dissipative and large?** Try BDF with sparse Jacobians. If it is Hamiltonian and long-time geometry matters, choose a symplectic method instead.
- **Does the solution oscillate?** Set a starting maximum step from the shortest important period, then verify phase and amplitude under refinement.
- **Are state scales heterogeneous or near zero?** Choose componentwise absolute tolerances and a dimensionless relative tolerance before judging cost.
- **Does the model switch, impact, or cross a threshold?** Define a smooth event function and localize a bracketed root; do not shrink the display grid as a substitute.
- **Is the method explicit?** Check its full stability region against relevant modes, not only its formal order.
- **Can the exact solution be avoided?** Use three-level refinement, invariant drift, and balance checks as independent evidence.
- **Do implicit solves dominate?** Expose sparsity and escalate to appropriate sparse or matrix-free linear solvers.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Formal order and local error estimates do not replace stability, event, phase, or invariant checks. Use the stability region of the actual integrator.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 22.1.1 | Suspect stiffness when stability, not accuracy, dictates tiny steps | Workflow | empirical heuristic | well posed initial value problem; solver model compatibility; small parameter |
| 22.1.2 | Use BDF for large dissipative stiff systems | Workflow | empirical heuristic | well posed initial value problem; solver model compatibility; sparsity; large problem or asymptotic regime; dissipative dynamics |
| 22.1.3 | Use symplectic integrators for long Hamiltonian trajectories | Workflow | empirical heuristic | well posed initial value problem; solver model compatibility |
| 22.1.4 | Remember that local ODE error is one power higher than global error | Independent | asymptotic | well posed initial value problem; solver model compatibility |
| 22.1.5 | Resolve oscillations with several steps per shortest period | Independent | conventional threshold | well posed initial value problem; solver model compatibility |
| 22.2.1 | Scale ODE error with atol plus rtol times state magnitude | Workflow | empirical heuristic | meaningful component scales; reliable local error estimate |
| 22.2.2 | Change adaptive ODE steps with the error-order power | Specialized | empirical heuristic | well posed initial value problem; solver model compatibility |
| 22.2.3 | Locate ODE events with root finding, not output sampling | Workflow | exact under assumptions | continuous event function; bracketed event; valid dense output |
| 22.3.1 | Check explicit Euler against the stability disk | Workflow | exact under assumptions | well posed initial value problem; solver model compatibility |
| 22.3.2 | Expect RK4 global error to fall by sixteen on step halving | Workflow | asymptotic | well posed initial value problem; solver model compatibility; smoothness |
| 22.3.3 | Monitor invariants as an independent ODE error check | Workflow | exact under assumptions | well posed initial value problem; solver model compatibility |
| 22.3.4 | Provide Jacobian sparsity to stiff ODE solvers | Workflow | empirical heuristic | stable jacobian sparsity pattern; large stiff system |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [22-ode.ipynb](../../notebooks/22-ode.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Solve a decay problem and watch the stability limit** (rule 22.3.1). Is a stable sign-changing trajectory an accurate decay solution? Not necessarily. Stability bounds amplification, while the exact solution stays positive and smooth.
- **Verify RK4 by step halving** (rule 22.3.2). What error reduction does fourth order predict? A factor approaching sixteen when h is halved in the asymptotic regime.
- **Check an oscillator through its energy** (rule 22.1.3). Does bounded energy error prove an accurate phase? No. An integrator can track energy while accumulating a significant timing or phase error.
- **Watch stiffness force tiny explicit steps** (rule 22.1.1). Why does explicit Euler blow up at λ=1000 when the solution is smooth? Its stability limit is h<2/λ=0.002 s. Stability, not accuracy, forces about a thousand steps.
- **Count steps per period before trusting an oscillation** (rule 22.1.5). RK4 is fourth order. Is 4 steps per period enough? No. After ten periods it keeps only about 4% of the amplitude. Order only helps once the step resolves the motion.

## Teach and check understanding

Start with 22.1.1, 22.2.3, 22.3.1 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
