---
name: project-writeup
description: Turn raw project notes into a finished artifact — a STAR writeup, a portfolio card for index.html, a GitHub README, or a CV bullet. Use when Gabriel wants a project documented, improved, or published.
---

# Project writeups

## Input

Either a Notion project page (under `Carrier / Projects` or
`Carrier / My Summary / Projects that I did`), or notes he pastes. His notes are
usually Portuguese, stream-of-consciousness, and contain more detail than the polished
version — **mine them, don't just translate them.** The good material is in the
digressions: why the old thing was broken, what he tried, what he found.

## Output formats

**STAR** — the format already used in `career/projects.md`. Situation gets the *mess*
in concrete terms (what was duplicated, what wasn't parallelized, what was undocumented).
Action gets verbs and decisions. Result gets numbers or an honest "not yet measured".

**Portfolio card** — match the existing markup in `index.html` (`.glass-card`,
`.text-h2`, `.tag-tech` pills, section at `#projects`). Three to four sentences.
Tech pills from the stack list. **Only add a GitHub link if the repo is real, public,
and actually contains that project** — see `career/backlog.md` #1.

**README** — problem → architecture → stack → how to run → what's out of scope.
Mirror the structure of his own Conversational Analytics Agent spec; he already writes
excellent specs, so the README should look like a spec, not a brochure.

**CV bullet** — one line, verb-first, metric at the end if there is one. Match the
density of the existing CV bullets.

## Rules

- **Tier the evidence.** Before writing, decide: shipped and measured, shipped and
  unmeasured, or in progress. Write in the tense that matches. A design intent is
  never a result.
- **Numbers trace or they don't appear.** The verified set:
  3 hours → 5–10 minutes · 10–15 lists/month · 24+ hours → minutes · billions of rows.
  Everything else gets checked with him.
- Client stays anonymous in anything public.
- Portuguese in, English out.
- If the source page is thin (PDF RAG has a heading and nothing else; the CLV page
  contains a pasted copy of the analytics-agent text), say so and ask for the detail
  instead of inventing a project.

## After editing index.html

The site is a single file with a Tailwind CDN build. Open it and check it renders —
the `run` skill or a Playwright screenshot. Don't push a broken layout.
