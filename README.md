# propulse

A Claude Code plugin for running analysis engagements that produce no code: enterprise and solution architecture, product
and service design, process optimisation, IT ecosystem reviews, build-or-buy, costs and Québec compliance.

You talk normally ("new engagement for a company that wants to replace its CRM", "the client answered", "let's continue").
propulse finds the dossier, picks the step, applies good practice without being asked, keeps facts, decisions and open
questions in one place, and always proposes the next step.

**Status: skeleton, 2026-10-29.** See `docs/VISION.md` and `docs/NEXT-STEPS.md`.

## Install

In Claude Code:

```
/plugin install pro --marketplace jeffjrare/propulse
```

An engagement's dossier always lives in its own project's repository (`dossier/`), never in this one.

## Develop

```
claude --plugin-dir ./plugin
```

## License

MIT
