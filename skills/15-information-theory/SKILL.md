---
name: math-thumb-information-theory
description: "Apply Chapter 15 (Information Theory: Measuring Information and Its Limits) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to compute information quantities on a declared scale and identify the operational limit they express."
---

# Chapter 15. Information Theory: Measuring Information and Its Limits

Apply Chapter 15 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [15-information-theory.ipynb](../../notebooks/15-information-theory.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Probability distribution; log base and units; alphabet; conditioning or side information; channel/source assumptions; common evaluation data.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Is the question about one outcome?** Use surprisal. If it asks for the average over a source, use entropy or cross-entropy instead.
- **Is the alphabet finite?** Apply the log-alphabet ceiling before accepting a larger uncertainty or mutual-information claim.
- **Is a Bernoulli event rare?** Use the small-\(p\) entropy approximation only after checking the regime and whether temporal dependence changes the entropy rate.
- **Are predictive models being compared?** Keep the tokenization, evaluation data, conditioning information, and log base fixed before comparing perplexity.
- **Is dependence the target?** Mutual information is broader than correlation, but finite-sample estimation and causal interpretation remain separate issues.
- **Has information passed through a transformation?** Draw the Markov diagram and identify any side information before invoking data processing.
- **Must an information discrepancy become an event error?** State the KL direction and units, then use Pinsker.
- **Is the question operational?** Match the exact source, channel, code, or probabilistic-data-structure assumptions before using the corresponding limit or tuning formula.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** Bits and nats are different units. Equal-looking perplexities from different tokenizations are not direct evidence of equal predictive quality.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 15.1.1 | Surprisal Is Minus Log Probability | Independent | exact under assumptions | positive modeled probability; specified log base |
| 15.1.2 | Entropy Cannot Exceed Log Alphabet Size | Independent | exact under assumptions | finite discrete alphabet |
| 15.1.3 | Entropy of a Rare Bernoulli Event | Independent | first-order approximation | small event probability; binary event |
| 15.1.4 | Perplexity Is Exponentiated Cross-Entropy | Independent | exact under assumptions | consistent log base; same tokenization |
| 15.2.1 | Mutual Information as a Dependence Screen | Independent | exact under assumptions | well defined joint distribution |
| 15.2.2 | Processing Cannot Create Information About the Source | Independent | exact under assumptions | markov chain conditional independence |
| 15.2.3 | Pinsker Converts KL Divergence to Probability Error | Independent | guaranteed bound | common measurable space; natural log kl |
| 15.3.1 | Gaussian Has Maximum Entropy at Fixed Variance | Independent | exact under assumptions | fixed finite variance; continuous distribution |
| 15.3.2 | Gaussian Channel Capacity Grows Logarithmically with SNR | Independent | exact under assumptions | memoryless channel; specified noise model; optimal coding |
| 15.3.3 | Binary Symmetric Channel Capacity | Independent | exact under assumptions | memoryless channel; specified noise model; optimal coding |
| 15.3.4 | Optimal Prefix Coding Is Within One Bit of Entropy | Independent | exact under assumptions | discrete memoryless source; binary prefix code |
| 15.3.5 | Bloom Filter Optimal Hash Count | Specialized | asymptotic | independent uniform hashes; known item count; fixed bit budget |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [15-information-theory.ipynb](../../notebooks/15-information-theory.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Separate rare-event surprisal from average entropy** (rule 15.1.3). Why is entropy low when p=.01? Most outcomes are the predictable common outcome. High surprisal of the rare outcome contributes only with weight .01.
- **Price a probability model mismatch** (rule 15.1.4). Where is cross-entropy minimized? At Q=P, where the KL excess is zero and cross-entropy equals entropy.
- **Read a channel limit as a limit** (rule 15.3.3). What information capacity remains at ε=.5? Zero. Output bits then carry no information about the input in this model.
- **Price signal power in bits** (rule 15.3.2). At 30 dB, what does doubling transmit power buy? About half an extra bit per real sample, from 4.98 to 5.48.
- **Pick the number of hashes for a Bloom filter** (rule 15.3.5). With 8 bits per item, are 20 hashes safer than 6? No. Six hashes give about 2.2%; twenty give about 18% because most bits are already set.

## Teach and check understanding

Start with 15.1.1, 15.1.2, 15.1.4 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
