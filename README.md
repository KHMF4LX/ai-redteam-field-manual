# AI Red Team Field Manual

Battle-tested methodology for AI bug bounty and red teaming — distilled from public competition data, official arena repos, winner write-ups, vendor advisories, and the audit harnesses the labs themselves use.

**What this is:** design-level knowledge that survives. How multi-criteria judges actually score agentic attacks, which mechanism families win or die against policy-tracked tool agents, what blue-team classifiers catch, and how to hunt the agentic attack surface (indirect prompt injection, coding agents, MCP).

**What this is not:** a payload dump. No verbatim attack strings are published — mechanisms transfer, strings don't, and publishing strings mostly helps defenders. Every technique is documented at the mechanism level: procedure, hard constraints, verification signals, applicability.

## Contents

| Path | Content |
|---|---|
| `judge-mechanics/` | How arena/BB judges score: the twelve laws, the official IPI judge anatomy, and how to build a calibrated local judge mirror |
| `mechanisms/` | Mechanism family taxonomy with win/death records (Surface A: direct agentic · Surface B: indirect injection) |
| `case-studies/` | Annotated campaign logs — 13 rounds against a hard-policy target |
| `claude/` | Hunting Claude: Anthropic's own audit harness (Petri) anatomy, Claude-specific attack surface corpus, design rules |
| `tooling/` | GitHub tools that actually help, in priority tiers |
| `watchlist/` | Living SOTA sources worth monitoring |
| `REFERENCES.md` | Every source, linked |

## Ethics

- Test only what you are authorized to test: bug bounty programs, public arenas/CTFs, your own deployments.
- Coordinated disclosure. One finding, one program.
- No CBRN content. Ever. Not in scope, not as a "benchmark", not as a joke.
- Platform interactions stay manual; automation is for your own local harness only.

## Maintainer

**Sauvage.sec** — AI bug bounty hunter (HackerOne: `saevus`). PRs and issues welcome if you have public-source additions or corrections.

License: CC BY 4.0 (see `LICENSE`).