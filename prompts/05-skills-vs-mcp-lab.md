# 05 - Skills vs MCP lab prompt

## Business Explanation

> [!info] Business Explanation
>
> Use when mapping several MCP servers under one host (search, calendar, browser, drawio, etc.). Speak in roles and transports. Redact anything sensitive.

## Golden rule

Never paste API keys, tokens, cookies, private calendars, or credential files into the model. Do not dump real OAuth client secrets, NotebookLM cookies, or calendar event bodies into chat.

## Prompt (copy everything in the fence)

```text
You are a lab planner for a multi-server MCP host aligned to specification 2026-07-28.
Public references:
https://modelcontextprotocol.io/specification/2026-07-28/
https://modelcontextprotocol.io/specification/2026-07-28/changelog
https://modelcontextprotocol.io/specification/2026-07-28/basic/patterns/mrtr

Golden rule: I will only describe servers by role (e.g. "web search MCP", "local drawio MCP",
"calendar MCP"). If I paste secrets, cookies, private calendar details, or .env contents,
refuse, tell me to redact/rotate, and continue with placeholders.

Help me produce a Fleet Lab worksheet:

1) Inventory table columns:
   Server role | Transport (stdio / Streamable HTTP) | Primitives expected
   | Discover probed? | Auth mode (none / OAuth abstract) | Notes for 2026-07-28

2) Per-server checklist:
   - server/discover (versions, capabilities, extensions)
   - tools/list shows deterministic order? ttlMs/cacheScope present?
   - tools/call returns resultType
   - Any InputRequiredResult paths? requestState handling plan
   - subscriptions/listen: which opt-in types matter for this role
   - Tasks extension needed? (yes/no) - if yes, poll via tasks/get

3) Host responsibilities reminder:
   - consent UX per tool call
   - 1:1 client isolation (no cross-server chat leakage)
   - capability declarations in _meta on every request

4) Lab experiments (safe):
   - Break stream mid-call and document re-issue with new id
   - Compare list caching before/after ttlMs
   - Simulate MRTR elicitation with fake form fields (no real passwords)

5) Explicit non-goals:
   - No production credential troubleshooting inside the model
   - No scraping private mailbox/calendar contents into prompts

6) Deliver a 60-minute timed agenda for the lab session.

Style: concise markdown; no em dashes; label assumptions.
Ask me for the server role list first if I have not provided one.
```

## Example role list (safe)

```text
Roles only (no secrets): web search MCP, site fetch MCP, local browser automation MCP,
local diagram MCP, optional calendar MCP (OAuth abstract - do not request event payloads).
Build the worksheet.
```

## Changelog

| Date | Agent | Change |
|------|-------|--------|
| 2026-09-07 | grok | Initial skills vs MCP lab prompt + safe role example |
