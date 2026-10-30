# Next steps, in order

Ordered by value: something usable on the user's next real engagement (expected within days) comes before everything else.

## 1. Make the entry point usable as is (top priority)

- Review `plugin/skills/dossier/SKILL.md` against `plugin/method/`: it must work **without the CLI**, reading and writing
  the dossier's files directly (IDs: highest in the register + 1, flagged as temporary).
- Test with `claude --plugin-dir ./plugin` in a throwaway project repository created for the purpose (never this one): open
  a dossier, ingest a short brief, produce the framing sheet, end on the next step. Check that the description triggers the
  skill without naming it, in French and in English.
- Make the plugin installable everywhere through this repository's marketplace.

## 2. The first real engagement

- Run it with propulse. Each time the user has to restate an instruction, fix the expertise module or the method it
  belonged to.

## 3. The minimal CLI (Node, no dependencies)

Only what the first engagement shows to be useful, probably:
- `pro dossier init`: creates the layout in `plugin/method/dossier-format.md`.
- `pro id next <type>`: assigns F-NNN, Q-NNN, DEC-YYYY-NNN and the dossier's naming prefixes; refuses a prefix already taken.
- `pro check`: every reference (fact, decision, question, deliverable revision) resolves; lists deliverables to revise when
  a fact changes.
- `pro map`: generates `STATE.md` (step, deliverables and revisions, pending decisions, questions by recipient).

## 4. Then

- House-style HTML templates (title block, verdict box, cost calculator with editable assumptions, dossier map).
- The method variants not yet exercised (process, IT ecosystem): run them on a real engagement before expanding them.
- Verify every dated legal reference in `plugin/expertise/quebec-compliance.md` at its source.
