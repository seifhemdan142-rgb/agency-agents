# Findings: written deliverables, 10 agents

The main run used short, single-question answers. This test checks whether personas do better on the work they were designed for: longer written deliverables such as plans, memos, specs, battlecards and procedures.

## What was run

- **Tasks:** 20 new tasks in `evals/cases-deliverables/`, 2 each for the same 10 randomly chosen agents as the Haiku test. Each task has its own checklist and red flags.
- **Answers:** written by the session's default model (`claude-opus-5-5`) in Claude Code sub-agents, with a 900-word limit.
- **Judging:** the same two judges, blinding and controls as before. All sub-agents were audited from their transcripts, and none touched a file outside its allowed set.

## Results

| | opus judge | sonnet judge |
|---|---|---|
| Persona / baseline / tie | 6 / 4 / 10 | 9 / 2 / 9 |
| Persona win rate among decisive verdicts | 60% (95% CI 31–83%) | 82% (52–95%) |
| Sign test p | 0.75 | 0.065 |
| Checks met, persona vs baseline | 94% vs 95% | 97% vs 98% |
| Red flags, persona vs baseline | 0 / 1 | 0 / 1 |
| Hidden controls passed | 4 / 4 | 4 / 4 |

Where the judges agreed, the persona was preferred in 4 cases and the baseline in 2.

## What it means

1. **This is the first test where both judges lean toward the persona.** It is not statistically significant with 20 cases: the stronger judge's lean has p = 0.065.
2. **The persona's advantage here is judgement, not coverage.** Both sides met nearly the same share of checks. Judges preferred persona answers for:
   - labelling assumptions and calibrating claims (fr-d1, st-d1, pm-d1);
   - explicitly ruling out the clinical decision support exemption and naming De Novo as a fallback (md-d1);
   - grounding partner discounts in a break-even model against direct sales (pc-d1);
   - separating remote SaaS access from software downloads (ec-d1);
   - pointing out that a prompt-only fix is insufficient (rt-d2);
   - launch gates and verified-resolution metrics (as-d1).
3. **Only the baseline triggered a red flag.** Its positioning framework presented invented time-savings figures as fact (pm-d1), and both judges flagged it. Across all four runs so far, no persona answer has triggered a red flag.
4. **Personas still sometimes narrow the answer:**
   - The Red Team persona's HR chatbot test plan was technically sharp but left out the threat model, escalation tests and chat-log retention (rt-d1). Across both of its tasks, the Red Team persona met 73% of checks against 100%.
   - The Edge AI persona did not plan accuracy testing on real footage (ea-d2).

## Limitations

Same as the main run, plus:

- Only 20 cases.
- The deliverable checklists were written by the same author as the personas.
