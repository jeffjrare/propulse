# propulse (`pro`) — CLAUDE.md

propulse is a Claude Code plugin for **analysis engagements that produce no code**: enterprise and solution architecture,
product and service design, process optimisation, IT ecosystem reviews, build-or-buy, costs and Québec compliance. `pro`
is the plugin name, the command prefix (`/pro:…`) and the name of the future CLI.

**Start here:** `docs/VISION.md` (what propulse is for and how V1 is designed), then `docs/NEXT-STEPS.md` (what to do now,
in order). Decisions already taken: `docs/DECISIONS.md`.

## What propulse is for

**The most well-informed decisions and deliverables a decision-maker actually uses**, at the lowest model cost that
delivers them. Every order propulse produces (next step, priority, rank of questions) leads with value to the client or
decision-maker. Everything else is a constraint, never a rival:

1. **The user never remembers a skill name.** One entry point, in natural language. The system finds the dossier, picks the
   step, loads the practices, and **always** ends by proposing the next step. Never "use X, then Y".
2. **Good practice is built in, never asked for again.** Architecture, product, Québec privacy law, costs, AI, house style:
   `plugin/expertise/`. If the user has to restate a good-practice instruction, that is a framework defect: fix the module.
3. **Never block.** Stop only when the answer lives in someone's head (the user, the client, counsel). A missing answer
   becomes "To be established" plus a question in the register, and work continues on everything else.
4. **One fact, one source.** A figure, a volume or a price lives once in the dossier's `FACTS.md`; deliverables cite it.
5. **Deterministic where it can be, model where it must be.** The CLI owns IDs, registers, cross-references and the dossier
   map; the model owns judgment. Work a script could settle but left to the model is paid again on every turn.
6. **Spend tokens like money.** Never re-read what already succeeded; state the bound before spending.

## Critical rules

- **This repository is public and is a framework: it holds no trace of any engagement or other project.** No client, person,
  company, deliverable link or engagement fact, ever. Examples in modules are generic and invented.
- **A dossier always lives in its own project's repository** (by default `dossier/` at that repo's root), never here.
- **Never modify `~/.claude/` directly.** Develop with `claude --plugin-dir ./plugin`.
- **Nothing is sent to a client.** propulse prepares; the user sends. Artifacts are published private.
- **No legal advice.** Every legal point becomes a question for the client's counsel.

## Languages

The repository (code, skills, modules, docs, commits) is in **English**. propulse talks to the user in the user's language,
and writes deliverables in the dossier's language (`DOSSIER.md`; default Québec French), translating template headings.

## Map

- `plugin/skills/dossier/SKILL.md`: the single entry point (V0 draft).
- `plugin/method/`: `steps.md` (the steps and how to pick the next one), `dossier-format.md` (the dossier's files, the
  future CLI's contract).
- `plugin/expertise/`: built-in practices, dated. `plugin/templates/`: framing sheet, build-or-buy grid, decision note
  (and ADR), domain analysis.
- `docs/`: VISION, NEXT-STEPS, DECISIONS.
