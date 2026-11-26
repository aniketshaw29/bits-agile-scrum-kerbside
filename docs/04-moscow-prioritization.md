# 04 — MoSCoW Prioritization

The PO prioritised the backlog with the team using **MoSCoW**: **M**ust-have, **S**hould-have, **C**ould-have, **W**on't-have-this-time. The guiding question for each story was *"If we shipped without this, would the product still deliver its core promise — a spot can be found, adopted, and kept up on a shared map?"*

> Totals below are the **final reconciled** numbers (after the US-41 planning-poker split in [doc 07](07-estimation-planning-poker.md)): **47 user stories + 6 technical stories = 53 backlog items = 226 points.**

## Distribution

| MoSCoW | Items | Points | % of points | Meaning for this product |
|---|---|---|---|---|
| **Must** | 26 | 124 | 55% | Core stewardship loop + the technical foundation it stands on. Without these there is no demoable product. |
| **Should** | 19 | 77 | 34% | Important and high-value, but the core loop survives a release without them. First to flex if a sprint slips. |
| **Could** | 8 | 25 | 11% | Nice-to-have polish and edge cases. Included only when capacity allows. |
| **Won't (this time)** | 5 | — | — | Explicitly out of scope for the current roadmap (see below). Recorded so they are *decided*, not forgotten. |
| **Total** | **53** | **226** | 100% | |

> Healthy shape: Musts are ~55% of effort (not 90%+), leaving real room for Shoulds/Coulds to absorb slippage — the whole point of MoSCoW.

## Must (the non-negotiable core)

The thin thread that must exist end-to-end: **see the map → add/see a spot → adopt it → schedule & do upkeep → report conditions → recognise & hand over**, standing on **auth + data model + API + CI/CD**.

| ID | Story | Pts |
|---|---|---|
| T1 | CI/CD pipeline | 3 |
| T2 | Core data model & migrations | 5 |
| T3 | Auth & role-based authorization | 5 |
| T4 | Backend API layer | 8 |
| US-01 | Browse the asset map | 5 |
| US-02 | View a spot's details & status | 3 |
| US-04 | Add a new asset | 5 |
| US-05 | Adopt a spot as sole steward | 5 |
| US-09 | Create a recurring upkeep task | 5 |
| US-10 | Rotate a task across co-stewards | 3 |
| US-13 | Get a reminder before my turn | 5 |
| US-14 | Mark my turn done | 3 |
| US-17 | Submit a condition report | 5 |
| US-19 | View a spot's condition timeline | 5 |
| US-21 | Mark a report resolved | 3 |
| US-25 | Officer adoption queue | 5 |
| US-26 | Approve / decline an adoption | 5 |
| US-29 | Escalate beyond resident scope | 5 |
| US-30 | Officer triage of escalations | 8 |
| US-33 | Schedule a working bee | 5 |
| US-36 | RSVP to an event | 3 |
| US-37 | Check in on the day | 5 |
| US-39 | Upkeep streaks | 5 |
| US-41a | Coverage dashboard (adopted/unadopted + %) | 5 |
| US-43 | Start a guided handover | 5 |
| US-44 | Review & accept a handover | 5 |

## Should (high value, deferrable)

`US-03` filter map (3) · `US-06` invite co-steward (5) · `US-07` stewardship overview (3) · `US-11` rota schedule (3) · `US-15` request cover (5) · `US-16` accept/decline cover (3) · `US-18` before/after photos (3) · `US-22` flag escalation (5) · `US-23` officer escalation list (5) · `US-27` notify adoption decision (3) · `US-31` request supplies (5) · `US-32` auditable log (5) · `US-34` tools/materials list (3) · `US-38` turnout record (5) · `US-40` milestone badges (3) · `US-45` claim orphaned spot (5) · `US-41b` lapsing detection + drill-down (5) · `T5` media upload & storage (5) · `T6` observability (3). **(19 items · 77 pts)**

## Could (polish / edge cases)

`US-08` release a spot (3) · `US-12` edit/pause task (3) · `US-20` in-app camera capture (3) · `US-24` notify reporter (3) · `US-28` filter/sort adoption queue (3) · `US-35` assign volunteer roles (3) · `US-42` anti-gaming verification (5) · `US-46` handover confirmation (2). **(8 items · 25 pts)**

## Won't (this time) — explicit exclusions

Recorded so scope decisions are visible and defensible:

| Item | Why deferred |
|---|---|
| Multi-neighborhood / city-wide rollout | v1 scope is one street (vision guardrail #1). |
| Integration with real external municipal/council IT systems | Authority is modelled as an internal queue only (guardrail #3). |
| In-app resident-to-resident chat / messaging feed | Kerbside is asset-centric, not a social feed — deliberately out of scope. |
| Native push-notification infrastructure beyond basic reminders | Reminders cover the core need; rich push is premature. |
| Public third-party API | No external consumers exist for a student-scope v1. |

## How MoSCoW drives the plan

- **Release 1** is built almost entirely from **Must** items (foundation + E1 core) — see [doc 10](10-release-planning.md).
- When a sprint is at risk, the SM/PO drop the lowest-priority **Could**, then **Should**, items first — never a **Must**.
- MoSCoW is **re-reviewed every release** at grooming; priorities are not frozen for the life of the product.
