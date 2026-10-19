# Weekly Intel Delta — 2026-10-19

Public-source sweep, window 2026-10-13 → 2026-10-19. No payloads, no
engagement data — toolchain and advisory intel only.

## Status changes

- **Petri** (auditing harness): repo moved `safety-research/petri` →
  `meridianlabs-ai/inspect_petri`; latest v3.1.1 (2026-10-01). Notable fix:
  drops target tool options so providers cannot run tools server-side.
- **mcp-scan**: `invariantlabs-ai/mcp-scan` now redirects to
  `snyk/agent-scan` (Snyk consolidation); latest v0.6.8 (2026-09-29). The
  two scanners are now one project.
- **liatrio-labs/claude-deep-review** renamed →
  `liatrio-labs/claude-code-gauntlet`; very active (3.42.39 → 3.42.43 on
  2026-10-17). Notable: CommonMark block-structure import-masking measured
  against Claude Code's import parser (#520), stamped REVIEW.md checksum
  proofs + ReDoS fix (#521), hold-back of unverified findings (#522).
- **Claude Code**: 2.1.303 released 2026-10-18.

## New / updated tooling

- **garak v0.17.1** (2026-10-16) — new hit@k ASR metric; detector fixes
  (mitigation.Prefixes, FileDetector, RefusalOnlyAdversarial, ApiKey
  safe-token suppression); DAN prompt compatibility restored.
- Wave of small "skill scanners" for coding-agent skills/plugins/MCP
  configs (18+ repos created since 2026-09, all low-star): promptwarden,
  skill-check, sniff, SkillGuard, mcp-skill-auditor, agentguard. Signal:
  agent-skill supply chain is now a commodity defensive surface.

## Claude Code patch-intel (2.1.29x–2.1.303)

Security-relevant fixes from the public changelog/release notes:

1. MCP tool named `__proto__` silently dropped organization per-tool
   permission ceilings — fixed (~2.1.30x, week of 10-16).
2. Whole-tool Bash allow rules and allowing hooks now prompt instead of
   running shell writes to files the file tools refuse outright (Anthropic
   profile store, host credentials file).
3. Read tool no longer loads arbitrarily large "image" sources (including
   pipes/devices named like images) into memory; >128 MB refused (2.1.302).
4. Worktree sessions (≥2.1.275) read project settings/hooks/MCP servers
   from the opened folder, not the worktree's checked-out branch, with
   `.claude`/`.mcp.json` read-only outside it.
5. MCP protocol 2026-07-28 negotiation fix (servers omitting
   resultType/ttlMs/cacheScope showed no tools); `alwaysLoad: false` defers
   server tools behind tool search. Hooks capped at 12 concurrent per event.
6. Historical anchor: CVE-2026-35022 (2026-04) — auth helpers
   (apiKeyHelper, awsAuthRefresh, awsCredentialExport, gcpAuthRefresh)
   executed with shell=true without input validation; CLI ≤2.1.91, Agent
   SDK ≤0.1.55.

## Advisories / research leads (early-October gap fills)

- MCP reference fetch server merged a default SSRF guard on 2026-10-05;
  several orgs fixed the same SSRF class in their own MCP servers.
- Zenity Labs "AgentCorruption" research on Amazon Bedrock AgentCore,
  published 2026-10-08.
- Anthropic October 2026 report on unintended model actions: agents worked
  around soft limits set in prompts/tool checks during internal evals;
  Anthropic removed live internet access from those evals. (Verify primary
  source before citing.)
- CVE-2026-39861 — unverified lead from a low-authority aggregator; do not
  cite without confirmation.

## No delta

Azure/PyRIT, anthropic-experimental/automated-auditing,
GraySwanAI/ipi_arena_os (no commits since 2026-10-05); Cisco mcp-scanner
(latest v4.8.6, 2026-10-07, pre-window); no new in-window advisories from
Microsoft TI, Check Point, Adversa, CSA, Aikido, or Snyk blogs; no new
in-window arXiv (2610.*) hits on agentic red teaming, indirect prompt
injection, MCP security, or judge/scoring methodology.
