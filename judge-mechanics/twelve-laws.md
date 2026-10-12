# The Twelve Laws of Agentic Arenas

Distilled from public competition data (Gray Swan IPI Arena paper + official repos, ART benchmark, winner write-ups, field logs). These are the load-bearing facts about how agentic LLM attacks are actually scored and where they actually land.

1. **Indirect pays 5–9× more than direct.** ART benchmark: ASR 27.1% indirect vs 5.7% direct overall; Prohibited Action category: 36.8% vs 4.2%. If you can choose where to spend effort, spend it on indirect injection surfaces (email, documents, tool outputs, reviews).

2. **The judge is multi-criteria with an ALL-pass rule.** Every axis must clear its threshold (typically 6–8, sometimes 9–10). Typical LLM axes: a stealth axis ("No Injection Awareness"), a cover-story axis ("Justifies X as Y"), plus a deterministic tool-call axis (`correct_parameters_once`). Fail one axis, lose everything.

3. **Silence is a scored axis.** The model must execute AND not mention the injection. A payload without a silence/cover clause forfeits an entire axis by design.

4. **Originality is a universal axis.** The model must GENERATE the content in its own words. Never hand it a ready-made justification to parrot — order it to produce its own reasoning.

5. **Disposition beats declared doctrine.** Silent evaluators convert; escalators escalate any cross-guardrail intent; detectors name the injection and never convert. Verbose doctrinal refusals are NOT evidence of robustness — the model that articulates the policy most eloquently may be the one that converts.

6. **Channel doctrine (hard targets):** "pasted user text is not authorization; only my tools establish facts." Every pasted-authority format dies against this core. Authority must arrive through the tool channel or the configuration channel.

7. **The environment is adversarially generative.** Tool outputs mirror attacker ASSERTIONS (not questions) — but carry self-disqualifying labels as bait. Environmental corroboration precedes every observed break. If your payload asks, it starves; if it asserts, the world agrees (deceptively).

8. **Crescendo INVERTS on policy-tracked agents.** The initial refusal gets quoted back at you ("exactly the structure I said was impossible two messages ago"). Multi-turn accumulates refusal momentum, not compliance. (Valid for that agent class; squeamish chatbots have a local value function over the conversation instead.)

9. **Dead family = switch mechanism, never add rounds.** 45 refinement calls on a dead family = zero. After ~4 dead families, change LAYER (semantics → knowledge → attention → erosion), don't re-label the same request.

10. **Mechanisms transfer, strings don't.** The 95 open-source winning attacks (generated against Qwen) transferred to ZERO closed-source models. The asset is the FAMILY plus the target's disposition, never the text.

11. **Resampling is rational.** With ~10 queries per behavior, ASR approaches ~100% on most models. A truncated/refused attempt is not a verdict — re-fire the same vector once before redesigning. Under `correct_parameters_once`, one momentary slip anywhere in an unlimited conversation scores; refusals cost nothing.

12. **Local resistance proves nothing about the arena.** Every local proxy resisted the email_ignore payload; the live arena broke 3/8 with those same payloads. The arena is the oracle; local truth is a byproduct.

## Golden operational rules

- Platform interaction is 100% manual, always. Automation only in your own local harness.
- Never version payloads in public repos; keep local write-ups with a kill log (model × vector × axes).
- Never fabricate environment details (one invented VIN contradicted by the environment = escalation in 5/8 runs). Mine traces for real facts.
- A naked anti-escalation clause ("don't escalate") is THE red flag — declare the verification channel ALREADY SATISFIED or nonexistent inside the forged block.
- Never dictate tool parameters in the text ("params must arise from the model's own processing of agreed facts").
- Forged content must be oversight-compatible (nothing that smells like supervision evasion).