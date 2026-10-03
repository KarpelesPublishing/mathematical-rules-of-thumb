---
name: math-thumb-linear-algebra
description: "Apply Chapter 7 (Linear Algebra: Choose Stable Matrix Methods Before Computing) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to choose a matrix method from verified structure and report what its residual actually certifies."
---

# Chapter 7. Linear Algebra: Choose Stable Matrix Methods Before Computing

Apply Chapter 7 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [07-linear-algebra.ipynb](../../notebooks/07-linear-algebra.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Matrix dimensions and structure; right-hand side; scale and conditioning; precision; memory limit; requested residual and forward accuracy.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Start with sensitivity.** Estimate conditioning and the digit budget before setting solver tolerances.
- **Verify claimed structure.** Check relative symmetry, positive definiteness, sparsity pattern, block meaning, and scale before choosing a specialized factorization.
- **Choose the direct method by matrix type.** Use Cholesky for verified SPD systems, pivoted LU for general dense systems, and QR or SVD for least squares according to conditioning and rank.
- **Avoid unnecessary objects.** Solve for inverse actions, apply Schur complements through block solves, and keep orthogonal factors implicit when possible.
- **Budget memory as well as flops.** Consider matrix-free actions, cache blocking, and fill-reducing ordering before the matrix outgrows the machine.
- **Verify outputs.** Scale residuals, inspect orthogonality where relevant, and refine a solve only while backward error continues to improve.
- **For spectra and compression, inspect cheap evidence first.** Use Gershgorin, eigenvalue ratios, storage counts, and singular-value tails before escalating to shift-invert or large decompositions.
- **For Krylov methods, separate problem difficulty from solver design.** Check SPD requirements, conditioning, clustering, preconditioner cost, restart behavior, and true residuals.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Residual and forward error are different quantities. A low-rank storage win, symmetry claim, or converged iteration must pass its own accuracy or structural check.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 7.1.1 | Estimate digits lost from the condition number | Independent | asymptotic | compatible matrix structure; scale aware tolerance; linearity |
| 7.1.2 | Check matrix symmetry relative to scale | Workflow | exact under assumptions | compatible matrix structure; scale aware tolerance; linearity; symmetry |
| 7.1.3 | Certify an eigenpair with its residual | Workflow | exact under assumptions | compatible matrix structure; scale aware tolerance; linearity |
| 7.1.4 | Equilibrate rows and columns with wildly different scales | Workflow | empirical heuristic | large row or column scale disparity; recoverable scaling factors |
| 7.1.5 | Use iterative refinement to recover linear-solve accuracy | Workflow | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity |
| 7.2.1 | Solve systems instead of forming an explicit inverse | Workflow | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity |
| 7.2.2 | Use partial pivoting for general dense LU | Workflow | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity |
| 7.2.3 | Treat Schur complements as first-class operators | Workflow | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity |
| 7.2.4 | Prefer QR to normal equations for accurate least squares | Workflow | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity |
| 7.2.5 | Use Cholesky for symmetric positive-definite systems | Workflow | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity; symmetric positive definite; symmetry |
| 7.2.6 | Prefer orthogonal transformations for numerical stability | Workflow | exact under assumptions | compatible matrix structure; scale aware tolerance; linearity |
| 7.2.7 | Go matrix-free when storage dominates arithmetic | Workflow | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity |
| 7.2.8 | Use blocked matrix algorithms to exploit fast BLAS-3 kernels | Workflow | empirical heuristic | large dense matrices; level three blas available; memory hierarchy reuse |
| 7.2.9 | Reorder sparse factorizations to control fill | Workflow | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity; sparsity |
| 7.3.1 | Use Gershgorin disks as a cheap eigenvalue screen | Independent | guaranteed bound | square matrix; matrix entries known |
| 7.3.2 | Power iteration speed is set by the eigenvalue ratio | Independent | asymptotic | compatible matrix structure; scale aware tolerance; linearity |
| 7.3.3 | Use shift-invert for interior or smallest eigenvalues | Specialized | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity |
| 7.3.4 | Check low-rank storage before compressing a matrix | Independent | exact under assumptions | compatible matrix structure; scale aware tolerance; linearity |
| 7.3.5 | Use the next singular value to price a low-rank approximation | Independent | guaranteed bound | compatible matrix structure; scale aware tolerance; linearity |
| 7.3.6 | Define numerical rank relative to the largest singular value | Workflow | conventional threshold | compatible matrix structure; scale aware tolerance; linearity; well scaled inputs |
| 7.3.7 | Expect conjugate-gradient work to scale with square-root conditioning | Independent | asymptotic | compatible matrix structure; scale aware tolerance; linearity; symmetric positive definite; large problem or asymptotic regime |
| 7.3.8 | Judge a preconditioner by clustered eigenvalues and total time | Workflow | empirical heuristic | compatible iterative solver; affordable preconditioner application |
| 7.3.9 | Increase GMRES restart when convergence stalls | Specialized | empirical heuristic | compatible matrix structure; scale aware tolerance; linearity |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [07-linear-algebra.ipynb](../../notebooks/07-linear-algebra.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Solve a sensitive system and inspect both errors** (rule 7.1.1). Does a small residual guarantee accuracy relative to unperturbed inputs? No. It checks the equation actually solved. Conditioning determines how much altered inputs can change its solution.
- **Fit data and read the residual pattern** (rule 7.2.6). Can a better solver fix a model that omitted the intercept? No. Solver stability and model adequacy are different issues; the omitted intercept changes the fitting problem.
- **Reconstruct a matrix at different ranks** (rule 7.3.5). What spectral error remains at rank two? The next singular value is 1, which equals the spectral norm of the omitted part.
- **Watch the eigenvalue ratio set the speed of power iteration** (rule 7.3.2). How many steps does ratio 0.9 need to reach 10⁻⁶? About 132. Each step only removes 10% of the error, so 60 steps leave it near 0.0018.
- **See the normal equations square the condition number** (rule 7.2.4). With κ=10⁶, about how many correct digits can the normal equations keep? About 4. κ²=10¹² eats 12 of the roughly 16 digits, while QR still keeps about 10.

## Teach and check understanding

Start with 7.1.1, 7.2.4, 7.3.4 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
