# Collaboration Log

*(Assignment Note 5: "Additional points will be given for showing the collaboration sessions / ideation / group activities including planning poker, task breakdown etc.")*

This log is the "how we worked" record. Dates are illustrative — adjust to your real session calendar. Each session notes which role perspective facilitated, per our [working agreement](00-team-and-roles.md).

> **Solo submission by Aniket Shaw.** The persona names below (*Aarav, Diya, Kabir, Meera, Rohan*) are **role perspectives** one person adopted to work through each Scrum role — not separate team members. See [doc 00](00-team-and-roles.md).

---

## Session 1 — Ideation workshop *(product selection)*
**Format:** divergent brainstorm → dot-vote → decision. **Facilitator:** Diya (SM). **Timebox:** 60 min.

The PO (Aarav) framed the brief: *a unique product, rich enough for ~25+ stories, demoable by a student team.* Each member brought one concept from a different domain so we wouldn't converge too early:

| Candidate | Domain | One-line pitch | Verdict |
|---|---|---|---|
| **Crateful** | Circular economy | Shared reusable-crate pool for food/bev SMEs with deposit tracking | Original & rich, but deposit-netting + return routing are hard to demo |
| **Baton (care)** | Caregiving | Shift-based care journal for families rotating care of a dependent | Strong, but leans "structured journal" |
| **Baton (clubs)** | Education | Role-anchored knowledge-handover for student clubs across turnover | Good, overlaps the care variant |
| **Kerbside** ✅ | Civic / neighbourhood | Map-first adoption & upkeep of shared street "spots" | **Chosen** |

**Decision & rationale:** Kerbside won on **uniqueness** (asset-centric & map-first — the unit is a *physical spot*, not a feed/person), **demoability** (a map + pins + adoption is concrete and visual), and **richness** (6 natural epics, 4 distinct actors). We sharpened scope: one street in v1, a **closed asset catalog**, council as an **optional** actor, gamification last, and **the map as the single source of truth**. *(Full rationale in [doc 01](01-product-vision.md).)*

---

## Session 2 — Epic & feature breakdown
**Facilitator:** Aarav (PO). The team mapped Kerbside into **6 epics → 12 features**, each tied to an actor and a user outcome, and agreed the ID scheme (`E#`, `F#.#`, `US-##`, `T#`) used across all artifacts. Output: [doc 02](02-epics-and-features.md).

---

## Session 3 — Story-writing workshop
**Format:** split into pairs, one epic each, then cross-review. Everyone wrote stories in the **"As a… I want… so that…"** template with ≥2 acceptance criteria (Given/When/Then). Rohan (QA) reviewed every card for *testable* criteria and flagged vague ones for rewrite. Output: the 46-story [product backlog](03-product-backlog.md).

---

## Session 4 — MoSCoW prioritisation
**Facilitator:** Aarav (PO), with team challenge. We walked every story against the question *"does the core loop survive without it?"* Debated items: US-06 co-stewarding (team pushed Must → PO held **Should**: a solo steward is a valid MVP); US-30 officer triage (kept **Must** — the authority boundary is a headline feature). We deliberately recorded 5 **Won't-this-time** items so exclusions were *decided, not forgotten*. Output: [doc 04](04-moscow-prioritization.md).

---

## Session 5 — Technical stories + dependency rebalancing
The team added **6 technical/enabler stories** (CI/CD, data model, auth, API, media, observability) to the backlog and ranked the backbone **Must**. We then drew the dependency graph and found and fixed **7 issues** — most importantly:
- a **Must story (US-17) blocked by a Should technical story (T5)** → pulled T5 into R2;
- a **forward dependency** (Could US-35 needing Must US-36) → reordered the build sequence.
Outputs: [doc 05](05-technical-stories.md), [doc 06](06-dependencies-and-rebalancing.md).

---

## Session 6 — Planning Poker *(group activity)*
**Facilitator:** Diya (SM). **Estimators:** Kabir, Meera, Rohan, Diya. **PO:** Aarav (presents & clarifies, does not vote). **Deck:** `2, 3, 5, 8, 10`.

We fixed three **anchors** (US-46 = 2, US-01 = 5, US-30 = 8), then estimated all stories, re-voting on any spread. Highlights (full vote tables in [doc 07](07-estimation-planning-poker.md)):
- **US-01** 5·5·8·3 → discussion (geolocation vs clustering) → **5**.
- **US-30** 8·8·10·5 → Diya under-counted a "status dropdown"; Rohan surfaced the decline-reason + audit hook → **8**.
- **US-41** converged on **10** → SM noted **10 > velocity 8**, so it *can't fit a sprint* → **split** into US-41a (5) + US-41b (5). A real group decision that also became rebalancing action R-4.

**Why planning poker:** simultaneous reveal prevents anchoring on the loudest voice; the spread *is* the signal — it surfaces hidden complexity and differing assumptions before code is written.

---

## Session 7 — Sprint planning *(Part 2)*
**Facilitator:** Diya (SM). Using velocity **8**, the team slotted all 47 stories into **32 sprints**, respecting dependencies and committing ≤8/sprint. We broke Sprint 1's stories into **hour-estimated tasks** (task breakdown — [doc 08](08-sprint-backlog-and-planning.md)) and spotted the **5-point packing inefficiency** (two 5s can't share an 8-point sprint), logging a retro action to split more 5s proactively.

---

## Session 8 — Release planning *(Part 2)*
**Facilitator:** Aarav (PO). Grouped the 32 sprints into **6 quarterly releases (R1–R6)**, each a shippable increment themed around a coherent user outcome, front-loaded with Musts and ordered by the dependency critical path. Output: [doc 10](10-release-planning.md).

---

## Artefacts of collaboration to attach at submission
- Photos of the **ideation whiteboard** and **dot-vote**.
- Screenshots of **planning-poker** reveals (cards per round) — or a shot of the online poker tool.
- The **task-breakdown** sticky wall for Sprint 1.
- Screenshots of the backlog in **Jira** (import [`backlog/kerbside-backlog.csv`](../backlog/kerbside-backlog.csv)).
- Stand-up / retro notes.
