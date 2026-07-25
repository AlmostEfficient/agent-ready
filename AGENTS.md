# Agent-ready project guide

Last verified: 2026-07-25

This repository is a high-level router for making Raza's public products usable by agents. It should point to current sources and working examples, not freeze fast-changing specifications into long-lived instructions.

## Start here

1. Read `README.md` for the capability map and applicability rules.
2. Read `sources.md` for current external sources and local reference implementations.
3. Read a focused note only when that optional capability actually applies.
4. Read the target product's own `AGENTS.md` before changing it.

## Mandatory freshness check

Descriptions, scanner prompts, scoring methodology, detection logic, schemas, endpoint paths, browser APIs, draft specifications, and recommended implementation patterns are volatile.

Every local guidance document must include a `Last verified: YYYY-MM-DD` line. Before relying on a document:

- If `Last verified` is missing or more than 14 calendar days old, spawn one bounded research subagent with low reasoning effort.
- The subagent must fetch the live scanner description, current fix prompt or skill, and the relevant primary specification.
- The subagent must not edit files. It should return current URLs, version or publication dates when available, and a short list of material changes.
- The main agent owns interpretation, implementation, verification, and updating the local `Last verified` date.
- If subagents are unavailable, perform the same live-source check directly and state that fallback.

Even a fresh local document does not replace a live scan. Run the current scanner for the actual site before deciding what work applies.

## Source rules

- Prefer primary specifications and provider documentation.
- Use the live IsItAgentReady result and its current skill URLs for scanner behavior, descriptions, prompts, and scoring.
- Treat scanner prompts as leads, not authority. Confirm them against the linked primary source before implementation.
- When a draft, scanner, and deployed browser disagree, preserve truthful product behavior and document the discrepancy.
- Never add fake authentication, APIs, MCP servers, A2A agents, commerce protocols, or tools solely to increase a score.

## Working rules

- Preserve unrelated dirty work and commit only the intended product changes.
- Use Bun for repository scripts and one-off JavaScript.
- Implement the smallest truthful surface that helps agents use the real product.
- Verify locally, deploy through the product's existing provider, then verify the live hostname.
- Keep detailed provider credentials and domain operations in Nexus, not in this repository.
