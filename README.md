# Kerbside — Agile / Scrum Assignment (BITS)

> **Product:** *Kerbside* — a map-first neighborhood app where residents **adopt and jointly look after the small shared "spots"** on their street (planters, grit bins, little free libraries, storm drains, verges, noticeboards), turning diffuse goodwill into visible, accountable upkeep rotas.

This repository is the complete submission for the Agile/Scrum assignment (Part 1 + Part 2). Every artifact is articulated step-by-step and cross-referenced so the backlog, prioritization, estimates, sprints, burn-down, and release plan all reconcile numerically.

---

## ⚠️ Before you submit — replace the placeholder team

The team members below are **placeholders**. Swap in your real BITS team members' names and IDs in [`docs/00-team-and-roles.md`](docs/00-team-and-roles.md) (and the collaboration log) before submitting. Roles are pre-assigned to a 5-person team; adjust to your group size.

| Role | Placeholder | Responsibility |
|---|---|---|
| Product Owner (PO) | *Aarav* | Owns the vision, backlog, priorities, acceptance |
| Scrum Master (SM) | *Diya* | Facilitates ceremonies, removes blockers, guards the process |
| Developer — Frontend / Map | *Kabir* | Map UI, client flows |
| Developer — Backend / API | *Meera* | Data model, API, services |
| QA / UX | *Rohan* | Acceptance tests, usability, accessibility |

---

## How this repo maps to the assignment

### Part 1 (before mid-sem)
| # | Assignment task | Artifact |
|---|---|---|
| 1 | PO identifies product; team derives features; create Epics/Features | [`docs/01-product-vision.md`](docs/01-product-vision.md), [`docs/02-epics-and-features.md`](docs/02-epics-and-features.md) |
| 2 | User stories (template) → Product Backlog | [`docs/03-product-backlog.md`](docs/03-product-backlog.md) |
| 3 | Prioritise with MoSCoW | [`docs/04-moscow-prioritization.md`](docs/04-moscow-prioritization.md) |
| 4 | Add technical stories | [`docs/05-technical-stories.md`](docs/05-technical-stories.md) |
| 5 | Re-look & rebalance by dependency | [`docs/06-dependencies-and-rebalancing.md`](docs/06-dependencies-and-rebalancing.md) |
| 6 | Estimation — story points via planning poker (2,3,5,8,10) | [`docs/07-estimation-planning-poker.md`](docs/07-estimation-planning-poker.md) |

### Part 2 (end of semester)
| # | Assignment task | Artifact |
|---|---|---|
| 1 | Sprint planning at velocity 8 → slot stories into sprints | [`docs/08-sprint-backlog-and-planning.md`](docs/08-sprint-backlog-and-planning.md) |
| 2 | Burn-down chart for one sprint | [`docs/09-burndown-chart.md`](docs/09-burndown-chart.md) + [`assets/burndown-sprint1.svg`](assets/burndown-sprint1.svg) |
| 3 | High-level release planning (quarterly = 6 sprints) | [`docs/10-release-planning.md`](docs/10-release-planning.md) |

### Supporting (bonus — collaboration evidence)
- [`docs/00-team-and-roles.md`](docs/00-team-and-roles.md) — roles, rotation, working agreement
- [`docs/collaboration-log.md`](docs/collaboration-log.md) — ideation, backlog grooming, planning-poker sessions, task breakdown
- [`backlog/kerbside-backlog.csv`](backlog/kerbside-backlog.csv) — Jira-importable backlog (issue type, epic link, MoSCoW, points)

---

## Key numbers (all artifacts reconcile to these)

| Metric | Value |
|---|---|
| Epics | 6 |
| Features | 12 |
| User stories | 46 (47 after one planning-poker split) |
| Technical / enabler stories | 6 |
| Total committed story points | **226** |
| Team velocity | **8 points / sprint** |
| Sprint length | 2 weeks (10 working days) |
| Release cadence | Quarterly = **6 sprints = 48-point** capacity |
| Total sprints (after dependency-aware packing) | **32** |
| Releases on the roadmap | **6 (R1–R6)** |

## Suggested reading order
1. Product vision → 2. Epics & features → 3. Product backlog → 4. MoSCoW → 5. Technical stories → 6. Dependencies & rebalancing → 7. Estimation → 8. Sprint planning → 9. Burn-down → 10. Release planning. The collaboration log is best read alongside as the "how we worked" narrative.
