# Template: build-or-buy grid

Evaluates a framed request's options with the same rigour for each. Neither "buy first" nor "build first": the grid decides,
with criteria fixed before looking at the options.

Second piece of the chain: framing sheet → grid → decision note → ADR. Same ID as the sheet.

Organisation configuration is read from `DOSSIER.md`: internal hourly rate, internal platform's annual cost per application,
the team's measured AI-assisted velocity, calculation horizon (3 years). A missing value is asked for or marked "To obtain";
never invented.

## Flow

1. **Start from the framing sheet** with the same ID. If there is none, frame first, or frame in three lines: the
   question, the options, the data involved.
2. **Classify the request** to set the default posture (table below).
3. **Lock the criteria and weights with the person, before any score.** Write: "Criteria locked on <date> by <name>". Any
   later change goes to the change log, with its reason.
4. **Build the 3-year total cost** with the same structure for every option (`expertise/costs.md`).
5. **Score each option** from 1 to 5 on each criterion, with a one-line justification and its source.
6. **Compute the weighted total**, then the sensitivity: for the three heaviest criteria, move the weight 10 points each
   way. Does the winner change?
7. **Conclude** with the result, the confidence level and what would change the answer. If the gap between the top two is
   under 10% of the total, or confidence is low, propose a duel or a test.
8. **Record the grid** (`sources/DEC-YYYY-NNN-grid.md`, status Under evaluation) and propose the next step: the decision note.

## Default posture

The posture sets the starting point. The grid can overturn it, with evidence.

| Nature of the request | Examples | Default posture |
| --- | --- | --- |
| Regulated commodity | Payroll, tax, statutory accounting | Buy |
| Commodity | Email, office tools, generic tools | Buy or reuse |
| Differentiating | What sets the offer or the way of serving apart | Build on the platform |
| Glue | What connects systems or holds master data | Build (connectors, reference data) rather than add a tool |

## Default criteria

Weights are adjustable; they always total 100.

| Criterion | Question asked | Weight |
| --- | --- | --- |
| Fit to need | Does it answer the sheet's question, without workarounds? | 20 |
| 3-year total cost | What does it cost, all in? | 15 |
| Integration and data | Does it follow the integration rules: one master per data, exchanges by API or events, central identity? | 15 |
| Time to first value | When do users get a first real benefit? | 10 |
| Differentiation and control | Do we keep control of what sets us apart and of its roadmap? | 10 |
| Reversibility | What would it cost to exit, and how long would it take? | 10 |
| Security and compliance | Is there a pre-approved pattern? Is sensitive data involved? | 10 |
| Operations and maintenance | Who runs it, with what effort, at what service level? | 10 |

Score scale: 1 = blocking, 2 = weak, 3 = acceptable with reservations, 4 = good, 5 = excellent.

## 3-year total cost

Same structure for every option. Each line carries an amount and its source: quote, measurement, or whose estimate. An
unknown line is marked "To obtain", and confidence drops.

| Item | Reuse | Buy | Build |
| --- | --- | --- | --- |
| Licences or subscriptions, with expected user growth | | | — |
| Implementation or first version | | | |
| Integrations, one line per required exchange | | | |
| Customisation and configuration | | | |
| Data migration | | | |
| Operations and support | | | |
| Evolution over 3 years | | | |
| Share of the internal platform | — | — | |
| Training and change support | | | |
| Exit: migration to another solution | | | |
| Internal time (hours × hourly rate) | | | |
| **3-year total** | | | |

Symmetry rules:
- **On the buy side**, always count integrations and exit. They are the two most often forgotten items.
- **On the build side**, estimate the first version from the team's measured AI-assisted velocity, not historical
  estimates. Always count operations and evolution.
- A vendor's claim is marked "according to the vendor" until verified.

## Rules

- Present the best honest argument for each option. Never weaken one to favour another.
- Criteria are locked before scores. If asked to change a weight after seeing the scores, do it, log it, and show both
  results.
- Separate facts from judgments. A score is a judgment; its justification cites a fact.
- The grid recommends; it does not decide. The decision belongs to the named decision-maker, through the decision note.
- Never copy real personal information into the grid.

## The duel

When the gap is thin or confidence low, propose a duel instead of a debate:
- a team of two or three people, at least one from security or infrastructure;
- three weeks at most for a usable version on the internal platform, against a vendor trial or demo;
- the same locked criteria, a demo to the business owner, then the results carried into the grid.

For a smaller engagement, a scripted test with a pass/fail protocol plays the same role.

## Output template

```markdown
---
id: DEC-YYYY-NNN
type: grid
title: <sheet's title>
status: Under evaluation
criteria_locked_on: <YYYY-MM-DD>
criteria_locked_by: <name>
confidence: <High | Medium | Low>
date: <YYYY-MM-DD>
---

# Build-or-buy grid: <title>

## Nature of the request and default posture
<Class, posture, one sentence of justification.>

## Locked criteria
<Criteria and weights table.>

## 3-year total cost
<Cost table, with each line's source.>

## Scores
| Criterion | Weight | Reuse | Buy | Build |
| --- | --- | --- | --- | --- |
| <criterion> | <weight> | <score>: <justification and source> | | |
| **Weighted total (out of 5)** | 100 | | | |

## Result
<Leading option, gap to the next, in two or three sentences.>

## Sensitivity
<Does the result hold when the three main weights move 10 points?>

## Confidence and what would change the answer
<Confidence level, figures to obtain, assumptions that would flip the result.>

## Proposed duel or test
<Only if the gap is under 10% or confidence is low.>

## Change log
<Date, change, reason, author.>
```

Weighted total: the sum of (score × weight) divided by 100, which gives a score out of 5.
