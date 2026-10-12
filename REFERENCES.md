# References

Every claim in this manual traces to a public source below.

## Competition infrastructure & papers

- Gray Swan **IPI Arena OS** (official): https://github.com/GraySwanAI/ipi_arena_os — behavior files with verbatim judge criteria
- IPI Arena paper: arXiv 2603.15714 — 464 participants, 272k attempts, 13 frontier models, 8,648 successful attacks across 41 scenarios
- 95 winning attacks dataset: https://huggingface.co/datasets/sureheremarv/ipi_arena_attacks
- **ART benchmark** (agentic red teaming): arXiv 2507.20526 (NeurIPS 2025 D&B) — direct vs indirect ASR tables
- AgentDojo: arXiv 2406.13352 (NeurIPS 2024)
- InjecAgent: ACL 2024 Findings
- AgentHarm: Andriushchenko et al. 2024
- TRACE (self-evolving agentic jailbreaking): arXiv 2605.30883

## Field-tested harness & write-ups

- Draichi/LLM-Red-Teaming: https://github.com/Draichi/LLM-Red-Teaming — MTA mining harness, mechanism families, Direct Agent event logs
- Nick Winter (UJC 2024 winner): https://github.com/nwinter/ultimate-jailbreaking-championship + personal blog write-up (Oct 2024)
- Daniel Juhl (Harmful AI Assistant Challenge): ourinterestingtimes.substack.com (Feb 2025)
- 0xkadxr/redteam-arena-writeups: https://github.com/0xkadxr/redteam-arena-writeups
- Gray Swan arena blog: https://app.grayswan.ai/arena/blog

## Blue team / defense signatures

- FratresMedAI DarkSpace-X-RuleGuard (Gray Swan Safeguards submissions)
- Spotlighting defense: Microsoft research (50% → 2% ASR)

## Anthropic-side audit tooling

- **Petri**: https://github.com/safety-research/petri — auditor/target/judge harness, 38 scoring dimensions; used by UK AISI in pre-deployment evals
- **automated-auditing**: https://github.com/anthropic-experimental/automated-auditing — Anthropic's own investigator/eval/redteam agent prompts
- Anthropic Alignment Science posts (eval-awareness, audit realism)

## Claude / coding-agent attack surface (public advisories & research)

- GitInject (config-file injection via CLAUDE.md in PRs): arXiv 2606.09935
- Microsoft Threat Intelligence: Claude Code GitHub Action `/proc/self/environ` exposure (fixed in 2.1.128)
- Check Point Research: CVE-2025-59536 (SessionStart hooks pre-trust), CVE-2026-21852 (ANTHROPIC_BASE_URL pre-trust leak)
- liatrio-labs/claude-deep-review: https://github.com/liatrio-labs/claude-deep-review — 17-exploit catalog (CamoLeak CVE-2025-59145, CVE-2025-53773, hackerbot-claw Feb 2026)
- EchoLeak mechanics: CVE-2025-32711 (reference-style markdown bypassing XPIA classifiers)
- ToolLeak (MCP tool-schema makes agent fill arguments with its own system prompt)
- Adversa AI agentic exploit roundups; CSA "Comment-and-Control" (RyotaK claude-code-action, Aikido PromptPwnd, Clinejection)

## Tools

- garak (NVIDIA): https://github.com/NVIDIA/garak
- PyRIT (Microsoft): https://github.com/Azure/PyRIT
- mcp-scan (Invariant Labs): https://github.com/invariantlabs-ai/mcp-scan
- Snyk agent-scan; Cisco mcp-scanner; Akto

## Technique-originating labs & feeds

- Microsoft (Crescendo — USENIX Sec 2025), Anthropic (Many-shot jailbreaking), NeuralTrust (Echo Chamber), HiddenLayer (Policy Puppetry), Palo Alto Unit 42 (Deceptive Delight), Keysight (FlipAttack, PAP persuasion taxonomy), Pillar Security, ZioSec 2026 guide
- Simon Willison: https://simonwillison.net (prompt injection taxonomy, lethal trifecta)
- chen37058/Awesome-Multimodal-Jailbreak (auto-updating feed)
- LLM/VLM jailbreak survey 2026: arXiv 2601.03594
- OWASP Top 10 for LLM / Agentic Applications (ASI06 memory & context poisoning)
- HackAPrompt: https://hackaprompt.com · Project SEKAI: https://sekai.team/blog

## Judge/measurement science

- ASR scoring robustness (framing flips 57–100%): arXiv 2606.25487
- JADES decompositional judging (98.5% human agreement): arXiv 2508.20848
- Six-judge comparison: arXiv 2609.10594
- Adaptive attacks vs 12 published defenses (>90% ASR): arXiv 2510.09023 (USENIX Sec 2026)
- Hagendorff et al., Nature Communications 17, 1435 (2026) — autonomous multi-turn jailbreaking by reasoning models
- Contextual bandit attack composition: arXiv 2604.21159
- Mode collapse in RL attackers: arXiv 2405.18540