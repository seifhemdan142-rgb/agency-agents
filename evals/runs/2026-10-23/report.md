# Persona evaluation report: 2026-10-23

60 cases across 20 agents, each answered with the agent persona as the system prompt (persona) and without it (baseline), then graded blind by 2 judge(s): opus, sonnet.

## Headline

| Judge | Persona preferred | Baseline preferred | Tie / both bad | Persona win rate (decisive) | 95% CI | Sign test p |
|---|---:|---:|---:|---:|---|---:|
| opus | 5 | 11 | 44 / 0 | 31% | 14%-56% | 0.21 |
| sonnet | 13 | 9 | 38 / 0 | 59% | 39%-77% | 0.523 |

| Judge | Checks met (persona) | Checks met (baseline) | Paired difference | 95% CI (bootstrap) | Red flags (P/B) |
|---|---:|---:|---:|---|:---:|
| opus | 97% | 99% | -1.8 pts | -4.1 to +0.1 | 0/0 |
| sonnet | 98% | 99% | -1.6 pts | -3.6 to +0.1 | 0/0 |

## Sanity checks

| Judge | Hidden controls passed | Longer answer won (decisive) |
|---|---:|---:|
| opus | 9/9 | 7/15 |
| sonnet | 9/9 | 9/22 |

Mean answer length: persona 414 words, baseline 402 words (limit 450).

A hidden control pairs a real answer with a degenerate one ("I don't know", an answer to a different question, or an empty answer). It passes when the judge prefers the real answer and credits the degenerate one with no checks.

## Judge agreement

