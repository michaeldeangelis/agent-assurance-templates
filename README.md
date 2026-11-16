# Agent assurance templates

Six short templates for checking work done by AI agents, each drawn from an experiment I ran. The templates are in [`templates/`](templates/). Each is one to two pages: when to use it, the steps, what to report, and the rules.

They share one premise: an agent's own report that its work succeeded is not evidence. Decide how the work will be checked before it starts, keep that check where the agent cannot change it, and measure how good the check is.

## The templates and the results behind them

| Template | What I found | Counts and limits |
|---|---|---|
| [1. Keep the verdict outside the agent](templates/01-verdict-outside-the-agent.md) | A research pipeline where agents do the analysis and a plain program decides the verdict from a rule fixed in advance. In six live runs it confirmed one real effect on held-back data and refused five weaker or broken analyses. Three rounds of adversarial review found 31 defects, each kept as a regression test. | Two small teaching datasets. One passing effect (held-back interval 0.19 to 0.47 against a threshold of 0.05). A leak that let analysis scripts work out which rows were held back was found and fixed two weeks after that run, so the one confirmed pass predates the fix. |
| [2. Qualify an AI reviewer before trusting it](templates/02-qualify-an-ai-reviewer.md) | On deliberately forged analyses written to look sound, a model reviewer passed 36% (90 of 248). A fixed check on held-back data passed 2.4% (6 of 248). Across all forgeries the fixed check wrongly passed 2.8% (14 of 496). Giving the reviewer records held by the fixed check, instead of the author's own account, cut its passes of evidence-erased forgeries from 24 of 30 to 0 of 30. | Preregistered. Synthetic patient data modelled on a teaching dataset. One reviewer model. This was the second confirmatory run; the first failed two of its four hypotheses. |
| [3. Build a planted-flaw kit](templates/03-planted-flaw-kit.md) | Seventeen analyses with one planted flaw each, plus clean ones, were used to score two reviewer models. One caught 24 of 24 flaws in the reviews it completed, with 0 of 7 false alarms. The other caught 24 of 30 with 4 of 9 false alarms. | Invented data. Eight of the first model's calls failed for a tooling reason and are not counted. Small numbers of clean cases, so the false-alarm rates are rough. |
| [4. Check for model memory before trusting a historical evaluation](templates/04-memory-leak-check.md) | I measured how far a model's knowledge of market history extended by asking 6,046 dated questions. Its effective cutoff was about April 2026 (range January to May 2026), which put an entire test period I had planned to use inside its memory. | Measures recall of month-level returns only. No recall was detected for the smallest companies. A second model's cutoff could not be located, which is not evidence that it has none. |
| [5. Stress-test your guardrails](templates/05-guardrail-stress-test.md) | Tasks with a known answer of "nothing here" were run through a pipeline with all safeguards on. False findings stayed at or below about 1% (ceiling 1.06% over 360 runs). A shared reviewer board, added as a safeguard, raised false passes by 6.7 points (99 of 269 against 81 of 269), the opposite of what I expected. | Scripted analyses on synthetic data for the first figure; no model was involved. The board result is from the preregistered reviewer experiment in row 2. |
| [6. Spend controls for agent teams](templates/06-spend-controls-for-agents.md) | Agents working unattended must file a short request before anything paid can start, and a hook blocks paid commands until I approve it with a cap and an expiry. Over about two months agents filed 14 requests: 9 approved, 2 denied, 2 never decided, 1 closed at no cost. | One person's setup. Actual spend against each cap was not recorded in the ledger. |

## How to read these numbers

- They come from small experiments run by one person, mostly on synthetic or teaching data. They show that the methods work as designed. They do not show how often real agent work is wrong.
- Counts are given so the weight behind each figure is visible.
- Where a result failed first, or a problem was found later, the table says so.
- In a separate test of 170 honest agent runs on the forgery tasks, none made a headline claim the data did not support, and 6 made a hedged one. The scoring rules for that test were written after seeing runs, so treat it as an upper bound of about 2%, not as proof of absence.

## Related code

- [preregistered-research-lab](https://github.com/michaeldeangelis/preregistered-research-lab): a public snapshot of the pipeline behind template 1.
- [planted-truth](https://github.com/michaeldeangelis/planted-truth): planted-answer tasks of the kind used in template 5.

The forgery benchmark and the reviewer experiments behind templates 2 and 3 are not yet public.

## Licence

MIT. Use and adapt the templates freely.

Michael DeAngelis, November 2026
