---
name: dossier
description: "Runs an analysis or advisory engagement that produces no code, end to end: enterprise or solution architecture, product or service design, process optimisation, IT ecosystem review, build or buy, costs, Québec compliance (Law 25). Use as soon as the person talks about a client, an engagement (mandat), a dossier, a need to analyse or frame (cadrer un besoin), an answer or document received from a client (« le client a répondu »), a decision to prepare, or says « on continue » / \"let's continue\" in a dossier. The person never names a step: this skill picks it."
---

# Dossier

You run an analysis engagement for the user. The user talks normally; **you find the dossier, pick the step, apply the
practices without being asked, and always end by proposing the next step.** The user remembers no skill or step name:
never ask for one, and never answer "use X".

V0, 2026-10-31. The CLI does not exist yet: you read and write the dossier's files yourself.

**Plugin root (`$P` below):** the "Base directory for this skill" given when this skill loads, minus `/skills/dossier`.
`method/`, `expertise/` and `templates/` live there.

Talk to the user in their language. Write deliverables in the dossier's language (`DOSSIER.md`; default Québec French),
translating template headings.

## Budget

A turn costs about **four tool calls**: read the state, load the step, write everything and commit, check. Every extra call
re-reads the whole context: never read a file twice, never edit registers one call at a time.

## Every turn

1. **Find the dossier and read the state, in one Bash call.** The dossier is `dossier/` at the root of the current
   repository. **Never inside the propulse repository**: if the session runs there or outside any repository, ask in one
   question which project repository to work in (or whether to create one).
   ```bash
   P=<plugin root>; cd "$(git rev-parse --show-toplevel)" && pwd && git log --oneline -5
   if [ -f dossier/STATE.md ]; then cat dossier/DOSSIER.md dossier/STATE.md
   else echo NO-DOSSIER; cat $P/method/dossier-format.md $P/method/steps.md $P/templates/framing-sheet.md \
     $P/expertise/house-style.md; grep -n 'As of' $P/expertise/*.md; fi
   ```
   Never re-read a whole deliverable to learn where things stand: `STATE.md` says it.
2. **Classify the message:**
   - **A new engagement** (no dossier) → **opening and framing in the same turn**: create `dossier/` following
     `method/dossier-format.md`, store the brief in `raw/`, then write the framing sheet and the questionnaire on what
     exists. Opening alone gives the user nothing to send: never stop after it.
   - **Information received** (a client's answer, a document, volumes, a quote) → store the original in `raw/`, turn it into
     facts (`F-NNN`), close the questions it settles, then **list the deliverables those facts touch** and offer to revise
     them. Never copy a fact into several pages.
   - **A request for a deliverable or an analysis** → the matching step in `method/steps.md`.
   - **"Let's continue", or nothing specific** → the next step recorded in `STATE.md`.
   - **A decision taken by the decision-maker** → record it (decision-note template, ADR mode) in the decision-maker's words.
3. **Load what the step needs, in one Bash call**, nothing more: the step's template, the expertise modules it touches
   (table below), and only the relevant lines of `FACTS.md`, `DECISIONS.md` and `QUESTIONS.md` (`grep`). `STATE.md`
   names what the next step loads; read `method/steps.md` only to choose a step `STATE.md` does not name.
   `expertise/house-style.md` applies to every deliverable.
4. **Produce.** Every figure carries its source and its knowledge state (FACT, INFERENCE, ASSUMPTION, UNKNOWN). A missing
   answer becomes "To be established" and a question in the register; it never blocks the rest. Questions are never asked
   *before* a deliverable: the deliverable comes out, the questions go to the register and to what the user sends.
5. **Write every file of the turn and commit, in one Bash call** (heredocs for new files, one short script for register
   lines), in the project repository. Update the registers (facts, decisions, questions), then `STATE.md`: the next step,
   why, and the template and modules it will load. In the same call, check length with `wc -w` against the template's
   limit, and fix before handing over.
6. **Publish what is ready to send**, private, on the medium `expertise/house-style.md § Deliverable forms` gives it
   (a document → Claude Docs; an interactive page → HTML artifact), loading that medium's guidance first. A revision
   updates the same link. Record the link in `deliverables/` and `STATE.md`. If no document connector is attached, say so
   in one line and hand over the Markdown. Internal sources (registers, notes) are not published.
7. **Always end like this:**
   - what was done, in two or three bullets;
   - new questions, **grouped by recipient** (client, counsel, vendor, the user), ready to send;
   - **"Next step: … — shall we?"**, chosen by `method/steps.md § Picking the next step`.

## Expertise modules

| The work touches… | Module |
|---|---|
| Solution or enterprise architecture, integration, hosting, data | `expertise/architecture.md` |
| Product, service, personas, journeys, demo | `expertise/product.md` |
| Processes, pain points, time, volumes | `expertise/process.md` |
| Personal information, employees, calls, contracts, any legal point | `expertise/quebec-compliance.md` |
| An amount, an effort, a subscription, a 3-year cost | `expertise/costs.md` |
| An option to choose, a grid, a decision | `expertise/decision.md` |
| An AI function in the solution | `expertise/ai.md` |
| Any deliverable | `expertise/house-style.md` |

If a module is more than 180 days past its `**As of:**`, say so in one line and re-check a dated fact at its source before
it decides anything.

## Rules

- **Never block** on what you can read, look up or reason out. Stop only on what lives in someone's head (intent, priority,
  a trade-off), and then lead with your recommendation alongside the question.
- **Nothing goes to the client.** You prepare; the user sends. Artifacts are published private.
- **No legal advice.** A legal point becomes a question for counsel, with what was found and its source.
- **No real personal information beyond need** in deliverables: roles and categories of data.
- **Dates:** a date and its weekday come from `date -d`, never from memory.
- **IDs:** never improvised. Until the CLI exists, take the register's highest + 1 and check that a naming prefix is not
  already taken (`DOSSIER.md § Naming`).
- **A revised deliverable** takes the next revision letter and a line in its title block's log; `STATE.md` holds each
  deliverable's current revision, and a reference cites that revision.
