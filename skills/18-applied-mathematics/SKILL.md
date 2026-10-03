---
name: math-thumb-applied-mathematics
description: "Apply Chapter 18 (Applied Mathematics: Scaling, Regimes, and Model Sanity) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to reject inconsistent models and use dimensionless ratios to choose a plausible first approximation."
---

# Chapter 18. Applied Mathematics: Scaling, Regimes, and Model Sanity

Apply Chapter 18 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [18-applied-mathematics.ipynb](../../notebooks/18-applied-mathematics.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Output and accuracy target; variables with dimensions; geometry; characteristic length, speed and time; property values; relevant regimes.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

1. Define the output, domain, and decision accuracy. List variables with units.
2. Check dimensional homogeneity, signs, conservation, symmetries, and easy limits before solving.
3. Choose characteristic scales that make typical variables order one; allow different scales in different regions.
4. Form independent dimensionless groups and identify plausible dominant balances.
5. Compute relevant regime ratios with explicitly defined \(U,L,T\), properties, and geometry.
6. Select the simplest model consistent with those ratios, then substitute the approximation back into every discarded term.
7. Compare with data or a higher-fidelity model near thresholds; escalate when multiple ratios are order one or uncertainty crosses regimes.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Dimensionally consistent does not mean physically correct. State characteristic scales explicitly and re-check discarded terms after choosing a regime.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 18.1.1 | Reject equations that are not dimensionally homogeneous | Workflow | exact under assumptions | quantities have defined dimensions; consistent unit semantics |
| 18.1.2 | Test every model in easy limiting cases | Workflow | empirical heuristic | known limit behavior; specified limit path |
| 18.1.3 | Report parameter sensitivity as a dimensionless elasticity | Independent | first-order approximation | valid characteristic scales; physical model validity |
| 18.2.1 | Scale variables so typical dimensionless values are order one | Workflow | empirical heuristic | valid characteristic scales; physical model validity; small parameter |
| 18.2.2 | Reduce dimensional variables with Buckingham Pi | Independent | exact under assumptions | valid characteristic scales; physical model validity; independence |
| 18.2.3 | Find leading behavior by balancing the largest competing terms | Independent | asymptotic | valid characteristic scales; physical model validity |
| 18.2.4 | Compare process timescales before coupling models | Workflow | asymptotic | scale separation; stable fast subsystem; valid characteristic times |
| 18.3.1 | Use Reynolds number to compare inertia with viscosity | Workflow | empirical heuristic | valid characteristic scales; physical model validity |
| 18.3.2 | Use Peclet number to compare advection with diffusion | Workflow | empirical heuristic | valid characteristic scales; physical model validity |
| 18.3.3 | Use Damkohler number to compare reaction with transport | Workflow | empirical heuristic | valid characteristic scales; physical model validity; uniform grid or scale |
| 18.3.4 | Use Fourier number to estimate diffusion penetration time | Independent | asymptotic | valid characteristic scales; physical model validity |
| 18.3.5 | Use lumped thermal capacitance only for small Biot number | Workflow | conventional threshold | valid characteristic scales; physical model validity; uniform grid or scale |
| 18.3.6 | Check Mach number before neglecting compressibility | Workflow | conventional threshold | valid characteristic scales; physical model validity; small parameter |
| 18.3.7 | Check Knudsen number before using continuum equations | Workflow | conventional threshold | valid characteristic scales; physical model validity; small parameter |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [18-applied-mathematics.ipynb](../../notebooks/18-applied-mathematics.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Screen a lumped thermal model** (rule 18.3.5). Does a computed time constant validate the material properties? No. It is conditional on the assumed properties, geometry and applicable lumped model.
- **Compare transport time scales** (rule 18.3.2). What does Pe≫1 indicate here? Advection acts over the length scale faster than diffusion; it does not by itself determine every feature of the solution.
- **Construct a dimensionless flow comparison** (rule 18.3.1). Can one Reynolds cutoff classify all geometries? No. A threshold adopted for one flow arrangement is not a universal turbulence rule.
- **Feel the square law of diffusion time** (rule 18.3.4). How much longer does a 4 cm slab take than a 2 cm slab? Four times as long: 160 s versus 40 s.

## Teach and check understanding

Start with 18.1.1, 18.2.4, 18.3.5 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
