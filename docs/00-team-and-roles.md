# 00 — Team & Roles

## Submission

**Submitted by: Aniket Shaw** — *solo submission.*

This is an individual submission: one person (Aniket Shaw) performed **all Scrum roles** for the exercise. The role **personas** named below are used in the [collaboration log](collaboration-log.md) and the [planning-poker session](07-estimation-planning-poker.md) to document how each role's *perspective* was applied when writing, prioritising, estimating, and planning the backlog — e.g. a back-end viewpoint sizing hidden API work, a QA viewpoint demanding testable criteria. They are perspectives, not additional team members.

> If this is submitted as part of a group, add your other team members here and reassign the personas to real people (Assignment Note 2: "Teams to clearly identify role taken by each team member").

## Roles performed (all by Aniket Shaw)

| Scrum role | Persona used in session logs | Responsibilities exercised |
|---|---|---|
| **Product Owner (PO)** | *Aarav* | Product vision & backlog; writing/accepting stories; MoSCoW priority; representing residents & council stakeholders; Definition of Done sign-off |
| **Scrum Master (SM)** | *Diya* | Facilitating planning / stand-up / review / retro; removing impediments; protecting velocity; maintaining the burn-down |
| **Developer — Frontend / Map** | *Kabir* | Map rendering, client flows (adoption, reporting, RSVP), UI accessibility |
| **Developer — Backend / API** | *Meera* | Data model, API layer, auth/roles, reminders & scheduling services |
| **Developer — QA / UX** | *Rohan* | Acceptance-test design, exploratory testing, usability & a11y review, demo prep |

## Working agreement (norms applied throughout)

- **Definition of Ready (DoR):** a story is sprint-ready when it has the user-story template filled, ≥2 acceptance criteria, a MoSCoW tag, an estimate, and no unresolved blocking dependency.
- **Definition of Done (DoD):** code merged via PR + green CI, acceptance criteria demonstrably met, unit tests for new logic, no known Sev-1/2 defects, demoed to PO.
- **Ceremonies:** Sprint Planning (start), daily 15-min stand-up, Sprint Review + Retro (end). Backlog grooming mid-sprint.
- **Capacity:** velocity **8 story points / 2-week sprint** (deliberately conservative for a part-time student carrying a full course load).
- **Estimation:** Planning Poker with the Fibonacci-style deck **{2, 3, 5, 8, 10}**, estimating from each role perspective. A story that converges on **10 is treated as too big to fit a single 8-point sprint** and must be split.
- **Decision rule:** the PO perspective decides *priority*; the development perspectives decide *estimates*; the SM perspective guards *process*.
