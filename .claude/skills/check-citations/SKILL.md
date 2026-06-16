---
name: check-citations
description: >-
  Checks the legal citations in a draft against the Canadian Guide to Uniform
  Legal Citation (the "McGill Guide") by delegating to the citation-checker
  subagent. Use when the user asks to "check citations", "check my cites",
  "are these in McGill form", or to review case citations, neutral citations,
  pinpoints, statute references, or ibid/supra consistency in a legal draft —
  case comments, factums, journal articles, memos. Returns a per-citation
  verdict with the corrected McGill form. Does not proofread prose or verify
  what a source says.
_nf_types:
  name: text
  description: text
---

# Check Citations

A focused citation pass for legal writing. Use it before a draft goes to a journal, a court, or a colleague — anywhere the citations need to be in proper **McGill Guide** form.

## How to invoke

Delegate the work to the **citation-checker** subagent. Don't do the citation review yourself in the main thread — the subagent carries the McGill rules and the right output format.

```
Invoke citation-checker with:
- The draft (full text)
- The jurisdiction(s) cited, if not obvious (Canadian / comparative)
```

## What this skill is for

- Pre-submission check on case comments, factums, journal articles, seminar papers
- Catching wrong pinpoints (page vs paragraph), missing neutral/parallel citations, malformed statute cites
- Checking `ibid` / `supra note` discipline and short-form consistency

## What this skill is NOT for

- **Clarity, grammar, tone** → use the `proofread` skill (writing-editor)
- **Whether a case actually stands for the cited proposition, or a date is right** → use the `critical-review` skill (the fact-checker verifies substance; with A2AJ connected it checks against the real Canadian decisions)
- **US (Bluebook) or UK (OSCOLA) house styles** → this checks Canadian McGill form

## Pairs with

The natural academic sequence is **`proofread` → `check-citations`**: tidy the prose first, then check that every authority is cited correctly. Run `check-citations` again after any edit that touches a citation.

## Output

The citation-checker returns a per-citation table (as written → issue → corrected McGill form → rule) plus a list of the citations that are already correct. Present its output as-is — the author needs to see exactly which cite to fix and how.

## Reference

See [checklist.md](checklist.md) for the McGill citation rules the subagent applies.
