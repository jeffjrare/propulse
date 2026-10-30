# Decision

**As of:** 2026-10-29

The full method is in the templates: `templates/framing-sheet.md` → `templates/build-or-buy-grid.md` →
`templates/decision-note.md` (note, then ADR). This module only says how propulse holds them together.

- **One ID, DEC-YYYY-NNN**, follows a request from framing to ADR; it lives in the dossier's `DECISIONS.md`.
- **The architect frames, the decision-maker decides.** A recommendation is never written as a decision taken.
- **"Default choice, to confirm":** when work must move on, take the recommended default, record it as Awaiting decision
  with the date, and continue. The user or the decision-maker confirms or overturns it.
- **Criteria locked before scores**, scores from 1 to 5 justified by a fact, weighted total, sensitivity, and **"what would
  reverse the answer"**. Gap under 10% or low confidence: a test or a duel settles it.
- **Symmetric options:** always do nothing, reuse, buy, build (and assemble when credible); the best honest argument for each.
- **Knowledge states:** every claim that weighs in a grid is FACT, INFERENCE, ASSUMPTION or UNKNOWN, with its provenance.
  AI-drafted content stays separate from approved facts.
- **Reversibility** is noted for every decision: what it costs to get out.
- **A decision taken is never edited:** a new ADR supersedes it and cites the old one.
- **An overdue decision escalates:** the decision-note template, escalation mode.
