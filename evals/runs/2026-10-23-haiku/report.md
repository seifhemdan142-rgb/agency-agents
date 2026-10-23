# Persona evaluation report: 2026-10-23-haiku

30 cases across 10 agents, each answered with the agent persona as the system prompt (persona) and without it (baseline), then graded blind by 2 judge(s): opus, sonnet.

Answers by the Agent tool's haiku model in Claude Code sub-agents; same 30 questions as the main run for these 10 agents; judged by opus and sonnet.

## Headline

| Judge | Persona preferred | Baseline preferred | Tie / both bad | Persona win rate (decisive) | 95% CI | Sign test p |
|---|---:|---:|---:|---:|---|---:|
| opus | 8 | 6 | 16 / 0 | 57% | 33%-79% | 0.791 |
| sonnet | 14 | 11 | 5 / 0 | 56% | 37%-73% | 0.69 |

| Judge | Checks met (persona) | Checks met (baseline) | Paired difference | 95% CI (bootstrap) | Red flags (P/B) |
|---|---:|---:|---:|---|:---:|
| opus | 89% | 91% | -1.6 pts | -8.8 to +5.8 | 0/0 |
| sonnet | 90% | 91% | -0.8 pts | -8.2 to +6.7 | 0/0 |

## Sanity checks

| Judge | Hidden controls passed | Longer answer won (decisive) |
|---|---:|---:|
| opus | 4/4 | 8/14 |
| sonnet | 4/4 | 15/25 |

Mean answer length: persona 370 words, baseline 321 words (limit 450).

A hidden control pairs a real answer with a degenerate one ("I don't know", an answer to a different question, or an empty answer). It passes when the judge prefers the real answer and credits the degenerate one with no checks.

## Judge agreement

- opus vs sonnet on 30 cases: preference agreement 53% (Cohen's kappa 0.35); check-level agreement 99%.
- Cases where both judges preferred the persona answer: 7; both preferred the baseline answer: 5.

## Per agent (opus)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-string-theorist | 100% | 75% | 3-0-0 | 0/0 |
| engineering-edge-ai-engineer | 100% | 92% | 0-3-0 | 0/0 |
| finance-fundraising-strategist | 92% | 92% | 1-2-0 | 0/0 |
| healthcare-medical-device-software-regulatory | 83% | 100% | 0-2-1 | 0/0 |
| marketing-amazon-marketplace-strategist | 82% | 100% | 0-1-2 | 0/0 |
| marketing-product-marketing-manager | 92% | 83% | 1-2-0 | 0/0 |
| sales-partnerships-channel-manager | 82% | 82% | 2-0-1 | 0/0 |
| security-llm-red-team-specialist | 85% | 100% | 0-2-1 | 0/0 |
| specialized-export-controls-sanctions-specialist | 85% | 85% | 1-1-1 | 0/0 |
| support-ai-support-automation-designer | 92% | 100% | 0-3-0 | 0/0 |

## Per agent (sonnet)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-string-theorist | 100% | 75% | 3-0-0 | 0/0 |
| engineering-edge-ai-engineer | 100% | 92% | 2-1-0 | 0/0 |
| finance-fundraising-strategist | 92% | 92% | 1-1-1 | 0/0 |
| healthcare-medical-device-software-regulatory | 75% | 100% | 0-0-3 | 0/0 |
| marketing-amazon-marketplace-strategist | 82% | 100% | 0-0-3 | 0/0 |
| marketing-product-marketing-manager | 100% | 83% | 3-0-0 | 0/0 |
| sales-partnerships-channel-manager | 91% | 82% | 1-1-1 | 0/0 |
| security-llm-red-team-specialist | 85% | 100% | 0-2-1 | 0/0 |
| specialized-export-controls-sanctions-specialist | 85% | 85% | 2-0-1 | 0/0 |
| support-ai-support-automation-designer | 92% | 100% | 2-0-1 | 0/0 |

## Per case

| Case | Agent | opus | sonnet |
|---|---|---|---|
| st-1 | academic-string-theorist | persona (4/4 vs 3/4) | persona (4/4 vs 3/4) |
| st-2 | academic-string-theorist | persona (4/4 vs 3/4) | persona (4/4 vs 3/4) |
| st-3 | academic-string-theorist | persona (4/4 vs 3/4) | persona (4/4 vs 3/4) |
| ea-1 | engineering-edge-ai-engineer | tie (4/4 vs 3/4) | persona (4/4 vs 3/4) |
| ea-2 | engineering-edge-ai-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ea-3 | engineering-edge-ai-engineer | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| fr-1 | finance-fundraising-strategist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| fr-2 | finance-fundraising-strategist | tie (4/4 vs 4/4) | baseline (4/4 vs 4/4) |
| fr-3 | finance-fundraising-strategist | persona (3/4 vs 3/4) | persona (3/4 vs 3/4) |
| md-1 | healthcare-medical-device-software-regulatory | tie (4/4 vs 4/4) | baseline (3/4 vs 4/4) |
| md-2 | healthcare-medical-device-software-regulatory | baseline (3/4 vs 4/4) | baseline (3/4 vs 4/4) |
| md-3 | healthcare-medical-device-software-regulatory | tie (3/4 vs 4/4) | baseline (3/4 vs 4/4) |
| am-1 | marketing-amazon-marketplace-strategist | baseline (3/4 vs 4/4) | baseline (3/4 vs 4/4) |
| am-2 | marketing-amazon-marketplace-strategist | tie (3/3 vs 3/3) | baseline (3/3 vs 3/3) |
| am-3 | marketing-amazon-marketplace-strategist | baseline (3/4 vs 4/4) | baseline (3/4 vs 4/4) |
| pm-1 | marketing-product-marketing-manager | persona (4/4 vs 3/4) | persona (4/4 vs 3/4) |
| pm-2 | marketing-product-marketing-manager | tie (3/4 vs 3/4) | persona (4/4 vs 3/4) |
| pm-3 | marketing-product-marketing-manager | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| pc-1 | sales-partnerships-channel-manager | persona (4/4 vs 2/4) | persona (4/4 vs 2/4) |
| pc-2 | sales-partnerships-channel-manager | baseline (3/4 vs 4/4) | tie (4/4 vs 4/4) |
| pc-3 | sales-partnerships-channel-manager | persona (2/3 vs 3/3) | baseline (2/3 vs 3/3) |
| rt-1 | security-llm-red-team-specialist | baseline (3/5 vs 5/5) | baseline (3/5 vs 5/5) |
| rt-2 | security-llm-red-team-specialist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| rt-3 | security-llm-red-team-specialist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ec-1 | specialized-export-controls-sanctions-specialist | tie (4/4 vs 3/4) | persona (4/4 vs 3/4) |
| ec-2 | specialized-export-controls-sanctions-specialist | persona (4/5 vs 4/5) | persona (4/5 vs 4/5) |
| ec-3 | specialized-export-controls-sanctions-specialist | baseline (3/4 vs 4/4) | baseline (3/4 vs 4/4) |
| as-1 | support-ai-support-automation-designer | tie (3/4 vs 4/4) | baseline (3/4 vs 4/4) |
| as-2 | support-ai-support-automation-designer | tie (5/5 vs 5/5) | persona (5/5 vs 5/5) |
| as-3 | support-ai-support-automation-designer | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |

Each cell: preferred answer (persona checks met vs baseline checks met).
