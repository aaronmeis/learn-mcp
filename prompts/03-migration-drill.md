# 03 - Migration drill prompt

## Business Explanation

> [!info] Business Explanation
>
> Paste this to rehearse a migration plan or to critique a fictional legacy server. Keep examples synthetic.

## Golden rule

Never paste API keys, tokens, cookies, private calendars, or credential files into the model.

## Prompt (copy everything in the fence)

```text
You are running a migration drill from MCP protocol habits associated with 2025-11-25
to the 2026-07-28 specification. Public sources only:
https://modelcontextprotocol.io/specification/2026-07-28/changelog
https://modelcontextprotocol.io/specification/2026-07-28/basic/patterns/mrtr
https://modelcontextprotocol.io/specification/2026-07-28/basic/transports/streamable-http
https://modelcontextprotocol.io/specification/2026-07-28/deprecated

Scenario (synthetic - no real secrets):
A remote MCP server today:
- calls initialize / notifications/initialized
- issues Mcp-Session-Id and relies on sticky sessions
- sends elicitation/create as a server-initiated request on a held stream
- uses experimental core Tasks with blocking tasks/result and tasks/list
- uses HTTP GET + resources/subscribe for change notifications
- omits resultType
- registers OAuth clients only via DCR (RFC7591)
- sometimes resumes SSE with Last-Event-ID

Tasks for you:
1) Produce a break/fix matrix: each legacy behavior → required 2026-07-28 replacement.
2) Draft a 30/60/90-day plan (bullets) for server and client SDK work.
3) Write a sample InputRequiredResult JSON sketch (no real PII) for tools/call needing
   a form elicitation, including requestState as an opaque string placeholder.
4) Explain how Tasks should look under io.modelcontextprotocol/tasks (get/update/cancel).
5) List acceptance tests a CI job should run (discover, headers Mcp-Method/Mcp-Name,
   resultType present, list cache fields, reject session header dependency).
6) End with residual risks if requestState is not integrity-protected.

Constraints: no em dashes; no secrets; cite public URLs beside major claims.
If I paste production configs with credentials, refuse and tell me to redact/rotate.
```

## Follow-up prompt

```text
Critique my migration memo below against MCP 2026-07-28. Score Spec fidelity,
Change prioritization, Security judgment, Clarity, Evidence each 0–3 using a strict
reading of the public changelog. List factual errors first. Memo follows:


```

## Changelog

| Date | Agent | Change |
|------|-------|--------|
| 2026-09-07 | grok | Initial migration drill + memo critique follow-up |
