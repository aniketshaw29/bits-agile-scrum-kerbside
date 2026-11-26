# 01 — Product Vision

## The product: Kerbside

**Kerbside** is a map-first neighborhood app where residents **adopt and jointly look after the small shared "spots"** on their street — planters, grit bins, little free libraries, storm drains, verges, and noticeboards — turning diffuse goodwill into visible, accountable upkeep rotas.

## The problem

Small shared neighborhood assets fall into neglect because responsibility is **diffuse**: councils are stretched, and no one can tell whether a given planter, grit bin, or storm drain is being looked after, by whom, or when it was last touched. The result is work done twice, work never done, and well-meaning volunteers who quietly drop off with **no handover**. There is no durable, shared record of who stewards what and what state it is in.

## What makes it unique (Assignment Note 1: "Each idea needs to be unique")

Unlike feed-and-post neighborhood social networks, Kerbside is **asset-centric and map-first**: the unit of the product is a *physical spot*, not a person or a message. Every spot carries a persistent **stewardship record** — an upkeep rota, a dated condition-and-photo history, and a lightweight handshake with the council. It optimizes for **continuity** (adoption, clean handovers, whole-street coverage) rather than engagement, making the invisible labor of keeping a neighborhood tidy legible and shareable. The scope is narrow and concrete enough for a student team to model and demo, yet spans real multi-actor workflows (adoption, scheduling, reporting, escalation, events, recognition).

## Vision statement

> *For* residents who want their street to stay cared-for,
> *who* are let down by diffuse, invisible responsibility,
> *Kerbside* is a neighborhood-stewardship app
> *that* makes every shared spot adoptable, scheduled, and accountable on a shared map,
> *unlike* feed-based neighborhood social networks,
> *our product* is organized around the physical spot and its continuous upkeep history.

## Target users (personas)

| Persona | Who | Goal in Kerbside |
|---|---|---|
| **Resident / Steward** | A neighbor who wants to look after spots near home | Find, adopt, and keep up a spot; report conditions; hand over cleanly |
| **Community Association Volunteer / Organizer** | Coordinates neighbors | See coverage, recruit for unadopted spots, run working bees |
| **Council Liaison Officer** *(optional actor)* | Local-authority contact | Approve adoptions, handle escalations beyond residents' scope, fulfil supplies |

## Scope guardrails (v1 — kept student-sized)

1. Constrain to **one street / small neighborhood** in v1; do not model a real municipality.
2. Asset catalog is a **closed list**: planter, grit bin, little free library, storm drain, verge, noticeboard (no free-text types).
3. The **council/authority is an optional actor** backed by a simple internal queue — no integration with external municipal systems.
4. Gamification stays **deliberately lightweight** (streaks / badges / coverage %) and is pushed to the final release so it never competes with core stewardship flows.
5. **The map is the single source of truth** — every feature (adoption, rota, report, event, handover) is reachable from a spot on the map, keeping navigation and the demo narrative coherent.

## Product goals / success measures

- **Coverage:** % of mapped spots that are adopted and *actively* maintained.
- **Continuity:** % of departures that complete a clean handover (vs. silent lapse).
- **Responsiveness:** median time from condition report → resolved/escalated.
- **Participation:** working-bee check-in rate vs. RSVPs.
