---
name: math-thumb-guide
description: Use Mathematical Rules of Thumb as one skill covering all 25 chapters and 400 rules. Help a reader choose the right chapter and rule, solve a practical problem with their own inputs, learn with the chapter notebooks, or audit a calculation. Use when the reader wants the whole book or does not know which rule fits.
---

# Mathematical Rules of Thumb

*Mathematical Rules of Thumb* by Jason Karpeles collects 400 numbered rules across 25 chapters, from algebra to control theory. Each rule is a quick, checkable step: an identity, an approximation, a bound, a diagnostic, or a heuristic, with the conditions under which it holds. This skill routes a question to the right chapter skill, then applies that chapter's rules to the reader's inputs.

Start with: "Help me work out [my problem] and choose the right rules."

## Chapters

| Ch | Title | Use when you need to | Chapter skill | Notebook |
|---|---|---|---|---|
| 1 | Algebra: See the Structure Before You Solve | Choose a useful representation and decide whether a first-order estimate is accurate enough. | [skill](../01-algebra/SKILL.md) | [notebook](../../notebooks/01-algebra.ipynb) |
| 2 | Geometry: Estimate Shape Before Measuring It | Use scaling and feasibility checks before committing to a geometric calculation. | [skill](../02-geometry/SKILL.md) | [notebook](../../notebooks/02-geometry.ipynb) |
| 3 | Trigonometry: Control Angles, Directions, and Oscillations | Choose angle representations that preserve quadrants and quantify a small-angle approximation. | [skill](../03-trigonometry/SKILL.md) | [notebook](../../notebooks/03-trigonometry.ipynb) |
| 4 | Calculus: Turn Local Change into Global Control | Turn a local model into a checked estimate and distinguish an error scale from a proved bound. | [skill](../04-calculus/SKILL.md) | [notebook](../../notebooks/04-calculus.ipynb) |
| 5 | Analysis: Know When Limits and Proofs Are Safe | Write the hypotheses that make a convergence or stopping claim defensible. | [skill](../05-analysis/SKILL.md) | [notebook](../../notebooks/05-analysis.ipynb) |
| 6 | Complex Analysis: Turn Analytic Structure into Bounds and Counts | Use complex structure to obtain a valid bound or zero count before seeking exact values. | [skill](../06-complex-analysis/SKILL.md) | [notebook](../../notebooks/06-complex-analysis.ipynb) |
| 7 | Linear Algebra: Choose Stable Matrix Methods Before Computing | Choose a matrix method from verified structure and report what its residual actually certifies. | [skill](../07-linear-algebra/SKILL.md) | [notebook](../../notebooks/07-linear-algebra.ipynb) |
| 8 | Number Theory: Reduce Large Arithmetic to Small Structure | Reduce integer calculations while preserving divisibility and invertibility. | [skill](../08-number-theory/SKILL.md) | [notebook](../../notebooks/08-number-theory.ipynb) |
| 9 | Combinatorics: Counting Without Exhaustion | Define the sample space before choosing a counting formula. | [skill](../09-combinatorics/SKILL.md) | [notebook](../../notebooks/09-combinatorics.ipynb) |
| 10 | Graph Theory: Structural Tests for Networks | Use a graph obstruction or structure test without mistaking a necessary condition for a proof. | [skill](../10-graph-theory/SKILL.md) | [notebook](../../notebooks/10-graph-theory.ipynb) |
| 11 | Asymptotics: Finding What Matters at Scale | Choose a scale estimate that survives the requested algebra and finite-input tolerance. | [skill](../11-asymptotics/SKILL.md) | [notebook](../../notebooks/11-asymptotics.ipynb) |
| 12 | Probability: Fast Reasoning Under Uncertainty | Choose among an exact complement, approximation, and guaranteed probability bound. | [skill](../12-probability/SKILL.md) | [notebook](../../notebooks/12-probability.ipynb) |
| 13 | Statistics: From Data to Defensible Decisions | Plan precision and report uncertainty using the actual independent sampling units. | [skill](../13-statistics/SKILL.md) | [notebook](../../notebooks/13-statistics.ipynb) |
| 14 | Stochastic Processes: Rates, Waiting, and Dependence | Recognize when a steady-state queue estimate exists and why delay rises near capacity. | [skill](../14-stochastic-processes/SKILL.md) | [notebook](../../notebooks/14-stochastic-processes.ipynb) |
| 15 | Information Theory: Measuring Information and Its Limits | Compute information quantities on a declared scale and identify the operational limit they express. | [skill](../15-information-theory/SKILL.md) | [notebook](../../notebooks/15-information-theory.ipynb) |
| 16 | Measurement and Uncertainty: Building Trustworthy Results | Build a measurement uncertainty budget and report a result without hiding covariance or bias. | [skill](../16-measurement/SKILL.md) | [notebook](../../notebooks/16-measurement.ipynb) |
| 17 | Financial Mathematics: Comparing Money Across Time | Place hypothetical cash flows on one time and rate basis before comparing them. | [skill](../17-financial-mathematics/SKILL.md) | [notebook](../../notebooks/17-financial-mathematics.ipynb) |
| 18 | Applied Mathematics: Scaling, Regimes, and Model Sanity | Reject inconsistent models and use dimensionless ratios to choose a plausible first approximation. | [skill](../18-applied-mathematics/SKILL.md) | [notebook](../../notebooks/18-applied-mathematics.ipynb) |
| 19 | Optimization: Scale, Search, and Certify | Choose a step and stopping test that match the optimization problem's assumptions. | [skill](../19-optimization/SKILL.md) | [notebook](../../notebooks/19-optimization.ipynb) |
| 20 | Numerical Methods: Approximation You Can Trust | Budget a numerical computation and verify its accuracy with an independent check. | [skill](../20-numerical-methods/SKILL.md) | [notebook](../../notebooks/20-numerical-methods.ipynb) |
| 21 | Scientific Computing: Precision, Performance, and Reproducibility | Distinguish arithmetic accuracy from speed and set a measurable computational contract. | [skill](../21-scientific-computing/SKILL.md) | [notebook](../../notebooks/21-scientific-computing.ipynb) |
| 22 | Ordinary Differential Equations: Choosing and Checking Time Integrators | Separate time-integrator stability from accuracy and verify the quantities the application needs. | [skill](../22-ode/SKILL.md) | [notebook](../../notebooks/22-ode.ipynb) |
| 23 | Partial Differential Equations: Discretize, Resolve, and Verify | Compute scheme-specific stability limits and design a refinement check that separates space and time errors. | [skill](../23-pde/SKILL.md) | [notebook](../../notebooks/23-pde.ipynb) |
| 24 | Signal Processing: Sampling, Resolution, and Spectral Judgment | Separate spectral display spacing from information acquired and plan sampling before aliasing occurs. | [skill](../24-signal-processing/SKILL.md) | [notebook](../../notebooks/24-signal-processing.ipynb) |
| 25 | Control Theory: Performance, Robustness, and Implementation Reality | Translate implementation constraints into a delay and sampling budget before tuning a controller. | [skill](../25-control-theory/SKILL.md) | [notebook](../../notebooks/25-control-theory.ipynb) |

