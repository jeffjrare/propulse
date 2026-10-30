# Solution and enterprise architecture

**As of:** 2026-10-29

Applied by default: never make the user ask for these.

## Solution

- **Orchestrate rather than replace.** The software connects the tools in place; specialists keep their trade. Replace a
  tool only when connecting it costs more.
- **One internal contract per category, one adapter per vendor.** The core talks to the contract ("telephony",
  "communications", "AI"); changing vendor changes the adapter, never the core. Adapters decide nothing: an ambiguous item
  waits in a "To sort" queue.
- **Always a no-integration mode.** Every integration has a manual fallback that works the day the vendor fails or is not
  chosen yet.
- **One case or project ID everywhere**: every event, call, email or document attaches to it.
- **Event-driven integration** (webhooks, buses) rather than polling, when the vendor allows it.
- **One master per data.** For each entity, the system of record is named; a second source of truth to synchronise is a
  cost to count, not a detail.
- **Designed for many companies, built for one.** Multi-tenancy is in the data model from the first table when resale is
  on the table; the rest waits.
- **Think in layers** (e.g. for telephony: numbers, switching, event capture, transcription, summary, AI reception) and say,
  layer by layer, what is built and what is bought. Build the glue; buy the commodity.
- **Reversible by default.** For every commitment: what the exit costs and how long it takes. No long contract while a
  decision is open.
- **Data residency.** A named hosting region for every service that receives personal information
  (`quebec-compliance.md`).
- **Decided / open.** An architecture page separates what is decided (with its DEC) from what remains open (options, for,
  against, status).

## Enterprise (internal engagements)

Default principles. The organisation's own principles (`DOSSIER.md`) replace them.

1. Capabilities first, technology second.
2. Decisions rather than documents.
3. The rule lives in the platform.
4. The paved road is the easiest road.
5. One data, one master.
6. Interfaces before integration.
7. Build what differentiates us and what connects our systems; rent the commodity.
8. Accountability is named.
9. Reversible by default.
10. AI is governed by risk, not banned.
11. Done means switched off.
12. Finish before starting.

A recommendation that conflicts with a principle names it by number, with the person who accepts the exception and its
due date.

- **Capability map:** tie every request to a capability (L1, L2) before talking about solutions.
- **Application portfolio:** for each application, the capability served, owner, master data, integrations, annual cost,
  condition; a decision per application: tolerate, invest, migrate, eliminate. "Done means switched off": retiring the old
  system and terminating its contract are part of the workstream.
- **Transform while delivering:** each roadmap step delivers value while it transforms.
