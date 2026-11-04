> **Public copy note:** This is the project's working build log, lightly privacy-edited for publication: the founder's family members are referred to by role words instead of names, and the founder's production instance is called the "founder scope" (the demo instance is the "demo scope"). No entries, dates, findings, or results were changed.

# Parent Muse — Hackathon Build Log (Oct 26 – Nov 4, 2026)

Purpose: a dated record of what was actually built *during* the Meta Global AI Developer Hackathon window (Oct 26, 12:00 PM ET – Nov 4, 9:00 PM ET), kept separately from the pre-existing product. Started Oct 26, 2026 after the kickoff raised the "show only what your team built during the event" line. Eligibility for the Startup Track is NOT settled by this log — the official rules were still not visible on the public Cerebral Valley details page when checked Mon Oct 26, ~1:20 PM ET, and the organizers' written answer in Discord office hours is the other closer. This log documents facts either way.

## Built during the window

### Mon Oct 26, 2026 — Clean calendar-title extraction (Manus, supervised/verified by Muse)
- Dictated calendar events now save with a short extracted title instead of the raw dictated sentence.
  - "Please mark in the calendar that the kids on October 31st have a trunk or treat at 5:00 PM at McNabb Elementary…" → **"Trunk or Treat"**
  - Honor Roll dictation example → **"Honor Roll"**
- Test suite: 158 → **160 passed / 1 skipped**; the two new tests are the title-extraction cases.
- Scope held: no routing, alert, calendar-storage, or latency changes.
- Status: built and evidence-verified in the sandbox/preview. **Final gate still open:** Ben's live re-test in his own instance — re-dictating the Nov 4 Honor Roll event (Nov 4, 8:00 AM, McNab Elementary) doubles as that test and sets up the Nov 4, 7:00 AM alert proof.

## Pre-window baseline (for contrast — NOT claimed as built during the event)
- Parent Muse rebuild: all 7 pieces complete and verified Oct 21, 2026; feature-complete / demo-ready.
- Defects D10–D19 all closed live in Ben's instance by Oct 25, 2026 (D19 closed Oct 25, 11:43 AM ET).
- Application to the hackathon was made openly with Parent Muse as an existing product (Startup Track) and accepted Oct 20, 2026.

## Open items that belong in this log as they land
- [ ] Ben's live re-test of clean-title (via Nov 4 Honor Roll re-dictation)
- [ ] Demo video shoot window: Oct 29 – Nov 1, 2026 — log what is filmed and any build changes made for it
- [ ] Code freeze: Nov 3, 2026
- [ ] Submission: due Nov 4, 9:00 PM ET
- [ ] Official rules text (when posted/accepted) — file a copy here and note the pre-existing-work language verbatim
- [ ] Discord office-hours answer on Startup Track eligibility for an existing product — file verbatim

## Entry 2 — Reply flow streamlining (D20) — Mon Oct 26, 2026, 4:42 PM ET

Founder live-test finding (Ben, ~4:23 PM ET): Reply Mode forced a full coaching analysis screen and a second Draft Reply press before the draft. Fix brief sent to the Manus rebuild thread ~4:25 PM ET (acceptance A-RF-1). Built same day: one press of Draft Reply now produces the draft; the coaching read is collapsed under the draft as a one-line summary and expands in one tap, never gating. Both entry paths fixed (Compose → Reply Mode and Saved-message Reply Thread). Suite 164 passed / 1 skipped (baseline 160/1, +4 new tests); commit b258a93597e47780a05b9719da7faa1af103f863 on rebuild/muse-wonder; locked baseline 147cedc untouched; no changes to Ask M, calendar, retrieval, latency, or send behavior. Verified by M against the brief from the in-thread evidence. Final gate: Ben's live re-test.

