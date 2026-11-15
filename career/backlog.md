# Backlog — what's actually wrong, ranked

Found 2026-11-15 by auditing the CV, `index.html`, and the Notion Carrier tree against
each other. Ordered by how much damage it does. Nothing here has been changed yet.

---

## 1. 🔴 All three portfolio project cards link to the same repo

`index.html:316`, `:335`, `:351` — "View on GitHub" on *Automating Clienteling List
Generation*, *End-to-End Analytics Architecture* and the third card all point to
`github.com/GABRIELRANGELLEAL/AI_engineer`.

Two of those are proprietary client work that cannot be in a public repo. A recruiter
who clicks finds a repo unrelated to the card. This is the single most credibility-
damaging thing on the site — it reads as decoration, and it makes a reviewer doubt the
rest of the page.

**Fix:** remove the link from the two client projects (replace with a muted
"Client work — code not public" label), and point the agentic one at the real
`AI_engineer/api_caller_and_runtime` path.

---

## 2. 🔴 The public, verifiable projects are missing from the portfolio

The site shows three cards, all client work, none inspectable. Meanwhile the Research
Agent and the Agentic Loop Orchestrator are **public, on GitHub, and already written up
in his own words** — and they're nowhere on the site.

For an "AI / Data Engineer" positioning, those two are better proof than the Databricks
work, because a reviewer can actually read them.

**Fix:** add a second project row — "Personal / Open Source" — with Research Agent,
Agentic Loop Orchestrator, and the local skill-reading agent.

---

## 3. 🟡 The strongest artifact he owns is invisible

The Conversational Analytics Agent spec in Notion (`34b25c54-…`) is a serious piece of
product engineering: read-only guardrails with a SQL parser, PII classification by
heuristic + regex + LLM fallback with sensitivity tiers, workspace vs user model,
token-based billing with 80%/100% thresholds, schema re-profiling with diff detection
and a retry-once-on-schema-error path, and an explicit out-of-scope list that resolves
its own contradictions in writing.

That last part — the spec **argues with itself and resolves it** ("resolve a
contradição RLS × credencial compartilhada") — is exactly what distinguishes a senior
engineer from someone who writes specs. None of it is anywhere public.

**Fix:** it's in Portuguese and contains client context, so it can't be published
as-is. But it can become (a) a sanitized architecture section on the portfolio,
(b) the SDD / spec-driven-development LinkedIn post he already has on his backlog, and
(c) the best interview story he has for "tell me about a design decision you made".

---

## 4. 🟡 The RakBank / ELC duplication in Notion

`Carrier / My Summary` lists RakBank and ELC Companies as two roles, **same dates
(Jun 2023 – Oct 2026), identical bullets**. One is a copy-paste. Meanwhile the CV and
site say KIS/ELC "Present", and there's a `RakBank / Onboarding / Muneeb first
interview` page suggesting RakBank is new or prospective.

Until this is resolved, every CV generated from Notion is wrong.

**Fix:** needs Gabriel. Three questions: Is RakBank current, past, or a process in
flight? Did ELC end Oct 2026? Should the CV still say "Present"?

---

## 5. 🟡 CV cleanup

- `CV p.1` — "Databricks,,Azure" (double comma).
- `CV p.1` — "CICD: GitHub". GitHub alone isn't CI/CD. Either say "Version control:
  GitHub" or name the actual CI (GitHub Actions, Databricks Workflows, ADF).
- Skills block omits things he demonstrably has: Delta Lake, SQL Server, Azure Synapse,
  Azure Data Factory, BigQuery, MySQL, Metabase, Amplitude, Pandas, Plotly, SAS,
  CDC/SCD Type 1, data modeling.
- Header says "Data Scientist / Data & AI Engineer"; the site says "AI / Data Engineer";
  LinkedIn is a third thing. **Pick one.** Recommendation: **Data & AI Engineer** — it
  matches the evidence (pipelines + agents), and "Data Scientist" invites ML questions
  the portfolio can't answer (churn/forecasting are explicitly out of scope in his own
  spec).
- "AI Agentic Analytics Pipeline" is written in the present tense of a shipped thing
  ("Designing a multi-agent AI system… returning chat answers, Word reports, or
  dashboards directly to business partners"). The returning part isn't true yet.

---

## 6. 🟡 Notion says "Portfolio: loading"

`Carrier / My Summary` → Contact → "Portfolio: loading". The site exists. Put the URL
there, and on the CV header next to the LinkedIn and GitHub links — the CV currently
doesn't link the portfolio at all.

---

## 7. 🟢 LinkedIn is unreachable — by connector and by network

Connected in this workspace: **Notion**, Gmail, Google Drive, Google Sheets, GitHub.
Notion is the one that matters and it is already wired up as the source of truth.

**LinkedIn is not reachable, two ways over:**
- No usable connector exists, and LinkedIn's API doesn't permit third-party posting to
  personal profiles.
- `www.linkedin.com` doesn't resolve from this environment — the network policy denies
  the host. Allowing it wouldn't help much: LinkedIn serves a sign-in wall or a 999
  block to unauthenticated clients, so the profile still wouldn't be readable.

**This will stay copy-paste in both directions.** To work on his profile, Gabriel
pastes the current headline / About / experience text in. To publish a post, the agent
writes it and he pastes it out. Treat anything promising otherwise as wrong.

---

## 8. 🟢 Content cadence

Three posts total. The voice is good and the backlog of nine post ideas is already
written (`career/voice.md`). The gap is frequency, not quality. A standing weekly or
biweekly slot would compound; the material already exists in the Tier 3 projects.
