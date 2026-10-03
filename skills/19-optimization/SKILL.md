---
name: math-thumb-optimization
description: "Apply Chapter 19 (Optimization: Scale, Search, and Certify) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to choose a step and stopping test that match the optimization problem's assumptions."
---

# Chapter 19. Optimization: Scale, Search, and Certify

Apply Chapter 19 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [19-optimization.ipynb](../../notebooks/19-optimization.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Objective and constraints; units and variable scales; smoothness and convexity evidence; derivative access; noise; required optimality certificate.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Does the problem mix units or characteristic magnitudes?** Nondimensionalize variables and constraints, then transform derivatives, bounds, penalties, and reported sensitivities consistently.
- **Can the objective be evaluated safely?** Stabilize exponentials, logarithms, and reductions before diagnosing optimizer behavior.
- **Is the objective smooth and convex?** Use a reciprocal smoothness step or backtracking; use condition number to judge whether scaling, acceleration, or curvature is needed.
- **Are gradients noisy?** Identify the batch-variance and constant-step floor before tightening tolerances or declaring a bug.
- **Is second-order information available?** Globalize Newton with a line search or trust region; use L-BFGS when only a small vector history fits.
- **Is the landscape nonconvex?** Treat every local solve as one basin sample and escalate to global methods when a certificate matters.
- **Have derivatives been independently checked?** Sweep centered directional differences across several steps before trusting convergence behavior.
- **What does optimality mean here?** Use a duality gap for valid convex bounds, a projected mapping for closed convex sets, or full scaled KKT blocks for general constraints.
- **Is the diagnostic algorithm-specific?** Keep Newton decrement, ADMM balancing, and penalty continuation attached to their required method and assumptions.
- **Will a multiplier drive a decision?** Verify the active set, units, signs, regularity, and locality before interpreting it as marginal value.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Keep convergence claims attached to convexity, smoothness, scaling, and method conditions. Use constraint-aware optimality residuals at boundaries.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 19.1.1 | Nondimensionalize optimization variables before tuning | Workflow | empirical heuristic | well-scaled objective; reliable function evaluation |
| 19.1.2 | Scale features before coordinate descent | Workflow | empirical heuristic | well-scaled objective; reliable function evaluation |
| 19.1.3 | Shift by the maximum in log-sum-exp and softmax | Workflow | exact under assumptions | finite nonempty input or defined edge convention; floating point exponential |
| 19.1.4 | Condition number predicts gradient-descent speed | Independent | asymptotic | well-scaled objective; reliable function evaluation; smoothness; convexity; strong convexity |
| 19.1.5 | Expect constant-step stochastic optimization to hit a noise floor | Independent | asymptotic | well-scaled objective; reliable function evaluation; stationarity |
| 19.2.1 | Start smooth convex gradient descent at step 1 over L | Workflow | guaranteed bound | well-scaled objective; reliable function evaluation; smoothness; convexity |
| 19.2.2 | Use Armijo backtracking when the safe step is unknown | Workflow | empirical heuristic | well-scaled objective; reliable function evaluation |
| 19.2.3 | Damp Newton until the full step is trustworthy | Workflow | empirical heuristic | well-scaled objective; reliable function evaluation |
| 19.2.4 | Use the trust-region ratio to accept and resize steps | Specialized | empirical heuristic | meaningful local model; positive predicted reduction; reliable objective evaluation |
| 19.2.5 | Use L-BFGS when dense Hessian storage is impossible | Workflow | empirical heuristic | well-scaled objective; reliable function evaluation; smoothness; small parameter; large problem or asymptotic regime |
| 19.2.6 | Use multiple starts for nonconvex local optimization | Workflow | empirical heuristic | well-scaled objective; reliable function evaluation |
| 19.3.1 | Check gradients with directional differences, not every coordinate | Workflow | asymptotic | smooth objective; reliable function evaluation; well scaled directions |
| 19.3.2 | Use the duality gap as a global convex certificate | Workflow | guaranteed bound | well-scaled objective; reliable function evaluation; convexity |
| 19.3.3 | Stop constrained gradient methods with a projected-gradient mapping | Workflow | exact under assumptions | well-scaled objective; reliable function evaluation; convexity |
| 19.3.4 | Scale every block of the KKT residual | Workflow | exact under assumptions | well-scaled objective; reliable function evaluation; small parameter |
| 19.3.5 | Use the Newton decrement as a convex stopping certificate | Specialized | guaranteed bound | well-scaled objective; reliable function evaluation; smoothness; convexity; standard self-concordance; Newton decrement below one |
| 19.3.6 | Balance ADMM primal and dual residuals | Specialized | empirical heuristic | comparable residual scaling; consistent dual rescaling; admm iteration state |
| 19.3.7 | Do not make penalty parameters enormous too early | Specialized | empirical heuristic | well-scaled objective; reliable function evaluation |
| 19.3.8 | Read a Lagrange multiplier as marginal value | Workflow | exact under assumptions | optimal primal dual solution; constraint qualification; differentiable value function; stable active set; consistent sign and units |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [19-optimization.ipynb](../../notebooks/19-optimization.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Run gradient descent on a stiff quadratic** (rule 19.2.1). Why can α=.25 diverge? The y-direction multiplies by 1−10α=−1.5, whose magnitude exceeds one.
- **Shift exponentials without changing softmax** (rule 19.1.3). Does adding 1000 change softmax probabilities? No. The common exponential factor cancels; log-sum-exp increases by 1000.
- **Use a feasible stopping test at a boundary** (rule 19.3.3). Why is the raw gradient nonzero at the optimum? The decreasing direction points outside the feasible set. The projected-gradient mapping is zero at x=0.
- **See why condition number sets the pace** (rule 19.1.4). How many steps reach 1e-6 at κ=100? 1375 steps, versus 20 at κ=2. Rescaling variables is often cheaper than iterating.
- **See constant-step noise set a floor** (rule 19.1.5). Will running ten times longer at step .1 get closer to the optimum? No. The mean square stays near .1/1.9≈.053. Shrink the step or average the iterates.

## Teach and check understanding

Start with 19.2.1, 19.3.1, 19.3.3 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