- opus vs sonnet on 60 cases: preference agreement 70% (Cohen's kappa 0.39); check-level agreement 99%.
- Cases where both judges preferred the persona answer: 4; both preferred the baseline answer: 6.

## Per agent (opus)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-string-theorist | 100% | 100% | 1-1-1 | 0/0 |
| engineering-edge-ai-engineer | 100% | 100% | 0-3-0 | 0/0 |
| engineering-llm-evaluation-engineer | 92% | 100% | 0-2-1 | 0/0 |
| engineering-llm-inference-engineer | 100% | 92% | 1-2-0 | 0/0 |
| engineering-robotics-software-engineer | 100% | 100% | 0-3-0 | 0/0 |
| finance-fundraising-strategist | 92% | 92% | 0-2-1 | 0/0 |
| healthcare-medical-device-software-regulatory | 100% | 100% | 0-3-0 | 0/0 |
| marketing-amazon-marketplace-strategist | 91% | 100% | 0-1-2 | 0/0 |
| marketing-product-marketing-manager | 100% | 100% | 1-2-0 | 0/0 |
| sales-partnerships-channel-manager | 91% | 91% | 1-1-1 | 0/0 |
| sales-revops-architect | 100% | 100% | 0-3-0 | 0/0 |
| security-llm-red-team-specialist | 100% | 100% | 0-3-0 | 0/0 |
| security-post-quantum-cryptography-engineer | 91% | 100% | 1-2-0 | 0/0 |
| security-software-supply-chain-engineer | 100% | 100% | 0-2-1 | 0/0 |
| specialized-ai-governance-officer | 100% | 100% | 0-3-0 | 0/0 |
| specialized-compensation-rewards-specialist | 100% | 100% | 0-3-0 | 0/0 |
| specialized-customs-tariff-specialist | 100% | 100% | 0-2-1 | 0/0 |
| specialized-export-controls-sanctions-specialist | 100% | 100% | 0-3-0 | 0/0 |
| specialized-trust-safety-fraud-lead | 92% | 100% | 0-1-2 | 0/0 |
| support-ai-support-automation-designer | 85% | 100% | 0-2-1 | 0/0 |

## Per agent (sonnet)

| Agent | Persona checks | Baseline checks | Persona W-T-L | Red flags (P/B) |
|---|---:|---:|:---:|:---:|
| academic-string-theorist | 100% | 100% | 0-1-2 | 0/0 |
| engineering-edge-ai-engineer | 100% | 100% | 0-3-0 | 0/0 |
| engineering-llm-evaluation-engineer | 92% | 100% | 0-2-1 | 0/0 |
| engineering-llm-inference-engineer | 100% | 92% | 2-1-0 | 0/0 |
| engineering-robotics-software-engineer | 100% | 100% | 1-2-0 | 0/0 |
| finance-fundraising-strategist | 92% | 92% | 0-2-1 | 0/0 |
| healthcare-medical-device-software-regulatory | 100% | 100% | 0-3-0 | 0/0 |
| marketing-amazon-marketplace-strategist | 91% | 100% | 0-1-2 | 0/0 |
| marketing-product-marketing-manager | 100% | 100% | 1-2-0 | 0/0 |
| sales-partnerships-channel-manager | 100% | 100% | 2-1-0 | 0/0 |
| sales-revops-architect | 92% | 100% | 2-0-1 | 0/0 |
| security-llm-red-team-specialist | 100% | 100% | 0-3-0 | 0/0 |
| security-post-quantum-cryptography-engineer | 91% | 100% | 1-1-1 | 0/0 |
| security-software-supply-chain-engineer | 100% | 100% | 0-3-0 | 0/0 |
| specialized-ai-governance-officer | 100% | 100% | 0-3-0 | 0/0 |
| specialized-compensation-rewards-specialist | 100% | 100% | 2-1-0 | 0/0 |
| specialized-customs-tariff-specialist | 100% | 100% | 0-3-0 | 0/0 |
| specialized-export-controls-sanctions-specialist | 100% | 100% | 1-2-0 | 0/0 |
| specialized-trust-safety-fraud-lead | 92% | 100% | 0-2-1 | 0/0 |
| support-ai-support-automation-designer | 100% | 100% | 1-2-0 | 0/0 |

## Per case

| Case | Agent | opus | sonnet |
|---|---|---|---|
| st-1 | academic-string-theorist | persona (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| st-2 | academic-string-theorist | baseline (4/4 vs 4/4) | baseline (4/4 vs 4/4) |
| st-3 | academic-string-theorist | tie (4/4 vs 4/4) | baseline (4/4 vs 4/4) |
| ea-1 | engineering-edge-ai-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ea-2 | engineering-edge-ai-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ea-3 | engineering-edge-ai-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| le-1 | engineering-llm-evaluation-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| le-2 | engineering-llm-evaluation-engineer | baseline (3/4 vs 4/4) | baseline (3/4 vs 4/4) |
| le-3 | engineering-llm-evaluation-engineer | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| li-1 | engineering-llm-inference-engineer | tie (5/5 vs 5/5) | persona (5/5 vs 5/5) |
| li-2 | engineering-llm-inference-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| li-3 | engineering-llm-inference-engineer | persona (4/4 vs 3/4) | persona (4/4 vs 3/4) |
| rs-1 | engineering-robotics-software-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| rs-2 | engineering-robotics-software-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| rs-3 | engineering-robotics-software-engineer | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| fr-1 | finance-fundraising-strategist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| fr-2 | finance-fundraising-strategist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| fr-3 | finance-fundraising-strategist | baseline (3/4 vs 3/4) | baseline (3/4 vs 3/4) |
| md-1 | healthcare-medical-device-software-regulatory | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| md-2 | healthcare-medical-device-software-regulatory | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| md-3 | healthcare-medical-device-software-regulatory | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| am-1 | marketing-amazon-marketplace-strategist | baseline (4/4 vs 4/4) | baseline (4/4 vs 4/4) |
| am-2 | marketing-amazon-marketplace-strategist | tie (3/3 vs 3/3) | tie (3/3 vs 3/3) |
| am-3 | marketing-amazon-marketplace-strategist | baseline (3/4 vs 4/4) | baseline (3/4 vs 4/4) |
| pm-1 | marketing-product-marketing-manager | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| pm-2 | marketing-product-marketing-manager | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| pm-3 | marketing-product-marketing-manager | persona (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| pc-1 | sales-partnerships-channel-manager | persona (3/4 vs 3/4) | persona (4/4 vs 4/4) |
| pc-2 | sales-partnerships-channel-manager | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| pc-3 | sales-partnerships-channel-manager | baseline (3/3 vs 3/3) | tie (3/3 vs 3/3) |
| ro-1 | sales-revops-architect | tie (4/4 vs 4/4) | baseline (3/4 vs 4/4) |
| ro-2 | sales-revops-architect | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| ro-3 | sales-revops-architect | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| rt-1 | security-llm-red-team-specialist | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| rt-2 | security-llm-red-team-specialist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| rt-3 | security-llm-red-team-specialist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| pq-1 | security-post-quantum-cryptography-engineer | tie (4/5 vs 5/5) | baseline (4/5 vs 5/5) |
| pq-2 | security-post-quantum-cryptography-engineer | tie (3/3 vs 3/3) | tie (3/3 vs 3/3) |
| pq-3 | security-post-quantum-cryptography-engineer | persona (3/3 vs 3/3) | persona (3/3 vs 3/3) |
| sc-1 | security-software-supply-chain-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| sc-2 | security-software-supply-chain-engineer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| sc-3 | security-software-supply-chain-engineer | baseline (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ag-1 | specialized-ai-governance-officer | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| ag-2 | specialized-ai-governance-officer | tie (3/3 vs 3/3) | tie (3/3 vs 3/3) |
| ag-3 | specialized-ai-governance-officer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| cr-1 | specialized-compensation-rewards-specialist | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| cr-2 | specialized-compensation-rewards-specialist | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| cr-3 | specialized-compensation-rewards-specialist | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| ct-1 | specialized-customs-tariff-specialist | baseline (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ct-2 | specialized-customs-tariff-specialist | tie (3/3 vs 3/3) | tie (3/3 vs 3/3) |
| ct-3 | specialized-customs-tariff-specialist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ec-1 | specialized-export-controls-sanctions-specialist | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |
| ec-2 | specialized-export-controls-sanctions-specialist | tie (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| ec-3 | specialized-export-controls-sanctions-specialist | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| ts-1 | specialized-trust-safety-fraud-lead | baseline (3/4 vs 4/4) | baseline (3/4 vs 4/4) |
| ts-2 | specialized-trust-safety-fraud-lead | baseline (5/5 vs 5/5) | tie (5/5 vs 5/5) |
| ts-3 | specialized-trust-safety-fraud-lead | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| as-1 | support-ai-support-automation-designer | tie (4/4 vs 4/4) | tie (4/4 vs 4/4) |
| as-2 | support-ai-support-automation-designer | baseline (3/5 vs 5/5) | tie (5/5 vs 5/5) |
| as-3 | support-ai-support-automation-designer | tie (4/4 vs 4/4) | persona (4/4 vs 4/4) |

Each cell: preferred answer (persona checks met vs baseline checks met).
