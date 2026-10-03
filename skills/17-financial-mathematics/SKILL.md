---
name: math-thumb-financial-mathematics
description: "Apply Chapter 17 (Financial Mathematics: Comparing Money Across Time) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to place hypothetical cash flows on one time and rate basis before comparing them."
---

# Chapter 17. Financial Mathematics: Comparing Money Across Time

Apply Chapter 17 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [17-financial-mathematics.ipynb](../../notebooks/17-financial-mathematics.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Cash-flow amounts, signs, dates and currency; valuation date; effective period rate; nominal versus real basis; payment timing.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

1. Write the objective: quick scale estimate, valuation, affordability, or contract comparison.
2. Draw a timeline and mark every amount, sign, date, and currency.
3. Put rates on a common effective-period basis and decide whether amounts and rates are nominal or real.
4. Move every cash flow to one valuation date. Use a geometric closed form only after recognizing an exact pattern.
5. Check domain conditions: payment timing, \(r>0\), \(r>g\), fixed count, and compatible periods.
6. Stress-test cash flows and rates. Add taxes, fees, default, liquidity, and constraints when relevant.
7. Treat the number as a model output, not personal financial advice; escalate high-stakes decisions to contract-specific analysis and qualified professionals.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Treat exercise rates as explicit assumptions. Match rate periods and cash-flow timing; do not convert a classroom valuation into personalized investment or borrowing advice.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 17.1.1 | Rule of 72 for doubling time | Independent | asymptotic | consistent time unit; stable rate |
| 17.1.2 | Real return is approximately nominal return minus inflation | Independent | first-order approximation | consistent time unit; stable rate |
| 17.1.3 | Loss recovery is mathematically asymmetric | Independent | exact under assumptions | positive reference value; loss fraction between zero and one; no intervening flows for portfolio interpretation |
| 17.2.1 | Convert periodic rates to an effective annual rate | Independent | exact under assumptions | consistent time unit; stable rate |
| 17.2.2 | Discount each future cash flow to the same date | Workflow | exact under assumptions | consistent valuation date; constant periodic rate; cash flow timing known |
| 17.2.3 | Positive NPV is the basic discounted-cash-flow screen | Workflow | exact under assumptions | complete cash flow forecast; defensible discount rate; comparable risk |
| 17.3.1 | Present value of an ordinary annuity | Independent | exact under assumptions | consistent valuation date; constant periodic rate; cash flow timing known |
| 17.3.2 | Constant perpetuity value is payment divided by rate | Independent | exact under assumptions | consistent valuation date; constant periodic rate; cash flow timing known; infinite horizon |
| 17.3.3 | Growing perpetuity value depends on the rate spread | Independent | exact under assumptions | consistent valuation date; constant periodic rate; cash flow timing known; infinite horizon |
| 17.3.4 | Future value of regular end-of-period deposits | Independent | exact under assumptions | consistent valuation date; constant periodic rate; cash flow timing known |
| 17.3.5 | Level payment for an amortizing loan | Independent | exact under assumptions | consistent valuation date; constant periodic rate; cash flow timing known |
| 17.3.6 | Annuity-due values shift payments one period earlier | Specialized | exact under assumptions | consistent valuation date; constant periodic rate; cash flow timing known |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [17-financial-mathematics.ipynb](../../notebooks/17-financial-mathematics.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Change the rate and recheck present value** (rule 17.2.3). Can payment totals alone establish positive NPV? No. Discounted timing and the chosen rate matter; 1200 received later is not 1200 today.
- **Use the correct base for recovering a loss** (rule 17.1.3). What gain recovers a 50% loss? A 100% gain on the remaining half restores the original value.
- **Compare compounding conventions fairly** (rule 17.2.1). Is nominal 12% monthly compounding the same as effective 12% annually? No. Its effective rate is (1.01)¹²−1, about 12.6825%.
- **Check the rule of 72** (rule 17.1.1). When is the rule of 72 almost exact? Near 8%. Below it the rule runs long; above it the rule runs short.
- **Watch a growing perpetuity blow up** (rule 17.3.3). Why is a growing-perpetuity value with g close to r unreliable? Because value depends on 1/(r−g). At a half-point spread, adding a quarter point of growth doubles the value.

## Teach and check understanding

Start with 17.2.2, 17.2.3, 17.3.1 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
