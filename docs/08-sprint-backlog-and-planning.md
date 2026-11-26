# 08 — Sprint Backlog & Sprint Planning

*(Assignment Part 2, task 1: "Using team velocity of 8 points per sprint, do sprint planning and slot stories into sprints".)*

## Sprint model

| Parameter | Value |
|---|---|
| Velocity | **8 story points / sprint** |
| Sprint length | 2 weeks (10 working days) |
| Release window | 6 sprints = **48-point** capacity (quarterly) |
| Planning rule | A sprint commits **≤ 8 points**; a story may only be scheduled **after** every story it depends on ([doc 06](06-dependencies-and-rebalancing.md)) |

## Release 1 — detailed sprint plan (the worked exercise)

**Release 1 goal:** *"A resident can see the street's spots on a map, add new ones, and adopt them — on a deployed, authenticated app with a green CI pipeline."* This is the walking skeleton + the E1 core.

| Sprint | Sprint goal | Stories (points) | Committed |
|---|---|---|---|
| **S1** | Project skeleton, pipeline green, schema live | T1 CI/CD **(3)**, T2 Data model **(5)** | **8** |
| **S2** | Identity & visibility in place | T3 Auth & roles **(5)**, T6 Observability **(3)** | **8** |
| **S3** | One source of truth for data | T4 API layer **(8)** | **8** |
| **S4** | The map renders real spots | US-01 Browse map **(5)** | **5** |
| **S5** | Add & inspect spots | US-04 Add asset **(5)**, US-02 Spot details **(3)** | **8** |
| **S6** | First adoptions | US-05 Adopt **(5)**, US-03 Filter map **(3)** | **8** |
| | | **Release 1 total** | **45 / 48** |

### Example task breakdown — Sprint 1 (bonus: task decomposition)

Each committed story is broken into tasks with hour estimates (the basis of the [burn-down](09-burndown-chart.md)). Sprint 1 capacity ≈ **40 hours**.

| Story | Task | Est (h) |
|---|---|---|
| T1 (3 pts) | Repo + branch protection + CI skeleton | 4 |
| T1 | Lint + unit-test stage | 4 |
| T1 | Build + staging-deploy stage | 6 |
| T2 (5 pts) | ERD: Assets, Adoptions, Rotas, Reports, Users | 6 |
| T2 | Schema + migrations | 10 |
| T2 | Seed data + repository layer | 6 |
| T2 | Model unit tests | 4 |
| | **Total** | **40** |

## Full sprint slotting (all 32 sprints)

Every story from the backlog, slotted ≤ 8 points/sprint, dependency-respecting. Validated: no story appears before any of its dependencies.

### Release 1 — Foundations + Map & Adopt
| S1 | S2 | S3 | S4 | S5 | S6 |
|---|---|---|---|---|---|
| T1, T2 | T3, T6 | T4 | US-01 | US-04, US-02 | US-05, US-03 |
| 8 | 8 | 8 | 5 | 8 | 8 |

### Release 2 — Stewardship in motion (co-steward, rotas, reminders, media)
| S7 | S8 | S9 | S10 | S11 | S12 |
|---|---|---|---|---|---|
| US-06, US-07 | US-09, US-08 | US-10, US-12 | US-11, US-13 | US-14, US-15 | US-16, T5 |
| 8 | 8 | 6 | 8 | 8 | 8 |

### Release 3 — Eyes on the street (reporting & timeline + council intake)
| S13 | S14 | S15 | S16 | S17 | S18 |
|---|---|---|---|---|---|
| US-17 | US-19, US-18 | US-22, US-20 | US-23, US-21 | US-25, US-24 | US-26, US-28 |
| 5 | 8 | 8 | 8 | 8 | 8 |

### Release 4 — Authority & events (escalation/supply + working bees)
| S19 | S20 | S21 | S22 | S23 | S24 |
|---|---|---|---|---|---|
| US-29, US-27 | US-30 | US-33 | US-36, US-31 | US-34, US-32 | US-37, US-35 |
| 8 | 8 | 5 | 8 | 8 | 8 |

### Release 5 — Recognition & handover
| S25 | S26 | S27 | S28 | S29 | S30 |
|---|---|---|---|---|---|
| US-39 | US-38, US-40 | US-43 | US-41a | US-41b | US-44 |
| 5 | 8 | 5 | 5 | 5 | 5 |

### Release 6 — Final polish & launch hardening
| S31 | S32 | S33–S36 (rest of quarter) |
|---|---|---|
| US-45, US-46 | US-42 | Hardening · pilot-street beta · accessibility audit · launch prep |
| 7 | 5 | — |

## Reconciliation & a planning insight

| Release | Sprints | Points | Theme |
|---|---|---|---|
| R1 | S1–S6 | 45 | Foundations + Map & Adopt |
| R2 | S7–S12 | 46 | Stewardship in motion |
| R3 | S13–S18 | 45 | Eyes on the street |
| R4 | S19–S24 | 45 | Authority & events |
| R5 | S25–S30 | 33 | Recognition & handover |
| R6 | S31–S32 | 12 | Final polish & launch |
| **Total** | **32 sprints** | **226** | |

> **📌 Planning insight — why 32 sprints, not the naïve 226 ÷ 8 = 28?**
> The backlog skews heavily to **5-point stories**. Since `5 + 5 = 10 > 8`, two 5-pointers can't share a sprint, so many sprints carry a single 5 (fill ≈ 63%). Average fill across the plan is **≈ 7.1 / 8 (≈ 88%)**, and the "wasted" capacity stretches delivery by ~4 sprints.
> **Retro action:** split more 5-point stories into `3 + 2` during grooming to pack sprints tighter — the same lesson that forced the US-41 split, applied proactively. We flag this rather than hide it (Assignment Note 4: articulate all steps).
