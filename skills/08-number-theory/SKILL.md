---
name: math-thumb-number-theory
description: "Apply Chapter 8 (Number Theory: Reduce Large Arithmetic to Small Structure) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to reduce integer calculations while preserving divisibility and invertibility."
---

# Chapter 8. Number Theory: Reduce Large Arithmetic to Small Structure

Apply Chapter 8 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [08-number-theory.ipynb](../../notebooks/08-number-theory.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Integers and modulus; whether an exact answer or scale estimate is needed; coprimality; one-number versus many-number workload.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Do you need a gcd but not a factorization?** Use the Euclidean algorithm. Record its equations if an inverse or Bézout coefficients may be needed next.
- **Is a complete factorization already known?** Translate exponent choices directly into a divisor count. Do not enumerate divisors unless the list itself is required.
- **Do you need an aggregate prime estimate?** Use $n/\log n$ for scale. If you need exact primes, choose between trial division, a sieve, and a larger-scale primality method based on workload.
- **Is the answer requested modulo $m$?** Reduce throughout addition and multiplication. Before dividing, test invertibility with a gcd.
- **Can the modulus be separated into coprime factors?** Solve the smaller congruences and reconstruct with the Chinese remainder theorem.
- **Is the obstacle a huge exponent?** Verify coprimality, identify a valid group period, and reduce the exponent before powering.
- **Is the question about the power of one prime in a product, sum, factorial, or gcd?** Replace full integers with valuations and watch for equal-valuation cancellation.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Check coprimality before modular inversion, exponent-period reduction, or the simplest CRT formula. Prime-count estimates do not certify primality.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 8.1.1 | Use remainders instead of factoring to find a gcd | Independent | exact | integer inputs not both zero |
| 8.1.2 | Read the divisor count from prime exponents | Independent | exact under assumptions | positive integer; complete prime factorization |
| 8.1.3 | Estimate prime counts by n over log n | Independent | asymptotic | large positive bound; natural logarithm |
| 8.2.1 | Reduce modulo m at every arithmetic step | Workflow | exact | common modulus; operations respect congruence |
| 8.2.2 | Use extended Euclid to find modular inverses | Independent | exact under assumptions | integer modulus greater than one; coprime value and modulus for inverse |
| 8.2.3 | Split coprime congruences with the Chinese remainder theorem | Independent | exact under assumptions | pairwise coprime moduli; integer residues |
| 8.3.1 | Test divisors only through the square root | Workflow | exact | positive integer candidate; all possible divisors through square root checked |
| 8.3.2 | Use a sieve when you need many primes at once | Workflow | exact under assumptions | known finite upper bound; many queries or full prime list needed |
| 8.3.3 | Reduce modular exponents using the group period | Workflow | exact under assumptions | base coprime to modulus; known totient or prime modulus |
| 8.3.4 | Use p-adic valuations to track prime-power divisibility | Workflow | exact | nonzero integer or rational input; fixed prime |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [08-number-theory.ipynb](../../notebooks/08-number-theory.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Find an inverse only when arithmetic permits it** (rule 8.2.2). Why does a=43 have no inverse modulo 43? Every product with 43 is zero modulo 43, so it cannot equal one.
- **Intersect congruences in a small exact search** (rule 8.2.3). Why does one solution determine all others modulo fifteen? The Chinese remainder theorem gives a unique residue class modulo the product of the coprime moduli.
- **Compare counted primes with their asymptotic scale** (rule 8.1.3). Does disagreement at n=100 refute asymptotic equivalence? No. Asymptotic equivalence describes the ratio as n tends to infinity, not exact equality at a small n.
- **Reduce a huge exponent by the period of the powers** (rule 8.3.3). What is 10²³ mod 11 without multiplying? 10≡−1 mod 11, so its powers alternate 10, 1. The exponent 23 is odd, giving 10.
- **See why trial division can stop at the square root** (rule 8.3.1). Do you need to test 11 to decide whether 97 is prime? No. 11 > √97 ≈ 9.85, so any factor 11 or larger would have a partner below 9.85, which the trials 2 to 9 already ruled out.

## Teach and check understanding

Start with 8.1.1, 8.2.2, 8.2.3 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
