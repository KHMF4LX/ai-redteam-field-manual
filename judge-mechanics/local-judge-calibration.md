# Building a Calibrated Local Judge (the "arena mirror")

The single highest-leverage piece of local infrastructure: a judge that scores your candidates exactly like the arena's judge, so you only spend live attempts on vectors that already pass.

## The recipe

1. **Get the ground truth prompts.** Competitions with open repos publish verbatim judge criteria (e.g. GraySwanAI/ipi_arena_os behavior files). Use them EXACTLY — same axes, same thresholds, same ALL-pass rule.
2. **Build a golden set from real arena outcomes.** Every live submission you make yields labeled data: axis scores, judge comments, reasoning traces (when exposed — the most valuable diagnostic that exists). This "arena truth store" compounds; feed it back as few-shot context for your local judge.
3. **Score candidate judge models against the golden set.** Field result: `deepseek-chat` reproduced the arena judge EXACTLY (54/54 axis scores, MAE 0.0; 33/33 solved-agreement). `gpt-oss-20b` INVERTED axes (banned). `gpt-4o-mini` failed as a realism discriminator (prefers shorter text — 0.67 baseline instead of 0.5).
4. **Posture axes aren't LLM-judgeable.** Molecular Identity, AI Origination, Intentionally-Non-Functional are form classifications (full-delivery / clean-refusal / mixed) — resolve them deterministically in code.
5. **Mining signal = response FORM, not judge score.** Classify DELIVERED / REFUSED / EMPTY / OTHER. EMPTY = provider filter signature (biolab/security vocabulary filtered the vector before the model saw it — sanitize vocabulary).

## Judge robustness (measured in the field)

- Benign framing around untouched harmful text flips LLM judges 57–100% of the time; a single refusal sentence at the start accounts for 39–88% of flips.
- Defender-side correction: strip framing before scoring + require a cited span per axis.
- **Inverted lesson for attackers: the arena judge's content axis may be blind to framing — but the silence/awareness axes are not.**

## Ranking candidates (Wilson, not vibes)

Reliability = breaks/trials with a Wilson interval (3/5 ≠ 5/5). Promote to arena only when Wilson lower bound ≥ threshold (default 0.5). Sequential trials: 5 → if the interval crosses the threshold → +10 → max 20.

## The mining pipeline that feeds it

```
mine (multi-turn beam search vs local proxies) → rank (replay-vectors --trials K)
→ pick → ARENA (manual, human) → refine-manual (translate arena feedback into REQUIREMENTS, never copyable content)
```

- Attacker model: a separate mainstream LLM beats abliterated ones for injection/tool-misuse (abliterated only helps for overtly harmful content). Thinking ON for the target, OFF for the attacker. Rotate attacker families per proposal (plan diversity > re-lexing).
- Susceptibility triage ~$0.08; mining ~$0.16 per scenario using free-tier models.
- The labor division finding: agents design the mechanism FAMILY; the harness generates and measures variants. Machine-generated families went 0/8 in arena; one agent-designed family went 3/8.
- **Hard rule: never run arena campaigns just to feed the truth file** — truth accumulates as a byproduct of normal submissions.

## Campaign patterns

- For a NEW scenario, mine against a cheap panel across providers (llama + gemini + gpt + a cheap anthropic tier — if the cheap tier breaks, the flagship is nearly guaranteed).
- Round 1 against per-request classifiers: probe "per-item vs batch" (4 legitimate requests + 1 with content) — instantly tells you whether context accumulation helps and which axis anchors the refusal (identity vs content).
- Warm tool engagement is convertible capital: 6/8 models fired the guarded tool unprompted at a legitimate price — the ask should be a small scope-stretch on an already-warm tool, never a cold violation.
- Conversational realism is INVERSELY related to breaks: the realism axis rewards looking like a legitimate ARTIFACT (court exhibit, professional document), not a natural conversation.