# Agent-ready

Last verified: 2026-07-25

This is the single reusable playbook for making Raza's websites and public pages extremely easy for agents to discover, read, search, and use.

Point an agent here when:

- a website or set of pages is being designed or built; or
- a website is already finished and needs to become indexable, searchable, and LLM-reachable.

The agent should apply this guide to the target repository. Do not duplicate the full setup or methodology into every product repository.

## Recommended handoff

Give the agent the target repository and canonical hostname, then say:

> Use `/Users/raza/Projects/agent-ready` as the shared playbook. Make this site as agent-ready as its real product capabilities allow. Follow the target repo's own instructions, verify the live site, and do not invent endpoints or services for a score.

If the site is not deployed yet, provide its intended hostname and hosting provider when known. The agent can still build the local surfaces, but DNS and live verification remain unfinished until a canonical hostname exists.

## What belongs where

`agent-ready` owns the reusable method, applicability rules, freshness policy, source index, and pointers to proven implementations.

The target product repository owns its product truth, page content, framework integration, tests, and any small implementation files needed to expose that product to agents. It may contain a short pointer back here, but should not carry a copied version of this playbook.

Nexus owns shared operational guidance and credentials for deployment, DNS, DNSSEC, and registrar automation.

## What “agent-ready” means here

An agent-ready product exposes the real public product in machine-usable forms without inventing capabilities the product does not have.

The recurring capability groups are:

1. **Discovery and crawl policy**: a valid crawl policy, canonical URL inventory, useful HTTP discovery links, and explicit content-use preferences.
2. **Readable content**: concise machine-oriented summaries and a Markdown representation of meaningful public pages.
3. **Product capability discovery**: a small, truthful Agent Skills index describing what an agent can accomplish.
4. **In-page actions**: WebMCP tools for genuine browser-visible actions such as search, filtering, or public data retrieval.
5. **API discovery**: an API catalog and machine-readable contract only when a real public API exists.
6. **Network discovery and trust**: DNS-AID records backed by DNSSEC for public agent endpoints.
7. **Operational verification**: build checks, browser checks, live response checks, DNS validation, and a fresh readiness scan.

See `sources.md` before implementing any of these. Exact formats and detection methods change quickly.

## Applicability comes before score

Most public products benefit from discoverability, Markdown, Agent Skills, truthful WebMCP tools, and DNS discovery.

Other checks are conditional:

- Auth.md and OAuth metadata apply only when agents can genuinely register or authenticate.
- MCP Server Cards apply only when the product runs an actual remote MCP server.
- A2A Agent Cards apply only when the product exposes an actual A2A service.
- API catalogs apply only when a real API contract can be published.
- Commerce protocols apply only to real commerce flows.

A high applicable score is more valuable than a larger raw score produced by fictional endpoints.

## The working loop

Use the same loop whether agent readiness is designed in from the beginning or added after launch:

1. **Understand:** read the target instructions and identify the site's meaningful public content and actions.
2. **Baseline:** inspect the local implementation and run the current scanner against the canonical hostname when one exists.
3. **Decide:** separate generally useful capabilities from conditional ones that would be fictional or misleading.
4. **Research:** use `sources.md` and apply the freshness gate in `AGENTS.md`.
5. **Implement:** use the target framework's native static files, routes, middleware, headers, and browser APIs.
6. **Verify:** run repository checks, inspect actual HTTP behavior and browser registration, deploy through the existing provider, then scan the live hostname again.
7. **Hand off:** state the achieved level, applicable passes, intentional omissions, deployment state, and any unpushed or unrelated local changes.

## Typical implementation shape

Prefer framework-native delivery rather than a shared runtime package:

- Static metadata for crawl, summary, and skill discovery.
- Edge or framework middleware for response headers and Markdown negotiation.
- Small client-side tool registration modules for WebMCP.
- Framework route handlers where a truthful API catalog was available.
- Cloudflare HTTPS discovery records and zone-wide DNSSEC.
- Provider-specific deployment followed by live scanner and browser verification.

Use the reference implementations in `sources.md` to find the closest framework match. Reuse the architectural shape, then re-check current specifications instead of copying old schemas blindly.

## Proven reference products

| Product surface | High-level coverage |
| --- | --- |
| Plans public catalogue (`outout`) | Vite/Vercel baseline, truthful public event tools, and skill discovery |
| `raza.lol` and Bloomscroll (`pf2`) | Cloudflare Pages baseline, project discovery tools, and the desktop product's web landing content |
| Borrow | Vite/Vercel baseline, public item discovery tools, and a focused skill |
| Travel (`presence.raza.lol`) | Vite/Vercel baseline, public presence checking, and a focused skill |
| Dinner | Next.js baseline, public availability tools, a focused skill, and a truthful API catalog |
| Launched web | Next.js baseline, public launch discovery tools, a focused skill, and a truthful API catalog |
| Instagram/Bloomscroll desktop app | Not directly scored as a website; its public web surface is covered through `pf2` |

“Baseline” refers to the generally applicable capability groups above, not a permanent list of files or endpoint schemas.

## Definition of done

The work is not finished when files exist or a deployment command succeeds. Verify:

- the repository's own lint, test, and build commands;
- the rendered site in a browser with no broken primary flow;
- correct status codes, content types, `Vary` behavior, and discovery headers;
- Agent Skills integrity and truthful descriptions;
- WebMCP registration in a supported browser or the current scanner;
- authoritative DNS records plus DNSSEC validation;
- the deployed canonical hostname with a fresh readiness scan.

Then report:

- the live hostname and achieved scanner level;
- which applicable capabilities pass;
- which capabilities were intentionally omitted and why;
- whether DNS, deployment, and source control are fully complete;
- any unrelated dirty work that was preserved.

The live site is the source of truth.

## Operations boundary

Deployment, Cloudflare DNS, and Porkbun registrar credentials live in Nexus. Follow:

`/Users/raza/Projects/nexus/docs/operations/cloudflare.md`

Agents running on this computer can combine provider CLI authentication with the scoped credentials in Nexus. The deployed Nexus Worker does not automatically receive those privileges.
