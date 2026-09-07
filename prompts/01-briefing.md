# 01 - Briefing prompt

## Business Explanation

> [!info] Business Explanation
>
> Paste the block below into a model when you need a shared overview before coding or migration planning. Public specification only.

## Golden rule

Never paste API keys, tokens, cookies, private calendars, or credential files into the model.

## Prompt (copy everything in the fence)

```text
You are briefing a competent software engineer on the Model Context Protocol (MCP)
specification revision 2026-07-28. Use only public documentation, especially:
- https://modelcontextprotocol.io/specification/2026-07-28/changelog
- https://modelcontextprotocol.io/specification/2026-07-28/
- https://modelcontextprotocol.io/specification/2026-07-28/basic/patterns/mrtr
- https://blog.modelcontextprotocol.io/posts/2026-07-28/

Constraints:
- No secrets. If I paste credentials by mistake, refuse and tell me to rotate them.
- No em dashes in your output.
- Prefer MUST/SHOULD language from the spec over marketing fluff.
- If unsure, say so and point to the closest public URL.

Deliver this structure:

1) One-paragraph headline: what changed and why (stateless core).
2) Roles refresher: Host, Client (1:1), Server, primitives (tools/resources/prompts).
3) Breaking changes table with columns: Old (≤2025-11-25 era) | New (2026-07-28) | SEP/note.
   Must include: initialize/session removal, server/discover, subscriptions/listen,
   MRTR / InputRequiredResult / resultType, Tasks moved to extension, SSE resume removal.
4) Minor but important: Mcp-Method / Mcp-Name, ttlMs / cacheScope, deterministic tools/list.
5) Deprecated (do not adopt in new code): Roots, Sampling, Logging, HTTP+SSE, DCR vs
   Client ID Metadata Documents, includeContext thisServer/allServers.
6) Feature lifecycle in one sentence (Active → Deprecated ≥12 months → Removed).
7) 5 study questions I should be able to answer after reading your briefing.

Keep the whole briefing under 700 words excluding the study questions.
```

## Changelog

| Date | Agent | Change |
|------|-------|--------|
| 2026-09-07 | grok | Initial briefing prompt |
