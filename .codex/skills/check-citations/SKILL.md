---
name: check-citations
description: Checks the legal citations in a draft against the Canadian Guide to Uniform Legal Citation (the "McGill Guide") by spawning the citation-checker subagent. Use when the user asks to "check citations", "check my cites", "are these in McGill form", or to review case citations, neutral citations, pinpoints, statute references, or ibid/supra consistency in a legal draft — case comments, factums, journal articles, memos. Returns a per-citation verdict with the corrected McGill form. Does not proofread prose or verify what a source says.
metadata:
  short-description: McGill Guide legal-citation pass
---

# Check Citations

A focused citation pass for legal writing. Use it before a draft goes to a journal, a court, or a colleague — anywhere the citations need to be in proper **McGill Guide** form.

## How to invoke

Spawn a subagent with **agent_role: "citation_checker"** (registered in `.codex/config.toml` as `[agents.citation_checker]`, persona in `.codex/agents/citation-checker.toml`). Spawn it by name; give it as the prompt:

- The draft (full text)
- The jurisdiction(s) cited, if not obvious (Canadian / comparative)

If subagent spawning is disabled in this session, follow the citation-checker persona yourself in the main thread (it's in `.codex/agents/citation-checker.toml`) — it's a single-pass task, so this works fine.

## What this skill is for

- Pre-submission check on case comments, factums, journal articles, seminar papers
- Catching wrong pinpoints (page vs paragraph), missing neutral/parallel citations, malformed statute cites
- Checking `ibid` / `supra note` discipline and short-form consistency

## What this skill is NOT for

- **Clarity, grammar, tone** → use the `proofread` skill (writing-editor)
- **Whether a case actually stands for the cited proposition, or a date is right** → use the `critical-review` skill (the fact-checker verifies substance; with A2AJ connected it checks against the real Canadian decisions)
- **US (Bluebook) or UK (OSCOLA) house styles** → this checks Canadian McGill form

## Pairs with

The natural academic sequence is **`proofread` → `check-citations`**: tidy the prose first, then check every authority is cited correctly. Run `check-citations` again after any edit that touches a citation.

## Output

The citation-checker returns a per-citation table (as written → issue → corrected McGill form → rule) plus a list of the citations already correct. Present its output as-is.

## Reference

- **`.codex/agents/citation-checker.toml`** — the canonical persona Codex loads (registered via `[agents.citation_checker]` in `config.toml`)
- [references/citation-checker.md](references/citation-checker.md) — readable copy of the same persona
- [checklist.md](checklist.md) — the McGill citation rules the subagent applies