## Start in the reader's language

Infer the mode: solve, learn, audit, or explore. Ask only if the difference changes the response. Identify the desired result, known inputs and units, and the accuracy or decision threshold. Ask the next question that changes the route; do not demand a full intake form or subject vocabulary. A reader who asks for a worked solution gets one.

If the reader does not know where to start, ask what they are trying to work out, then use this table:

| Their starting point | Follow-up that distinguishes the job | Chapter family |
|---|---|---|
| Everyday numbers, change, shapes, or angles | "What changes, and which quantity do you need?" | 1-4; 17 for money across dates |
| Risk, data, measurements, or uncertainty | "Are you calculating an event's chance, drawing a conclusion from observations, or combining measurement errors?" | 12-16 |
| Counting, integer puzzles, or networks | "Do you need a count, a divisibility result, or a property of a network?" | 8-10; 11 for large-scale estimates |
| A proof or an approximation that may not be valid | "Which step needs justification, and over what domain?" | 5-6 and 11; 4 for local changes |
| A model, solver, or calculation that seems wrong or slow | "Is the issue the model, the numerical answer, or the implementation's speed?" | 7 and 18-21 |
| A changing physical system, recorded signal, or controller | "Are you predicting evolution, interpreting observations, or designing feedback?" | 22-25; 18 for model regimes |

