# Template: decision note, ADR and escalation

You prepare the decision; the decision-maker takes it. The note names exactly what is asked, of whom, and by when. Once the
decision is taken, you record it as an ADR. If the due date passes, you prepare the escalation.

Third piece of the chain: framing sheet → build-or-buy grid → decision note → ADR. All carry the same ID.

Organisation configuration (decision-rights matrix, executive sponsor) is read from `DOSSIER.md`.

## Pick the mode

- **Mode A, prepare the note:** a sheet or a grid exists, and the decision is not taken yet.
- **Mode B, record as ADR:** the decision-maker has decided.
- **Mode C, escalate:** the due date has passed without a decision.

Infer the mode from the dossier's state; ask in one question only if it truly cannot be inferred.

## Mode A: prepare the note

1. Read the sheet and the grid with the same ID. If neither exists, frame first.
2. Identify the decision-maker and due date from the organisation's matrix, or the default matrix below.
3. Write the note from the template.
4. Check it against the checklist.
5. Record it (`sources/DEC-YYYY-NNN-note.md`, status Awaiting decision) and state the due date.

Rules:
- The architect frames, the decision-maker decides. Never write the decision as if it were taken.
- The requested decision starts with a verb: approve, fund, accept the risk, choose between, stop.
- Fund only the next step, with its proof criterion, never the whole project at once.
- Every accepted risk and every exception to a principle has a named person who accepts it and a due date.
- Always state what happens if no decision is taken by the due date.
- One page. No figure without the source carried over from the grid. No real personal information.
- If the recommendation departs from the grid's default posture, say so in one sentence with the reason.

### Note template

```markdown
---
id: DEC-YYYY-NNN
type: note
title: <title>
status: Awaiting decision
decision_maker: <name and role>
due: <YYYY-MM-DD>
escalate_to_if_overdue: <next level>
confidence: <High | Medium | Low>
date: <YYYY-MM-DD>
---

# Decision note: <title>

## Decision requested
<Verb, object, scope and amount. Example: "Approve the Build option and fund the first step: 6 weeks, two people.">

## Context
<Three sentences at most: the problem, the value, why now.>

## Options examined
| Option | 3-year cost | Time to first value | Main risks | Weighted score |
| --- | --- | --- | --- | --- |

## Recommendation
<The option, the reason in two or three sentences, the confidence level and key assumptions.>

## Risks accepted on approval
| Risk | Accepted by | Mitigation |
| --- | --- | --- |

## Exceptions to principles
| Principle | Deviation | Accepted by | Due |
| --- | --- | --- | --- |

## Next funded step and proof criterion
<What is funded now, and what must be shown to fund the rest.>

## Definition of "done" for this workstream
1. The new system is in production and actually used.
2. The integrations planned in the target architecture are in place.
3. Data is migrated, the old system is switched off and its contract terminated.
4. Access goes through the target identity provider.
5. Catalogue, maps and ADRs are up to date.
6. An operations owner is named.

## If no decision is taken by the due date
<Concrete consequence of the delay, and the level that will be seized.>

## Decision (to be filled in by the decision-maker)
- Decision:
- Conditions:
- Date:
- Decision-maker:
```

Adapt the six "done" conditions to the workstream, removing none without a written reason.

### Checklist

- [ ] The requested decision starts with a verb and fits in one or two sentences.
- [ ] The decision-maker is a named person, not a vague committee.
- [ ] The due date and escalation level are stated.
- [ ] Only the next step is funded, with its proof criterion.
- [ ] Every risk and exception has a person and a due date.
- [ ] The "Decision" section is empty.

## Mode B: record the decision as an ADR

1. Take the note with the same ID and the decision-maker's exact words.
2. Write the ADR from the template.
3. Set the status to Decided in the note and in `DECISIONS.md`.
4. If the decision differs from the recommendation, record it as is, without comment.
5. Never modify an existing ADR. To revisit a decision, create a new ADR that supersedes the old one and cites its ID.

### ADR template

```markdown
---
id: DEC-YYYY-NNN
type: adr
title: <title>
status: Decided
decision_maker: <name and role>
decided_on: <YYYY-MM-DD>
supersedes: <ID of a previous ADR, or empty>
review: <date or event that will trigger a review>
---

# ADR DEC-YYYY-NNN: <title>

## Context
<Three to five sentences.>

## Decision
<One sentence, in the decision-maker's words.>

## Options rejected and why
- <Option>: <one-line reason>

## Consequences
- What it enables:
- What it costs or constrains:
- What we commit to:

## Exceptions and due dates
<Carried over from the note.>

## Review
<When, or on what condition, to revisit this decision.>
```

## Mode C: escalate an overdue decision

Write a message of five lines at most, addressed to the next level:
1. The requested decision and its ID.
2. The missed due date and the original decision-maker.
3. The concrete impact of the delay.
4. The options and the recommendation, one line each.
5. The request: decide before a specific date.

Factual tone, no blame. Set the status to Escalated in `DECISIONS.md`. The user sends the message.

## Default matrix and escalation

Used when the organisation's matrix is not available.

| Type of decision | Decision-maker | Target delay | Escalation if overdue |
| --- | --- | --- | --- |
| Minor deviation from a standard | App team, validated by the domain expert | 48 hours | Architecture board |
| Reuse, buy or build | Business owner, with architecture | 2 weeks | Executive sponsor |
| Major deviation or irreversible decision | Architecture board | 2 weeks | Executive sponsor |
| Risk acceptance | Named accountable executive | Before production | Executive committee |
| Level-1 principles | Executive committee | Annual review | — |

## Register statuses

Open → Under evaluation → Awaiting decision → Decided → Closed. A decision can also be Escalated. "Closed" means the
workstream is done in the sense of the six conditions, not only that the decision was taken.
