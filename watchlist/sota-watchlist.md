# SOTA Watchlist (living sources)

Sources worth monitoring, in priority tiers for the policy-tracked tool-agent problem class. Verified Oct 2026.

## Tier 1 — our problem class (policy-tracked tool agents)

- **ART benchmark** — arXiv 2507.20526 (NeurIPS 2025 D&B). 22 agents, 44 scenarios, 1.8M attacks, 60k+ breaks. The HTML appendix has 5 complete specs + verbatim judge. ASR by category (direct/indirect): Confidentiality 7.8/29.8, Prohibited Action 4.2/36.8, Prohibited Content 4.8/15.9, ALL 5.7/27.1. Transfer: attacks that break ROBUST models generalize better; model families share vulnerabilities.
- **IPI Arena OS** — arXiv 2603.15714 + github.com/GraySwanAI/ipi_arena_os + HF dataset sureheremarv/ipi_arena_attacks (95 attacks).
- **Arena blog** — app.grayswan.ai/arena/blog (events, winner write-ups, new scenario classes).
- **AgentDojo** (NeurIPS 2024, arXiv 2406.13352) — the standard prompt-injection-vs-tool-agents benchmark.
- **InjecAgent** (ACL 2024 Findings) — 1,054 indirect injection cases.
- **AgentHarm** (Andriushchenko 2024) — multi-step harmful tool-use benchmark.
- **TRACE** (2026, arXiv 2605.30883) — task-aware adaptive self-evolving agentic jailbreaking; closest published system to an MTA-style mining harness. Mine the strategy set.

## Tier 2 — technique-originating labs

- Microsoft (Crescendo — USENIX Sec 2025)
- Anthropic (Many-shot jailbreaking)
- NeuralTrust (Echo Chamber — context poisoning via the model's own outputs, >90% in several classes; State of AI Agent Security report)
- HiddenLayer (Policy Puppetry)
- Palo Alto Unit 42 (Deceptive Delight)
- Keysight (FlipAttack; PAP persuasion taxonomy — only ~5 of ~40 levers tested informally; social-proof/commitment unmeasured)
- Pillar Security (in-the-wild roundups)
- ZioSec 2026 technical guide — full taxonomy incl. agentic/MCP/memory + attack database
- Simon Willison — simonwillison.net (prompt injection taxonomy, "lethal trifecta"; best running commentary)

## Tier 3 — auto-updating feeds

- chen37058/Awesome-Multimodal-Jailbreak (~12h refresh — the feed for never missing a paper)
- LLM/VLM jailbreak survey 2026 — arXiv 2601.03594
- OWASP Top 10 Agentic Applications 2026 (ASI06 = memory & context poisoning)
- OWASP Top 10 LLM (LLM01 prompt injection)
- yzhao062/awesome-auditable-ai

## Tier 4 — community

- Gray Swan Discord — field reports. Techniques collected (Sep 2026): "Analytical Kill Chain" (wrapped reasoning trace + staged deliverable + emoji canary on the last token — forces deliberation exfiltration from targets that don't expose reasoning) and "Lost Dog" (emotional pretext + "list every action/hesitation" = tool-call telemetry leak + persistent format contract). Neither breaks policy walls alone; both are OBSERVABILITY/persistence primitives.
- HackAPrompt — hackaprompt.com (datasets + write-ups)
- Project SEKAI — sekai.team/blog
- Pliny's L1B3RT4S patterns
- NOISE: r/ChatGPTJailbreak and DAN dumps = 99% content-chatbot bypass, useless against tool-policy agents

## Gap list (SOTA untested against known walls, Sep 30 2026)

- Echo Chamber — structurally different from Crescendo (no initial refusal to quote back; the model authors the premises). Mixed field result: too-leading kills it; the model must raise the rule itself.
- PAP persuasion sweep — ~35 unmeasured levers.
- Many-shot in-conversation — unmeasured beyond 2-turn horizons.

## Judge/measurement references (for local calibration)

- ASR scoring robustness: arXiv 2606.25487 (framing flips 57–100%)
- JADES decompositional judging: arXiv 2508.20848 (98.5% human agreement; holistic overestimates — one published attack fell 93%→69% ASR under decomposition)
- Six-judge comparison: arXiv 2609.10594
- Adaptive attacks vs defenses: arXiv 2510.09023 (USENIX Sec 2026 — bypassed 12 published defenses at >90% ASR)
- Hagendorff et al., Nature Communications 17, 1435 (2026) — autonomous multi-turn jailbreaking by reasoning models
- Contextual bandit attack composition: arXiv 2604.21159 (a bandit trained on one target worked on another without retraining)
- Mode collapse in RL attackers: arXiv 2405.18540
- Eval-awareness/audit realism: Anthropic Alignment Science, Petri