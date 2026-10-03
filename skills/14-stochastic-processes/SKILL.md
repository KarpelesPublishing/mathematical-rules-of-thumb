---
name: math-thumb-stochastic-processes
description: "Apply Chapter 14 (Stochastic Processes: Rates, Waiting, and Dependence) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to recognize when a steady-state queue estimate exists and why delay rises near capacity."
---

# Chapter 14. Stochastic Processes: Rates, Waiting, and Dependence

Apply Chapter 14 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [14-stochastic-processes.ipynb](../../notebooks/14-stochastic-processes.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Rate and time units; arrival/service model; stationarity; dependence; system boundary; whether count, wait, inventory, or mixing is sought.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Do you have a stable event rate and an exposure?** Use $\lambda t$ for a Poisson count scale. Use the zero-count complement for event risk and $1/\lambda$ for an exponential mean wait.
- **Are event streams being combined or split?** Add rates only for independent Poisson streams. Multiply by label probabilities only for eventwise-independent thinning.
- **Is the total count fixed?** Simulate homogeneous event locations as sorted uniforms; otherwise retain the exponential-gap view.
- **Is randomness accumulating through independent centered increments?** Expect root-time or root-step spread. Add drift separately and inspect dependence.
- **Is a time series persistent?** Translate $\phi$ into half-life and stationary variance only after checking $|\phi|<1$ and the adequacy of an AR(1) model.
- **Is a smoother or renewal process being summarized?** Convert EWMA weight to a variance-equivalent window, or wait moments to a long-horizon count approximation, while keeping their regimes explicit.
- **Is a Markov chain being run?** Estimate its slowest dependence scale, then use multiple-chain evidence and estimand-specific ESS rather than nominal iterations.
- **Is a queue or flow system involved?** Apply Little's law with consistent boundaries. For M/M/1 calculations, establish $\rho<1$ before evaluating delay and preserve capacity headroom.
- **Is $0.234$ proposed as a tuning target?** Confirm high-dimensional random-walk Metropolis assumptions; otherwise use diagnostics appropriate to the actual sampler.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Little's law uses compatible system boundaries and long-run averages; M/M/1 delay adds specific queue assumptions. Nominal simulation draws are not automatically independent draws.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 14.1.1 | Poisson Count Equals Rate Times Exposure | Independent | exact under assumptions | homogeneous poisson process; known rate and exposure |
| 14.1.2 | At Least One Poisson Arrival | Independent | exact under assumptions | homogeneous poisson process; known rate and exposure |
| 14.1.3 | Mean Exponential Wait Is the Inverse Rate | Independent | exact under assumptions | homogeneous poisson arrivals; positive constant rate |
| 14.1.4 | Memorylessness Means No Aging | Independent | exact under assumptions | nonnegative waiting time; exact memoryless property |
| 14.1.5 | Superposed Poisson Rates Add | Independent | exact under assumptions | independent poisson streams; compatible time units |
| 14.1.6 | Poisson Thinning Multiplies the Rate | Independent | exact under assumptions | poisson input stream; independent constant retention |
| 14.1.7 | Poisson Arrival Times Are Uniform Given the Count | Independent | exact under assumptions | homogeneous poisson process; fixed interval; conditioned event count |
| 14.2.1 | Random-Walk Displacement Grows as Root N | Independent | asymptotic | independent zero mean steps; finite step variance |
| 14.2.2 | Diffusion Distance from \(2Dt\) | Independent | exact under assumptions | one dimensional brownian diffusion; constant diffusivity |
| 14.2.3 | AR(1) Shock Half-Life | Independent | exact under assumptions | positive ar1 coefficient below one; stable coefficient |
| 14.2.4 | AR(1) Long-Run Variance Amplification | Independent | exact under assumptions | stationary ar1 process; independent finite variance innovations |
| 14.2.5 | EWMA Effective Window Length | Independent | first-order approximation | constant smoothing factor; long series; uncorrelated input noise |
| 14.2.6 | Renewal Count Mean and Variance at Long Times | Independent | asymptotic | iid positive interarrivals; finite mean and variance; long time horizon |
| 14.2.7 | Markov Mixing Scale from the Second Eigenvalue | Independent | asymptotic | finite reversible ergodic chain; known nonstationary eigenvalue |
| 14.3.1 | Little's Law: Inventory Equals Throughput Times Time | Independent | exact under assumptions | stable flow system; consistent customer boundary; long run averages |
| 14.3.2 | M/M/1 Stability Requires Utilization Below One | Workflow | exact under assumptions | m m 1 queue; steady state objective |
| 14.3.3 | M/M/1 Delay Blows Up Near Capacity | Independent | exact under assumptions | poisson arrivals; exponential service; single server; steady state; arrival rate below service rate |
| 14.3.4 | MCMC Effective Sample Size from Autocorrelation | Workflow | asymptotic | stationary ergodic chain; reliable autocorrelation estimate |
| 14.3.5 | Burn In for Several Dependence Time Scales | Workflow | empirical heuristic | ergodic markov chain; estimated relaxation time; overdispersed multiple starts |
| 14.3.6 | The 0.234 Random-Walk Metropolis Benchmark | Workflow | asymptotic | high dimension; smooth product like target; random walk proposal |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [14-stochastic-processes.ipynb](../../notebooks/14-stochastic-processes.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Approach the queue capacity boundary** (rule 14.3.3). Can you report a negative wait when λ exceeds μ? No. The stationary formula is invalid at or above capacity; a negative output would be a model-use error.
- **Follow a correlated shock through time** (rule 14.2.3). Does a higher φ make the same shock vanish sooner? No. A higher positive φ retains more of the shock each step and increases its half-life.
- **Turn exposure into a Poisson count** (rule 14.1.1). What mean count do you expect over two hours? Twice the hourly rate. The exposure duration must accompany the rate.
- **Watch a random walk spread like a square root** (rule 14.2.1). If a walker takes 100 times more steps, how much farther does it typically get? Ten times farther, since √100=10.
- **Check whether waiting makes the end nearer** (rule 14.1.4). For an exponential wait with mean 10 minutes, after 15 minutes of waiting, what is the expected extra wait? Still 10 minutes. The exponential forgets the past; only an aging model shortens the remaining wait.

## Teach and check understanding

Start with 14.3.1, 14.3.2, 14.3.3 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
