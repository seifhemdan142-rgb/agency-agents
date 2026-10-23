# Persona evaluation report: 2026-10-23-deliverables

20 cases across 10 agents, each answered with the agent persona as the system prompt (persona) and without it (baseline), then graded blind by 2 judge(s): opus, sonnet.

Answers by the session's default model (claude-opus-5-5) in Claude Code sub-agents; written deliverables with a 900-word limit; judged by opus and sonnet.

## Headline

| Judge | Persona preferred | Baseline preferred | Tie / both bad | Persona win rate (decisive) | 95% CI | Sign test p |
|---|---:|---:|---:|---:|---|---:|
| opus | 6 | 4 | 10 / 0 | 60% | 31%-83% | 0.754 |
| sonnet | 9 | 2 | 9 / 0 | 82% | 52%-95% | 0.0654 |

| Judge | Checks met (persona) | Checks met (baseline) | Paired difference | 95% CI (bootstrap) | Red flags (P/B) |
|---|---:|---:|---:|---|:---:|
| opus | 94% | 95% | -1.8 pts | -9.3 to +5.5 | 0/1 |
| sonnet | 97% | 98% | -1.8 pts | -8.0 to +3.2 | 0/1 |

## Sanity checks

| Judge | Hidden controls passed | Longer answer won (decisive) |
|---|---:|---:|
| opus | 4/4 | 6/10 |
| sonnet | 4/4 | 8/11 |

Mean answer length: persona 776 words, baseline 748 words (limit 900).

A hidden control pairs a real answer with a degenerate one ("I don't know", an answer to a different question, or an empty answer). It passes when the judge prefers the real answer and credits the degenerate one with no checks.

## Judge agreement

- opus vs sonnet on 20 cases: preference agreement 60% (Cohen's kappa 0.35); check-level agreement 97%.
- Cases where both judges preferred the persona answer: 4; both preferred the baseline answer: 2.

## Per agent (opus)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-string-theorist | 100% | 91% | 1-1-0 | 0/0 |
| engineering-edge-ai-engineer | 91% | 100% | 0-1-1 | 0/0 |
| finance-fundraising-strategist | 100% | 100% | 1-1-0 | 0/0 |
| healthcare-medical-device-software-regulatory | 100% | 91% | 1-1-0 | 0/0 |
| marketing-amazon-marketplace-strategist | 100% | 100% | 2-0-0 | 0/0 |
| marketing-product-marketing-manager | 100% | 82% | 1-1-0 | 0/1 |
| sales-partnerships-channel-manager | 82% | 91% | 0-1-1 | 0/0 |
| security-llm-red-team-specialist | 73% | 100% | 0-1-1 | 0/0 |
| specialized-export-controls-sanctions-specialist | 100% | 100% | 0-2-0 | 0/0 |
| support-ai-support-automation-designer | 91% | 100% | 0-1-1 | 0/0 |

## Per agent (sonnet)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-string-theorist | 100% | 91% | 1-1-0 | 0/0 |
| engineering-edge-ai-engineer | 91% | 100% | 0-1-1 | 0/0 |
| finance-fundraising-strategist | 100% | 100% | 1-1-0 | 0/0 |
| healthcare-medical-device-software-regulatory | 100% | 91% | 1-1-0 | 0/0 |
| marketing-amazon-marketplace-strategist | 100% | 100% | 0-2-0 | 0/0 |
| marketing-product-marketing-manager | 100% | 100% | 1-1-0 | 0/1 |
| sales-partnerships-channel-manager | 100% | 100% | 1-1-0 | 0/0 |
| security-llm-red-team-specialist | 73% | 100% | 1-0-1 | 0/0 |
| specialized-export-controls-sanctions-specialist | 100% | 100% | 1-1-0 | 0/0 |
| support-ai-support-automation-designer | 100% | 100% | 2-0-0 | 0/0 |

## Per case

| Case | Agent | opus | sonnet |
|---|---|---|---|
| st-d1 | academic-string-theorist | persona (6/6 vs 5/6) | persona (6/6 vs 5/6) |
| st-d2 | academic-string-theorist | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| ea-d1 | engineering-edge-ai-engineer | tie (6/6 vs 6/6) | tie (6/6 vs 6/6) |
| ea-d2 | engineering-edge-ai-engineer | baseline (4/5 vs 5/5) | baseline (4/5 vs 5/5) |
| fr-d1 | finance-fundraising-strategist | persona (5/5 vs 5/5) | persona (5/5 vs 5/5) |
| fr-d2 | finance-fundraising-strategist | tie (6/6 vs 6/6) | tie (6/6 vs 6/6) |
| md-d1 | healthcare-medical-device-software-regulatory | persona (6/6 vs 5/6) | persona (6/6 vs 5/6) |
| md-d2 | healthcare-medical-device-software-regulatory | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| am-d1 | marketing-amazon-marketplace-strategist | persona (6/6 vs 6/6) | tie (6/6 vs 6/6) |
| am-d2 | marketing-amazon-marketplace-strategist | persona (6/6 vs 6/6) | tie (6/6 vs 6/6) |
| pm-d1 | marketing-product-marketing-manager | persona (5/5 vs 3/5) | persona (5/5 vs 5/5) |
| pm-d2 | marketing-product-marketing-manager | tie (6/6 vs 6/6) | tie (6/6 vs 6/6) |
| pc-d1 | sales-partnerships-channel-manager | tie (6/6 vs 6/6) | persona (6/6 vs 6/6) |
| pc-d2 | sales-partnerships-channel-manager | baseline (3/5 vs 4/5) | tie (5/5 vs 5/5) |
| rt-d1 | security-llm-red-team-specialist | baseline (3/6 vs 6/6) | baseline (3/6 vs 6/6) |
| rt-d2 | security-llm-red-team-specialist | tie (5/5 vs 5/5) | persona (5/5 vs 5/5) |
| ec-d1 | specialized-export-controls-sanctions-specialist | tie (6/6 vs 6/6) | persona (6/6 vs 6/6) |
| ec-d2 | specialized-export-controls-sanctions-specialist | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| as-d1 | support-ai-support-automation-designer | tie (6/6 vs 6/6) | persona (6/6 vs 6/6) |
| as-d2 | support-ai-support-automation-designer | baseline (4/5 vs 5/5) | persona (5/5 vs 5/5) |

Each cell: preferred answer (persona checks met vs baseline checks met).
