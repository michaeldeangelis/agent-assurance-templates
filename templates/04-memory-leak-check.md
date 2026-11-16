# Template 4: Check for model memory before trusting a historical evaluation

## Use it when
A model is evaluated on past events (forecasts, market or credit outcomes, document sets with dates) and the result will be used to predict how it performs on new ones.

## The problem
A model may already know how past events turned out. A test period that falls before the end of its training data measures recall, not skill.

## Steps
1. Find the model's stated training cutoff. Treat it as a claim to be measured.
2. Measure the effective cutoff: ask dated factual questions across a range of months and find where accuracy drops to the guessing rate. Record the estimate with its range.
3. Compare the test period with the effective cutoff. Any part before it is contaminated.
4. If the cutoff cannot be measured for a model, treat all history as contaminated for that model.
5. For contaminated periods use one of:
   - forward-only testing on events after the cutoff;
   - a frozen forecast made today and scored later;
   - removal of names and dates, with a check that the model cannot re-identify the case.
6. Record which results are clean and which are contaminated. Never pool them.

## Report
- Stated cutoff, measured cutoff and its range, and how it was measured.
- The share of the test period that is clean.
- Results for clean and contaminated periods separately.

## Rules
- Re-measure for every model version.
- Removing names is not enough on its own. Test whether the model can name the stripped case.
- A strong result on a contaminated period is not evidence either way.
