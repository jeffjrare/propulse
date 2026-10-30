# Template: framing sheet

Frames a request in one page before any solution is chosen. The sheet asks the right question, ties the request to a
capability, declares the data involved, and opens the options without favouring any.

First piece of a chain: framing sheet → build-or-buy grid → decision note → ADR. All four carry the same ID.

Organisation configuration (decision registry, decision-rights matrix, level-1 capability map) is read from `DOSSIER.md`.
When a value is missing, use the defaults below and say so under "Confidence and open questions".

## Flow

1. Read everything provided (message, attachments, forwarded email, `raw/`, `FACTS.md`). Never ask a question the material
   already answers.
2. Ask the missing questions in one message, six at most, chosen from:
   - What problem, experienced by whom, how often?
   - What does it cost today (time, money, risk)?
   - Who would be the business owner, accountable for the value?
   - Which categories of data are involved?
   - Which systems must the solution exchange with?
   - What is the real deadline, and why?
3. If the person does not know, write "To be established". A missing answer never blocks the sheet.
4. Write the sheet from the template.
5. Check it against the checklist and fix it before handing it over.
6. Record it: `sources/DEC-YYYY-NNN-framing.md`, and a line in `DECISIONS.md` (status Open).
7. Propose the next step: the build-or-buy grid if at least two options are realistic, otherwise the decision note.

## Rules

- One page: about 500 words, not counting the options table.
- The question to decide fits in one sentence that calls for a decision: "Should we…", "Which option should we choose for…".
- You frame, you do not recommend. No option is presented as the winner in the sheet.
- The options always include: do nothing, reuse what exists, buy, build on the internal platform. An option is removed only
  with a written reason.
- No invented figures. Every figure carries its source: measured, quoted, or whose estimate.
- Never copy real personal information into the sheet (named employees, salaries, ID numbers). Describe categories of data.
- Flag by number any principle the request touches or conflicts with.
- Clear, short sentences, no vendor jargon.

## Template

```markdown
---
id: DEC-YYYY-NNN
type: framing
title: <short title>
status: Open
requester: <name>
business_owner: <name or To be established>
capability: <L1 / L2 capability or To be established>
classification: <Public | Internal | Confidential | Sensitive>
proposed_decision_maker: <role, per the matrix>
decision_due: <YYYY-MM-DD>
date: <YYYY-MM-DD>
---

# <Title>

## The question to decide
<One sentence.>

## The problem
<Who experiences it, how often, what it costs today. Three to five sentences.>

## Expected value
<What becomes possible, and how we will know it worked: one to three indicators.>

## Scope
- Users and volumes:
- Data involved and classification:
- Systems and required exchanges:
- Constraints (regulatory, timing, budget):

## Options to evaluate
| Option | In one line | Why consider it |
| --- | --- | --- |
| Do nothing | | |
| Reuse what exists | | |
| Buy | | |
| Build on the platform | | |

## Proposed criteria
<Criteria and weights proposed for the grid. They will be locked before evaluation.>

## Principles involved
<Principle number, and one line of explanation.>

## Confidence and open questions
- Framing confidence: High | Medium | Low
- Assumptions:
- Open questions:
```

## Default decision-maker and due date

Used when the organisation's matrix is not available.

| Type of decision | Decision-maker | Target delay |
| --- | --- | --- |
| Design within the platform's paved road | App team | Immediate |
| Minor deviation from a standard | App team, validated by the domain expert | 48 hours |
| Reuse, buy or build | Business owner, with architecture | 2 weeks |
| Major deviation or irreversible decision | Architecture board | 2 weeks |
| Risk acceptance | Named accountable executive | Before production |

The due date is today plus the target delay. A decision past its due date escalates one level.

## Data classification

- **Public:** already published.
- **Internal:** staff only, no serious impact if leaked.
- **Confidential:** contracts, finances, client data that is not personal information.
- **Sensitive:** personal information, payroll, health, identification data.

Sensitive data triggers a privacy impact assessment (Law 25). Add it to the open questions if it is not already planned.

## Default principles

The organisation's principles (`DOSSIER.md`) replace these. The list is in `expertise/architecture.md § Enterprise`.

## Checklist

- [ ] The question fits in one sentence and calls for a decision.
- [ ] The four options are present, or their removal is justified.
- [ ] No figure without a source.
- [ ] No real personal information.
- [ ] Capability, classification, decision-maker and due date filled in, or marked "To be established".
- [ ] The sheet fits on one page.
