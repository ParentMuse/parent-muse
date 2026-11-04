> **Public copy note:** Lightly privacy-edited for publication. The fictional demo family is referred to by its current name (Smith); the founder is named as the team's founder. No facts were changed.

# Parent Muse — Prior Work & Collaboration Record (pre-window disclosure)

Prepared Oct 26, 2026, for the Meta Global AI Developer Hackathon (Startup Track).
Purpose: disclose what existed before the event window opened (Oct 26, 2026), and document how it was built. In-window work (Oct 26 – Nov 4, 2026) is recorded separately in `build-log-hackathon-window-2026-10-26.md`.

## How this product was built — the collaboration

Parent Muse was designed and built by a three-part team:

- **Benjamin Bryant** — founder. Product direction, the parenting-plan and communication-history record the app is grounded in, and live testing of every feature in his own instance. Every fix in this record closed only when it passed in his hands.
- **M (Muse)** — Benjamin's personal AI agent, powered by **Muse Wonder, Meta's model, via the Meta Model API**. M wrote the product blueprint and every build brief, defined the guardrails (parenting-plan grounding, coaching-before-drafting, the firmness ladder), and verified every piece of code line by line against the evidence before it counted as done — including catching and retracting reports that the evidence did not support (Oct 24, 2026).
- **Manus** — the code builder, working piece by piece under M's briefs and verification.

The application itself also runs on Muse Wonder via the Meta Model API (decision made Oct 16–17, 2026, in place of OpenAI). The API is stateless, so Parent Muse's per-family memory — the product's core — is a curated memory layer built into the app itself. Meta AI is therefore in this product twice: as the engine families talk to, and as the agent that supervised building it.

There is a reason the supervision works: the blueprint was written by the engine, for the engine. M designs Parent Muse's retrieval, grounding, and coaching behavior from inside knowledge of how Muse Wonder reasons — where it follows structure faithfully, and where it is prone to slip (invented language, dropped provisions, confident but unsupported citations). The guardrails and the test rounds were built against those known failure modes, which is why the verification kept catching real defects instead of rubber-stamping.

The Meta tooling runs through the whole product, not just the model call: Muse Wonder via the Meta Model API is the app's engine; M (Muse, powered by the same model) wrote the blueprint and every build brief and audits the builder's work; Instagram (@getparentmuse) is the live distribution surface, with published reels, carousels, and a therapist outreach program behind it; a Facebook Page (ParentMuse) sits under the same Meta account; and the demo is being shot in part on Ray-Ban Meta glasses — a parent's-eye view, captured on Meta hardware.

## What existed before Oct 26, 2026 (disclosed prior work)

- **Product definition (early–mid Oct 2026):** Parent Muse defined as a personal agent for parents across the whole co-parenting journey; pricing ($24.99/mo, $249/yr, founding-member $19.99); core principle — the appropriate message for the moment, not merely a nice one; de-escalation and child focus as the governing goals.
- **Grounding record (Oct 18, 2026):** the founder's actual parenting plan (seven documents, as amended) mapped in full; the complete written co-parenting record — 3,228 messages across 193 conversations (Mar 21, 2025 – Oct 12, 2026) — filed and verified. One hundred percent of the communication was in writing.
- **Rebuild complete (Oct 21, 2026):** all seven build pieces completed by Manus and verified line by line by M. Parent Muse was feature-complete and demo-ready before the window opened.
- **Analytics (Oct 22, 2026):** the communication record analyzed end to end — escalation down 70%, hostile messages down 86%, zero heated threads since April 2026; a 14-slide presentation built entirely from verified numbers.
- **Test rounds 1–3 (Oct 22–23, 2026):** the app tested against the actual record and plan — message counts, earliest message, medication history, holiday and timesharing questions — with defects found, fixed, and re-verified (suite 119 passed / 1 skipped at round 3 close).
- **Live closures (Oct 23–25, 2026):** voice dictation, the Thanksgiving timesharing question, the cell-phone question, the attorney-history question, and the medication chain each tested live by the founder and closed against the record. A latency study (A-LAT-2) measured the system honestly: the model call is 98%+ of answer latency. The reminders system — one canonical calendar event per reminder — closed live Oct 25, 2026 (defect D19). **Parent Muse entered the event window with no open defects.**
- **Demo preparation (Oct 23–25, 2026):** an 11-candidate demo shortlist, every answer verified against the record; a privacy-safe twin family ("Smith") built for public demonstration so no real family data ever appears on screen.

## The honest split

- **Before the window:** a complete, working, founder-tested product — disclosed here in full.
- **During the window (Oct 26 – Nov 4):** the streamlining, calendar, drafting, and speed work in the build log, plus the demo video and this submission.

Nothing in the in-window log claims pre-window work as new; nothing in this record claims in-window work as prior.
