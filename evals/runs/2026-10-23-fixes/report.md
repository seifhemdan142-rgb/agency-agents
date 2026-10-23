# Persona evaluation report: 2026-10-23-fixes

9 cases across 3 agents, each answered with the agent persona as the system prompt (persona) and without it (baseline), then graded blind by 2 judge(s): opus, sonnet.

## Headline

| Judge | Persona preferred | Baseline preferred | Tie / both bad | Persona win rate (decisive) | 95% CI | Sign test p |
|---|---:|---:|---:|---:|---|---:|
| opus | 4 | 0 | 5 / 0 | 100% | 51%-100% | 0.125 |
| sonnet | 1 | 0 | 8 / 0 | 100% | 21%-100% | 1 |

| Judge | Checks met (persona) | Checks met (baseline) | Paired difference | 95% CI (bootstrap) | Red flags (P/B) |
|---|---:|---:|---:|---|:---:|
| opus | 100% | 100% | +0.0 pts | +0.0 to +0.0 | 0/0 |
| sonnet | 100% | 100% | +0.0 pts | +0.0 to +0.0 | 0/0 |

## Sanity checks

| Judge | Hidden controls passed | Longer answer won (decisive) |
|---|---:|---:|
| opus | 2/2 | 4/4 |
| sonnet | 2/2 | 1/1 |

Mean answer length: persona 409 words, baseline 375 words (limit 450).

A hidden control pairs a real answer with a degenerate one ("I don't know", an answer to a different question, or an empty answer). It passes when the judge prefers the real answer and credits the degenerate one with no checks.

## Judge agreement

- opus vs sonnet on 9 cases: preference agreement 67% (Cohen's kappa 0.27); check-level agreement 100%.
- Cases where both judges preferred the persona answer: 1; both preferred the baseline answer: 0.

## Per agent (opus)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-string-theorist | 100% | 100% | 1-2-0 | 0/0 |
| marketing-amazon-marketplace-strategist | 100% | 100% | 1-2-0 | 0/0 |
| specialized-customs-tariff-specialist | 100% | 100% | 2-1-0 | 0/0 |

## Per agent (sonnet)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-string-theorist | 100% | 100% | 1-2-0 | 0/0 |
| marketing-amazon-marketplace-strategist | 100% | 100% | 0-3-0 | 0/0 |
| specialized-customs-tariff-specialist | 100% | 100% | 0-3-0 | 0/0 |

## Per case

| Case | Agent | opus | sonnet |
|---|---|---|---|
| st-1 | academic-string-theorist | persona (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| st-2 | academic-string-theorist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| st-3 | academic-string-theorist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| am-1 | marketing-amazon-marketplace-strategist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| am-2 | marketing-amazon-marketplace-strategist | tie (3/3 vs 3/3) | tie (3/3 vs 3/3) |
| am-3 | marketing-amazon-marketplace-strategist | persona (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ct-1 | specialized-customs-tariff-specialist | persona (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ct-2 | specialized-customs-tariff-specialist | tie (3/3 vs 3/3) | tie (3/3 vs 3/3) |
| ct-3 | specialized-customs-tariff-specialist | persona (4/4 vs 4/4) | tie (4/4 vs 4/4) |

Each cell: preferred answer (persona checks met vs baseline checks met).
