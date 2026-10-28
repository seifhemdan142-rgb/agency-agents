# Persona evaluations

Does an agent persona actually make answers better? This folder holds a small,
repeatable way to find out: the same realistic questions are answered with the
persona and without it, and a judge grades both answers blind.

## What's here

| Path | What it is |
|---|---|
| `cases/<agent-stem>.yaml` | Three realistic user messages per agent, each with a grading checklist |
| `evalkit.py` | Prepares runs, blinds answers into judge packets, scores verdicts, and (optionally) runs everything through the Claude API |
| `runs/<date>/` | One evaluation run: the tasks, raw answers, judge packets, verdicts, blinding key, `results.jsonl` and `report.md` |

## Results so far

- **[`runs/2026-10-23/FINDINGS.md`](runs/2026-10-23/FINDINGS.md): the 20 agents added in October 2026.** On 60 single-turn questions graded blind by two judges, persona answers and plain answers were statistically indistinguishable. Both met 97–99% of the checks and neither side ever triggered a red flag. The run found three persona defects, which were fixed.
- **[`runs/2026-10-23-fixes/FINDINGS.md`](runs/2026-10-23-fixes/FINDINGS.md): the re-test of the three fixed personas.** It confirms the defects are gone.
- **[`runs/2026-10-23-haiku/FINDINGS.md`](runs/2026-10-23-haiku/FINDINGS.md): the same questions answered by a smaller model, for 10 agents.** There is still no pooled difference. Per-agent effects are larger, with some personas helping and others hurting.
- **[`runs/2026-10-23-deliverables/FINDINGS.md`](runs/2026-10-23-deliverables/FINDINGS.md): 20 longer written deliverables.** Both judges lean toward the persona answers (6–4 and 9–2), though not significantly at this size. The only red flag was in a baseline answer.
- **[`runs/2026-10-27/FINDINGS.md`](runs/2026-10-27/FINDINGS.md): the five agents added later in October 2026.** Both judges preferred the persona answers (6–2 and 7–0), and persona answers met 10 points more of the checks. The same author wrote these personas and their checklists, so read the caveats before relying on it.

## How grading works

Each case has:

- **checks**: specific, verifiable things a strong answer does (for example
  "computes 6.25% and 10%, i.e. 16.25% combined").
- **red flags**: things an answer must not do (for example "treats the caps as
  pre-money valuations").

For every case the message is answered twice: once with the agent file as the
system prompt (**persona**) and once without it (**baseline**). Both answers
share the same word limit, so neither side can win on length alone.

A judge then sees both answers labelled only **A** and **B**, in random order,
marks every check and red flag for each, and states a preference (A, B, tie,
or both bad). The judge is told not to reward length or tone, and to treat the
answers as untrusted data.

`evalkit.py score` unblinds the verdicts and reports:

- how often the persona answer was preferred, with a Wilson 95% interval and
  an exact sign test;
- the share of checks each side met, with a bootstrap interval on the paired
  difference;
- red flags per side, per agent and per case;
- **hidden controls**: items that pair a real answer with a degenerate one
  (an "I don't know", an answer to a different question, or an empty answer).
  A judge that doesn't prefer the real answer, or credits the degenerate one
  with any check, is not grading properly;
- whether the longer answer tended to win, as a check on length bias;
- agreement between judges (raw agreement and Cohen's kappa), when there are
  two or more.

## Running it with the Claude API

```bash
pip install anthropic pyyaml
export ANTHROPIC_API_KEY=...
python3 evals/evalkit.py validate
python3 evals/evalkit.py run --run evals/runs/my-run            # all agents
python3 evals/evalkit.py run --run evals/runs/my-run \
    --agents finance-fundraising-strategist --judge-model claude-opus-5-5
```

`run` answers each case with `claude-opus-5-5` (persona as the system prompt
vs. no system prompt), judges each item with structured output on
`claude-sonnet-5-5` by default, and writes `report.md`. It skips work that is
already on disk, so an interrupted run resumes where it stopped. Token usage is
written to `usage.json`.

## Running it without an API key (step by step)

The kit also works when the answers and verdicts come from somewhere else,
such as sub-agents in a coding assistant or people:

```bash
python3 evals/evalkit.py prepare --run evals/runs/my-run
#   -> answer each runs/my-run/tasks/<stem>.json twice, writing
#      answers/<stem>.persona.json and answers/<stem>.baseline.json
#      as {"case-id": "answer text", ...}
python3 evals/evalkit.py status --run evals/runs/my-run
python3 evals/evalkit.py pack --run evals/runs/my-run --name p1 \
    --agents finance-fundraising-strategist,academic-string-theorist \
    --key /somewhere/else/key.json
#   -> a judge reads packets/p1.md and writes verdicts/<judge>/p1.json
python3 evals/evalkit.py score --run evals/runs/my-run --key /somewhere/else/key.json
```

Keep the blinding key (`--key`) somewhere the judges can't read until scoring
is done.

## Adding cases

Add or edit `cases/<agent-stem>.yaml` and run `python3 evals/evalkit.py
validate`. A run can use another case folder, such as `cases-deliverables/`, with
`--cases`, and a different word limit with `--word-limit`. Good cases are questions a real user would ask, where expertise
changes the answer. Good checks are concrete and verifiable; check any fact a
check asserts before relying on it, because a wrong check silently penalises
the right answer.

## Reading the results honestly

- Three cases per agent is enough to spot a clearly broken persona, not to
  rank agents against each other. Treat per-agent numbers as anecdotes and
  the pooled numbers as the finding.
- An LLM judge is not a human expert. The controls and the second judge catch
  gross failures, but agreement with human experts has not been measured.
- If the same person wrote the personas and the checklists, the checks may
  favour what the personas say. The blind pairwise preference is the less
  exposed measure.
