---
name: math-thumb-control-theory
description: "Apply Chapter 25 (Control Theory: Performance, Robustness, and Implementation Reality) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to translate implementation constraints into a delay and sampling budget before tuning a controller."
---

# Chapter 25. Control Theory: Performance, Robustness, and Implementation Reality

Apply Chapter 25 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [25-control-theory.ipynb](../../notebooks/25-control-theory.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Plant and loop structure; bandwidth/crossover conventions; delays; sample rate; actuator limits; noise; robustness and time-response targets.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Is the requirement stated in time units?** Translate it into a bandwidth interval, then verify the full step response rather than trusting one constant.
- **Is the persistent disturbance approximately constant?** Add integral structure only if the loop can remain stable and the actuator has enough authority.
- **Will a reduced model guide tuning?** Compare pole decay, residues, zeros, and full-versus-reduced responses in every important channel.
- **Is the loop ordinary SISO with a clear crossover?** Use phase and gain margins as starting screens, then inspect peak sensitivity.
- **Are there multiple crossovers, unstable poles, or MIMO coupling?** Escalate from classical margins to Nyquist, disk, or structured robustness analysis.
- **What latency is unavoidable?** Convert every component to phase at crossover before raising bandwidth.
- **Will the design run digitally?** Include sample, hold, computation, jitter, filtering, and quantization in the implemented model.
- **Can the actuator saturate or the derivative see noise?** Add anti-windup and derivative filtering before nonlinear simulation or hardware tests.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** State Hz versus rad/s and identify the actual crossover. Classical margins and sampling ratios are design screens, not permission to deploy a controller without model and implementation checks.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 25.1.1 | Estimate rise time from closed-loop bandwidth | Independent | first-order approximation | model fidelity; closed loop stability |
| 25.1.2 | Add integral action for zero steady-state error to constant disturbances | Workflow | empirical heuristic | model fidelity; closed loop stability |
| 25.1.3 | Trust a dominant-pole approximation only with clear separation | Workflow | conventional threshold | model fidelity; closed loop stability; large problem or asymptotic regime |
| 25.2.1 | Start loop shaping near 45 to 60 degrees phase margin | Workflow | conventional threshold | model fidelity; closed loop stability |
| 25.2.2 | Seek at least about 6 dB classical gain margin | Workflow | conventional threshold | model fidelity; closed loop stability |
| 25.2.3 | Keep peak sensitivity near or below two when feasible | Workflow | conventional threshold | model fidelity; closed loop stability |
| 25.3.1 | Convert every delay into phase lag at crossover | Workflow | exact under assumptions | model fidelity; closed loop stability |
| 25.3.2 | Sample a digital control loop at least ten times faster than bandwidth | Workflow | conventional threshold | model fidelity; closed loop stability |
| 25.3.3 | Add anti-windup whenever integral control can saturate | Specialized | empirical heuristic | model fidelity; closed loop stability |
| 25.3.4 | Always filter derivative action | Specialized | empirical heuristic | model fidelity; closed loop stability |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [25-control-theory.ipynb](../../notebooks/25-control-theory.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Connect a real step response with bandwidth** (rule 25.1.1). Why can two systems with similar bandwidth have different overshoot? Their pole and zero structures differ. The first-order model here has no overshoot.
- **Budget latency at an assumed crossover** (rule 25.3.1). Does a positive remaining nominal margin prove the implemented loop is robust? No. Other crossovers, model uncertainty, discretization and nonlinear actuator behavior also need checks.
- **Simulate integral windup and a remedy** (rule 25.3.3). Why does the old integral keep pushing after the target drops? During saturation it accumulated an error the actuator could not correct. Limiting integration prevents much of that stored excess.
- **Remove steady error with integral action** (rule 25.1.2). Why does Ki=0 never reach the setpoint? A proportional controller only pushes when error exists, so some error must remain. The integral keeps pushing until the error is zero.
- **See what phase margin looks like in a step response** (rule 25.2.1). Why do designers start near 45 to 60 degrees? At 30° this loop overshoots about 42% and rings; at 60° about 9%. Below 45° a little extra delay can push it toward instability.

## Teach and check understanding

Start with 25.2.1, 25.3.1, 25.3.2 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
