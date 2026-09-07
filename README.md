# Learn MCP

![Learn MCP study console](assets/readme/header.jpg)

A personal, self-contained study console for the Model Context Protocol revision **2026-07-28**: host/client/server, tools/resources/prompts, Streamable HTTP, MRTR, subscriptions, Tasks extension, security habits, and a migration drill.

**Study material only.** Not an official MCP product and not affiliated with Anthropic or the MCP steering group.

**Live:** https://aaronmeis.github.io/learn-mcp/

## What's here

- `index.html` (+ `cards-data.json`, `shorts-catalog.json`, `media/`, `assets/`): the study console. Single-page app, no build step, no external dependencies beyond Google Fonts. Flashcards, quiz, glossary, popular MCP showcase, and shorts carousel. Published via GitHub Pages from the repo root.
- `assets-src/`: source outlines behind the console (Gamma deck sketch, NotebookLM week briefs).
- `prompts/`: reusable prompt templates (briefing, Socratic examiner, migration drill, security review, skills vs MCP lab).

## Running locally

Open `index.html` in any browser, or serve the folder:

```bash
npx serve .
```

## Spec pin

Primary public docs:

- https://modelcontextprotocol.io/specification/2026-07-28/
- https://modelcontextprotocol.io/specification/2026-07-28/changelog
- https://blog.modelcontextprotocol.io/posts/2026-07-28/

## Secrets

This repo contains no API keys, OAuth client secrets, cookies, or private calendars. Do not add them.
