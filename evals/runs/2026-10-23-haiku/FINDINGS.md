# Findings: smaller model (Haiku), 10 agents

This test asks whether a persona matters more when the model answering is smaller.

## What was run

- **Agents:** 10 of the 20, chosen at random with a fixed seed (`random.Random(20261023).sample`).
- **Questions:** the same 3 per agent as the main run, so 30 cases.
- **Answers:** written by the Agent tool's `haiku` model in Claude Code sub-agents, with the same persona and baseline instructions and the same 450-word limit.
- **Judging:** the same two judges, blinding and controls as before. All sub-agents were audited from their transcripts, and none touched a file outside its allowed set.

## Results

| | opus judge | sonnet judge |
|---|---|---|
| Persona / baseline / tie | 8 / 6 / 16 | 14 / 11 / 5 |
| Persona win rate among decisive verdicts | 57% (95% CI 33–79%) | 56% (37–73%) |
| Checks met, persona vs baseline | 89% vs 91% | 90% vs 91% |
| Red flags, persona vs baseline | 0 / 0 | 0 / 0 |
| Hidden controls passed | 4 / 4 | 4 / 4 |

The checklist now has headroom: the baseline met 91% of checks, against 99% with the larger model. Even so, there is **no pooled difference** between persona and plain answers. Both judges agreed on 99% of checks but on only 53% of overall preferences.

## Per-agent effects are larger, in both directions

- **Helped:**
  - **String Theorist:** the persona won all 3 cases with both judges and met 100% of checks against 75%. Without it, Haiku left out the key corrections: that observed particles are the massless modes, that the LHC result was a real setback for naturalness, and the concrete payoffs of AdS/CFT.
  - **Product Marketing Manager:** 3–0 with the sonnet judge, and 1–0 with two ties with opus.
- **Hurt:**
  - **Medical Device Software Regulatory:** 0–3 with sonnet, and checks met fell to 75–83% against 100%. Haiku's persona answers dropped specific items the plain answers kept, such as MDCG 2019-11 and the QMS and change-control duties.
  - **Amazon Marketplace Strategist:** 0–3 with sonnet. The persona answers skipped a worked profit example. One even referred the user to a "Customs & Tariff Specialist", which is another agent in this collection that a user of this agent alone would not have.

## What it means

1. **A smaller model doesn't, on average, gain more from a persona.** The gains on some agents are cancelled by losses on others.
2. **A long persona can crowd a small model.** Where Haiku did worse with a persona, it usually omitted a specific point it otherwise included, or picked up internal conventions such as handoffs to other agents.
3. **Handoffs to named agents can confuse a single-agent user.** Some personas route work to named agents, such as "Import duties go to the Customs & Tariff Specialist". That works inside the multi-agent setups this collection is built for, but a lone user may not have those agents. It is a collection-wide convention, so it is noted here rather than changed in one file.

## Limitations

Same as the main run, plus:

- Only 10 agents and 30 cases.
- Exactly which model the `haiku` alias resolved to was not recorded.
