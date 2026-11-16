# Template 1: Keep the verdict outside the agent

## Use it when
An AI agent produces a result that someone will act on (an analysis, an extraction, a code change), and the agent's own report of success is not enough.

## The idea
The agent does the work. A plain program the agent cannot change decides whether the work passes. The rule for passing is written and locked before the agent starts.

## Roles
| Role | Does | Must not |
|---|---|---|
| Owner | Writes the pass rule, approves the lock, reads the verdict | Change the rule after seeing results |
| Working agent | Produces the work in its own area | Read held-back data, edit checks, write the record |
| Runner (plain program) | Runs the checks, applies the rule, writes the record | Call the agent to decide anything |
| Record | Stores every run, add-only | Be edited |

## Steps
1. State the question or task in one sentence.
2. Write the pass rule: what is measured, the threshold, and what counts as "cannot tell".
3. Split off anything the agent must not see (held-back data, answer keys).
4. Lock: take a hash of the rule, the checks and the data split. Store the hashes where the agent cannot write.
5. Run the agent in an area where it can write only its own output.
6. The runner re-checks every hash, runs the checks, applies the rule.
7. Record the verdict: pass, fail, cannot tell, or invalid (something locked changed).

## Report
- The rule as locked, with its hash and time.
- The verdict and the numbers behind it.
- How many times this locked design has been run.
- Anything the agent tried to change.

## Common failures
- The rule is adjusted after a failed run and the change is not recorded.
- The agent can reach the held-back data through a shared folder or tool.
- A crash in a check is reported as a pass or a fail instead of invalid.
- The agent's summary is read in place of the runner's verdict.
