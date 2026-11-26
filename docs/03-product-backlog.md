# 03 — Product Backlog (User Stories)

Every story follows the standard template:

> **As a** `<role>`, **I want** `<goal>`, **so that** `<benefit>`.

Each card shows its metadata as `[feature · MoSCoW · story points · depends on]`. MoSCoW rationale is in [doc 04](04-moscow-prioritization.md); estimates (and the one split) in [doc 07](07-estimation-planning-poker.md); dependencies and the rebalanced build order in [doc 06](06-dependencies-and-rebalancing.md). Technical stories live in [doc 05](05-technical-stories.md).

**46 story cards · 195 points as drafted → 197 points / 47 stories after the US-41 split** (226 incl. the 6 technical stories).

---

## E1 — Street Asset Map & Adoption

### F1.1 — Interactive Street Asset Map

#### US-01 — Browse the asset map  `[F1.1 · Must · 5 · depends on: —]`
**As a** resident, **I want** to browse geolocated micro-assets on a map centered on my street, **so that** I can discover the shared spots near me that need looking after.
- Given I open the app, when the map loads, then it centers on my current or saved location and renders asset pins within the visible area.
- Given assets of different catalog types exist, when they appear on the map, then each pin uses a distinct icon for its type (planter, grit bin, little free library, storm drain, verge, noticeboard).
- Given no assets exist in the current view, when the map loads, then an empty-state message invites me to add the first spot.

#### US-02 — View a spot's details & stewardship status  `[F1.1 · Must · 3 · depends on: US-01]`
**As a** resident, **I want** to tap a pin and see that asset's details and current stewardship status, **so that** I understand what the spot is and whether someone already cares for it.
- Given I tap an asset pin, when the detail panel opens, then it shows the asset type, a short description, and its stewardship status (unadopted / adopted / co-stewarded).
- Given an asset is adopted, when I view its details, then the current steward names are shown.
- Given I close the detail panel, when I return to the map, then my previous map position and zoom are preserved.

#### US-03 — Filter the map  `[F1.1 · Should · 3 · depends on: US-01]`
**As a** resident, **I want** to filter the map by asset type and stewardship status, **so that** I can quickly find unadopted spots or a specific kind of asset to care for.
- Given the filter control is open, when I select one or more asset types, then only pins of those types remain visible.
- Given I filter by "unadopted", when the map updates, then only spots with no steward are shown.
- Given I clear all filters, when the map updates, then every asset in view is shown again.

#### US-04 — Add a new asset  `[F1.1 · Must · 5 · depends on: US-01]`
**As a** resident, **I want** to add a new asset by dropping a pin and choosing a type from the fixed catalog, **so that** spots on my street that no one is tracking yet become visible and adoptable.
- Given I tap "Add spot", when I place a pin on the map, then I am prompted to pick a type from the fixed catalog only (no free-text type).
- Given I confirm a new asset, when it is saved, then it appears on the map as unadopted and visible to other residents.
- Given I try to add an asset without selecting a catalog type, when I confirm, then validation blocks submission and tells me a type is required.

### F1.2 — Adoption & Stewardship Lifecycle

#### US-05 — Adopt a spot as sole steward  `[F1.2 · Must · 5 · depends on: US-02]`
**As a** resident, **I want** to adopt an unadopted spot as its sole steward, **so that** I take clear, visible responsibility for looking after it.
- Given an asset is unadopted, when I tap "Adopt", then I become its steward and its status changes to adopted.
- Given I have adopted a spot, when other residents view it, then they see my name as steward and the "Adopt" action is no longer offered.
- Given an asset is already adopted, when I view it, then I am offered to request co-stewardship rather than a fresh adoption.

#### US-06 — Invite a co-steward  `[F1.2 · Should · 5 · depends on: US-05]`
**As a** resident, **I want** to invite a neighbor to co-steward a spot with me, **so that** we can share the upkeep so the spot is covered even when one of us is away.
- Given I am a steward, when I invite a neighbor as co-steward, then they receive an invitation they can accept or decline.
- Given a neighbor accepts, when the asset is viewed, then both of us are listed as co-stewards.
- Given a neighbor declines or the invite expires, when I view the asset, then it remains solely adopted by me and I can invite again.

