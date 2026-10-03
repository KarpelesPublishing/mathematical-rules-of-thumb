---
name: math-thumb-probability
description: "Apply Chapter 12 (Probability: Fast Reasoning Under Uncertainty) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to choose among an exact complement, approximation, and guaranteed probability bound."
---

# Chapter 12. Probability: Fast Reasoning Under Uncertainty

Apply Chapter 12 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [12-probability.ipynb](../../notebooks/12-probability.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Event and threshold; distribution information; number of opportunities; dependence; moments; whether a guarantee or approximation is needed.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Need a guaranteed bound with little distributional information?** Start with Markov, Chebyshev, Cantelli, or the union bound according to the available moments and tail direction.
- **Know event overlaps?** Add the Bonferroni pairwise correction and decide whether the resulting bracket is narrow enough.
- **Combining uncertainty?** Check covariance before using root-sum-of-squares, and condition explicitly before splitting total variance.
- **Facing repeated rare opportunities?** Use the exact complement first, then recognize Poisson, birthday, coupon, or exponential scales only in their regimes.
- **Updating evidence?** Convert the base rate to prior odds and multiply only conditionally independent likelihood ratios.
- **Replacing a distribution?** Check support, expected successes and failures, skew, moments, and tail location before selecting a normal, Poisson, or exponential approximation.
- **Transforming an estimate?** Use Jensen for bias direction, the lognormal formula for an exact normal-log model, or the delta method for local uncertainty propagation.
- **Need sharper tail control?** Ask what extra fact is defensible: direction, a hard bound, total variance, or sub-Gaussian decay.
- **Running a simulation?** Report root-$N$ Monte Carlo error, then audit correlation, bias, weight concentration, and proposal support.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Do not silently multiply probabilities or likelihood ratios when the required independence is unverified. Distinguish bounds from approximate event rates.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 12.1.1 | Markov's One-Moment Tail Bound | Independent | guaranteed bound | nonnegative random variable; finite mean; positive threshold |
| 12.1.2 | Chebyshev's Distribution-Free Sigma Rule | Independent | guaranteed bound | finite mean; finite variance |
| 12.1.3 | Union Bound for Many Failure Modes | Independent | guaranteed bound | well defined event probabilities |
| 12.1.4 | Two-Term Bonferroni Correction for Overlap | Workflow | guaranteed bound | known pairwise intersections |
| 12.1.5 | Root-Sum-of-Squares for Independent Noise | Independent | exact under assumptions | independent or uncorrelated terms; finite variances |
| 12.1.6 | Total Variance: Within Plus Between | Independent | exact under assumptions | finite second moment; well defined conditioning variable |
| 12.1.7 | Jensen's Curvature Check | Independent | exact under assumptions | integrable random variable; convex or concave function |
| 12.1.8 | At Least One Rare Event | Independent | asymptotic | independent equal probability trials; small event probability |
| 12.1.9 | Birthday Collision Threshold | Independent | asymptotic | independent uniform draws; large state space |
| 12.1.10 | Coupon Collector Scale | Independent | asymptotic | independent uniform categories; large category count |
| 12.2.1 | Bayes Updating in Odds Form | Independent | exact under assumptions | valid prior odds; calibrated likelihood ratio; conditional independence for repeated evidence |
| 12.2.2 | Laplace Rule of Succession | Independent | exact under assumptions | exchangeable binary trials; uniform beta prior |
| 12.2.3 | Central-Limit Approximation for a Sample Mean | Independent | asymptotic | iid observations; finite variance; large sample |
| 12.2.4 | The 68-95-99.7 Normal Rule | Independent | empirical heuristic | approximately normal distribution |
| 12.2.5 | Normal Approximation to a Binomial Count | Workflow | conventional threshold | independent bernoulli trials; constant success probability; large expected successes and failures |
| 12.2.6 | Normal Approximation to a Poisson Count | Workflow | conventional threshold | poisson count model; moderate or large rate |
| 12.2.7 | Half-Unit Continuity Correction | Workflow | first-order approximation | integer valued count; normal approximation already appropriate |
| 12.2.8 | Berry-Esseen Check on CLT Accuracy | Workflow | guaranteed bound | iid summands; finite nonzero variance; finite third absolute moment |
| 12.2.9 | Poisson Approximation to a Binomial Count | Workflow | asymptotic | independent bernoulli trials; small success probability; moderate expected count |
| 12.2.10 | Exponential Approximation to a Geometric Wait | Workflow | asymptotic | small step probability; independent memoryless trials |
| 12.2.11 | Lognormal Mean Correction | Independent | exact under assumptions | normal log values; known log variance |
| 12.2.12 | Delta Method for a Smooth Transformation | Workflow | asymptotic | asymptotically normal estimator; differentiable transform; nonzero local derivative |
| 12.3.1 | Cantelli's One-Sided Variance Bound | Workflow | guaranteed bound | finite mean; finite nonzero variance; one sided event |
| 12.3.2 | Hoeffding Bound for a Bounded Sample Mean | Independent | guaranteed bound | independent observations; known finite bounds |
| 12.3.3 | Multiplicative Chernoff Bound for Counts | Independent | guaranteed bound | independent bernoulli trials; known expected count |
| 12.3.4 | Bernstein's Variance-Aware Tail Bound | Workflow | guaranteed bound | independent bounded summands; known or bounded variance |
| 12.3.5 | Maximum of Many Sub-Gaussian Errors | Independent | asymptotic | centered subgaussian variables; common scale; finite collection |
| 12.3.6 | Mills-Ratio Approximation for a Normal Tail | Independent | asymptotic | standard normal tail; large positive z |
| 12.3.7 | Monte Carlo Error Falls as One Over Root N | Independent | asymptotic | independent draws; finite output variance |
| 12.3.8 | Importance-Weight Effective Sample Size | Workflow | empirical heuristic | nonnegative normalized weights; target support covered |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [12-probability.ipynb](../../notebooks/12-probability.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Accumulate a rare risk across opportunities** (rule 12.1.8). If all failures happen together, can you still use the product complement? No. Perfect dependence gives any-event probability p rather than 1−(1−p)ⁿ.
- **Make the base rate visible in an update** (rule 12.2.1). Why can many positive results be false when prevalence is tiny? The large noncase population contributes false positives that can outnumber the true positives, despite high sensitivity.
- **Run a finite Monte Carlo estimate** (rule 12.3.7). How much more computation halves standard error? Four times as many independent trials, because standard error scales as N⁻¹ᐟ².
- **See how soon random labels collide** (rule 12.1.9). How many people make a shared birthday more likely than not? 23. With 365 days, 1.1774×√365≈22.5, and the exact count first passes 50% at 23.
- **See why the last coupons take longest** (rule 12.1.10). How many random birthdays do you expect to need before every day of a 365-day year appears? About 2,365, since 365×H₃₆₅≈2,364.6. That is about 6.5 people per day of the year.

## Teach and check understanding

Start with 12.1.3, 12.1.8, 12.2.1 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
