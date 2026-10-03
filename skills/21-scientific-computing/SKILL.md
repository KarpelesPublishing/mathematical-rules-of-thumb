---
name: math-thumb-scientific-computing
description: "Apply Chapter 21 (Scientific Computing: Precision, Performance, and Reproducibility) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to distinguish arithmetic accuracy from speed and set a measurable computational contract."
---

# Chapter 21. Scientific Computing: Precision, Performance, and Reproducibility

Apply Chapter 21 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [21-scientific-computing.ipynb](../../notebooks/21-scientific-computing.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Precision and data scale; permitted absolute/relative error; reproducibility contract; profile; data movement; processor count or failure spacing.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Is the claimed accuracy close to machine precision?** Combine unit roundoff with conditioning and algorithmic error; do not equate `eps` with final accuracy.
- **Does an expression subtract nearly equal values?** Search for a stable equivalent such as `log1p`, `expm1`, compensated summation, or a scaled formulation.
- **Do parallel runs differ?** Quantify the discrepancy, rule out races and undefined behavior, then choose a tolerance, deterministic tree, or reproducible accumulator consistent with the contract.
- **Are tests flaky?** Derive absolute and relative tolerances from expected error and units, including explicit policies for nonfinite values and arrays.
- **Is the program too slow?** Profile the complete representative workload before changing code, then reprofile after each intervention.
- **Is a hot kernel limited by arithmetic or data motion?** Measure arithmetic intensity and hardware ceilings before choosing vectorization, blocking, fusion, or traffic reduction.
- **Will more processors help?** Measure strong scaling and use the effective serial fraction to bound the gain.
- **Can the run outlive reliable hardware?** Estimate checkpoint cost and job-level failure spacing, calculate a starting interval, and test actual restart.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Do not promise bitwise reproducibility from a tolerance check. Avoid reading machine epsilon as guaranteed final accuracy or a theoretical ceiling as measured performance.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 21.1.1 | Budget binary64 as about sixteen decimal digits | Independent | exact under assumptions | representative workload; floating point execution |
| 21.1.2 | Use log1p and expm1 for small arguments | Independent | exact under assumptions | representative workload; floating point execution; small parameter |
| 21.2.1 | Expect parallel floating reductions to change low bits | Independent | exact under assumptions | representative workload; floating point execution |
| 21.2.2 | Compare floating results with absolute plus relative tolerance | Workflow | empirical heuristic | meaningful absolute scale; meaningful relative scale |
| 21.2.3 | Profile before optimizing scientific code | Workflow | empirical heuristic | representative workload; representative build configuration |
| 21.3.1 | Know whether a kernel is compute-bound or bandwidth-bound | Workflow | empirical heuristic | representative workload; floating point execution |
| 21.3.2 | Use Amdahl's law to bound strong scaling | Independent | guaranteed bound | representative workload; floating point execution |
| 21.3.3 | Set checkpoint interval from checkpoint cost and failure rate | Independent | first-order approximation | independent exponential failures; fixed checkpoint cost; periodic checkpointing |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [21-scientific-computing.ipynb](../../notebooks/21-scientific-computing.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Preserve a small logarithmic change** (rule 21.1.2). Why can log(1+x) vanish at x=10⁻¹⁶? The addition can round to exactly one. log1p works without first losing that small increment.
- **Bound speedup before buying more processors** (rule 21.3.2). What is the ceiling when s=.1? Ten, even with infinitely many processors under the ideal model.
- **Balance checkpoint overhead against lost work** (rule 21.3.3). If failure interval quadruples, how does the optimal interval change? It doubles because the leading optimum scales as √M.
- **See why parallel sums disagree in the last digits** (rule 21.2.1). Is a parallel result wrong if it differs from the serial result in the last digits? No. Both are rounded answers that took different paths. Compare them with a tolerance, not with exact equality.
- **Find out whether memory or arithmetic sets the speed limit** (rule 21.3.1). A kernel does 1 FLOP per byte. Will a chip with twice the arithmetic peak make it faster? No. At 1 FLOP/byte it is capped at 100 GFLOP/s by memory bandwidth, far below either peak. Raise its data reuse or the bandwidth.

## Teach and check understanding

Start with 21.1.2, 21.2.2, 21.3.2 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
