# 04 - Security review prompt

## Business Explanation

> [!info] Business Explanation
>
> Use for design reviews and capstone A3 practice. Describe architecture abstractly; never paste live credentials.

## Golden rule

Never paste API keys, tokens, cookies, private calendars, or credential files into the model.

## Prompt (copy everything in the fence)

```text
You are reviewing MCP client/server security posture against the public 2026-07-28 spec.
Primary references:
https://modelcontextprotocol.io/specification/2026-07-28/basic/patterns/mrtr
https://modelcontextprotocol.io/specification/2026-07-28/changelog
https://modelcontextprotocol.io/specification/2026-07-28/basic/authorization/client-registration#client-id-metadata-documents
https://modelcontextprotocol.io/community/feature-lifecycle

I will describe a design WITHOUT secrets. If anything looks like a key/token/cookie,
stop and ask me to redact.

Produce a security review with:

A. Trust boundaries
   - Host consent vs server isolation (1:1 client)
   - Tool annotations treated as untrusted unless server is trusted

B. Stateless / MRTR risks
   - requestState as attacker-controlled input
   - Integrity protection (HMAC/AEAD), principal binding, TTL, originating-request binding
   - Replay limits vs single-use requirements
   - Client MUST echo requestState unchanged; MUST NOT parse it

C. Transport / gateway
   - Mcp-Method / Mcp-Name consistency with body (HeaderMismatch)
   - No dependence on Mcp-Session-Id
   - Cancellation via closing Streamable HTTP response stream

D. Auth registration direction
   - Prefer Client ID Metadata Documents; DCR deprecated but may exist for compatibility
   - iss validation when present; issuer-bound credentials

E. Deprecation hygiene
   - Do not build new Roots/Sampling/Logging features
   - Logging → stderr / OpenTelemetry

F. Findings table: ID | Severity (Blocker/Major/Minor) | Spec point | Recommendation

G. Test plan: 8 concrete tests (pass/fail) including a malicious requestState tamper case.

Rules: public-spec only; no em dashes; no secret exfiltration requests; mark speculation clearly.
```

## Mini scenario (optional paste after the prompt)

```text
Synthetic design under review:
- Streamable HTTP behind a reverse proxy that routes on Mcp-Method only and ignores body
- requestState = base64(JSON({ userId, role, toolArgs })) with no MAC
- Client retries MRTR with the same JSON-RPC id
- OAuth clients registered via DCR only; iss not validated
- Server still accepts Mcp-Session-Id for "compat"
Review this design.
```

## Changelog

| Date | Agent | Change |
|------|-------|--------|
| 2026-09-07 | grok | Initial security review prompt + synthetic mini scenario |
