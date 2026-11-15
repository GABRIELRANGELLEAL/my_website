---
name: linkedin-post
description: Write a LinkedIn post in Gabriel's voice, or rework a draft of his. Use for any LinkedIn content — a project announcement, a technical explainer, a lessons-learned post — and for LinkedIn profile copy (headline, About, experience sections).
---

# LinkedIn

## Read first

`career/voice.md` — the full voice analysis, his own generator prompt, his post
backlog and the shape his posts take. Do not write before reading it.

## His standing instruction

From Notion `Carrier / Contents`, he wrote his own generator prompt. The operative
line: **"always send me only the post, nothing else, in English."**

So: when he asks for a post, output the post. No preamble, no "here's a draft", no
three variants unless he asks for variants. If something needs flagging, put it in one
line *after* the post, clearly separated.

## His three inputs

He expects to supply: (1) past posts for voice — already captured in `career/voice.md`;
(2) material for the post — files, repo, project page; (3) a sketch of the tone he
wants. If (3) is missing, ask for it in one sentence rather than guessing the angle.

## Where material comes from

- Tier 3 projects in `career/projects.md` — the Research Agent, the Agentic Loop
  Orchestrator, the local skill-reading agent. These are public and postable.
- His post backlog in `career/voice.md` — nine ideas already listed.
- **Not** client work, unless it's abstracted past recognition. No ELC, no brand names,
  no screenshots of internal dashboards.

## Quality bar

The test is the one from his own backlog, João's tip: *the hard part is getting the AI
to talk like you would.* Before delivering, check:

- Is there a real concession in it? ("Would it be easier with LangChain? Probably.")
- Is there one specific realization, not a list of takeaways?
- Would he have admitted this much not-knowing? He should.
- Any hype words? Strip them.
- Does the closing question have a real answer someone could give?

A post that is technically accurate but sounds like a consultant has failed.

## Profile copy

Headline, About and experience bullets are a different register from posts — tighter,
third-person-ish, no metaphors. But same honesty rules: no unverified metrics, client
anonymous, and the title should match whatever is settled in `career/backlog.md` #5.

## Posting

There is no LinkedIn connector and LinkedIn's API doesn't allow third-party posting to
personal profiles. **Output is copy-paste.** Never imply the post was or can be
published automatically.
