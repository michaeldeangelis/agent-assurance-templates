# Template 2: Qualify an AI reviewer before trusting it

## Use it when
A model is used to review other work (code review, checking an analysis, grading outputs) and its "looks good" will be relied on.

## The idea
Measure the reviewer the way you would measure a test: give it work with known errors and work that is known to be clean, and count what it catches and what it wrongly flags.

## Steps
1. Build a case set for the kind of work being reviewed:
   - cases with one known, real error each (see Template 3);
   - clean cases that look similar, with no error.
2. Hide the answer key from the reviewer and from anyone prompting it.
3. Run the reviewer on every case with the exact prompt, model and settings to be used in production. Repeat each case at least three times.
4. Score:
   - catch rate = errors flagged / errors planted;
   - false alarm rate = clean cases flagged / clean cases;
   - agreement across repeats.
5. Keep a part of the case set unseen. If the reviewer's prompt is tuned, tune on one part and score on the other.
6. Decide in advance what rates are acceptable for this use, and what the reviewer is allowed to decide alone.

## Report
- Both rates as counts ("24 of 30"), never as a bare percentage.
- The model, version, prompt and date.
- Which kinds of error it missed.
- What it is cleared to do: advise only, block, or approve.

## Rules
- Re-qualify when the model, the prompt or the kind of work changes.
- A reviewer that sees the author's reasoning can be talked into agreeing. Test with and without it.
- A reviewer with a high catch rate and a high false alarm rate is not qualified; it is noisy.
- Do not let the reviewer be the only safeguard for anything a fixed check could cover.