#### US-07 — Neighborhood stewardship overview  `[F1.2 · Should · 3 · depends on: US-03]`
**As a** community association volunteer, **I want** to see at a glance which spots are unadopted, adopted, or co-stewarded across the neighborhood, **so that** I can target recruitment at the spots that still have no one caring for them.
- Given multiple assets exist, when I open the status overview, then counts of unadopted / adopted / co-stewarded spots are shown.
- Given I pick a status in the overview, when I select it, then the map filters to show only those spots.
- Given stewardship changes, when I reopen the overview, then the counts reflect the current state.

#### US-08 — Release a spot  `[F1.2 · Could · 3 · depends on: US-05]`
**As a** resident, **I want** to release a spot I steward when I move on, **so that** the spot cleanly returns to the pool so someone else can adopt it.
- Given I am the sole steward, when I confirm release, then the asset returns to unadopted and my name is removed.
- Given I am one of several co-stewards, when I release, then I am removed but the asset stays adopted by the remaining co-stewards.
- Given I trigger release, when the confirmation dialog appears, then I must confirm before the change is applied.

---

## E2 — Upkeep Rotas & Reminders

### F2.1 — Recurring Task Rotas

#### US-09 — Create a recurring upkeep task  `[F2.1 · Must · 5 · depends on: US-05]`
**As a** steward, **I want** to create a recurring upkeep task on a spot (e.g. "water the planter" every week) with a name, frequency, and start date, **so that** the small jobs a spot needs are captured and repeat on their own instead of relying on memory.
- Given I am a steward of a spot, when I add a task with a name, a frequency (daily/weekly/monthly), and a start date, then the task is saved and listed under that spot.
- Given a saved recurring task, when its due date passes, then the next occurrence is automatically generated for the following interval.
- Given I submit a task with a missing name or frequency, when I try to save, then I see a validation error and the task is not created.

#### US-10 — Rotate a task across co-stewards  `[F2.1 · Must · 3 · depends on: US-09]`
**As a** steward, **I want** to add co-stewards to a task so that each occurrence rotates to the next person, **so that** the workload is shared fairly rather than falling on one person.
- Given a recurring task, when I add two or more co-stewards, then each new occurrence is assigned to the next co-steward in round-robin order.
- Given a rotation, when one completes their turn, then the following occurrence is assigned to the next co-steward and wraps back to the first after the last.
- Given I remove a co-steward from the rotation, when the next occurrence is generated, then that person is skipped and no longer receives turns.

#### US-11 — See the rota schedule  `[F2.1 · Should · 3 · depends on: US-10]`
**As a** co-steward, **I want** to see a clear schedule showing whose turn each upcoming occurrence is and when my own next turn falls, **so that** I know exactly what I am responsible for and when.
- Given I am in a task rotation, when I open the task, then I see upcoming occurrences each labelled with the assigned co-steward and due date.
- Given upcoming occurrences, when I view the schedule, then my own next turn is clearly highlighted.
- Given a task with no occurrences left this cycle, when I view it, then I see a message that the schedule is up to date.

#### US-12 — Edit or pause a task schedule  `[F2.1 · Could · 3 · depends on: US-09]`
**As a** steward, **I want** to edit or pause a task's schedule (e.g. change frequency or pause over winter), **so that** the rota adapts to seasons instead of nagging people about jobs that no longer apply.
- Given an existing task, when I change its frequency and save, then future occurrences follow the new frequency while past records are unchanged.
- Given an active task, when I pause it, then no new reminders or occurrences are generated until I resume it.
- Given a paused task, when I resume it, then occurrences and reminders begin again from the next interval.

### F2.2 — Reminders, Cover & Swaps

