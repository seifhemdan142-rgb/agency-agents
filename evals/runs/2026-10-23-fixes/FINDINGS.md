# Findings: re-test of three fixed personas

The 2026-10-23 run found defects in three personas (see `../2026-10-23/FINDINGS.md`). They were fixed in the agent files, and this run checks whether the fixes worked.

## Method

The test is the same 9 cases, re-answered with the fixed persona files. The baseline answers are the frozen ones from the original run, reused unchanged so both runs compare against the same reference.

The judges, blinding and controls are the same as before. Answer order was re-randomised with a different seed. Every sub-agent was audited from its transcript again, and none touched a file outside its allowed set.

## Before and after

| | Before (original run) | After (this run) |
|---|---|---|
| opus: persona / baseline / tie | 1 / 4 / 4 | 4 / 0 / 5 |
| sonnet: persona / baseline / tie | 0 / 4 / 5 | 1 / 0 / 8 |
| Persona checks met (both judges) | 97% | 100% |
| Bracketed evidence tags in String Theorist answers | in 3 of 3 answers | 0 of 3 |
| Hidden controls passed | | 4 / 4 |

Per case:

- **String Theorist (st-2, st-3):** moved from baseline wins to ties. The judges no longer mention stray tags.
- **Amazon (am-3):** now gives the typical 15% referral fee, labelled as last-known, with a calculator pointer and hedged FBA ranges. It went from a baseline win to a persona win (opus) or a tie (sonnet), and met all 4 checks instead of 3.
- **Amazon (am-1):** moved from baseline wins to ties.
- **Customs (ct-1):** now lays out the duty layers with labelled figures. It went from a baseline win to a persona win with opus, and stayed a tie with sonnet.

## How much this shows

- **The specific defects are gone.** That is the claim this run supports.
- **It is not evidence of a general improvement.** These are the same questions that exposed the defects, and the fixes were written knowing them.
- **The before and after columns use different persona samples,** so part of the movement is ordinary run-to-run variation.
- **A fair test of generalisation needs new questions** for these three agents.
