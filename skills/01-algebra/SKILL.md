---
name: math-thumb-algebra
description: "Apply Chapter 1 (Algebra: See the Structure Before You Solve) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to choose a useful representation and decide whether a first-order estimate is accurate enough."
---

# Chapter 1. Algebra: See the Structure Before You Solve

Apply Chapter 1 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [01-algebra.ipynb](../../notebooks/01-algebra.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Starting and ending values; whether change is additive or multiplicative; domain exclusions; required accuracy.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Is the question about change?** Use a ratio when the baseline matters. If the model is exponential, translate rate into doubling time.
- **Is there a small, dimensionless quantity?** Match the surrounding function: binomial power, exponential, logarithm, or nearby radical. Estimate the first omitted correction.
- **Is there a long sum or tail?** Check for constant spacing or a constant ratio before touching individual terms.
- **Is magnitude enormous or multiplicative?** Move to a logarithmic representation.
- **Is the object a polynomial?** Use the leading term for distant behavior. For a quadratic, normalize, inspect for factors, and compute the discriminant before choosing a full root procedure. For a higher-degree integer polynomial, use the rational-root theorem only as a finite screen.
- **Is the object rational?** Factor the denominator. If decomposing a function, let the factors build the partial-fraction template. If solving an inequality, let the factor zeros build the sign chart.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** A small-looking percentage is insufficient: compare the actual discarded effect with the requested tolerance. Preserve denominator exclusions and inequality signs.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 1.1.1 | Compare proportional change with ratios, not differences | Independent | exact | common reference quantity; nonzero denominator |
| 1.1.2 | Estimate doubling time from the exponential rate | Independent | exact under assumptions | constant exponential rate; positive growth rate |
| 1.1.3 | Linearize a small binomial perturbation | Independent | first-order approximation | small parameter; dimensionless perturbation; finite exponent |
| 1.1.4 | Replace a small exponential by one plus its exponent | Independent | first-order approximation | small argument; dimensionless argument |
| 1.1.5 | Replace log one plus x by x for small x | Independent | first-order approximation | small parameter; argument greater than minus one |
| 1.2.1 | Average the endpoints of an arithmetic list | Independent | exact under assumptions | constant spacing; finite sequence |
| 1.2.2 | Estimate a geometric tail from its first omitted term | Independent | exact under assumptions | geometric sequence; ratio magnitude below one |
| 1.2.3 | Let the leading term predict polynomial end behavior | Independent | asymptotic | polynomial function; large argument |
| 1.2.4 | Rationalize a difference of nearby square roots | Independent | exact | real square roots or consistent complex branch |
| 1.2.5 | Use logarithms to tame products and powers | Workflow | exact under assumptions | positive real factors or consistent complex branch |
| 1.3.1 | Make a quadratic monic before reading its structure | Workflow | exact under assumptions | nonzero leading coefficient |
| 1.3.2 | Complete the square to read a quadratic's geometry | Workflow | exact | quadratic function |
| 1.3.3 | Factor before reaching for the quadratic formula | Workflow | empirical heuristic | quadratic polynomial; visible simple factors |
| 1.3.4 | Use the discriminant to triage quadratic roots | Workflow | exact | quadratic polynomial |
| 1.3.5 | Use the rational-root theorem as a shortlist | Workflow | exact under assumptions | integer coefficients; nonzero leading coefficient |
| 1.3.6 | Let denominator factors dictate partial fractions | Workflow | exact under assumptions | proper rational function; factored denominator |
| 1.3.7 | Cross-multiply inequalities only after checking signs | Workflow | exact under assumptions | known denominator signs; nonzero denominators |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [01-algebra.ipynb](../../notebooks/01-algebra.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Watch a small change become a large response** (rule 1.1.3). Does a 10% input increase imply exactly a 50% response increase? No. The exact multiplier is 1.1⁵=1.61051, a 61.051% increase; 50% is only the linear estimate.
- **Price the omitted geometric tail** (rule 1.2.2). Is the first omitted term a reliable tail estimate when r=.9? It supplies the scale, but the entire positive tail is ten times that term because 1/(1−.9)=10.
- **See roots appear at a discriminant boundary** (rule 1.3.4). What changes at b=2? The discriminant is zero and x²+2x+1=(x+1)². Two distinct real roots merge into one repeated root.
- **Check the rule of 70 for doubling time** (rule 1.1.2). At 7% per year, does money double in exactly 10 years? Not quite. The exact time is ln 2/ln 1.07 = 10.24 years. The rule is about 2.4% short, fine for a quick estimate.
- **Check the denominator sign before cross-multiplying** (rule 1.3.7). Is x=1 a solution of (x+1)/(x−3)≤0? Yes. The fraction equals 2/(−2)=−1≤0. The naive answer x≤−1 rejects it because it ignored that x−3<0 there.

## Teach and check understanding

Start with 1.1.1, 1.1.3, 1.3.7 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