#### US-13 — Get a reminder before my turn  `[F2.2 · Must · 5 · depends on: US-10]`
**As a** co-steward, **I want** to receive a reminder shortly before a turn I am assigned is due, **so that** I do not forget my upkeep turn and the spot stays looked after.
- Given I am assigned an upcoming occurrence, when it is within the configured lead time (e.g. the day before), then I receive a reminder naming the spot, the task, and the due date.
- Given a reminder has already been sent for an occurrence, when the system runs again, then it does not send a duplicate for the same occurrence.
- Given a task is paused, when reminders are processed, then no reminder is sent for its occurrences.

#### US-14 — Mark my turn done  `[F2.2 · Must · 3 · depends on: US-11]`
**As a** co-steward, **I want** to mark my turn as done when I have completed the task, **so that** the rota advances and others can see the spot has been looked after.
- Given an occurrence assigned to me, when I mark it done, then it is recorded as completed with my name and a timestamp.
- Given a completed occurrence, when others view the task, then the completion is visible and the next occurrence is shown as upcoming.
- Given an occurrence is not yet due, when I mark it done early, then it is accepted and the next turn is still scheduled by the normal interval.

#### US-15 — Request cover for a turn  `[F2.2 · Should · 5 · depends on: US-13]`
**As a** co-steward who is unavailable, **I want** to request cover or a swap for a turn I cannot do, **so that** the task still gets done and I am not stuck with a turn I genuinely cannot make.
- Given an occurrence assigned to me, when I request cover, then the other co-stewards are notified that this turn needs covering.
- Given a cover request is open, when I view the occurrence, then it is clearly flagged as "cover requested" and still shows its due date.
- Given I requested cover by mistake, when I cancel the request, then the occurrence returns to me and others are notified it no longer needs cover.

#### US-16 — Accept or decline a cover request  `[F2.2 · Should · 3 · depends on: US-15]`
**As a** co-steward, **I want** to accept or decline a cover request from another steward, **so that** turns are reassigned only by mutual agreement so no one is landed with work they did not accept.
- Given an open cover request, when I accept it, then the occurrence is reassigned to me and the original steward is notified.
- Given an open cover request, when I decline it, then it remains open for other co-stewards and the requester sees it is still unfilled.
- Given a cover request that no one accepts before the due date, when the due date passes, then it stays assigned to the original steward and is flagged as still needing cover.

---

## E3 — Condition Reporting & Photo Timeline

### F3.1 — Report a Spot's Condition with Photos

#### US-17 — Submit a condition report  `[F3.1 · Must · 5 · depends on: US-02]`
**As a** resident, **I want** to submit a condition report for a spot with a text note and one or more photos, **so that** neighbors and stewards can see exactly what needs attention.
- Given I am viewing a spot, when I tap "Report condition" and enter a note, then a report is created and attached to that spot.
- Given I am creating a report, when I add at least one photo, then the photo is uploaded and shown as a thumbnail.
- Given I submit a report, when it saves, then it records the current date/time and my resident identity.
- Given I leave the note empty and add no photo, when I try to submit, then submission is blocked with a validation message.

#### US-18 — Tag before/after photos  `[F3.1 · Should · 3 · depends on: US-17]`
**As a** resident, **I want** to tag photos in a report as "before" or "after", **so that** the improvement or decline of a spot is visually obvious at a glance.
- Given I am adding a photo, when I pick a label, then I can mark it "before" or "after".
- Given a report has before and after photos, when it is displayed, then the two are shown side by side.
- Given I do not choose a label, when the photo is saved, then it defaults to "before".

#### US-19 — View a spot's condition timeline  `[F3.1 · Must · 5 · depends on: US-17]`
**As a** neighbor, **I want** to view a dated timeline of all condition reports for a spot, **so that** I can see how the spot's condition has changed over time.
- Given a spot has multiple reports, when I open its history, then reports are listed newest-first with their dates.
- Given a report has photos, when I view it in the timeline, then its thumbnails are shown inline.
- Given a spot has no reports yet, when I open its history, then an empty-state message is shown.

