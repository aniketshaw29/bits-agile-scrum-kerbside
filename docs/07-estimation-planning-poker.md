# 07 — Estimation: Planning Poker

*(Assignment Part 1, task 6: high-level story-point estimate via Planning Poker, using the deck **{2, 3, 5, 8, 10}**.)*

## Method

- **Relative sizing, not hours.** Story points capture *effort + complexity + uncertainty* relative to known anchors — not calendar time.
- **Deck:** `2 · 3 · 5 · 8 · 10` (a capped Fibonacci-style deck, per the assignment).
- **Estimators:** the Development Team — *Kabir* (FE/Map), *Meera* (BE/API), *Rohan* (QA/UX), and *Diya* (SM, who also builds). **Aarav (PO)** presents each story and answers questions but **does not vote** (he owns *what/why*, the team owns *how big*).
- **Process per story:** PO reads the story → Q&A → everyone reveals a card simultaneously → if cards agree, record it → if they diverge, the **highest and lowest** explain, then **re-vote** (max 3 rounds) until convergence.

## Anchor (baseline) stories

To keep estimates consistent we fixed three reference points first:

| Anchor | Story | Why it anchors that number |
|---|---|---|
| **2** | US-46 Handover confirmation | One notification + a status flip. Smallest real unit of work. |
| **5** | US-01 Browse the asset map | A screen + data fetch + typed pins + empty state. "A normal story." |
| **8** | US-30 Officer triage of escalations | Multi-status workflow + mandatory decline reason + resident-visible sync + audit hook. "Large but still one story." |

## Planning-poker sessions (representative rounds)

> The team poker'd all 46 stories across two grooming sessions; five instructive rounds are reproduced here in full. The rest are summarised in the estimate table below.

### US-01 — Browse the asset map
| Round | Kabir | Meera | Rohan | Diya | Outcome |
|---|---|---|---|---|---|
| 1 | 5 | 5 | 8 | 3 | **Spread** — discuss |
| 2 | 5 | 5 | 5 | 5 | **✅ 5** |

*Discussion:* Rohan (8) worried about geolocation permissions **and** pin clustering. Meera clarified clustering is out of v1 scope (one street, few pins). Diya (3) had assumed static pins; agreed the fetch + typed-icon + empty-state work is real. Converged on **5**.

### US-04 — Add a new asset
| Round | Kabir | Meera | Rohan | Diya | Outcome |
|---|---|---|---|---|---|
| 1 | 5 | 3 | 5 | 5 | Discuss low vote |
| 2 | 5 | 5 | 5 | 5 | **✅ 5** |

*Discussion:* Meera (3) expected to reuse the pin component cheaply; the others noted drop-pin placement + fixed-catalog picker + validation + persistence + "appears as unadopted" all add up. Converged **5**.

### US-30 — Officer triage of escalations
| Round | Kabir | Meera | Rohan | Diya | Outcome |
|---|---|---|---|---|---|
| 1 | 8 | 8 | 10 | 5 | **Wide spread** — discuss |
| 2 | 8 | 8 | 8 | 8 | **✅ 8** |

*Discussion:* Diya (5) pictured a simple status dropdown. Rohan (10) listed four statuses, a **mandatory decline reason**, resident-visible status sync, and the audit-log hook. The team agreed it's genuinely large but still a single coherent story — **8** (our anchor for "large").

### US-13 — Get a reminder before my turn
| Round | Kabir | Meera | Rohan | Diya | Outcome |
|---|---|---|---|---|---|
| 1 | 3 | 5 | 5 | 5 | Discuss low vote |
| 2 | 5 | 5 | 5 | 5 | **✅ 5** |

*Discussion:* Kabir (3) thought "just a notification". Meera flagged the hidden backend work: a **scheduled job**, **lead-time config**, **de-duplication** (don't resend), and **respecting paused tasks**. Kabir revised up — **5**.

### US-41 — Street-coverage dashboard → the "too big" case
| Round | Kabir | Meera | Rohan | Diya | Outcome |
|---|---|---|---|---|---|
| 1 | 10 | 8 | 10 | 10 | Discuss |
| 2 | 10 | 10 | 10 | 10 | **⚠ 10** |

*Discussion:* The dashboard bundles **three status derivations** (Adopted-Active / Adopted-Lapsing / Unadopted), the **time-window "lapsing" rule**, a **street coverage %**, and **per-spot drill-down**. Meera argued 8 but conceded the lapsing logic is non-trivial. Consensus **10**.

> **🔑 Key estimation decision — split a 10.** Diya (SM) pointed out that **10 > our sprint velocity of 8**, so this story *cannot be completed in a single sprint*. Per our working agreement, a story that lands on 10 is split. The team broke it into:
>
> | New story | Scope | MoSCoW | Pts |
> |---|---|---|---|
> | **US-41a** | Dashboard listing adopted/unadopted spots + overall coverage % | Must | **5** |
> | **US-41b** | "Lapsing" detection (time-window rule) + per-spot drill-down | Should | **5** |
>
> This is also a *rebalancing* action ([doc 06, R-4](06-dependencies-and-rebalancing.md)): the Must half now fits a sprint and ships first; the Should half can slip independently.

## Final estimated backlog

| Epic | Stories & points | Subtotal |
|---|---|---|
| **E1** Map & Adoption | US-01 **5**, US-02 **3**, US-03 **3**, US-04 **5**, US-05 **5**, US-06 **5**, US-07 **3**, US-08 **3** | **32** |
| **E2** Rotas & Reminders | US-09 **5**, US-10 **3**, US-11 **3**, US-12 **3**, US-13 **5**, US-14 **3**, US-15 **5**, US-16 **3** | **30** |
| **E3** Reporting & Timeline | US-17 **5**, US-18 **3**, US-19 **5**, US-20 **3**, US-21 **3**, US-22 **5**, US-23 **5**, US-24 **3** | **32** |
| **E4** Council & Escalation | US-25 **5**, US-26 **5**, US-27 **3**, US-28 **3**, US-29 **5**, US-30 **8**, US-31 **5**, US-32 **5** | **39** |
| **E5** Working Bees | US-33 **5**, US-34 **3**, US-35 **3**, US-36 **3**, US-37 **5**, US-38 **5** | **24** |
| **E6** Recognition & Handover | US-39 **5**, US-40 **3**, US-41a **5**, US-41b **5**, US-42 **5**, US-43 **5**, US-44 **5**, US-45 **5**, US-46 **2** | **40** |
| **User-story total** | 47 stories | **197** |
| **Technical stories** | T1 **3**, T2 **5**, T3 **5**, T4 **8**, T5 **5**, T6 **3** | **29** |
| **Grand total** | 53 backlog items | **226** |

## What the estimate tells us (feeds Part 2)

- **226 points ÷ 8 points/sprint = 28 sprints** as a naïve lower bound; after dependency-aware packing (the backlog skews to 5-point stories, which pack inefficiently against a velocity of 8) it slots into **≈ 32 sprints** — see the [packing insight](08-sprint-backlog-and-planning.md#reconciliation--a-planning-insight).
- At a **quarterly (6-sprint) release cadence**, that is **6 releases (R1–R6)** — see [release planning](10-release-planning.md).
- **No story now exceeds the velocity of 8**, so every item is sprint-fittable after the US-41 split — a precondition for the sprint planning in [doc 08](08-sprint-backlog-and-planning.md).
