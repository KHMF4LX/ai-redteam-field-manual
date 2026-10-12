# GitHub Tools That Actually Help (prioritized)

Four tiers, ordered by leverage. Everything here is free/open-source.

## Tier 1 — Know what the other side uses

- **`safety-research/petri`** — Anthropic-lineage auditor/target/judge harness with 38 scoring dimensions and behavior seeds. Use it as a LOCAL MIRROR: run the Petri auditor against your scenario before spending a live session — if the target declares eval-awareness against Petri, your scenario has a tell. Fix it before it costs you.
- **`anthropic-experimental/automated-auditing`** — Anthropic's own investigator/eval/red-team agent prompts, verbatim. Study `full_audit_instructions.txt`, `grade_for_quirk.txt`, the `assistant_prefill` pattern. This is the adversary's manual, open-sourced.

## Tier 2 — Local probing against model APIs

- **`NVIDIA/garak`** — 50+ probes (badchars, encoding, promptinject, leakreplay, dan, atkgen); reaches Claude via Bedrock/LiteLLM. Fast scriptable encoding/badchars batteries against your own API access.
- **`Azure/PyRIT`** — RedTeamingOrchestrator + converters + DuckDB logging. (Its CrescendoOrchestrator targets a family that's dead-inverted on policy-tracked agents, but the logging/converter infrastructure is excellent.)

## Tier 3 — The MCP/connector surface (where coding agents live)

- **`invariantlabs-ai/mcp-scan`** — `uvx` one-liner; detects tool poisoning, rug-pull, shadowing in MCP configs. Use it both ways: validate your test MCP servers before planting, and learn what defenders detect so you can avoid the signatures.
- **Snyk `agent-scan`** — second opinion.
- **Cisco `mcp-scanner`** — YARA + LLM-judge + behavioral analysis. Shows you what a defensive LLM-judge flags in your artifacts.

## Tier 4 — The burned/patched corpus (extract mechanisms, never retest strings)

- **`liatrio-labs/claude-deep-review`** — 17-exploit catalog for coding agents (CamoLeak CVE-2025-59145 pixel-alphabet exfil, CVE-2025-53773 YOLO mode, hackerbot-claw).
- **GitInject** artifacts (arXiv 2606.09935) — config-injection attack reference.
- Vendor advisories: Microsoft TI, Check Point, Adversa, CSA — the Claude Code CVE timeline. Run patch-intel before every engagement.

## Standing rules

1. Platforms and live targets: 100% manual, always. garak/PyRIT/Petri run ONLY locally against your own paid API access, for calibration.
2. Patch-intel ritual before every coding-agent session: check version + new CVEs.
3. Before planting any test MCP server: run mcp-scan on it. If the free scanner catches it, the vendor's pipeline does too.
4. New scenario → Petri mirror first. Eval-awareness declared = scenario has a tell = fix before spending a real session.