#### US-20 — Capture a photo in-app  `[F3.1 · Could · 3 · depends on: US-17]`
**As a** resident, **I want** to capture a photo with my phone camera or pick one from my camera roll while reporting, **so that** I can report a spot's condition on the go without extra steps.
- Given I am adding a photo, when I choose "Take photo", then the device camera opens and the captured image attaches to the report.
- Given I am adding a photo, when I choose "Choose from library", then I can select an existing image.
- Given the app has no camera permission, when I tap "Take photo", then I am prompted to grant permission or fall back to the library.

### F3.2 — Resolve & Escalate Reported Issues

#### US-21 — Mark a report resolved  `[F3.2 · Must · 3 · depends on: US-17]`
**As a** steward, **I want** to mark a reported issue as resolved, **so that** the spot's status reflects current reality and neighbors know it was handled.
- Given an open report, when I mark it resolved, then its status changes to "Resolved" and records who resolved it and when.
- Given a resolved report, when anyone views the spot timeline, then the resolved status is clearly shown.
- Given I am a plain resident (not a steward), when I view a report, then the "Resolve" action is not available to me.

#### US-22 — Flag an issue for escalation  `[F3.2 · Should · 5 · depends on: US-17]`
**As a** steward, **I want** to flag an issue for escalation to the council liaison with a reason, **so that** work beyond residents' scope is handed off to the right authority.
- Given an open report, when I flag it for escalation and enter a reason, then its status becomes "Escalated".
- Given an issue is escalated, when I view it, then the escalation reason and timestamp are recorded.
- Given an escalated issue, when I view the spot, then it is visually distinguished from normal open reports.

#### US-23 — Officer view of escalated issues  `[F3.2 · Should · 5 · depends on: US-22]`
**As a** council liaison officer, **I want** to see a list of escalated issues with their notes and photo history, **so that** I can triage them and schedule official work.
- Given issues have been escalated, when I open the escalations view, then I see only escalated issues with spot name, reason, and date.
- Given I select an escalated issue, when I open it, then I can see its full photo timeline and notes.
- Given no issues are escalated, when I open the escalations view, then an empty-state message is shown.

#### US-24 — Notify reporter of outcome  `[F3.2 · Could · 3 · depends on: US-21]`
**As a** resident, **I want** to be notified when a report I submitted is resolved or escalated, **so that** I know my report was acted on and what happened next.
- Given I submitted a report, when a steward resolves it, then I receive a notification naming the spot and new status.
- Given I submitted a report, when it is escalated, then I receive a notification with the escalation reason.
- Given a status change occurs, when I open the notification, then it links me directly to that report in the timeline.

---

## E4 — Council Liaison & Escalation

### F4.1 — Adoption Approval Queue

#### US-25 — Officer adoption queue  `[F4.1 · Must · 5 · depends on: US-05]`
**As a** council liaison officer, **I want** to see a single queue of all pending adoption requests for spots in my area, **so that** I can review who wants to look after what in one place instead of chasing scattered messages.
- Given residents have submitted adoption requests, when I open the liaison queue, then I see each pending request with spot name, type, street, requesting resident, and request date.
- Given a request has already been approved or declined, when I view the queue, then it no longer appears in the "pending" list.
- Given there are no pending requests, when I open the queue, then I see an empty-state message rather than a blank screen.

#### US-26 — Approve / decline an adoption  `[F4.1 · Must · 5 · depends on: US-25]`
**As a** council liaison officer, **I want** to approve or decline an adoption request and attach a short reason, **so that** residents receive a clear decision and the authority keeps an auditable record of why.
- Given a pending request, when I click Approve, then the spot's status becomes "adopted" and the resident is recorded as its steward.
- Given a pending request, when I click Decline, then I am required to enter a reason before the decision is saved.
- Given I have made a decision, when the action completes, then the decision, my officer identity, and a timestamp are written to the audit log.

