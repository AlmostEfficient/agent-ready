# Current sources and reference implementations

Last verified: 2026-07-25

Use this file as an index. Fetch the linked source before implementing its capability, and apply the 14-day freshness rule in `AGENTS.md`.

## Live scanner

- [IsItAgentReady overview and API](https://isitagentready.com/llms.txt): current check categories and scan API.
- [IsItAgentReady skill index](https://isitagentready.com/.well-known/agent-skills/index.json): current skill URLs, descriptions, and content digests.
- `POST https://isitagentready.com/api/scan` with the target URL: current detection behavior.
- `POST https://isitagentready.com/api/scan` with `format: "agent"`: current combined descriptions and fix prompts.

Always fetch the relevant skill from the live index. Do not assume a previously observed skill path, description, prompt, or digest is still current.

## Primary capability sources

- Crawl policy: [RFC 9309](https://www.rfc-editor.org/rfc/rfc9309) and the [Sitemaps protocol](https://www.sitemaps.org/protocol.html).
- Content-use preferences: [Cloudflare managed robots.txt and Content Signals](https://developers.cloudflare.com/bots/additional-configurations/managed-robots-txt/).
- Markdown content negotiation: [Cloudflare Markdown for Agents](https://developers.cloudflare.com/fundamentals/reference/markdown-for-agents/).
- LLM-oriented summaries: [llms.txt proposal](https://llmstxt.org/).
- WebMCP: [current Community Group draft](https://webmachinelearning.github.io/webmcp/) and [specification repository](https://github.com/webmachinelearning/webmcp).
- Agent Skills: [current specification](https://agentskills.io/specification) and its linked documentation index.
- API discovery: [RFC 9727 API Catalog](https://www.rfc-editor.org/info/rfc9727/).
- DNS-AID: [current IETF draft](https://datatracker.ietf.org/doc/draft-mozleywilliams-dnsop-dnsaid/) and [DNS-AID project](https://dns-aid.org/).
- A2A discovery: [current A2A specification](https://a2a-protocol.org/latest/specification/) and [Agent Card discovery](https://a2a-protocol.org/latest/topics/agent-discovery/).
- Cloudflare DNS and registrar automation: `/Users/raza/Projects/nexus/docs/operations/cloudflare.md`.

## Local reference implementations

These are implementation examples, not canonical specifications:

- Vite on Vercel: `/Users/raza/Projects/outout`, `/Users/raza/Projects/borrow`, `/Users/raza/Projects/travel`.
- Vite on Cloudflare Pages: `/Users/raza/Projects/pf2`.
- Next.js route handlers and API catalog: `/Users/raza/Projects/dinner`.
- Next.js nested under another product: `/Users/raza/Projects/launched/web`.
- DNS, DNSSEC, Cloudflare, Porkbun, and deployment operations: `/Users/raza/Projects/nexus/docs/operations/cloudflare.md`.

When consulting a reference implementation:

1. Read its repository instructions.
2. Inspect its deployment provider and framework version.
3. Compare the implementation with the current external source.
4. Reuse only the pattern that still applies.

