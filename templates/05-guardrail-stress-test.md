# Template 5: Stress-test your guardrails

## Use it when
An automated analysis or agent pipeline has several safeguards and nobody knows which of them do anything.

## The idea
Run tasks where the right answer is known to be "nothing here" or is known exactly, then count how often a wrong finding gets through. Do it with all safeguards on, and with each one off in turn.

## Steps
1. Build tasks with a known truth:
   - data with no real effect;
   - data with a planted effect of known size;
   - traps where a common mistake produces a convincing false result.
2. List the safeguards in the pipeline.
3. Run every task many times with all safeguards on. Count false findings and missed real effects.
4. Switch off one safeguard at a time and repeat.
5. For each safeguard record how much the false-finding rate changes when it is removed.

## Report
- False-finding rate and miss rate with all safeguards on, as counts.
- For each safeguard: the change when it is off.
- The task types that still get through with everything on.
- What was got wrong in building the test.

## How to read it
- A safeguard whose removal changes nothing is not protecting you on these tasks.
- A pipeline that refuses nearly everything is safe and not useful. The miss rate matters as much as the false-finding rate.
- Traps that pass with everything on are the priority list for new checks.