#### US-27 — Notify resident of adoption decision  `[F4.1 · Should · 3 · depends on: US-26]`
**As a** resident, **I want** to be notified when my adoption request is approved or declined, **so that** I know whether I can start looking after the spot and don't have to keep checking.
- Given my request is approved, when the officer saves the decision, then I receive a notification confirming I am now the steward.
- Given my request is declined, when the officer saves the decision, then I receive a notification including the reason given.
- Given I open the notification, when I follow it, then I land on the relevant spot's detail view.

#### US-28 — Filter / sort the adoption queue  `[F4.1 · Could · 3 · depends on: US-25]`
**As a** council liaison officer, **I want** to filter and sort the queue by street, spot type, or request age, **so that** I can prioritise the oldest or most sensitive requests when the queue is long.
- Given multiple pending requests, when I filter by a spot type such as "grit bin", then only requests of that type are shown.
- Given multiple pending requests, when I sort by request date, then the oldest request appears first.
- Given I have applied a filter, when I clear it, then the full pending queue is shown again.

### F4.2 — Escalations & Supply Fulfilment

#### US-29 — Escalate an issue beyond resident scope  `[F4.2 · Must · 5 · depends on: US-02]`
**As a** resident, **I want** to escalate an issue beyond my scope, such as a cracked planter or blocked storm drain, **so that** the authority can take on work I am not allowed or able to do myself.
- Given I am viewing a spot I steward, when I raise an escalation, then I can choose an issue type and add a description and optional photo.
- Given I submit an escalation, when it is saved, then it appears in the officer's escalation queue with status "new".
- Given I submit an escalation, when it is saved, then the spot shows an "escalated to authority" marker so other residents know it is being handled.

#### US-30 — Officer triage of escalations  `[F4.2 · Must · 8 · depends on: US-29]`
**As a** council liaison officer, **I want** to triage an escalated issue and move it through statuses (accepted, in progress, resolved, declined), **so that** residents and officers can always see who owns the work and where it stands.
- Given a "new" escalation, when I set its status to accepted / in progress / resolved / declined, then the new status and my identity are saved against it.
- Given I decline an escalation, when I save, then I must provide a reason explaining why it is not authority work.
- Given a status changes, when the resident views the spot or escalation, then they see the current status without needing to contact me directly.

#### US-31 — Request supplies  `[F4.2 · Should · 5 · depends on: US-05]`
**As a** resident, **I want** to request supplies such as salt or compost for the spot I look after, **so that** I can keep maintaining my spot without buying materials out of my own pocket.
- Given I steward a spot, when I create a supply request, then I can select a supply type and quantity and submit it.
- Given I submit a supply request, when it is saved, then it appears in the officer's queue to be fulfilled or declined.
- Given an officer marks my request fulfilled, when I view it, then its status shows as fulfilled with the date.

#### US-32 — Auditable authority log  `[F4.2 · Should · 5 · depends on: US-26, US-30]`
**As a** council liaison officer, **I want** an auditable log of every adoption decision, escalation status change, and supply fulfilment, **so that** the boundary between resident-handled and authority-handled work stays clear and defensible.
- Given any decision or status change is made, when it is saved, then the log records the action, actor, timestamp, and related spot.
- Given I open the audit log for a spot, when it loads, then entries are shown in reverse chronological order.
- Given a log entry has been written, when anyone views it, then it cannot be edited or deleted, only appended to.

---

## E5 — Working Bees & Volunteer Coordination

### F5.1 — Event Scheduling & Resource Planning

#### US-33 — Schedule a working bee  `[F5.1 · Must · 5 · depends on: US-01]`
**As a** community association organizer, **I want** to create a working bee event tied to a specific spot or street area with a date, time, and description, **so that** residents can see exactly what is happening, where, and when, and decide whether to join.
- Given I am a logged-in organizer on a spot/area page, when I tap "Schedule working bee" and enter a title, date, start/end time, and description, then the event is saved and linked to that spot/area.
- Given an event has been created, when a resident opens the linked spot, then the upcoming event is shown with its date, time, and description.
- Given I try to save an event with a past date or missing title, when I submit, then the save is blocked and a validation message explains what to fix.