## Choose from the intended output

| Similar-sounding requests | Choose by this distinction | Ask only if unclear |
|---|---|---|
| Probability / statistics | Model and event probability supplied: 12. Unknown population quantity inferred from sampled data: 13. | "Is the event probability an input or what you're trying to estimate?" |
| Statistics / measurement | Sampling and inference about a population: 13. A measurement equation and instrument/correction errors: 16. | "Does the uncertainty come from sampling people/items or from measuring the inputs?" |
| Probability / stochastic processes | A static event or distribution: 12. Arrivals, queues, paths, or time dependence: 14. | "Does the order or timing of events change the answer?" |
| Calculus / numerical methods | Derive or understand a local model or derivative: 4. Choose or check a finite algorithm: 20. | "Do you need a mathematical relation or a computed answer with an error check?" |
| Linear algebra / optimization | Solve a matrix equation or inspect matrix structure: 7. Minimize an objective under constraints: 19. | "Is the target an equation solution or the best feasible choice?" |
| Numerical methods / scientific computing | Method accuracy or convergence: 20. Floating arithmetic, reproducibility, memory, or runtime: 21. | "Does the answer fail a mathematical check, or does the implementation miss a precision/performance target?" |
| Algebra / financial mathematics | General growth or proportions: 1. Rates and dated cash flows: 17. | "Do payment dates, compounding periods, or valuation dates affect the comparison?" |
| ODE / PDE | Evolution only in time for state variables: 22. Spatial field, mesh, and boundary conditions: 23. | "Does the state vary over space as well as time?" |
| Signal processing / control | Acquire or interpret a signal: 24. Change system behavior through feedback: 25. | "Are you measuring what happened or using the signal to control what happens?" |
| Analysis / asymptotics | Establish quantified convergence or a theorem's hypotheses: 5. Describe dominant scale in a specified limit: 11. | "Do you need a proof of convergence or a useful approximation at large/small scale?" |

For a multi-part problem, decide which operation must happen first and keep the rest as named next steps.

## Route, then do the work

1. Pick the primary chapter and say in one sentence what it will produce for the reader. Name a second chapter only if it supplies a needed next operation.
2. Open that chapter's skill, choose the numbered rule, and check its conditions before applying its formula.
3. Frame the question, calculate with the reader's inputs, verify with an independent check, and return the decision or next step.
4. For learning, use the chapter notebook as a worked template: change its inputs and rerun the cell.

## Re-route when evidence changes

- A "small error" turns out to be a solver residual: use Chapter 20 and conditioning from Chapter 7 before interpreting it as an answer error.
- A queue's arrival rate reaches its service rate: reject the stationary finite-delay formula in Chapter 14 and identify the capacity or modeling question; do not return a negative delay.
- Repeated measurements on the same people invalidate independent sampling: return to Chapter 13's design rules, with Chapter 14 only when an appropriate temporal model is needed.
- A required FFT resolution exceeds what the acquired duration can support: Chapter 24 changes the acquisition plan; adding zeros cannot satisfy the requirement.
- A claimed controller margin ignores delay or saturation: Chapter 25 must check the implemented loop before accepting the nominal result.
- A domain restriction, unsupported model, or unmet theorem hypothesis fails: report that specific boundary, then choose a supported alternative if available.

On each transition, carry the question, units, verified assumptions, result type, uncertainty, and the unresolved operation.

## Rules that govern every route

- Keep the role of a rule (Independent or Workflow) separate from its kind (identity, approximation, bound, diagnostic, heuristic). A rule that chooses a method has not finished the calculation.
- Preserve units, domains, signs, independence or covariance assumptions, and error limits. When a condition fails, change the route or name the missing evidence.
- Verify in a way suited to the claim: a remainder bound, an alternative calculation, a limiting case, a residual read with its conditioning, or a refinement study. A finite example does not prove a general theorem.
- Cite the rule number. Label any example or method that comes from outside the book.

## Return a result

Give: the route and why, the rule numbers, assumptions, calculation, check, result with uncertainty, and next action. Scale this to the question; a simple estimate can fit in one paragraph.
