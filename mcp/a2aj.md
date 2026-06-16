# Add A2AJ (Canadian legal data) — for the agent

**You are an AI coding agent (Claude Code or Codex). The user wants to add the
A2AJ legal-data source so they can research Canadian case law and legislation —
~250,000 court and tribunal decisions and ~10,800 laws — just by asking.** This
connects the **A2AJ** MCP server (Access to Algorithmic Justice — a free, open
project from Osgoode Hall and Lincoln Alexander law schools, an open alternative
to CanLII). It powers the `canadian-case-law` and `trade-jurisprudence` skills in
this kit, and grounds the `fact-checker` agent's verification in real decisions.

**No API key, nothing to install** — A2AJ is a **remote (hosted) MCP**: you point
the tool at a URL and it just works.

```
MCP Server URL:  https://mcp.a2aj.ca/mcp
```

Explain each step to the user in plain English, and confirm before you change a
config file. Then follow the path for their runtime.

---

## Step 1 (Claude — Desktop app or claude.ai) — add the connector

The simplest path, and the one A2AJ documents. **Requires a paid Claude account**
(Pro, Team, or Enterprise).

1. Open Claude → **Settings → Connectors**.
2. Click **Add custom connector**.
3. **Name:** `a2aj` · **MCP Server URL:** `https://mcp.a2aj.ca/mcp`
4. Save, then **start a new chat**.

Your agent now has three A2AJ tools: **search** across all decisions and
legislation, **fetch** the full text of any document by citation, and check
**coverage** across courts and date ranges.

---

## Step 2 (Claude Code — CLI) — add the server

If the user runs the Claude Code **terminal CLI**:

```bash
claude mcp add --transport http a2aj https://mcp.a2aj.ca/mcp
```

**If you get `claude: command not found`** (common when only the Claude Code
*desktop app* is installed), add it by editing `~/.claude.json` directly. Find the
top-level `"mcpServers"` object (create it if absent) and add — **without
disturbing anything else in the file**:

```json
"a2aj": {
  "type": "http",
  "url": "https://mcp.a2aj.ca/mcp"
}
```

> Verify the command/field names against your installed Claude Code version — the
> remote-MCP (`--transport http`) syntax is recent. If `mcp add` rejects it,
> fall back to the Desktop connector in Step 1.

---

## Step 3 (Codex) — note on support

A2AJ officially documents the Claude connector (Step 1) and a *programmatic*
ChatGPT path; a turn-key Codex CLI path is not published. Codex's support for
**remote (streamable-HTTP) MCP servers** depends on your version. If yours
supports it, append to `~/.codex/config.toml`:

```toml
[mcp_servers.a2aj]
url = "https://mcp.a2aj.ca/mcp"
```

Then verify with `/status` that `a2aj` loaded. **If it doesn't appear, use Claude
for the A2AJ-powered skills** — the connector path in Step 1 is the reliable one.
Don't assert a config that didn't load; tell the user plainly and switch runtimes.

---

## Step 4 — Restart, then verify

MCP servers load at **startup**, so the new tools will **not** appear in the
current session.

1. Tell the user to fully **quit and reopen** Claude / Codex (a new chat isn't
   enough in the desktop app — quit the app).
2. Then have them try:
   > *"Using A2AJ, find Supreme Court of Canada decisions on the reasonableness
   > standard since 2019 — give me three, each with its neutral citation."*
3. Confirm real decisions and **neutral citations** (e.g. `2019 SCC 65`) come
   back. Once they do, `canadian-case-law` and `trade-jurisprudence` will route
   through A2AJ automatically.

---

## Notes

- **Free, no key. Read-only.** Good habits for legal work: read-only first,
  trusted servers only — no client files, no privileged material, no secrets.
- **Scope — Canadian domestic only.** Federal courts and tribunals (SCC, FC/FCA,
  Tax Court, CITT, CHRT, RAD/RPD…) plus some provincial appellate courts. **No
  WTO, no foreign courts, no Quebec civil law**; most datasets start in the 2000s.
  The skills say this out loud — keep doing so.
- **Anti-hallucination is the point.** A2AJ exists so the agent cites decisions it
  actually fetched, instead of inventing citations from memory. Never let the
  agent "reconstruct" a citation.
- Source: <https://a2aj.ca/data/>. Working paper: <https://arxiv.org/abs/2509.13032>.