#### US-34 — List tools & materials needed  `[F5.1 · Should · 3 · depends on: US-33]`
**As a** community association organizer, **I want** to list the tools and materials needed for the event and how many of each, **so that** volunteers know what to bring and gaps in supplies are visible before the day.
- Given I am editing an event, when I add tool/material items each with a name and quantity, then the list is saved and displayed on the event page.
- Given an event has a tools/materials list, when a resident views the event, then they can see each item and the quantity still needed.
- Given I remove or edit an item, when I save, then the updated list is shown to everyone viewing the event.

#### US-35 — Assign volunteer roles  `[F5.1 · Could · 3 · depends on: US-36]`
**As a** community association organizer, **I want** to assign simple roles (weeder, waterer, litter picker) to volunteers who have RSVP'd, **so that** everyone arrives knowing their task and the work is evenly shared.
- Given volunteers have RSVP'd yes, when I open the event roster, then I see each attendee and can assign a role from a short predefined list.
- Given a role is assigned, when the volunteer views the event, then they see their assigned role.
- Given I reassign a volunteer, when I save, then the volunteer's displayed role updates accordingly.

### F5.2 — RSVP & Day-of Check-in

#### US-36 — RSVP to an event  `[F5.2 · Must · 3 · depends on: US-33]`
**As a** resident, **I want** to RSVP yes, no, or maybe to a working bee event, **so that** the organizer can plan the right turnout, tools, and materials.
- Given I am viewing an upcoming event, when I select an RSVP of yes/no/maybe, then my response is saved and reflected in my view.
- Given I have already RSVP'd, when I change my response before the event date, then the new status replaces the old one.
- Given residents have responded, when the organizer opens the event, then they see counts of yes/no/maybe and the list of "yes" attendees.

#### US-37 — Check in on the day  `[F5.2 · Must · 5 · depends on: US-36]`
**As a** resident, **I want** to check in on the day of the event, **so that** my actual attendance is recorded rather than just my earlier RSVP.
- Given it is the day of an event I RSVP'd to, when I tap "Check in", then I am marked present with a timestamp.
- Given I try to check in before the event day, when I open the event, then the check-in action is unavailable and explains it opens on the event day.
- Given I have checked in, when I view the event, then my status shows "Checked in" and I cannot check in twice.

#### US-38 — Turnout record  `[F5.2 · Should · 5 · depends on: US-37]`
**As a** community association organizer, **I want** to view a turnout record comparing who RSVP'd against who actually checked in, **so that** I have an accurate record to report upkeep and recognize the volunteers who showed up.
- Given an event has passed, when I open its turnout record, then I see total RSVPs, total check-ins, and the list of attendees who checked in.
- Given some who RSVP'd yes did not check in, when I view the record, then they are clearly flagged as no-shows.
- Given I am viewing the turnout record, when I export or share it, then the counts and attendee list are included in the output.

---

## E6 — Recognition & Clean Handover

### F6.1 — Upkeep Recognition & Street-Coverage Dashboard

#### US-39 — Upkeep streaks  `[F6.1 · Must · 5 · depends on: US-14]`
**As a** resident steward, **I want** to build an upkeep streak that increments each period I log care on my adopted spot, **so that** my sustained, repeated effort is visibly recognized rather than lost.
- Given I logged a verified upkeep action in the current period, when the period closes, then my streak count for that spot increases by one.
- Given I missed logging upkeep for a full period, when the next period starts, then my streak resets to zero and the previous best is retained as a "longest streak" record.
- Given I view my spot, when the page loads, then my current streak and longest streak are displayed with the date of the last logged action.

#### US-40 — Milestone badges  `[F6.1 · Should · 3 · depends on: US-39]`
**As a** resident steward, **I want** to earn badges at upkeep milestones (first adoption, 10 actions, a season of care), **so that** I feel motivated and can show others I am a dependable steward.
- Given I complete an action crossing a milestone threshold, when the action is saved, then the matching badge is awarded once and shown on my profile.
- Given a badge is already earned, when I cross the same threshold again, then no duplicate badge is created.
- Given I open my profile, when it renders, then all earned badges appear with their earned date and a short description.

