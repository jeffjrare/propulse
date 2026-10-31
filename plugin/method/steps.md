# The steps of an engagement

The default order. It is not a checklist: a step is skipped when the engagement does not need it, and the system says why.

## Steps

| # | Step | Produces | Done when | Template, modules |
|---|---|---|---|---|
| 0 | **Opening** | `DOSSIER.md`, brief in `raw/`, first facts and questions | Engagement type, decision-maker and request are known or "To be established". Never ends a turn: framing follows at once | `dossier-format.md` |
| 1 | **Framing** | Framing sheet DEC-YYYY-NNN; ranked pain points; questionnaire on what exists | The question to decide fits in one sentence; the questionnaire is ready to send | `templates/framing-sheet.md` |
| 2 | **Current state** | Facts: tools, processes, data, volumes, current costs | Questionnaire answers are facts; what is missing is in questions | `architecture`, `process` |
| 3 | **Vision and service** | Personas, journeys, service blueprint (stages × layers) | The decision-maker recognises their business in it | `product` |
| 4 | **Scenarios** | 3 or 4 symmetric scenarios (do nothing, reuse, buy, assemble, build), function × scenario matrix, recommendation | Each scenario has its best honest argument | `templates/build-or-buy-grid.md`, `decision`, `costs` |
| 5 | **Target architecture** | What is decided; decisions still open, with options | Every open point is a decision in the register | `architecture`, `quebec-compliance` |
| 6 | **Costs and delivery** | Deliveries, ranges over 1 and 3 years by who builds, editable assumptions, break-even | No amount without a source; "what is not counted" is written | `costs` |
| 7 | **Domain analyses** | One domain analysis per domain that deserves it | The domain has its decision in principle, and its grid if two options hold | `templates/domain-analysis.md` |
| 8 | **Compliance and legal** | Privacy impact assessments to plan; a file for counsel (questions, findings, sources) | Every legal point is a question for counsel | `quebec-compliance` |
| 9 | **Decision** | Decision note, then ADR once the decision-maker decides | The decision-maker has one page, a due date, and what happens without a decision | `templates/decision-note.md` |
| 10 | **Roadmap** | Deliveries or initiatives ordered by value, with dependencies | Each delivery is usable on its own; constraints (seasons, freezes) are in it | `product`, `costs` |
| 11 | **Demo** (when needed) | Clickable prototype with a guided tour | The decision-maker can walk a real journey unaided | `product`, `house-style` |

Each step updates `STATE.md`. Steps 2 to 8 overlap: a client's answer can reopen scenarios or costs, and the system says so.

## Variants by engagement type

- **Product or software for a client:** the full path.
- **Enterprise architecture (internal):** 0, 1, 2 as an application-portfolio and capability inventory, then target
  architecture and principles (5), transformation roadmap (10), one decision per workstream (9). The organisation's
  principles (`DOSSIER.md`) replace the defaults.
- **Process optimisation:** 0, 1, 2 as the measured current process, then target process and gains
  (`expertise/process.md`), costs (6), roadmap (10). Not yet exercised: confirm on a real engagement.
- **IT ecosystem review:** 0, 1, 2 as a full application inventory, then rationalisation (tolerate, invest, migrate,
  eliminate), target architecture (5), costs (6), roadmap (10). Not yet exercised.

## Picking the next step

In this order:
1. **What gives the decision-maker the decision they need soonest.** Value to the client comes before completeness.
2. **What does not depend on pending answers.** A question sent to the client never blocks: move on with what it does not
   condition, and record what it will reopen.
3. **What fixes an alert in `STATE.md`** (changed fact, stale reference) before adding a deliverable.
4. Then the order of the table.

The proposal fits in one line: the step, why now, what it will produce. The user says "go" or corrects it.
