# Vision

Written 2026-10-29.

## Why propulse exists

Analysis engagements (a client's software project, an enterprise architecture review, a process to streamline, a
build-or-buy call) follow a recognisable path: frame the need, inventory what exists, lay out scenarios, cost them, design
the target, check compliance, decide, plan. Done by free prompting, the work can be excellent, but the person carries the
method, the dossier's memory and every good-practice instruction alone, and repeats them. A chain of separate skills does
not fix that either: nobody remembers which skill comes next.

propulse carries the method, the memory and the practices, behind a single entry point that always proposes the next step.

## Failure modes it prevents

Free-form engagements that produce a dozen deliverables over a few weeks drift in predictable ways. Each has a structural
answer:

| Failure mode | Typical symptom | propulse's answer |
|---|---|---|
| Contradicting figures | The same cost line has two different ranges in two deliverables | `FACTS.md`: one fact, one source; deliverables cite it |
| Stale cross-references | A deliverable cites revision C of another that is now at revision E | The CLI resolves every reference and lists deliverables to revise |
| Colliding or drifting IDs | One prefix means both an architecture and a test; milestones and deliveries have no mapping | The CLI assigns IDs and refuses a prefix already taken |
| Facts retyped everywhere | The client's answers copied by hand into four pages, each needing a revision | An answer is ingested once as facts; the system lists what it touches |
| No single state | Decisions scattered as "to decide" lines across documents | Decision and question registers from day one; a generated dossier map |
| Questions with no owner | The same question repeated in several deliverables | `QUESTIONS.md`: one question, one recipient, what it decides |
| Next steps that go nowhere | "This week" with no date and no follow-up | Every turn ends with the proposed next step |
| Repeated boilerplate | The same compliance note and AI rule restated in every page | Practices live in `plugin/expertise/` and are applied by default |

## V1

**One entry point** (`plugin/skills/dossier/SKILL.md`), triggered by natural language in any language the user speaks.

**One dossier per engagement**, inside that engagement's project repository (`dossier/`), never in this repository. Format:
`plugin/method/dossier-format.md`.

**A default method** (`plugin/method/steps.md`) with variants per engagement type; the next step is chosen by value,
without waiting for answers it does not depend on.

**Built-in practices** (`plugin/expertise/`) and **templates** (`plugin/templates/`): framing sheet → build-or-buy grid →
decision note → ADR, under one ID `DEC-YYYY-NNN`.

**Knowledge states.** Every claim that weighs on a recommendation is FACT, INFERENCE, ASSUMPTION or UNKNOWN, with its
provenance. A figure without a source does not exist. AI-drafted content stays visibly separate from approved facts.

**A small CLI** (Node, no dependencies) for what is deterministic: open a dossier, assign IDs, check references (facts,
decisions, revisions), generate `STATE.md`. Not built yet.

## Out of V1

- An application with its own UI.
- Sending anything to a client: the user sends.
- Document-management integrations (SharePoint, Microsoft 365): only if an engagement requires one.

## Open questions (for the user)

None. The deliverable medium is decided: `D-deliverable-medium`.
