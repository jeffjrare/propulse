# Next steps, in order

Ordered by value: something usable on the user's next real engagement (expected within days) comes before everything else.

## 1. Make the entry point usable as is — done 2026-10-31

Tested end to end in a throwaway project (French and English triggers, opening, client answer, "continue", publishing).
Opening now chains into framing in one session; reads and writes are batched; the framing sheet drafts to word budgets.
Measured per session: opening + framing 8 turns / $0.77 (was two sessions, 18 turns / $1.22); client answer 6 turns /
$0.54 (was 10 / $0.73); publishing a document 7 turns / $0.40. Installable: `/plugin marketplace add jeffjrare/propulse`
then `/plugin install pro@propulse`.

## 2. The first real engagement

- Run it with propulse. Each time the user has to restate an instruction, fix the expertise module or the method it
  belonged to.

## 3. The minimal CLI (Node, no dependencies)

Only what the first engagement shows to be useful. Evidence from the end-to-end test, by value:
- `pro map`: generates `STATE.md` (step, next step and what it loads, deliverables and revisions, pending decisions,
  questions by recipient). The model rewrites it by hand every turn: the surest recurring cost.
- `pro check`: every reference (fact, decision, question, deliverable revision) resolves; lists deliverables to revise
  when a fact changes; word counts against template limits. Done well by the model on a small dossier; worth it once the
  dossier holds a dozen deliverables.
- `pro id next <type>` and `pro dossier init`: no collision and a one-call opening in the test. Build only if the
  engagement shows a need.

Layout: `plugin/bin/pro` (thin shim) → `plugin/lib/cli.mjs` (`main(argv)`), register parsing in `plugin/lib/registers.mjs`;
JSON on stdout, errors as JSON on stderr with exit code 2; ES modules, Node built-ins only.

## 4. Then

- House-style HTML templates (title block, verdict box, cost calculator with editable assumptions, dossier map).
- The method variants not yet exercised (process, IT ecosystem): run them on a real engagement before expanding them.
