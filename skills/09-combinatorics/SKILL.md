---
name: math-thumb-combinatorics
description: "Apply Chapter 9 (Combinatorics: Counting Without Exhaustion) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to define the sample space before choosing a counting formula."
---

# Chapter 9. Combinatorics: Counting Without Exhaustion

Apply Chapter 9 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [09-combinatorics.ipynb](../../notebooks/09-combinatorics.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: What makes outcomes distinct; whether order matters; replacement; capacities; identical versus distinct objects; symmetry action.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Can the answer be forced without enumeration?** Define boxes and try pigeonhole, or identify unrestricted binary membership.
- **Are identical units being distributed?** Use stars and bars only when recipients are labeled and capacities are unlimited.
- **Are several cases being combined?** Add disjoint alternatives, multiply staged choices, and subtract intersections when alternatives overlap.
- **What makes outcomes distinct?** Decide whether order matters and whether rotation, reflection, or another symmetry identifies descriptions.
- **Is a restriction awkward?** Count its complement, or design recurrence states that remember precisely what legal extension depends on.
- **Is the object random?** Express the target count as indicators before trying to analyze dependencies.
- **Is an identity the goal?** Define one incidence set and count it in two orders.
- **Is the exact count enormous?** Use adjacent ratios, logarithms, or a regime-appropriate approximation to expose scale.
- **Does the construction split recursively or add component sizes?** Look for Catalan structure or encode the components with a generating function.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Do not divide by a symmetry count unless every orbit has that size. Re-check independence of choices and capacity restrictions before multiplying.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 9.1.1 | Use the ceiling form of pigeonhole | Independent | guaranteed bound | finite objects and boxes; every object assigned to a box |
| 9.1.2 | Remember that an n-set has two to the n subsets | Independent | exact | finite set of distinct elements; independent include exclude choices |
| 9.1.3 | Use stars and bars for identical items in labeled boxes | Independent | exact under assumptions | indistinguishable items; labeled boxes; nonnegative integer allocations |
| 9.1.4 | Approximate choose n k by n to the k over k factorial | Independent | asymptotic | k fixed or much smaller than n; nonnegative integers |
| 9.1.5 | Subtract overlap after adding two sets | Independent | guaranteed bound | finite event or set family; pairwise intersections available |
| 9.1.6 | Divide by symmetry only when every orbit has the same size | Independent | exact under assumptions | uniform orbit size; finite group action or equivalent symmetry |
| 9.2.1 | Decide first between the sum and product principles | Workflow | exact under assumptions | disjoint alternative cases for sum; well defined sequential choices for product |
| 9.2.2 | Ask whether order changes the outcome | Workflow | exact | finite distinct objects or adjusted multiplicities |
| 9.2.3 | Count the complement when the restriction is awkward | Workflow | exact | finite universe or known total; desired and forbidden partition universe |
| 9.2.4 | Choose recurrence states that remember exactly what the future needs | Workflow | empirical heuristic | future behavior determined by state |
| 9.2.5 | Count with indicator variables and linearity | Workflow | exact | well defined indicator events; finite sum or justified interchange |
| 9.2.6 | Prove identities by counting the same incidences twice | Workflow | exact | same finite incidence set; both counts include equal multiplicity |
| 9.3.1 | Expect the largest binomial coefficient in the middle | Independent | exact | fixed nonnegative integer n |
| 9.3.2 | Expect one binary-search step per bit of search space | Independent | exact under assumptions | roughly equal halving; successful monotone decision test |
| 9.3.3 | Estimate derangements by factorial over e | Independent | asymptotic | permutations of distinct objects; no fixed points; nearest integer rounding |
| 9.3.4 | Estimate multinomial counts on the log scale | Independent | asymptotic | large counts; category proportions sum to one; consistent log base |
| 9.3.5 | Use generating functions to turn convolution into multiplication | Workflow | exact under assumptions | well defined formal or convergent series; correct indexing |
| 9.3.6 | Look for Catalan numbers in balanced recursive structures | Workflow | empirical heuristic | recursive two part structure; noncrossing or prefix constraint |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [09-combinatorics.ipynb](../../notebooks/09-combinatorics.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Choose whether order changes the outcome** (rule 9.2.2). What creates the factorial multiplier? Every chosen committee has exactly k! bijections to the k distinct jobs.
- **Check counts by exhaustive enumeration** (rule 9.1.2). How many strings contain at least one 1? There are 2ⁿ total strings and exactly one all-zero string, giving 2ⁿ−1.
- **Expose unequal symmetry orbits** (rule 9.1.6). Why is dividing 2ⁿ by n generally wrong? Some patterns have rotational symmetry and shorter orbits. Constant strings already supply orbit size one.
- **See the no-match probability lock onto 1/e** (rule 9.3.3). Is a no-match much rarer with 100 guests than with 8? No. With 8 the chance is already 0.36788, and it stays within a hair of 1/e for any larger n.

## Teach and check understanding

Start with 9.1.3, 9.2.2, 9.2.3 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
