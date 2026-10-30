# Decisions

<!-- Registry of architectural, product and functional decisions. An ID is a permanent citation key: never renumbered, never reused. -->

| # | Date | Scope | Topic | Decision | Status |
|---|------|-------|-------|----------|--------|
| D-single-entry-point | 2026-10-29 | ux | entry | One natural-language entry point; the system picks the step and always proposes the next; never a chain of skills to remember. | Active |
| D-built-in-practices | 2026-10-29 | prod | expertise | Good practice (architecture, product, Québec privacy, costs, AI, house style) is built in and applied by default; an instruction the user must restate is a defect to fix in a module. | Active |
| D-dossier-in-project-repo | 2026-10-29 | arch | dossiers | This repository is a public framework with no trace of any engagement; a dossier always lives in its own project's repository (`dossier/`). | Active |
| D-one-fact-one-source | 2026-10-29 | arch | facts | A fact lives once in the dossier's FACTS.md; deliverables cite it and never copy it. | Active |
| D-cli-owns-structure | 2026-10-29 | arch | cli | The CLI owns IDs, registers, cross-references and the dossier map; the model owns judgment. | Active |
| D-english-repo | 2026-10-29 | arch | language | The repository is in English; deliverables are written in the dossier's language. | Active |

---

## D-single-entry-point — the user never remembers a skill name

**Scope:** ux
**Topic:** entry
**Date:** 2026-10-29
**Status:** Active
**Basis:** mandate — the maintainer, 2026-10-29: they will not remember skill names and want the system to think about the next steps for them.

The steps (framing, grid, note, domain analysis…) are internal. The single skill triggers on its description; every turn
ends with the proposed next step.

## D-built-in-practices — good practice is never asked for twice

**Scope:** prod
**Topic:** expertise
**Date:** 2026-10-29
**Status:** Active
**Basis:** mandate — the maintainer, 2026-10-29: no restating classic good-practice instructions for architecture, product development, compliance, Québec's Law 25 or cost management.

## D-dossier-in-project-repo — the framework holds no engagement

**Scope:** arch
**Topic:** dossiers
**Date:** 2026-10-29
**Status:** Active
**Basis:** mandate — the maintainer, 2026-10-29: the repository is public; dossiers and projects are always saved in another repository, the project's own; the framework carries no trace of any other project.

## D-one-fact-one-source — FACTS.md is the only home of a figure

**Scope:** arch
**Topic:** facts
**Date:** 2026-10-29
**Status:** Active
**Basis:** failure mode — in free-form engagements the same figure drifts between deliverables and client answers are retyped into several pages (`docs/VISION.md`).

## D-cli-owns-structure — deterministic work goes to the CLI

**Scope:** arch
**Topic:** cli
**Date:** 2026-10-29
**Status:** Active
**Basis:** failure mode — colliding prefixes, unmapped numbering and references to stale revisions (`docs/VISION.md`); a script settles them once instead of the model on every turn.

## D-english-repo — English repository, deliverables in the dossier's language

**Scope:** arch
**Topic:** language
**Date:** 2026-10-29
**Status:** Active
**Basis:** mandate — the maintainer, 2026-10-29: the repository is in English.
