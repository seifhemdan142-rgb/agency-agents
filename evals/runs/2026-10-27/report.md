# Persona evaluation report: 2026-10-27

15 cases across 5 agents, each answered with the agent persona as the system prompt (persona) and without it (baseline), then graded blind by 2 judge(s): opus, sonnet.

Five agents added in PR #9. Answers by the session's default model (claude-opus-5-5) in Claude Code sub-agents; judges: default model (opus) and the Agent tool's sonnet.

## Headline

| Judge | Persona preferred | Baseline preferred | Tie / both bad | Persona win rate (decisive) | 95% CI | Sign test p |
|---|---:|---:|---:|---:|---|---:|
| opus | 6 | 2 | 7 / 0 | 75% | 41%-93% | 0.289 |
| sonnet | 7 | 0 | 8 / 0 | 100% | 65%-100% | 0.0156 |

| Judge | Checks met (persona) | Checks met (baseline) | Paired difference | 95% CI (bootstrap) | Red flags (P/B) |
|---|---:|---:|---:|---|:---:|
| opus | 97% | 87% | +10.0 pts | +3.8 to +17.3 | 0/0 |
| sonnet | 98% | 88% | +10.0 pts | +4.7 to +16.7 | 0/0 |

## Sanity checks

| Judge | Hidden controls passed | Longer answer won (decisive) |
|---|---:|---:|
| opus | 2/2 | 8/8 |
| sonnet | 2/2 | 7/7 |

Mean answer length: persona 401 words, baseline 387 words (limit 450).

A hidden control pairs a real answer with a degenerate one ("I don't know", an answer to a different question, or an empty answer). It passes when the judge prefers the real answer and credits the degenerate one with no checks.

## Judge agreement

- opus vs sonnet on 15 cases: preference agreement 80% (Cohen's kappa 0.65); check-level agreement 97%.
- Cases where both judges preferred the persona answer: 6; both preferred the baseline answer: 0.

## Per agent (opus)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-membrane-materials-scientist | 94% | 88% | 1-2-0 | 0/0 |
| engineering-thermal-energy-storage-engineer | 93% | 73% | 2-1-0 | 0/0 |
| specialized-arabic-technical-translator | 100% | 93% | 1-0-2 | 0/0 |
| specialized-patent-prior-art-strategist | 100% | 100% | 0-3-0 | 0/0 |
| specialized-saudi-regulatory-navigator | 100% | 83% | 2-1-0 | 0/0 |

## Per agent (sonnet)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-membrane-materials-scientist | 100% | 88% | 1-2-0 | 0/0 |
| engineering-thermal-energy-storage-engineer | 93% | 80% | 2-1-0 | 0/0 |
| specialized-arabic-technical-translator | 100% | 93% | 1-2-0 | 0/0 |
| specialized-patent-prior-art-strategist | 100% | 100% | 0-3-0 | 0/0 |
| specialized-saudi-regulatory-navigator | 94% | 78% | 3-0-0 | 0/0 |

## Per case

| Case | Agent | opus | sonnet |
|---|---|---|---|
| mm-1 | academic-membrane-materials-scientist | persona (4/5 vs 3/5) | persona (5/5 vs 3/5) |
| mm-2 | academic-membrane-materials-scientist | tie (6/6 vs 6/6) | tie (6/6 vs 6/6) |
| mm-3 | academic-membrane-materials-scientist | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| te-1 | engineering-thermal-energy-storage-engineer | persona (5/5 vs 3/5) | persona (5/5 vs 4/5) |
| te-2 | engineering-thermal-energy-storage-engineer | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| te-3 | engineering-thermal-energy-storage-engineer | persona (4/5 vs 3/5) | persona (4/5 vs 3/5) |
| at-1 | specialized-arabic-technical-translator | persona (5/5 vs 4/5) | persona (5/5 vs 4/5) |
| at-2 | specialized-arabic-technical-translator | baseline (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| at-3 | specialized-arabic-technical-translator | baseline (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| pa-1 | specialized-patent-prior-art-strategist | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| pa-2 | specialized-patent-prior-art-strategist | tie (6/6 vs 6/6) | tie (6/6 vs 6/6) |
| pa-3 | specialized-patent-prior-art-strategist | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| sr-1 | specialized-saudi-regulatory-navigator | tie (6/6 vs 6/6) | persona (6/6 vs 5/6) |
| sr-2 | specialized-saudi-regulatory-navigator | persona (6/6 vs 5/6) | persona (6/6 vs 5/6) |
| sr-3 | specialized-saudi-regulatory-navigator | persona (6/6 vs 4/6) | persona (5/6 vs 4/6) |

Each cell: preferred answer (persona checks met vs baseline checks met).