- Oct 26, ~6:23 PM ET — Entry 2 LIVE-VERIFIED: Ben re-ran the original braces case for his daughter in his own instance; the draft appeared on ONE press with the coaching collapsed beneath it, and the app fused two dictated topics (a Wednesday school event + his daughter's braces) into one draft grounded in both historical threads. D20 CLOSED LIVE.

## Entry 3 — D21: reminder date-parse + save-path fix (Oct 26, 2026)
Found live by Ben on day one of the event: a fragmented dictation ("On the 29th of October. I have at 2:00...") drew a redundant "what date?" question, and the follow-up "saved" confirmation produced NO calendar event. Fixed same-day: day-first dates parse; fragmented utterances are combined before parsing; child names normalize to the kid records (a misspelled first name → the daughter's kid record); and both save branches — direct and post-clarification — now verify the canonical calendar event exists before the app may say "saved." Regression on the exact dictation: 2026-10-29 14:00, daughter, 60-minute alert. Suite 169 passed / 1 skipped (baseline 164/1, +5). Commit a185d1d7ee06ae9d1a94ba743347aed8e87a63a1. Live gate: Ben's re-dictation of the original phrase — pending at log time.

## Entry 4 — Home-screen voice calendar add (Oct 26, 2026)
Ben's idea, raised while live-testing that evening: a microphone button on the Home "Today & upcoming" card (desktop + mobile). One tap opens the same reviewed dictation flow Ask M already uses — transcript shown before anything saves — and routes through the canonical reminder pipeline: auto-save, child linking, alert defaults, with the save verified via Calendar/Home queries before the app confirms. Non-calendar utterances hand off to Ask M with the transcript prefilled, never a dead end. Verified against acceptance A-HV-1 using a disposable test event (Nov 4, 2026, 2:00 PM, 60-minute alert; cleanup confirmed). Commit 376ebedf on rebuild/muse-wonder. Live gate: Ben's Home-screen test — pending at log time.

## Entry 5 — One-tap draft controls (Oct 26, 2026)

Chips under every draft (Reply Mode + Compose): **Shorter** (same content and tone, tighter), **Softer** (same ask, warmer), **Firmer** — capped at the firmness level the thread record justifies (ignored count × importance); at the ceiling, tapping Firmer shows the one-line coaching note instead of regenerating hotter. One tap regenerates in place and the coaching summary updates to match. Live-route evidence on a disposable draft: Shorter took a 40-word draft to 25 words in place; Softer warmed the wording with the same ask; Firmer on a first-touch thread did NOT regenerate hotter — the draft stayed at the evidence-capped soft level and the ceiling note displayed. Suite 179 passed / 1 skipped (baseline 172/1, +7 across the home-voice and draft-controls work). Commit 44813a239bbfed956ba02594847a65b3a21bb35a on rebuild/muse-wonder; locked baseline 147cedc untouched. Live gate: Ben's chips test in his own instance — pending at log time.

## Entry 6 — D22: named-holiday dates resolve (Oct 26, 2026)

Found live by Ben on day one of the event, exercising the new Home voice add: "Add Christmas Day to the calendar. We are having family over at 10:00 AM" drew a "What date should I use?" question — a named holiday was not resolved to a date, so nothing saved. Fixed same-day: the reminder parser now resolves named holidays to concrete dates (next occurrence on or after today), and a named holiday counts as an explicit date — the app never asks a clarifying date question for one. Regression on the exact dictation: one turn, no clarifying question, saved 2026-12-25 10:00 with the default one-hour alert, surfacing in Calendar and Home Today & upcoming with the clean title "Christmas Day". Floating-holiday evidence: "Thanksgiving Day" said in October 2026 resolved to 2026-11-26. Suite 182 passed / 1 skipped (baseline 179/1, +3). Commit f30790bd354a8321aba77e65598fa021a42c73c7 on rebuild/muse-wonder; locked baseline 147cedc untouched. Live gate: Ben's re-dictation of the Christmas request in his own instance — pending at log time.

## Entry 7 — Ask M → draft handoff (A-AH-1) — Mon Oct 26, 2026, 9:11 PM ET

From Ben's build-week slate: answering a plan/history question and then acting on the answer were two separate trips through the app. Built same day: an Ask M answer now carries one button — "Draft a reply about this" — which opens the compose/reply flow with the parent-visible substance of the answer carried in as editable starting intent (never a pre-written message); from there the one-press draft flow (Entry 2) takes over. Plan-first source priority untouched; the handoff carries only what the answer already showed the parent. Focused tests 59/59; suite 191 passed / 1 skipped (baseline 182/1, +9). Checkpoint 96d4d848 on rebuild/muse-wonder; locked baseline 147cedc untouched. Verified by M as reported from the in-thread evidence — the Manus preview was unauthenticated, so the end-to-end visual pass is Ben's. Live gate: Ben's re-test in his own instance — pending at log time.

---

Companion document: `prior-work-record-2026-10-26.md` (same files folder) discloses the pre-window work and the Benjamin + M (Muse Wonder via the Meta Model API) + Manus collaboration record. Per Benjamin (Oct 26, 2026, ~9:26 PM ET), the kickoff guidance was that prior work must be NOTED — this record is that note, written to be pointed to and to ship with the submission.

## Entry 8 — Oct 26, 2026 (late evening) — A-LAT-3: perceived-latency pass (streaming), measured honestly

Phase 1 (check + measure only, no build): the provider does support streaming (first chunk at 3.425s on a tiny isolated probe — explicitly not a product benchmark), and prefix caching is NOT viable with our prompt construction — an identical repeat of a heavy question ran 49.95% SLOWER. Real-record baselines: light Ask M 31.9s, heavy plan answer 40.4s, heavy history answer 19.6s, with the model call at 89–99% of total time.

Phase 2 (build, commit 17b37cad): streamed rendering for Ask M answers only — provisional text appears while the answer generates; the existing final plan/citation validation still runs unchanged before an answer is final; drafts untouched. Suite 197 passed / 1 skipped; locked baseline untouched.

Measured result, stated plainly: first visible text was 34.2s / 40.3s / 21.8s on the three benchmarks — only 1.2–1.9s ahead of completion. Streaming did not materially change perceived latency on real questions; the model's time-to-first-token is the floor. The change is kept (a harmless, honest progress signal) and the demo plan is unchanged: pre-warm each shot, edit the waits. No inflated speed claim is made anywhere in this submission — this entry records what was tried and what it actually did.

## Entry 9 — Oct 26, 2026 (late evening) — D23: explicit alert offsets in reminder dictations

Found live by the founder the same evening: "Remind me one week ahead of time" was silently saved with the standard day-of default alert. Fix (commit a5670d7a): reminder dictations now parse explicit relative alert offsets — one week ahead, two days before, the day before, the morning of — and an explicit offset always replaces the default; all-day events fire the offset alert at 9:00 AM on the offset day, and the save confirmation states the alert actually set. Regression on the founder's exact dictation stores a Dec 9, 9:00 AM alert for the Dec 16 event. Focused tests 70/70; full suite 203 passed / 1 skipped. Verified as reported by Muse against the thread; the founder's live re-dictation is the closing gate.

## Entry 10 — Oct 26, 2026 (late evening) — Clean-title extraction, round 2 (A-CT-2)

Round 1 (Entry 1) cleaned simple dictations, but the founder's live Thanksgiving save that evening came out titled "Thanksgiving, November 26, I Believe" — the parsed date and a spoken hedge leaked into the title. Round 2 (commit e217e5b3): title extraction now strips the parsed date/time expression when the remainder is a clean event name, plus hedge/filler phrases ("I believe," "I think," "please") and leading instruction fragments; new saves only — no existing calendar event is modified. Regression on the founder's exact wording: title "Thanksgiving", 2026-11-26, all day, both children, default 9:00 AM alert; round-1 titles (Trunk or Treat, Honor Roll, Friend's 30th Birthday) individually intact, plus a non-holiday fallback case ("Family Dinner"). Focused tests 70/70; full suite 205 passed / 1 skipped. Verified by Muse against the thread's own test evidence. Live gate: the founder's re-dictation — pending at log time.

## Entry 11 — Oct 27, 2026 — D24: voice input in Compose Mode

Found live by the founder testing Compose Mode: he dictated naturally in conversation but the Compose "WHAT'S THE SITUATION?" field offered typing only — no voice control on desktop (mobile already had it). Same morning, the same Compose session produced a demo-worthy draft: his typed 30% cost-share was corrected to the plan's 75/25 split under Section V.I. Fixed same day (commit 9701c6f0): a "Speak your situation" control on the Compose situation field, same transcript-review flow as Ask M. Focused tests 19/19; full suite 205 passed / 1 skipped; locked baseline untouched; no scope data changed. Verified as reported by Muse. Live gate: the founder's live dictation in Compose — pending at log time.

## Entry 12 — Oct 27, 2026 — D25: holiday + alert-offset rendering unified (D22/D23 integration)

The D22 named-holiday resolution and D23 explicit alert offsets were integrated into one rendering pass over the shared reminder planner (parent commit 9701c6f). Focused tests 10/10; full regression 205 passed / 1 skipped; TypeScript and build pass; no data changes. A follow-up correction confirmed institutional-holiday injection is present in both scopes (founder-scope Dec 16 and Dec 25 cases, demo-scope Dec 25 case). Verified as reported by Muse. Live gates: the founder's Christmas re-dictation and a family birthday "one week ahead" re-dictation — pending at log time.

## Entry 13 — Oct 27, 2026 — D26: a non-child name must never block an event save

Found live by the founder via Home voice add: "On November 13th, I have a wine party with a friend. Please remind me two weeks ahead of time." The transcript rendered correctly, but the save demanded he match the name to a child profile — an adult social event held hostage by a child-link question with no correct answer — and nothing saved on the direct path (a later continuation saved it wrongly linked to both children). Root cause (Manus, confirmed in-thread): the shared reminder planner converted an unmatched "for/with [name]" into a blocking child clarification. Fix (commit 01c2c9aa): unmatched names no longer block; the event saves unlinked, and "two weeks ahead of time" parses as an alert offset on its own — the exact dictation now saves Nov 13 unlinked with a Fri Oct 30, 9:00 AM alert; a child-naming control dictation still links correctly. Suite 209 passed / 1 skipped; TypeScript and build pass; locked baseline intact; no scope-data changes. Verified as reported by Muse against the brief's acceptance items. Live gate: the founder re-dictates the exact wording in his own instance — pending at log time. D27 (event delete control, founder request same afternoon) was delivered to the thread immediately on this report landing and is building.

## Entry 14 — Oct 27, 2026 — D27: delete control on calendar events (founder request)

Requested by the founder the same afternoon (a wrongly-linked event on his dashboard had no removal path): every event row in Home Today & upcoming, the Calendar day panel, and Kids Up next now carries a trash icon with an inline "Delete? / Cancel" confirm — one extra tap, no modal, no navigation. Deleting removes the canonical event and its alert across all views (implemented as an owner-bound soft-delete with shared query invalidation). Built on the restored D26 state (see incident note below). Suite 213 passed / 1 skipped (baseline 209/1, +4). Commit 3523399551571539a91b0b300d9b06a36c6a2d50 on rebuild/muse-wonder; no scope data changed. Verified as reported by Muse. Live gate: the founder deletes the wrongly-linked wine-party event and re-dictates the D26 wording — pending at log time.

## Incident note — Oct 27, 2026, 1:45 PM ET (recorded for completeness)

During a routine automated supervision check of this thread, a stray click triggered a rollback to the D21 checkpoint (a185d1d7), reverting the active checkout. No work was lost: all builds exist as commits. The thread was restored to the completed D26 commit (01c2c9aa) and the recovery was gated on the full suite reproducing its exact pre-incident result — 209 passed / 1 skipped, clean tree, locked baseline unchanged — before D27 proceeded. The supervision check process was changed to read-only in response.

## Entry 15 — D28 Ask M question-path failure fixed (Oct 27, 2026, ~10:21 PM ET)

Founder live find (9:57 PM): a free-form Ask M question ("Hi M do I need to ask my co-parent if I plan on taking the kids to Europe in Three weeks six days and 23 hrs?") died behind a blocking browser alert — "M is unavailable. Please try again in a moment." Root cause found from server evidence by Manus: the port-3000 API process was missing the /api/parent-agent/stream route (404) — the question never reached the model; the client surfaced the failure as an alert(). Fix commit 3403fb9c0546c89e54a5acc3baa816c8dd0c52a8; suite 215 passed / 1 skipped; no scope data changed. Status: BUILT as reported; closes only on the founder's live re-ask of the Europe question.

## Entry 17 — D30 travel grounding fixed (Oct 27, 2026, ~11:24 PM ET)

Founder live find (10:39 PM): Ask M answered the Europe travel question "I do not see a filed rule…" — but the plan DOES cover travel (out-of-country: 30 days' notice, written itinerary ≥1 week before, passport cooperation; out-of-state: 7 days' notice). Root cause (Manus code trace): travel was not a recognized plan topic, so its provisions were excluded from the question-relevant excerpts before the model was called — the model never saw the travel pages. Fix (commit ef0ff347bb8045c5752328d9551905bf1507d8a2): travel retrieval now prioritizes operative plan clauses, recognizes natural child-trip phrasing, distinguishes domestic vs international (no passport terms demanded for an out-of-state trip), adds calendar-day notice-period comparisons, and drops fragment echoes. Reported live-engine regressions: the founder's scope returned cited international and Georgia (out-of-state) answers; the demo scope honestly returned no travel coverage (verified absent). Suite 220 passed / 1 skipped; TypeScript clean; production build passed; locked baseline 147cedc intact; no scope data written. Verified as reported by Muse — the in-thread final message is a condensed summary, so per the brief D30 closes ONLY on the founder's live re-ask of the Europe question.

## Entry 16 — D29 duplicate Home card removed (Oct 27, 2026, ~10:21 PM ET)

Founder live find (10:01 PM): Home carried two doors to the same place — the top "Ask M" banner and a grid card "Ask M About Your Plan." Removed the grid card only; banner, Today & upcoming, Compose, Reply, and Calendar untouched (founder confirmed the calendar looks great — explicit do-not-touch). Commit a71812a1de2f4408e9ddeb970e787d759fa584cd; suite 216 passed / 1 skipped; locked baseline 147cedc intact; UI-only, no data changes. Status: BUILT as reported; closes on the founder's live look at Home.
