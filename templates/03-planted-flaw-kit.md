# Template 3: Build a planted-flaw kit

## Use it when
You need to know how good a check, a pipeline or a reviewer is at catching problems, and real failures are too rare or too ambiguous to measure with.

## The idea
Create work that contains one deliberate, confirmed error, alongside matching clean work. The share of planted errors that get caught is the catch rate.

## Steps
1. List the ways this kind of work goes wrong in practice. Group them into types.
2. For each type write several cases, each with exactly one error.
3. For each flawed case write a clean twin: the same work without the error.
4. Confirm every flaw is real. A second person or a separate program must agree that the flawed case is wrong and the twin is right. Drop any case that cannot be confirmed.
5. Include a few flaws the current checks are not designed to catch. They show blind spots.
6. Store the answer key apart from the cases.
7. Run the cases through the thing being tested and count.

## Sizing
- A dozen flaws and eight clean cases give a rough reading.
- Fifty or more are needed before tuning anything against them.
- Report counts so the reader can see how much the number rests on.

## Flaw types to consider
- The result disappears on data that was held back.
- The same result shows up where there should be none.
- One success picked from many attempts.
- Too few cases to conclude anything.
- Numbers in the write-up that differ from the output.
- Information from after the decision date used before it.
- A test that was skipped, deleted or made to pass without a real run.
- A quoted source that does not say what is claimed.

## Rules
- Unconfirmed flaws inflate or deflate the score at random. Confirm them all.
- Retire cases that have leaked into prompts or training material.
- Feed stored cases to the check directly where possible, so a full agent run is not needed for each one.
