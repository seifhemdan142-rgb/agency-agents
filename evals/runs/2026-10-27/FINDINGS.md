# Findings: the five agents added in October 2026

This run tests the five agents added in PR #9: Thermal Energy Storage Engineer, Membrane & Materials Scientist, Patent & Prior-Art Strategist, Saudi Regulatory Navigator, and Arabic Technical Translator.

## What was run

- **Questions:** 3 per agent, 15 in all, from `evals/cases/`. Each has a checklist and a red flag.
- **Answers:** written by the session's default model (`claude-opus-5-5`) in Claude Code sub-agents, once with the persona as the system prompt and once without it, with a 450-word limit.
- **Judging:** the same two judges, blinding and controls as the earlier runs. All 14 sub-agents were audited from their transcripts, and none touched a file outside its allowed set.
- **One correction:** the Saudi baseline answerer trimmed its answers to the word limit after the first judge packet was built. Both judges were stopped before writing anything, and the packet was rebuilt from the final answers.

## Results

| | opus judge | sonnet judge |
|---|---|---|
| Persona / baseline / tie | 6 / 2 / 7 | 7 / 0 / 8 |
| Persona win rate among decisive verdicts | 75% (95% CI 41–93%) | 100% (65–100%) |
| Sign test p | 0.29 | 0.016 |
| Checks met, persona vs baseline | 97% vs 87% | 98% vs 88% |
| Paired difference in checks met | +10 pts (95% CI +3.8 to +17.3) | +10 pts (+4.7 to +16.7) |
| Red flags, persona vs baseline | 0 / 0 | 0 / 0 |
| Hidden controls passed | 2 / 2 | 2 / 2 |

Both judges preferred the persona answer in 6 cases and never both preferred the baseline. They agreed on 80% of preferences (kappa 0.65) and 97% of checks.

## What the personas added

- **Thermal Energy Storage Engineer** (te-1, te-3): showed the 3.517 kW-per-ton conversion and the 1,760 kW power check, and required the storage to stay above 400 °C at the end of discharge to allow for heat-exchanger approach temperatures.
- **Membrane & Materials Scientist** (mm-1): defined the separation factor, computed the 7,000:1 and 140:1 magnesium-to-lithium figures, and asked for seal blanks, reference discs and a mass balance.
- **Saudi Regulatory Navigator** (sr-1 to sr-3): flagged ethics-committee approval for research with students, warned against nominee ownership under the anti-concealment law, named the UN 38.3 battery file, and sent the user to official sources. The baseline missed 3–4 of its 18 checks, depending on the judge; the persona missed at most 1.
- **Arabic Technical Translator** (at-1): kept "Gr. B" and the 6-inch mark exactly as written, where the baseline rewrote them in Arabic.

## Where the persona did not help

- **Patent & Prior-Art Strategist:** three ties with both judges, and both sides met every check. The base model already handles these questions well.
- **Arabic Technical Translator** (at-2, at-3): the opus judge preferred the baseline twice. Both answers met every check, and the baseline added more useful context, such as export zero-rating and how Saudi courts can adjust penalties. The persona's answers were correct but narrower.

## How much to trust this

This is the strongest result in any run so far, and the reasons to be careful are also stronger:

1. **The same author wrote the personas and the checklists, in the same session, for the same purpose.** Several checks match rules in the personas almost word for word: approach temperatures, ethics approval, keeping codes exactly as written. This likely explains part of the check gap. The blind preference is less exposed, but the judges' reasons cite the same points.
2. **The longer answer won every decisive verdict** (8 of 8 for opus, 7 of 7 for sonnet). The mean lengths were close, though: 401 words for the persona and 387 for the baseline.
3. **Only 15 cases**, three per agent. The pooled result is suggestive; the per-agent results are anecdotes.

A fair reading: on these questions the personas reliably add domain checks a plain answer skips, never added a red flag, and do nothing for questions the base model already answers well. An independent set of questions written by someone who has not read the personas would be the right next test.
