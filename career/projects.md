# Project base

Four tiers. Tier 1 is interview-ready. Tier 2 needs work. Tier 3 is raw.
Verified metrics are **bold**. Anything not bold is unverified — do not put it in
a CV, a post, or the site without checking with Gabriel first.

---

## Tier 1 — interview-ready, fully evidenced

### 1. Clienteling list generation (ELC, via KIS)

**Situation** — The CRM & analytics team generated monthly store-level clienteling
lists (birthday, product launch, lifecycle campaigns) through a legacy SAS process.
A master list was built in SAS, a macro split it by store, each file was password
protected, then uploaded to a platform that distributed to each store. The queries
weren't optimized, nothing was parallelized, and the same query was duplicated per
list — so one logic change had to be made in every copy. Campaign registration was a
manual web form, one submission per list.

**Task** — Rebuild the pipeline: kill the duplication, parallelize, automate the
registration insert, cut the runtime.

**Action** — Linked a GitHub branch to Databricks, one notebook per recurring list.
Reverse-engineered the SAS logic and translated it to PySpark. Built a reusable Python
class holding brand-specific query fragments as functions, so a change lands once.
Traced which table the registration web form wrote to and wrote a function that runs
checks and inserts the new list directly. Added a step that splits the master list by
store and password-protects each file with a Python Excel library. Added an automated
email with per-store counts, ready to forward to the business partner.

**Result** — **~3 hours → 5–10 minutes per list**, across **10–15 lists per month**.

**Stack** — Databricks, PySpark, Python (OOP), SAS (reverse-engineered), GitHub,
openpyxl-class Excel libs.

**Interview angles:** reverse-engineering an undocumented legacy system; the judgment
call to build a reusable class instead of 15 notebooks; finding the registration table
instead of accepting the manual form as fixed.

---

### 2. Consumer metrics — Tableau/SQL Server/Synapse → Databricks/Power BI (ELC, via KIS)

**Situation** — Dashboards ran on SQL Server stored procedures with mutable parameters
inserting into Synapse, orchestrated by Azure Data Factory, consumed by Tableau. The
queries were dense with CASE WHENs, procedures depended on each other, dynamic
parameters made the whole thing hard to read and harder to debug. Metrics were computed
*inside* Tableau rather than upstream, so dashboards were heavy. Nothing was
parallelized: the full refresh across all brands touched **billions of rows** and took
**over 24 hours**. The rest of the stack was Azure but the BI layer was Tableau. And
there was no clear metric documentation — some logic lived in the procedure, some in
the dashboard.

**Task** — Migrate to a single documented stack, establish one version of the truth,
centralize metric logic, parallelize, cut refresh time and cost.

**Action** — First drew the whole lineage as a flowchart: where data came from, where
it went, which tables fed what, and the rationale behind every metric. From that
document, built a **4-layer pipeline** in Databricks/PySpark:
1. **master** — most granular table
2. **enriched** — dimension enrichment (e.g. classifying customers high/medium/low spend)
3. **calculation** — metrics grouped by the dimensions the dashboard needs
4. **dashboard** — Power BI connected to Databricks, published to Power BI Service

Metric and enrichment logic live in functions on a Python class, so every indicator and
calculated dimension has one home. Notebooks take dynamic parameters, so Databricks Jobs
can filter the big table and parallelize the heavy calculation layer.

**Result** — Eliminated the day-long refresh (**24+ hours → minutes**). Single
documented source of truth for metric definitions. One vendor stack, lower cost.

**Stack** — Databricks, PySpark, Python (OOP), Power BI + Power BI Service, Databricks
Jobs, SQL Server + Azure Synapse (reverse-engineered), Azure Data Factory (legacy).

**Also claimed on the CV, verify before reuse:** a CUBE structure pre-aggregating KPIs,
and incremental loading with CDC + SCD Type 1 (MERGE INTO) in the gold layer. These
appear in the CV and the Notion role bullets but not in this project's own writeup —
confirm they belong to this project before putting them in the same paragraph.

**Interview angles:** the flowchart *first* — the strongest signal here is that he
documented before he built. Lead with that, not with the tech.

---

## Tier 2 — real but still in progress; the narrative is strong, the result is not yet provable

### 3. Multi-agent analytics pipeline (ELC, via KIS — in progress)

**Situation** — Business partners email the data team to request analyses for new
campaigns. They know the business rules but not code, so an analyst has to translate
each question. The back-and-forth — write the email, answer the analyst's clarifying
questions — turns an insight that should be fast into a slow one.

**Task** — Close the gap with a self-service agentic pipeline so the business partner
goes from raw data source to answer without waiting on an analyst.

**Action** — Designed a harness with three agents: a **Discovery agent** that clarifies
the business question, a **Planner agent** that lays out the analytical steps, and an
**Execution agent** that generates and runs the code. Output modes: chat answer, Word
report, or dashboard. Input: a database connection or a file such as CSV. Orchestration
in Python/FastAPI, PostgreSQL for conversation state and metadata, calling both the
Anthropic and OpenAI APIs.

**Result** — ⚠️ **Not yet measured.** The Notion STAR claims "days of asynchronous
emailing down to a single real-time interactive session" — that is the *design intent*,
not an observed outcome. Do not state it as a result. Say "designing" / "building", and
if asked for impact, give the baseline being attacked (the email round-trip) and what
will be measured.

**Stack** — Python, FastAPI, PostgreSQL, Anthropic API, OpenAI API.

> There is a much more detailed spec in Notion: `Carrier / Projects /
> 💽 [Project] - big data analytics agent` (`34b25c54-2a47-80a7-a0a3-fad4aafb0455`).
> It is a genuinely strong product spec — read-only guardrails, a SQL validation layer,
> PII classification with heuristics + regex + LLM fallback, workspace/member model,
> token-based billing, schema re-profiling with diff detection, and an explicit
> out-of-scope list. **That spec is underused.** It is better evidence of senior
> thinking than the STAR paragraph is. See `career/backlog.md` #3.

---

## Tier 3 — exists, not written up

Public/personal work, in `Carrier / Projects` and `Carrier / Contents`:

- **Research Agent** (FastAPI + Postgres, single container) — arXiv paper search:
  LLM extracts search phrases, searches arXiv, analyzes metadata and abstracts, ranks by
  relevance/recency/quality, streams progress. Notion: `2b825c54-2a47-801b-bb75-fb3cc94c82c4`
- **Agentic Loop Orchestrator** — hand-built agentic loop, no LangChain. Any LLM
  (Claude or GPT) receives a task, picks tools, executes, observes, repeats.
  https://github.com/GABRIELRANGELLEAL/AI_engineer/tree/main/api_caller_and_runtime
- **Local skill-reading agent** — the "lamplighter → electrician" post: an agent that
  reads a skill file and executes it, with his own file system, run loop and harness.
  The YAML-frontmatter-first insight for context economy came from this.
- **Jarvis — analista tributário** — `37825c54-2a47-803c-bada-e3eb4fab1bb0`
- **Bar Analytics** — `34225c54-2a47-8082-ae95-f4f17bbed1c7`
- **Marvim case** — `39c25c54-2a47-804b-81cb-fc0dbd8413cd`
- **PDF RAG** — named in Notion with no content at all
- **CLV model output into Braze** — ⚠️ the Notion page under this heading contains the
  *analytics agent* description pasted by mistake. There is no actual CLV writeup.

**None of Tier 3 is on the portfolio.** The site shows three cards, all work projects,
all linking to the same generic repo. The personal projects are the ones that are
actually public and verifiable. See `career/backlog.md` #1 and #2.
