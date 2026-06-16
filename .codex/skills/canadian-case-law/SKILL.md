---
name: canadian-case-law
description: >-
  Research Canadian court and tribunal decisions through the A2AJ legal-data
  MCP. Searches, reads, and synthesises real case law — every claim tied to a
  citation it actually fetched, never invented. Use for "what have the courts
  said about X", finding leading cases, or building a cited legal read.
version: 1.0.0
---

# Canadian Case Law Research

Turn a legal question into a synthesised, *cited* read of what Canadian courts and tribunals have actually said. Not a list of links, and not from memory — every point is grounded in a decision this skill fetched and read.

This skill runs on the **A2AJ MCP** (Access to Algorithmic Justice — a free, open Canadian legal-data project). It exposes three tools — `search`, `fetch`, and `coverage` — over 27 datasets and ~250,000 decisions.

**When to use this skill:**
- "What have the courts said about [issue]?"
- "Find the leading cases on [doctrine]."
- "Has [tribunal] ever dealt with [situation]?"
- "Summarise how [court] has applied [test] over the last decade."
- "Pull the full text of [citation] and tell me what it held."

---

## Before you start: it only knows what's in A2AJ

Be honest about scope up front — this is the single most important habit.

A2AJ covers **Canadian federal courts and tribunals plus a handful of provincial appellate courts** — not everything. As of writing it includes, among others:

- **Supreme Court of Canada** (1877–present)
- **Federal Court / Federal Court of Appeal**
- **Tax Court of Canada**, **Competition Tribunal**, **Canadian International Trade Tribunal**, **Canadian Human Rights Tribunal**, the refugee divisions (RAD/RPD), and more
- Appellate courts for **BC, Ontario, Nova Scotia, Yukon** (and BC/NS superior courts)

It does **not** have: most provincial superior/lower courts, Quebec civil law, anything international (no WTO, no foreign courts), and coverage starts in the 2000s for most datasets.

**So: if you're unsure whether the relevant court or era is in scope, call `coverage` first** and say plainly what is and isn't available before you give an answer. A confident answer drawn from a court A2AJ doesn't cover is worse than saying "that's outside this dataset."

---

## How it works

1. **Scope check (when needed).** If the question touches a court, tribunal, or time period you're not sure about, call `coverage` and confirm. State any gaps to the user.

2. **Search broadly.** Use `search` with the user's terms. Use the filters — date range, dataset (court), and language — to narrow. Run a few angles rather than one query; legal language varies (e.g. "reasonableness" vs "standard of review", "dumping" vs "injury").

3. **Read the real thing.** Pick the most relevant hits and `fetch` their full text by citation (e.g. `2023 SCC 17`). **Do not synthesise from search snippets alone** — fetch and read before you characterise a holding.

4. **Synthesise.** Write the answer yourself, weighing the cases. Don't paste summaries — find the through-line, note where courts diverge, and flag what's unsettled.

---

## Citation discipline (non-negotiable)

This is the whole point of using grounded legal data instead of a chatbot's memory:

- **Every legal proposition gets a real citation** — neutral citation (e.g. `2019 SCC 65`) or statutory reference — that you actually fetched.
- **Never invent or "reconstruct" a citation.** If you can't find support, say so. Hallucinated case citations have ended careers; this skill exists partly to prevent them.
- **Quote sparingly and accurately** from the fetched text for any holding you lean on.
- If a point is your inference rather than something a case says, mark it as such.

---

## What you get

A structured, top-down read:

1. **The question** — restated plainly.
2. **Short answer** — two or three sentences for the time-poor.
3. **The cases** — the leading/relevant decisions, each with its citation and a one-line holding.
4. **The picture** — how the law has developed, where courts agree, where they split.
5. **Caveats & gaps** — what A2AJ doesn't cover here, what would need a paid database (e.g. CanLII, Lexis) or primary research.
6. **Citations** — every decision relied on, with its neutral citation.

---

## Examples

### "How has the Federal Court treated the reasonableness standard in immigration judicial reviews since Vavilov?"
Scope check (FC is covered, post-2019 is covered) → search FC for Vavilov + reasonableness + judicial review → fetch the half-dozen most-cited → synthesise the trend, noting where the Court has split. Every proposition carries a citation.

### "Has the Competition Tribunal ever blocked a merger on these grounds?"
Search the CT dataset → fetch the on-point decisions → report what it actually held, with citations, and flag that the Tribunal's full history may predate A2AJ's coverage window.

### "Pull 2023 SCC 17 and tell me what it decided."
Straight `fetch` by citation → read → plain-English summary of the holding, the reasoning, and who won, anchored in quotes.

---

## A note for the workshop

This is the *general* skill — point it at any question and it works the same way. The thing worth noticing is what's encoded in it: not legal knowledge, but a **research discipline** — check coverage, search broadly, read before you characterise, cite everything, admit the gaps. That discipline is the reusable asset. The companion **Trade Jurisprudence** skill is the same engine with one scholar's field and analytical framework baked in — that's what "encoding your expertise into a skill" looks like in practice.

---

## Pairs well with

- **Trade Jurisprudence** — the specialised sibling, tuned to Canadian trade-law and a specific analytical lens.
- **Research Brief** — when the question is broader than case law and needs web sources too.
- **Visual Explainer** — turn a line of cases into a one-page timeline or map.
