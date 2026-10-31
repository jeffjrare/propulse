# Dossier format

The contract between the skill and the future CLI. Proposed 2026-10-29; to be confirmed on the first real engagement.

One dossier = one engagement. It **always lives in that engagement's project repository**, never in propulse: by default
`dossier/` at the repository root, which avoids clashing with any `docs/` the project already has. It is versioned with the
project.

```
dossier/
  DOSSIER.md     identity and configuration (written at opening, rarely changed)
  STATE.md       the dossier map (regenerated every turn; never edited by hand)
  FACTS.md       register of facts F-NNN
  DECISIONS.md   register of decisions DEC-YYYY-NNN
  QUESTIONS.md   register of questions Q-NNN
  sources/       Markdown sources: framing sheet, grid, note, ADR, analyses (DEC-YYYY-NNN-framing.md, …)
  deliverables/  HTML pages and their published links (one file per deliverable)
  raw/           documents received, as received (brief, answers, quotes); never modified
```

## DOSSIER.md

- **Engagement:** client (company) or internal (the user's organisation).
- **Requester, decision-maker, business owner:** roles and names.
- **Type:** product or software for a client · enterprise architecture · process optimisation · IT ecosystem review ·
  other. It selects the variant in `steps.md`.
- **Language and tone** of deliverables (default Québec French; informal or formal address of the client); default
  audience.
- **Organisation configuration** (what the templates mark "to configure"): the organisation's principles, decision-rights
  matrix, internal hourly rate, calculation horizon (3 years by default), level-1 capabilities if known. A missing value
  stays "To obtain", never invented.
- **Visual identity** of deliverables (typeface, colours); otherwise the default in `expertise/house-style.md`.
- **Naming:** every prefix used in the dossier and what it designates (e.g. `L` deliveries, `S` scenarios, `A`
  architectures, `T` tests). A prefix designates one thing only. Milestones and deliveries have a mapping table.
- **Standing statements** that would otherwise be repeated in every page (e.g. "no online payment", the AI rule).

## FACTS.md

One line per fact: `F-NNN | statement | value | state | source | date | verified`.
- **State:** FACT (observed, measured, stated by the client), INFERENCE (deduced, from what), ASSUMPTION (posited to move
  forward, to confirm), UNKNOWN (known not to be known).
- **Source:** `raw/<file>`, an answered `Q-NNN`, a dated web page, a quote.
- A fact that changes keeps its ID; the previous value moves to a history line beneath it.

## DECISIONS.md

One line per decision: `DEC-YYYY-NNN | title | status | decision-maker | due | reversibility | sources | basis`.
Statuses: Open → Under evaluation → Awaiting decision → Decided → Closed (+ Escalated), as in the templates.
"Default choice, to confirm" is an Awaiting-decision status with the recommendation recorded.

## QUESTIONS.md

One line per question: `Q-NNN | question | recipient | what it decides | status | answer (F-NNN)`.
Recipients: client, counsel, vendor, the user, us (to research). A question exists once.

## STATE.md (generated)

- Where things stand, dated, in three lines; the current step and **the next step**: why now, and the template and
  expertise modules it will load.
- Deliverables: title, current revision, published link, date, facts and decisions it cites.
- Pending decisions by due date. Open questions by recipient.
- Alerts: a deliverable citing a fact changed since its revision, a reference to a stale revision, a duplicated prefix.

## References in deliverables

A deliverable cites `F-012`, `DEC-2026-002`, `Q-031`, or another deliverable by title **and revision**. The CLI will check
that every reference resolves and that no copied value diverges from `FACTS.md`.
