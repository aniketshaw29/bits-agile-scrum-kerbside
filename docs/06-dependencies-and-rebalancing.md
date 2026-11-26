# 06 — Dependencies & Rebalancing

*(Assignment Part 1, task 5: "Relook and rebalance the story based on dependency".)*

Having written the backlog and prioritised it, the team re-looked at every story for **ordering constraints** — "what must exist before this can start?" — then **rebalanced** (reordered, re-prioritised, promoted, or split) where dependencies conflicted with priority or capacity.

## 1. Dependency table

| Story | Depends on | | Story | Depends on |
|---|---|---|---|---|
| T1 | — | | US-19 | US-17 |
| T2 | — | | US-20 | US-17, **T5** |
| T3 | T2 | | US-21 | US-17 |
| T4 | T2, T3 | | US-22 | US-17 |
| T5 | T4 | | US-23 | US-22 |
| T6 | T1 | | US-24 | US-21 |
| US-01 | T4 | | US-25 | US-05 |
| US-02 | US-01 | | US-26 | US-25 |
| US-03 | US-01 | | US-27 | US-26 |
| US-04 | US-01 | | US-28 | US-25 |
| US-05 | US-02 | | US-29 | US-02 |
| US-06 | US-05 | | US-30 | US-29 |
| US-07 | US-03 | | US-31 | US-05 |
| US-08 | US-05 | | US-32 | US-26, US-30 |
| US-09 | US-05 | | US-33 | US-01 |
| US-10 | US-09 | | US-34 | US-33 |
| US-11 | US-10 | | US-35 | US-36 |
| US-12 | US-09 | | US-36 | US-33 |
| US-13 | US-10 | | US-37 | US-36 |
| US-14 | US-11 | | US-38 | US-37 |
| US-15 | US-13 | | US-39 | US-14 |
| US-16 | US-15 | | US-40 | US-39 |
| US-17 | US-02, **T5***(photos)* | | US-41a | US-39 |
| US-18 | US-17 | | US-41b | US-41a |
| | | | US-42 | US-39 |
| | | | US-43 | US-05, US-19 |
| | | | US-44 | US-43 |
| | | | US-45 | US-43 |
| | | | US-46 | US-44 |

## 2. The critical path (longest dependency chain)

```mermaid
graph LR
  T2[T2 Data model] --> T3[T3 Auth]
  T3 --> T4[T4 API]
  T4 --> US01[US-01 Map]
  US01 --> US02[US-02 Spot details]
  US02 --> US05[US-05 Adopt]
  US05 --> US09[US-09 Create rota]
  US09 --> US10[US-10 Rotate]
  US10 --> US11[US-11 Schedule]
  US11 --> US14[US-14 Mark done]
  US14 --> US39[US-39 Streak]
  US39 --> US41a[US-41a Dashboard]
```

This chain — **T2 → T3 → T4 → US-01 → US-02 → US-05 → US-09 → US-10 → US-11 → US-14 → US-39 → US-41a** — is the backbone of the product. Nothing on it can be parallelised away, so it sets the **minimum number of sprints** before recognition features can appear and dictates the release order.

## 3. Problems found, and how we rebalanced

| # | Problem spotted | Rebalancing decision |
|---|---|---|
| **R-1** | **Everything** sits behind the technical backbone `T2 → T3 → T4`. If feature stories were pulled first, they'd stall. | **Front-load** T1, T2, T3, T4 into Sprints 1–3 of Release 1 before any user story. Technical stories were explicitly added to the backlog (doc 05) and ranked **Must** so they are scheduled first. |
| **R-2** | **US-17 "Submit a condition report" is a Must, but its photo upload depends on T5 "media storage", which was a Should** → a Must blocked by a lower priority. | **Split the dependency, not the priority:** the *text* report (US-17 core) needs only T4 and ships as Must in R2; *photo attachment* is gated on T5. We **pull T5 into Release 2** (scheduled immediately before E3's photo stories) so US-17/US-18/US-20 are unblocked exactly when needed — without promoting T5 all the way to R1 (which would be waste). |
| **R-3** | **US-35 "Assign volunteer roles" (Could) depends on US-36 "RSVP" (Must)** — a forward dependency within E5 where the earlier-numbered story needs a later one. | Reordered the **build sequence** so US-33 → US-36 → US-37 come before US-34/US-35. Priority is unchanged (US-35 stays Could); only the *implementation order* was corrected so the Could never blocks a Must. |
| **R-4** | **US-41 "Street-coverage dashboard" estimated at 10** (see [doc 07](07-estimation-planning-poker.md)) → a single story larger than a whole 8-point sprint; it can never fit. | **Split** into **US-41a** (adopted/unadopted + coverage %, Must, 5) and **US-41b** (lapsing detection + per-spot drill-down, Should, 5), with 41b depending on 41a. Now each fits a sprint and the Should half can slip independently. |
| **R-5** | **US-32 "Auditable log" depends on *two* stories** (US-26 approve/decline **and** US-30 triage) — easy to schedule too early. | Pinned US-32 to **after both** US-26 and US-30 complete (late in the E4 / Release 3 window). |
| **R-6** | **US-39 recognition (E6, Must) depends on US-14 "mark turn done" (E2, Must)** — a cross-epic dependency; recognition is meaningless before upkeep is logged. | Sequenced **E2 before E6**: streaks/dashboard land only after the rota "done" action exists. This is a key reason E6 is a late release. |
| **R-7** | **US-43 handover depends on US-05 and reads the US-19 condition history.** | Ensured **US-19 (R3)** precedes **handover (R5)** so a handover package can show real history. |

## 4. Rebalanced build order (dependency-respecting)

The reconciled order below drives [sprint planning](08-sprint-backlog-and-planning.md). Items in the same wave have no dependency on each other and may run in parallel; each wave depends only on earlier waves.

1. **Foundations:** T1, T2 → T3, T6 → T4
2. **Map core:** US-01 → US-02, US-03, US-04
3. **Adoption:** US-05 → US-06, US-07, US-08
4. **Rotas:** US-09 → US-10 → US-11 → US-14; US-12; US-13 → US-15 → US-16
5. **Reporting** *(needs T5)*: T5 → US-17 → US-18, US-19, US-20, US-21, US-22 → US-23; US-24
6. **Council:** US-25 → US-26 → US-27, US-28; US-29 → US-30; US-31; US-32
7. **Working bees:** US-33 → US-36 → US-37 → US-38; US-34; US-35
8. **Recognition:** US-39 → US-40, US-41a → US-41b, US-42
9. **Handover:** US-43 → US-44 → US-46; US-45

> No dependency cycles exist after rebalancing — the backlog is a valid DAG, so a complete sprint ordering is guaranteed.
