# 05 — Technical / Enabler Stories

*(Assignment Part 1, task 4: "Technical stories added to the backlog".)*

Technical (enabler) stories carry no direct end-user behaviour but are prerequisites for the user stories to be buildable, shippable, and operable. They are written from the **team's** point of view and sit in the same backlog, estimated with the same deck, and prioritised with MoSCoW alongside user stories. They are **front-loaded** because almost every user story depends on them (see the dependency graph in [doc 06](06-dependencies-and-rebalancing.md)).

| ID | Technical story | Rationale | MoSCoW | Pts | Depends on |
|---|---|---|---|---|---|
| **T1** | Set up a CI/CD pipeline with automated build, lint, test, and deploy stages | Fast, repeatable feedback and reliable deploys from day one so feature work ships safely. | Must | 3 | — |
| **T2** | Design & implement the core data model and migrations (Assets, Adoptions, Rotas, Reports, Users) | A shared, versioned schema underpins every epic from the map to reporting and rotas. | Must | 5 | — |
| **T3** | Build authentication and role-based authorization scaffolding (resident, volunteer, council liaison) | Adoption, escalation, and handover all need identity and permission boundaries before they can be built. | Must | 5 | T2 |
| **T4** | Implement the backend API layer exposing endpoints for assets, adoptions, rotas, and reports | A consistent API contract lets the map UI, reminders, and reporting integrate against one source of truth. | Must | 8 | T2, T3 |
| **T5** | Provision photo/media upload & object storage with thumbnailing for the condition timeline | The photo timeline needs durable image storage and resized variants to load efficiently. | Should | 5 | T4 |
| **T6** | Add observability: structured logging, error monitoring, and an automated test harness in CI | Centralised logs, alerts, and a test suite catch regressions before users and the council notice. | Should | 3 | T1 |

**Technical subtotal: 6 stories · 29 points** (Must 21, Should 8).

## Why these, and why now

- **T2 → T3 → T4** form the backbone: no user story that reads or writes data can start until the data model, auth, and API exist. They are the *critical path* through Release 1.
- **T1** (CI/CD) is first so every subsequent merge is validated automatically — cheap insurance that compounds.
- **T6** (observability) rides on T1 and is pulled into Release 1 so the team can see failures during the first feature sprints, not after.
- **T5** (media storage) is deliberately a **Should** and scheduled with E3 (condition reporting) in Release 2 — it is not needed until photos appear, so paying for it earlier would be waste.

## Mapping technical stories to the user stories they unblock

| Technical story | Unblocks (examples) |
|---|---|
| T2 Data model | US-01, US-04, US-05, US-09, US-17, US-25, US-33, US-39 … (essentially all) |
| T3 Auth & roles | US-05 (steward identity), US-21/US-26 (steward/officer-only actions), US-29 escalation, US-43 handover |
| T4 API layer | US-01, US-02, US-04, US-05 and every data-backed flow |
| T5 Media storage | US-17, US-18, US-19, US-20 (condition photos) |
| T6 Observability | underpins reliability of reminders (US-13) and scheduled jobs |
