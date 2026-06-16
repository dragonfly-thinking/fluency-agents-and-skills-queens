---
name: trade-jurisprudence
description: >-
  Research Canadian trade-law jurisprudence (CITT, Federal Court / FCA, SCC)
  through the A2AJ legal-data MCP, optionally read through the "Six Faces of
  Globalization" framework of Roberts & Lamp. A worked example of encoding a
  scholar's field and analytical lens into a skill. Use for Canadian trade
  remedies, dumping/subsidy/safeguard cases, or narrative analysis of trade law.
version: 1.0.0
---

# Trade Jurisprudence (Canadian)

A specialist version of [Canadian Case Law](../canadian-case-law/SKILL.md), tuned to **Canadian trade law** and equipped with an optional analytical lens drawn from *Six Faces of Globalization: Who Wins, Who Loses, and Why It Matters* (Anthea Roberts & Nicolas Lamp, Harvard University Press, 2021).

It runs on the same **A2AJ MCP** (`search`, `fetch`, `coverage`), but it knows where trade law lives in the data and reads cases the way a trade scholar would.

**When to use this skill:**
- "Find Canadian decisions on anti-dumping / countervailing duties / safeguards."
- "How has the CITT assessed injury to a domestic industry?"
- "Has the Federal Court of Appeal reviewed this CITT determination?"
- "Read these trade cases through the Six Faces lens — whose narrative is the tribunal adopting?"

---

## Scope — and a candid limit

This skill is built on **Canadian domestic trade law**. That's a real, deep corpus, but it is *not* the whole of trade law, and you should say so plainly when relevant.

**What A2AJ has (and this skill leans on):**
- **CITT — Canadian International Trade Tribunal** — ~5,400 decisions back to **1980**. The core: dumping, subsidies, safeguards, injury inquiries, procurement complaints, customs/tariff appeals.
- **Federal Court & Federal Court of Appeal** — judicial review of CITT and other trade measures.
- **Supreme Court of Canada** — the constitutional and leading trade cases.

**What it does NOT have — state this when it matters:**
- **No international trade law.** No WTO panel or Appellate Body reports, no NAFTA/CUSMA dispute panels, no foreign courts. A2AJ is Canadian domestic only.
- So this skill researches *how trade law is litigated inside Canada* — not the multilateral system. For a scholar whose centre of gravity is the WTO, that's the boundary to be honest about.

---

## How it works

1. **Locate the trade question in the data.** Default to searching **CITT** first, then **FC/FCA** for judicial review, then **SCC** for foundational cases. Call `coverage` if the time period is in doubt.

2. **Search with trade vocabulary.** Run several angles — the doctrine ("material injury", "normal value", "subsidy", "safeguard", "domestic industry"), the instrument (SIMA — the Special Import Measures Act), and the product/sector if given.

3. **Read the decisions.** `fetch` the full text of the most relevant determinations before characterising anything. Trade reasoning is technical — injury margins, like-goods analysis, causation — so read, don't skim snippets.

4. **Synthesise — and optionally apply the lens (below).**

---

## The Six Faces lens (optional, and the showpiece)

When the user asks for narrative or "winners and losers" analysis, read the cases through the six competing narratives Roberts & Lamp identify. The move is: *whose story is the tribunal telling when it decides who deserves protection?*

1. **Establishment** — globalisation is win-win; open trade benefits all. (Does the reasoning treat liberalised trade as the default good, protection as the exception?)
2. **Left-Wing Populist** — globalisation enriches the wealthy and corporations at workers' expense. (Is the "domestic industry" being protected framed in terms of workers and communities?)
3. **Right-Wing Populist** — the nation's working class loses to foreign competition. (Is the injury cast as harm to *the nation* against foreign producers?)
4. **Corporate Power** — large corporations capture the gains regardless of borders. (Who is the named complainant actually — workers, or a dominant domestic producer seeking shelter?)
5. **Geoeconomic** — trade as great-power rivalry; one state's gain is another's loss. (Does the case turn on a specific country of origin — China, the US — as strategic rival?)
6. **Global Threats** — shared risks (climate, pandemics, security) reframe trade. (Is the measure justified by supply-chain resilience, national security, environment?)

Output as a short **narrative map**: for each face, note whether and how the tribunal's reasoning sounds in it, with a citation and quote. The point isn't to force a case into one box — it's to surface *which globalisation story the law is quietly assuming*. Attribute the framework to Roberts & Lamp explicitly.

> Sanity-check the framing against the authors' own wording before presenting to a room that includes them — this is a faithful summary, not a substitute for the book.

---

## Citation discipline (non-negotiable)

Same rule as the general skill: **every proposition gets a real, fetched citation** (neutral citation like `2024 FCA 100`, or a SIMA section). Never invent a citation. Trade determinations are precise; quote the injury/causation findings you rely on rather than paraphrasing loosely.

---

## What you get

1. **The question** — restated plainly.
2. **Short answer** — two or three sentences.
3. **The cases** — leading CITT/FC/FCA/SCC decisions, each cited, with a one-line holding.
4. **The doctrine** — how the test (injury, dumping margin, causation, like goods) has been applied.
5. **Narrative map** *(if requested)* — the Six Faces read, attributed to Roberts & Lamp.
6. **Caveats & gaps** — the domestic-only boundary; anything outside A2AJ's window.
7. **Citations** — every decision relied on.

---

## Examples

### "How does the CITT decide whether a domestic industry has suffered material injury?"
Search CITT for injury inquiries → fetch several determinations → synthesise the framework (volume, price effects, causation), each step cited.

### "Read the recent steel safeguard cases through the Six Faces lens."
Find the safeguard decisions → fetch → narrative map: likely a tension between the Establishment narrative (trade-as-good) and Right-Wing Populist / Geoeconomic framings (protect the nation's industry against specific foreign producers) — with citations and quotes.

### "Has the FCA overturned a CITT dumping determination, and on what grounds?"
Search FCA for judicial review of CITT → fetch → report the standard of review applied and the outcome, with citations.

---

## Why this exists (the workshop point)

This skill is the same engine as **Canadian Case Law** with three things added: a *field* (Canadian trade law), a *map of where that field lives in the data* (CITT → FC/FCA → SCC), and an *analytical framework* (Six Faces). That's exactly what it means to **encode your expertise into a skill** — you're not teaching the model law, you're teaching it *how you, specifically, interrogate your corpus*. Any scholar in the room could fork this into their own field by swapping those three things.

---

## Pairs well with

- **Canadian Case Law** — the general engine this specialises.
- **Research Brief** — for the international/WTO side A2AJ can't reach.
- **Visual Explainer** — render the narrative map or a line of trade cases visually.
