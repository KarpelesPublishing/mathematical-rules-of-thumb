---
name: math-thumb-statistics
description: "Apply Chapter 13 (Statistics: From Data to Defensible Decisions) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to plan precision and report uncertainty using the actual independent sampling units."
---

# Chapter 13. Statistics: From Data to Defensible Decisions

Apply Chapter 13 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [13-statistics.ipynb](../../notebooks/13-statistics.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Estimand and target population; sampling or assignment design; independent units; variation; precision target; multiplicity and stopping plan.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

1. **Name the target.** Is it a finite-population total, a future-population mean, a treatment contrast, a proportion, a correlation, a predictive loss, or a model coefficient? Do not calculate until units and target population are explicit.
2. **Map the observation structure.** Mark clusters, repeated measurements, time order, strata, weights, blocks, pairs, censoring, and finite sampling fractions. Decide what the independent units really are.
3. **Choose the scale and summary.** Use arithmetic methods for additive variation, logarithms or geometric means for multiplicative variation, and resistant summaries when tails can dominate.
4. **Plan precision.** Select a meaningful margin or effect, estimate nuisance variation conservatively, apply the correct allocation and design effect, add attrition, and round upward.
5. **Choose inference from the design.** Use \(t\) when scale is estimated, Wilson or plus-four for ordinary proportions, exact or simulated table methods when sparse, and sequential boundaries for repeated looks.
6. **Declare the claim family.** Decide whether the goal is one protected conclusion, familywise control, or discovery screening. Set equivalence margins and multiplicity rules before outcomes are inspected.
7. **Fit and compare models.** Use AIC, BIC, or cross-validation only among scientifically plausible candidates fitted on comparable data. Preserve preprocessing inside resampling.
8. **Stress-test the answer.** Examine VIF, leverage, Cook’s distance, events per parameter, bootstrap convergence, tail rank, and sensitivity to flagged observations or design assumptions.
9. **Report the decision range.** Give the estimate, interval, assumptions, denominator, design, adjustment family, and the values within the uncertainty range that would reverse the decision.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Plan for the independent units and claim family. Screening thresholds do not automatically justify deletion, equivalence, model validity, or a universal sample-size guarantee.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 13.1.1 | Standard Error of a Mean | Independent | exact under assumptions | independent observations; finite variance; representative sample |
| 13.1.2 | Standard Error of a Sample Proportion | Independent | first-order approximation | independent bernoulli trials; probability away from boundaries; adequate sample |
| 13.1.3 | The 95% Interval Is Roughly Plus or Minus Two SE | Independent | first-order approximation | approximately normal estimator; valid standard error |
| 13.1.4 | Minimum Detectable Effect Shrinks as One Over Root N | Independent | asymptotic | fixed design; fixed noise; fixed alpha and power |
| 13.1.5 | Sample Size for a Mean Margin of Error | Independent | exact under assumptions | anticipated standard deviation; approximately normal estimator; simple random sample |
| 13.1.6 | Conservative Sample Size for a Proportion | Workflow | guaranteed bound | independent bernoulli sample; normal margin formula; unknown proportion |
| 13.1.7 | Two-Arm 80% Power Sample-Size Shortcut | Independent | first-order approximation | two equal independent normal groups; equal variance; two sided alpha 0 05; power 0 80 |
| 13.1.8 | Rule of Three for Zero Observed Events | Independent | asymptotic | zero observed events; independent identical trials; approximately 95 percent level |
| 13.1.9 | Prefer the Wilson Interval to the Wald Interval | Workflow | exact under assumptions | independent binomial sampling |
| 13.1.10 | Plus-Four Interval for a Proportion | Independent | first-order approximation | independent bernoulli trials; approximately 95 percent coverage |
| 13.1.11 | Use t Rather Than z When Sigma Is Estimated | Workflow | exact under assumptions | normal population or adequate sample; unknown sigma; independent observations |
| 13.1.12 | Fisher z Interval for a Correlation | Workflow | asymptotic | independent pairs; approximately bivariate normal; sample size above three |
| 13.1.13 | Correlation Significance Is Roughly Two Over Root N | Independent | asymptotic | independent pairs; bivariate normal null model; zero population correlation; two sided five percent test; sample size above two |
| 13.2.1 | Geometric Mean for Compound Growth | Independent | exact under assumptions | positive multiplicative factors; consistent periods |
| 13.2.2 | Log Transform for Multiplicative Variation | Workflow | empirical heuristic | strictly positive values; multiplicative error structure |
| 13.2.3 | Tukey's 1.5-IQR Outlier Fences | Independent | conventional threshold | univariate numeric data; meaningful quartiles |
| 13.2.4 | Robust z-Scores from the Median and MAD | Independent | empirical heuristic | roughly symmetric contaminated distribution; nonzero mad |
| 13.2.5 | Freedman-Diaconis Histogram Bin Width | Independent | asymptotic | univariate numeric data; nonzero iqr |
| 13.2.6 | Silverman's Rule-of-Thumb KDE Bandwidth | Independent | asymptotic | one dimensional continuous data; gaussian kernel; roughly unimodal density |
| 13.2.7 | AR(1) Effective Sample Size | Independent | asymptotic | long stationary ar1 series; positive or moderate autocorrelation |
| 13.2.8 | Kish Effective Sample Size for Unequal Weights | Independent | first-order approximation | positive weights; independent homoscedastic observations |
| 13.2.9 | Cluster Sampling Design Effect | Workflow | first-order approximation | equal cluster size; exchangeable intraclass correlation |
| 13.2.10 | Finite-Population Correction After a Noticeable Sampling Fraction | Workflow | conventional threshold | simple random sampling without replacement; known population size |
| 13.2.11 | Measurement Error Attenuates Correlation | Independent | exact under assumptions | classical independent measurement error; known reliabilities |
| 13.2.12 | Pair When Within-Pair Correlation Is Positive | Workflow | exact under assumptions | positive within pair correlation; valid pairing; difference analysis |
| 13.2.13 | Block What You Can, Randomize What You Cannot | Workflow | empirical heuristic | known nuisance factors; randomization feasible within blocks |
| 13.2.14 | Use 50-50 Allocation When Per-Unit Costs and Variances Match | Workflow | exact under assumptions | equal group variances; equal per unit costs; fixed total sample |
| 13.2.15 | Neyman Allocation for Unequal Stratum Variability | Independent | exact under assumptions | known stratum sizes; known stratum standard deviations; equal per unit costs |
| 13.2.16 | Use a Pilot to Update Variance, Not to Test the Final Claim | Workflow | empirical heuristic | pilot resembles main population; prespecified update plan |
| 13.2.17 | Add Replicated Center Points to Screen for Curvature | Workflow | empirical heuristic | quantitative factors; two level factorial base; center runs feasible |
| 13.2.18 | Use Resolution IV or Better to Screen Main Effects | Workflow | exact under assumptions | two level factorial screen; low order effect priority |
| 13.2.19 | Use a Foldover to Break Key Fractional-Factorial Aliases | Workflow | exact under assumptions | two level fractional factorial; known alias structure |
| 13.3.1 | Pair Every Effect Estimate with Its Confidence Interval | Workflow | conventional threshold | valid effect estimator; valid confidence interval |
| 13.3.2 | No Significant Difference Is Not Equivalence | Workflow | exact under assumptions | prespecified equivalence margin; valid confidence interval |
| 13.3.3 | Repeated Peeking Inflates False Positives | Workflow | exact under assumptions | repeated hypothesis tests; nominal fixed sample alpha |
| 13.3.4 | Bonferroni Familywise Error Control | Workflow | guaranteed bound | valid individual p values; planned test family |
| 13.3.5 | Benjamini-Hochberg False Discovery Rate Rule | Workflow | exact under assumptions | valid p values; independence or positive dependence; prespecified fdr level |
| 13.3.6 | Expected Cell Counts Around Five for Chi-Square Approximations | Workflow | conventional threshold | independent counts; fixed categories |
| 13.3.7 | Fisher's Exact Test for a Sparse 2-by-2 Table | Workflow | exact under assumptions | two by two table; fixed margins or valid sampling model; independent units |
| 13.3.8 | AIC Differences Under Two Are Usually Small | Workflow | conventional threshold | same data and likelihood; candidate models fitted; predictive objective |
| 13.3.9 | BIC Charges Log n per Added Parameter | Workflow | asymptotic | same data and likelihood; regular parametric models; large sample |
| 13.3.10 | One-Standard-Error Rule for Model Selection | Workflow | empirical heuristic | comparable cross validation estimates; ordered model complexity |
| 13.3.11 | Variance Inflation Factor Around Five as a Warning | Workflow | conventional threshold | fitted linear predictor matrix |
| 13.3.12 | High-Leverage Cutoff Around Two p Over n | Workflow | conventional threshold | fitted regression design matrix; parameter count includes intercept |
| 13.3.13 | Cook's Distance Screening Threshold | Workflow | conventional threshold | fitted linear regression; valid residual scale |
| 13.3.14 | Ten Outcome Events per Parameter as a Starting Check | Workflow | conventional threshold | ordinary logistic regression; binary outcome |
| 13.3.15 | Bootstrap Replicate Budget: Thousands, Not Dozens | Workflow | empirical heuristic | standard nonparametric bootstrap; finite compute budget |
| 13.3.16 | Check Bootstrap Tail Resolution by Expected Rank | Workflow | empirical heuristic | independent bootstrap replicates; requested tail probability |
| 13.3.17 | Jackknife Works Best for Smooth Statistics | Workflow | asymptotic | smooth statistical functional; approximately iid sample |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [13-statistics.ipynb](../../notebooks/13-statistics.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Count independent information rather than readings** (rule 13.2.9). Does collecting five readings on each unit equal five independent units? Only under an independence model. Positive within-unit correlation reduces effective information.
- **Put an upper bound on zero observed events** (rule 13.1.8). Do 200 zero-event trials establish risk below 1% at this confidence level? No. The exact upper bound is about 1.4867%, and the rule of three gives 1.5%.
- **Compare interval behavior near zero and one** (rule 13.1.9). What is wrong with the Wald interval at zero successes? Its estimated standard error is zero, causing a zero-width interval even though substantial probability uncertainty remains.
- **Count the cost of peeking at p-values** (rule 13.3.3). If you check results 20 times and stop at the first p<.05, is your error rate still 5%? No. In this simulation it is about 24%, nearly five times the promised rate.

## Teach and check understanding

Start with 13.1.5, 13.1.8, 13.2.9 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
