---
name: math-thumb-pde
description: "Apply Chapter 23 (Partial Differential Equations: Discretize, Resolve, and Verify) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to compute scheme-specific stability limits and design a refinement check that separates space and time errors."
---

# Chapter 23. Partial Differential Equations: Discretize, Resolve, and Verify

Apply Chapter 23 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [23-pde.ipynb](../../notebooks/23-pde.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: PDE, coefficients and units; domain and boundary/initial data; spatial and temporal schemes; grid spacing; conservation and error targets.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Is the PDE transport-dominated?** Follow characteristic direction, inspect cell Peclet numbers, and use limiting near discontinuities.
- **Must a quantity balance cell by cell?** Form one shared numerical flux per face and audit the telescoping global balance.
- **Is nominal high order missing?** Check solution regularity, geometry, quadrature, and solver tolerance before increasing polynomial degree.
- **Is time integration explicit?** Evaluate every applicable advection, diffusion, reaction, and source stability restriction.
- **Are waves or thin layers important?** Set the mesh from wavelength and layer thickness, then refine the output that depends on their derivatives or phase.
- **Do space and time errors interact?** Isolate each with separate studies before choosing a coupled refinement path.
- **Has the code been verified?** Run manufactured solutions and recover predicted order in relevant norms.
- **Could the domain or linear solve contaminate the answer?** Move artificial boundaries and tighten multigrid-preconditioned solves independently.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** CFL constants depend on dimension and scheme. Numerical stability is not a resolution certificate; verify boundaries, conservation, and order separately.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 23.1.1 | Bias transport discretization upwind | Workflow | empirical heuristic | well posed boundary value problem; consistent discretization |
| 23.1.2 | Use cell Peclet number to judge centered convection-diffusion | Workflow | conventional threshold | well posed boundary value problem; consistent discretization |
| 23.1.3 | Prefer finite volume when local conservation is nonnegotiable | Workflow | empirical heuristic | well posed boundary value problem; consistent discretization |
| 23.1.4 | Limit high-order reconstructions near discontinuities | Specialized | empirical heuristic | well posed boundary value problem; consistent discretization; smoothness; large problem or asymptotic regime |
| 23.1.5 | Do not expect finite-element order beyond solution regularity | Workflow | exact under assumptions | well posed boundary value problem; consistent discretization; smoothness |
| 23.2.1 | Keep explicit advection CFL near or below one | Workflow | conventional threshold | well posed boundary value problem; consistent discretization |
| 23.2.2 | Remember that explicit diffusion steps scale with mesh size squared | Independent | asymptotic | explicit time integration; diffusive operator; known smallest mesh scale |
| 23.2.3 | Resolve waves with at least about ten cells per wavelength | Independent | conventional threshold | well posed boundary value problem; consistent discretization |
| 23.2.4 | Place several cells across every boundary layer | Workflow | conventional threshold | well posed boundary value problem; consistent discretization |
| 23.2.5 | Balance temporal and spatial discretization errors | Workflow | asymptotic | separable leading error terms; known temporal and spatial orders; asymptotic refinement regime |
| 23.3.1 | Require every Fourier amplification factor to stay bounded | Workflow | exact under assumptions | well posed boundary value problem; consistent discretization; linearity; constant coefficients |
| 23.3.2 | Verify PDE codes with a manufactured solution | Workflow | exact under assumptions | smooth manufactured field; consistent forcing and boundary data; independent symbolic check |
| 23.3.3 | Estimate PDE order from normed errors on successive meshes | Workflow | asymptotic | well posed boundary value problem; consistent discretization; uniform grid or scale |
| 23.3.4 | Move artificial boundaries until the answer stops moving | Workflow | exact under assumptions | well posed boundary value problem; consistent discretization |
| 23.3.5 | Use multigrid when elliptic solves dominate | Workflow | empirical heuristic | well posed boundary value problem; consistent discretization; linearity; large problem or asymptotic regime; independence |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [23-pde.ipynb](../../notebooks/23-pde.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Evolve transport with a chosen CFL number** (rule 23.2.1). Can exact mass conservation alone certify accuracy? No. A conservative method can still be unstable or overly diffusive.
- **Execute diffusion against a known sine solution** (rule 23.2.2). Can one smooth mode look reasonable above the stability limit? Yes. An unstable high-frequency mode may initially be absent or tiny. The all-mode stability condition still matters.
- **Measure solution error on successive meshes** (rule 23.3.3). Why hold the time-error budget in mind during mesh refinement? A fixed time step can dominate the error and conceal spatial convergence.
- **See waves drift on a coarse grid** (rule 23.2.3). With ten cells per wavelength, is the wave in the right place after five wavelengths? No. It moves at 93.5% of the true speed and lags by about 116 degrees, a third of a wavelength.
- **See centered differences wiggle when flow outruns diffusion** (rule 23.1.2). The exact solution never goes below zero. Can the centered answer? Yes. Above Pe=2 it zigzags; at Pe=8 it dips to −0.6. Refine, or bias the scheme upwind.

## Teach and check understanding

Start with 23.2.1, 23.2.2, 23.3.2 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
