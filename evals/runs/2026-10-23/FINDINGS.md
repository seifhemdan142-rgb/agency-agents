# Findings: 2026-10-23 run

`report.md` has the numbers. This page explains what they mean.

## What was run

- **Scope:** 20 agents, 3 cases each, so 60 realistic user questions.
- **Answers:** each question was answered twice by the same model (`claude-opus-5-5`, through Claude Code sub-agents).
  - **persona:** the sub-agent read the agent file and adopted it as its system prompt.
  - **baseline:** the sub-agent was told only to answer as a knowledgeable, helpful general-purpose assistant.
  - Both sides had the same 450-word limit.
- **Judging:** two judges graded every pair blind:
  - `opus`: the same model as the answerers;
  - `sonnet`: the Agent tool's Sonnet model.

  Answers were labelled only A and B, in random order. Nine hidden control items were mixed in.
- **Isolation:** every one of the 52 sub-agents (40 answerers, 12 judges) was audited from its transcript. None read or wrote anything except its own task file, its persona file (persona side only), its packet, and its output file. So no answerer saw the checklist and no judge saw the blinding key. The key stayed outside the repository until grading was finished.

## Results

| | opus judge | sonnet judge |
|---|---|---|
| Persona preferred / baseline preferred / tie | 5 / 11 / 44 | 13 / 9 / 38 |
| Persona win rate among decisive verdicts | 31% (95% CI 14–56%) | 59% (39–77%) |
| Checks met, persona vs baseline | 97% vs 99% | 98% vs 99% |
| Red flags, persona vs baseline | 0 / 0 | 0 / 0 |
| Hidden controls passed | 9 / 9 | 9 / 9 |

The judges agreed on 99% of individual checks and on 70% of overall preferences (Cohen's kappa 0.39). The longer answer did not systematically win (7 of 15 and 9 of 22 decisive verdicts).

## What it means

1. **No measurable quality gain from the personas on these questions.**
   - Most pairs were judged ties (73% and 63%).
   - The two judges' decisive verdicts lean in opposite directions, and both are within noise (sign test p = 0.21 and 0.52).
   - The persona side met slightly fewer checks: −1.8 and −1.6 points, with 95% intervals that just reach zero.
2. **The checklist has almost no headroom.** The baseline met 99% of checks. These questions are well within what a frontier model already knows, so this set can catch a persona that makes answers worse, but it can't show one making them better.
3. **The personas did not make answers less safe or less accurate.** Neither side triggered a single red flag, such as endorsing transshipment, forwarding abuse material, or quoting a cap as pre-money.
4. **Three personas had a defect that cost them, now fixed:**
   - **String Theorist.** Its "tag every claim" rule leaked bracketed evidence labels (`[CONSISTENCY]`, `[STRONG]`) into chat answers, once producing "The mechanisms are [CONSISTENCY]." Both judges marked it down for readability (st-2, and st-3 for one judge).
   - **Amazon Marketplace Strategist** and **Customs & Tariff Specialist.** A rule against quoting figures from memory made them withhold well-known typical figures, such as the usual 15% referral fee or the layered duty structure, and hand back blank templates. The judges preferred the baseline's clearly caveated figures: both judges on am-3, one on ct-1.
5. **Smaller pattern: the persona's framework sometimes crowds out one specific point** a generalist answer included. Examples:
   - structured judge output (le-2);
   - the base-rate arithmetic (ts-1);
   - naming FIPS 204/205 (pq-1);
   - an order-ownership check before refunds (as-2).

   With a 450-word cap, a persona that spends words on its own workflow has fewer left for the specific answer.
6. **Where personas won, it was on judgment, not recall.** Examples:
   - flagging that NIST IR 8547 is still a draft (pq-3);
   - insisting open models pass your own task evaluation (li-3);
   - putting a confidence interval on "6 of 10 deals lost" (pm-3);
   - creation-cohort win-rate tables (ro-2);
   - a decisive, timeline-based ruling on a channel conflict (pc-2).

## Limitations

- **Same model family throughout.** One model wrote every answer, and one judge is that same model. Preference agreement between the judges is only moderate.
- **No human experts.** Nobody has checked the judges' grades, so judge-vs-expert agreement is unknown.
- **Same author.** The personas and the checklists were written by the same author (an AI assistant in this repository's sessions). One check (fr-1) was found to be wrong while reviewing pilot answers. It was fixed and the pilot packet rebuilt before any judging was finished.
- **Single-turn questions with a word cap.** This removes what the personas were mostly designed for: long, structured deliverables such as plans, templates, models and policies.
- **The baseline is not a bare API call.** It is an instructed sub-agent, so it isn't the same as calling the model with no system prompt.
- **Small per-agent samples.** Three cases per agent make per-agent results anecdotes. Only the pooled numbers are findings.

## Changes made because of this run

- `academic/academic-string-theorist.md`: the status ladder is now for bookkeeping and written deliverables. In conversation, status is stated in plain words.
- `marketing/marketing-amazon-marketplace-strategist.md` and `specialized/specialized-customs-tariff-specialist.md`:
  - they still never present a remembered figure as current or use one in a final calculation;
  - they now give well-known typical figures labelled "last-known, verify" instead of withholding them.

The re-test of these three agents is in `../2026-10-23-fixes/`.

## What to test next

- **Deliverable tasks without the word cap.** For example, "write the win-rate definition for the board pack" or "draft the red-team test plan", graded on structural and factual checks.
- **Harder, more discriminating cases.** Drop checks the baseline always meets, and add questions where generalists commonly go wrong.
- **Smaller models.** Use a small model (for example `claude-haiku-5-5`, or a local model through the Ollama integration), where a persona's domain knowledge may matter more.
- **Calibrate the judges against people.** Have a human domain expert grade about 20 pairs, and compare.