#### US-41 — Street-coverage dashboard  `[F6.1 · Must · 8 → split into US-41a + US-41b · depends on: US-39]`
**As a** community association volunteer, **I want** a street-coverage dashboard showing which spots are adopted, actively maintained, or lapsing, **so that** I can see at a glance where upkeep is strong and where to recruit help.
- Given a street with mapped spots, when I open the dashboard, then each spot shows a status of Adopted-Active, Adopted-Lapsing, or Unadopted based on recent upkeep activity.
- Given the dashboard is open, when it loads, then an overall coverage percentage for the street is displayed.
- Given I select a spot from the dashboard, when I click it, then I see its steward and last upkeep date.

> **⚠ Estimated at 10 in planning poker → exceeds the 8-point sprint velocity → split** (see [doc 07](07-estimation-planning-poker.md)):
> - **US-41a — Coverage dashboard: adopted vs unadopted + coverage %** `[Must · 5]`
> - **US-41b — Lapsing detection + per-spot drill-down** `[Should · 5]`

#### US-42 — Anti-gaming: count only verified actions  `[F6.1 · Could · 5 · depends on: US-39]`
**As a** council liaison officer, **I want** recognition to count only verified upkeep actions and ignore rapid repeat or empty logs, **so that** streaks and badges reflect genuine care and cannot be gamed for noise.
- Given I submit more than one upkeep log for the same spot within a short cool-down window, when the second log is saved, then it does not advance my streak.
- Given an upkeep log has no description or photo evidence, when it is submitted, then it is flagged unverified and excluded from streak/badge counts.
- Given a log is later verified by a reviewer, when verification is recorded, then it becomes eligible to count toward recognition.

### F6.2 — Guided Clean Handover

#### US-43 — Start a guided handover  `[F6.2 · Must · 5 · depends on: US-05]`
**As a** departing steward, **I want** to start a guided handover that packages my spot and its full upkeep history for a successor, **so that** care is passed on deliberately and never silently lapses when I leave.
- Given I steward a spot, when I choose "Hand over", then a wizard opens pre-filled with the spot details and a summary of its upkeep history.
- Given I am in the wizard, when I nominate a successor by name or invite, then a pending handover is created and the successor is notified.
- Given a handover is pending, when I view the spot, then it is marked "Handover in progress" and I remain responsible until it is accepted.

#### US-44 — Review & accept a handover  `[F6.2 · Must · 5 · depends on: US-43]`
**As an** incoming successor, **I want** to review the spot's complete history and care notes before I accept, **so that** I take over with full context and can continue upkeep without guesswork.
- Given I receive a handover invite, when I open it, then I see the full timeline of past upkeep actions, notes, and any council conditions.
- Given I have reviewed the details, when I click Accept, then stewardship transfers to me and the departing steward is notified.
- Given I click Decline, when confirmed, then the spot returns to its previous steward and is no longer marked "Handover in progress".

#### US-45 — Claim an orphaned spot  `[F6.2 · Should · 5 · depends on: US-43]`
**As a** community association volunteer, **I want** to reassign or claim a spot when a departing steward has no named successor, **so that** orphaned spots are picked up instead of quietly becoming neglected.
- Given a handover has no nominated successor, when I open the street's handover queue, then the spot appears as "Needs a steward".
- Given a spot needs a steward, when I assign it to a willing resident or claim it myself, then stewardship transfers and the history is carried over.
- Given no steward is found within a configurable window, when the window expires, then the spot is flagged as Unadopted on the coverage dashboard.

#### US-46 — Handover confirmation  `[F6.2 · Could · 2 · depends on: US-44]`
**As a** departing steward, **I want** a clear confirmation once my handover is fully accepted, **so that** I know responsibility has transferred and I can step away with peace of mind.
- Given my successor accepts the handover, when the transfer completes, then I receive a confirmation showing the new steward and transfer date.
- Given the handover is complete, when I view the spot, then I am listed under "Past stewards" and no longer shown as responsible.
