---
name: math-thumb-signal-processing
description: "Apply Chapter 24 (Signal Processing: Sampling, Resolution, and Spectral Judgment) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to separate spectral display spacing from information acquired and plan sampling before aliasing occurs."
---

# Chapter 24. Signal Processing: Sampling, Resolution, and Spectral Judgment

Apply Chapter 24 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [24-signal-processing.ipynb](../../notebooks/24-signal-processing.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Sample rate; acquired sample count and duration; signal bandwidth; anti-alias filtering; window; tone spacing or event duration; amplitude/power units.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Are analog or preexisting digital components above the new Nyquist limit?** Filter before sampling or decimation; after folding, recovery is not generally possible.
- **Is the question about bin labels or resolving components?** Use \(f_s/N\) for labels and acquired duration plus window width for resolution.
- **Does a tone fail to land on a bin?** Choose a taper, correct coherent gain and off-bin scalloping for tone amplitude, and apply ENBW only when the noise-density scaling requires it.
- **Does a denser spectrum look more detailed?** Check whether new samples were acquired or only zeros were appended.
- **Does the signal change in time?** Select STFT windows against both event duration and tone spacing; use more than one scale when necessary.
- **Is a level stated in decibels?** Identify power versus amplitude, reference level, impedance, and one-sided or RMS conventions before converting.
- **Is a PSD unstable?** Vary Welch segment length, quantify effective averaging, and report confidence rather than hiding variance with overlap.
- **Is a filter high order or zero phase?** Use SOS for numerical realization and reserve forward-backward application for offline records with explicit edge treatment.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** A denser FFT display does not add observations or remove leakage. Specify window corrections and anti-alias filtering before treating spectrum values as measurements.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 24.1.1 | Sample above twice the highest frequency with a guard band | Independent | conventional threshold | sampled signal model; known sampling rate |
| 24.1.2 | Low-pass before every downsampling step | Workflow | empirical heuristic | sampled signal model; known sampling rate |
| 24.1.3 | Compute FFT bin spacing as sample rate over transform length | Independent | exact under assumptions | sampled signal model; known sampling rate |
| 24.1.4 | Increase record duration to improve true frequency resolution | Independent | conventional threshold | sampled signal model; known sampling rate |
| 24.2.1 | Window noncoherent records before spectral measurement | Workflow | empirical heuristic | sampled signal model; known sampling rate |
| 24.2.2 | Use zero padding for spectral interpolation, not added resolution | Workflow | exact under assumptions | fixed observed record; unchanged windowed samples |
| 24.2.3 | Choose STFT window from the shortest event and closest tones | Workflow | empirical heuristic | sampled signal model; known sampling rate |
| 24.2.4 | Twenty decibels means tenfold amplitude or hundredfold power | Independent | exact under assumptions | positive ratio; declared reference; power proportional to amplitude squared; compatible impedance and amplitude definition |
| 24.3.1 | Trade Welch segment length against PSD variance | Specialized | empirical heuristic | sampled signal model; known sampling rate |
| 24.3.2 | Start Welch averaging with Hann windows and fifty-percent overlap | Specialized | conventional threshold | sampled signal model; known sampling rate; independence |
| 24.3.3 | Use equivalent noise bandwidth when converting FFT noise to density | Specialized | empirical heuristic | sampled signal model; known sampling rate |
| 24.3.4 | Implement moderate-to-high-order IIR filters as second-order sections | Specialized | empirical heuristic | sampled signal model; known sampling rate; large problem or asymptotic regime |
| 24.3.5 | Use forward-backward filtering only for offline zero-phase work | Workflow | exact under assumptions | sampled signal model; known sampling rate |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [24-signal-processing.ipynb](../../notebooks/24-signal-processing.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Create an alias by sampling above Nyquist** (rule 24.1.1). Where does a 600Hz sine appear at this sample rate? At 400Hz. The sampled data cannot distinguish those frequencies without additional information.
- **Compare longer acquisition with zero padding** (rule 24.2.2). Does an eightfold padded transform provide eight times the acquired information? No. It interpolates the spectrum of the same acquired samples.
- **Expose leakage and the window tradeoff** (rule 24.2.1). Does a lower sidelobe window improve every kind of spectral resolution? No. Lower sidelobes often come with a broader main lobe, changing the tradeoff between nearby strong and weak tones.
- **Filter before throwing samples away** (rule 24.1.2). At M=3, where does the 380 Hz tone appear without a filter? At 46.7 Hz, right beside the real 50 Hz tone. Filtering first removes it.

## Teach and check understanding

Start with 24.1.1, 24.1.4, 24.2.2 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.
