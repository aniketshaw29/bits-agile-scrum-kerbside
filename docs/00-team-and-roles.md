# 00 — Team & Roles

> **Note:** Names are placeholders — replace with your real BITS team members and IDs before submission. The *roles* and the role rotation are the graded part (Assignment Note 2: "Teams to clearly identify role taken by each team member").

## Team roster (5 members)

| # | Member (placeholder) | Primary Scrum role | Craft / specialism | Key responsibilities |
|---|---|---|---|---|
| 1 | *Aarav* | **Product Owner (PO)** | Domain / product | Owns product vision & backlog; writes/accepts stories; sets MoSCoW priority; represents residents & council stakeholders; signs off Definition of Done |
| 2 | *Diya* | **Scrum Master (SM)** | Process / facilitation | Facilitates planning, daily stand-up, review, retro; removes impediments; protects velocity; maintains burn-down |
| 3 | *Kabir* | Developer | Frontend / Map UI | Map rendering, client flows (adoption, reporting, RSVP), accessibility of UI |
| 4 | *Meera* | Developer | Backend / API & data | Data model, API layer, auth/roles, reminders & scheduling services |
| 5 | *Rohan* | Developer | QA / UX | Acceptance-test design, exploratory testing, usability & a11y review, demo prep |

> All five are **"the Development Team"** for delivery; the PO and SM wear their Scrum hats *in addition to* contributing to build where capacity allows (common in student teams). This is stated explicitly so grading can see role ownership without pretending a 5-person class team has dedicated non-coding roles.

## Role rotation (so everyone experiences each role)

The assignment is about *experiencing* Scrum roles. We rotate the **Scrum Master** each release and share **PO proxy** duties during grooming.

| Release | Scrum Master | PO (fixed) | Notes |
|---|---|---|---|
| R1 | Diya | Aarav | Kabir shadows SM |
| R2 | Kabir | Aarav | Diya shadows PO on grooming |
| R3 | Meera | Aarav | — |
| R4 | Rohan | Aarav | — |
| R5 | Diya | Aarav | — |
| R6 | Kabir | Aarav | Launch / hand-off / wrap-up |

## Working agreement (team norms)

- **Definition of Ready (DoR):** a story is sprint-ready when it has the user-story template filled, ≥2 acceptance criteria, a MoSCoW tag, an estimate, and no unresolved blocking dependency.
- **Definition of Done (DoD):** code merged via PR + green CI, acceptance criteria demonstrably met, unit tests for new logic, no known Sev-1/2 defects, demoed to PO.
- **Ceremonies:** Sprint Planning (start), daily 15-min stand-up, Sprint Review + Retro (end). Backlog grooming mid-sprint.
- **Capacity:** velocity **8 story points / 2-week sprint** (deliberately conservative for a part-time student team carrying a full course load).
- **Estimation:** Planning Poker with the Fibonacci-style deck **{2, 3, 5, 8, 10}**. A story that converges on **10 is treated as too big to fit a single 8-point sprint** and must be split.
- **Decision rule:** PO decides *priority*; the Development Team decides *estimates*; the SM decides *process*.
