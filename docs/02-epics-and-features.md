# 02 — Epics & Features

The product decomposes into **6 epics → 12 features → 46 user stories** (plus 6 technical stories in [doc 05](05-technical-stories.md)). IDs defined here (`E#`, `F#.#`) are used consistently across every later artifact.

## Hierarchy at a glance

```
Kerbside
├── E1  Street Asset Map & Adoption
│   ├── F1.1  Interactive Street Asset Map
│   └── F1.2  Adoption & Stewardship Lifecycle
├── E2  Upkeep Rotas & Reminders
│   ├── F2.1  Recurring Task Rotas
│   └── F2.2  Reminders, Cover & Swaps
├── E3  Condition Reporting & Photo Timeline
│   ├── F3.1  Report a Spot's Condition with Photos
│   └── F3.2  Resolve & Escalate Reported Issues
├── E4  Council Liaison & Escalation
│   ├── F4.1  Adoption Approval Queue
│   └── F4.2  Escalations & Supply Fulfilment
├── E5  Working Bees & Volunteer Coordination
│   ├── F5.1  Event Scheduling & Resource Planning
│   └── F5.2  RSVP & Day-of Check-in
└── E6  Recognition & Clean Handover
    ├── F6.1  Upkeep Recognition & Street-Coverage Dashboard
    └── F6.2  Guided Clean Handover
```

## Epics

| Epic | Title | Summary | Primary actor(s) |
|---|---|---|---|
| **E1** | Street Asset Map & Adoption | Map-first view of geolocated micro-assets residents can browse, filter, and add from a fixed catalog; adopt solo or as co-stewards; release cleanly on moving. | Resident, Volunteer |
| **E2** | Upkeep Rotas & Reminders | Stewards define recurring upkeep tasks per spot that rotate across co-stewards; the app reminds, and allows cover/swap requests. | Steward, Co-steward |
| **E3** | Condition Reporting & Photo Timeline | Anyone reports a spot's condition with notes + before/after photos, building a dated history; stewards resolve or escalate. | Resident, Steward |
| **E4** | Council Liaison & Escalation | Optional authority queue: approve/decline adoptions, triage escalated issues, fulfil supply requests — with an auditable boundary. | Council Liaison Officer |
| **E5** | Working Bees & Volunteer Coordination | Organizers schedule one-off group events tied to spots/areas, list tools/materials; residents RSVP, get roles, and check in. | Organizer, Resident |
| **E6** | Recognition & Clean Handover | Lightweight streaks/badges + street-coverage dashboard reward sustained upkeep; a guided handover passes a spot and its history to a successor. | Steward, Volunteer |

## Features (with the stories they contain — see [doc 03](03-product-backlog.md))

| Feature | Title | Stories |
|---|---|---|
| **F1.1** | Interactive Street Asset Map | US-01, US-02, US-03, US-04 |
| **F1.2** | Adoption & Stewardship Lifecycle | US-05, US-06, US-07, US-08 |
| **F2.1** | Recurring Task Rotas | US-09, US-10, US-11, US-12 |
| **F2.2** | Reminders, Cover & Swaps | US-13, US-14, US-15, US-16 |
| **F3.1** | Report a Spot's Condition with Photos | US-17, US-18, US-19, US-20 |
| **F3.2** | Resolve & Escalate Reported Issues | US-21, US-22, US-23, US-24 |
| **F4.1** | Adoption Approval Queue | US-25, US-26, US-27, US-28 |
| **F4.2** | Escalations & Supply Fulfilment | US-29, US-30, US-31, US-32 |
| **F5.1** | Event Scheduling & Resource Planning | US-33, US-34, US-35 |
| **F5.2** | RSVP & Day-of Check-in | US-36, US-37, US-38 |
| **F6.1** | Upkeep Recognition & Street-Coverage Dashboard | US-39, US-40, US-41, US-42 |
| **F6.2** | Guided Clean Handover | US-43, US-44, US-45, US-46 |

> **Release theming** (previewed here, detailed in [doc 10](10-release-planning.md)): R1 = E1 core + foundations, R2 = E1 tail + E2 + media, R3 = E3 + E4 intake, R4 = E4 finish + E5, R5 = E6 recognition + handover, R6 = tail polish + launch.
