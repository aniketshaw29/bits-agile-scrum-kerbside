# 10 — Release Planning

*(Assignment Part 2, task 3: "High-level release planning assuming a quarterly release cycle (6 sprints)".)*

## Cadence

- **1 sprint = 2 weeks.** **6 sprints = 12 weeks ≈ 1 quarter = 1 release.**
- Release capacity = 6 × 8 = **48 points** (actual commit ≤ 48 after dependency-aware packing — see the [planning insight](08-sprint-backlog-and-planning.md#reconciliation--a-planning-insight)).
- Total scope **226 points → 32 sprints → 6 quarterly releases (R1–R6)**, i.e. a ~18-month roadmap. Each release ends with a **potentially shippable increment** demoed to stakeholders.

## Roadmap at a glance

| Release | Quarter | Sprints | Pts | Theme | Shippable increment |
|---|---|---|---|---|---|
| **R1** | Q1 | S1–S6 | 45 | Foundations + Map & Adopt | See, add, and adopt spots on a deployed app |
| **R2** | Q2 | S7–S12 | 46 | Stewardship in motion | Co-steward, schedule rotas, get reminders |
| **R3** | Q3 | S13–S18 | 45 | Eyes on the street | Photo condition reports + timeline; council intake |
| **R4** | Q4 | S19–S24 | 45 | Authority & events | Escalation/supply workflow + working bees |
| **R5** | Q5 | S25–S30 | 33 | Recognition & handover | Streaks, coverage dashboard, clean handovers |
| **R6** | Q6 | S31–S32 (+hardening) | 12 | Final polish & launch | Orphan-claim, anti-gaming; GA launch |

## Release detail

### R1 — Foundations + Map & Adopt  *(Q1 · 45 pts)*
- **Goal:** a resident can see the street's spots on a map, add new ones, and adopt them — on an authenticated, CI/CD-deployed app.
- **Contains:** T1, T2, T3, T4, T6 (foundations) · US-01, US-02, US-03, US-04, US-05 (E1 core).
- **Milestone / demo:** live map of one pilot street; add + adopt a planter end-to-end.
- **Why first:** the entire backbone (`T2→T3→T4→US-01`) sits here; nothing else can start until it ships.

### R2 — Stewardship in motion  *(Q2 · 46 pts)*
- **Goal:** adopted spots become *actively maintained* — co-stewarding, recurring rotas, reminders, and the media foundation for photos.
- **Contains:** US-06, US-07, US-08 (E1 tail) · US-09–US-16 (E2 full) · T5 (media storage, pulled forward per [rebalance R-2](06-dependencies-and-rebalancing.md)).
- **Milestone / demo:** a planter with two co-stewards on a weekly watering rota, reminders firing, a turn marked done.

### R3 — Eyes on the street  *(Q3 · 45 pts)*
- **Goal:** anyone can report a spot's condition with before/after photos and a timeline; stewards resolve or escalate; the council can see what's coming.
- **Contains:** US-17–US-24 (E3 full) · US-25, US-26, US-28 (E4 adoption-queue core).
- **Milestone / demo:** a "cracked planter" report with photos, resolved by a steward; a pending adoption approved by an officer.

### R4 — Authority & events  *(Q4 · 45 pts)*
- **Goal:** the resident↔authority boundary is complete (escalate, triage, supplies, audit) and neighbours can organise working bees.
- **Contains:** US-27, US-29, US-30, US-31, US-32 (E4 full) · US-33–US-37 (E5 core).
- **Milestone / demo:** escalate a blocked storm drain → officer triages to "in progress"; schedule a clean-up working bee, RSVP, and check in.

### R5 — Recognition & handover  *(Q5 · 33 pts)*
- **Goal:** sustained care is visible (streaks, badges, coverage dashboard) and stewardship passes on cleanly instead of lapsing.
- **Contains:** US-38, US-39, US-40, US-41a, US-41b (recognition + turnout) · US-43, US-44 (handover core).
- **Milestone / demo:** a street-coverage dashboard showing active vs lapsing spots; a departing steward hands a spot (with full history) to a successor who accepts.

### R6 — Final polish & launch  *(Q6 · 12 pts + hardening)*
- **Goal:** close the long tail, harden, and launch to the pilot neighbourhood.
- **Contains:** US-45, US-46 (orphan claim + handover confirmation) · US-42 (anti-gaming verification) · then hardening, accessibility audit, pilot-street beta, launch prep.
- **Milestone / demo:** GA launch on the pilot street; orphaned spots auto-surface for claiming.

## Release-planning principles applied

- **Value-first ordering:** every release is a usable product slice, front-loaded with **Must** items; **Could**s cluster in R5–R6.
- **Dependency-driven sequencing:** release order follows the critical path (E1 → E2/E3 → E4 → E5/E6), never the reverse.
- **Fixed cadence, variable scope:** the 6-sprint window is fixed; if velocity dips, the **lowest-priority Should/Could items roll to the next release** — the date holds, the scope flexes.
- **Re-planned every quarter:** the roadmap is reviewed at each release boundary; estimates and MoSCoW are refreshed as the team learns its true velocity.
