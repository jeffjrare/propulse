# House style for deliverables

**As of:** 2026-10-31

Applies to every deliverable. Before publishing, load the medium's own guidance (the document connector's docs skill or
guide; the artifact design guidance for a page).

## Structure

- **Title block** at the top: document, **revision (letter)**, base or "compares with", audience, status, change log
  (date, change). The revision changes with every published modification.
- **Quick read / Verdict** right under the title: the answer in two or three sentences, before the detail.
- **"Where things stand (<date>)"** for a living document, and **"Linked pieces"** by ID and revision.
- Anchored table of contents, numbered sections, callout cards, status pills: Confirmed / To clarify; ok / cond. / no.
- **Questions grouped by recipient**, each with "what it decides".
- **Sources last**, each dated.

## Tone

- Clear language, short sentences, no vendor jargon. In Québec French deliverables, Québec usage.
- Address the client informally or formally per `DOSSIER.md`; neutral ("the owner") in technical analyses.
- Named vendors are **"examples to shop around, not recommendations"**, unless a grid made an explicit recommendation.
- "Not legal advice" on every legal point.

## Deliverable forms

| Form | For | Medium (`D-deliverable-medium`) |
|---|---|---|
| Document | Reading, commenting, forwarding: framing sheet, questionnaire, grid, decision note, file for counsel | Claude Docs (exports to Word or PDF) |
| Deck | Presenting to the decision-maker | Slides artifact type, if the account has one |
| Interactive page | Exploring: filters, a calculator with editable assumptions | HTML artifact |
| Clickable demo | Validating by playing | HTML artifact |
| Dossier map | Getting oriented: deliverables, decisions, questions (generated from `STATE.md`) | HTML artifact |

Everything is published **private**; the user shares. Registers and `STATE.md` are never published as such.

## Visual identity

One per dossier (`DOSSIER.md`), the same for every HTML page of the dossier.

## What is not repeated

Standing statements live once in `DOSSIER.md` or the dossier map; a page refers to them instead of restating them.
