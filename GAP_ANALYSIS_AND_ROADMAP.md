# FRSC Mobility Course — Gap Analysis & Build Roadmap

**Source:** National Student Road Safety & Responsible Mobility Framework, Chapters 7–9 (v1.0)
**Purpose:** Identify everything the current `index.html` build is missing against the official framework, and prioritize what to build next.

---

## 🚨 Critical Correction (Content Bug)

**The certificate name in the current app is WRONG.**

| Current App Says | Framework Says |
|---|---|
| "Cubbes Digital Safety Certificate" | **"Cubbes Certified Road Safety & Responsible Mobility Certificate"** |

This appears in: `view-tracker` timeline, Module 15 quiz description, `home-progress-banner`, and all `.md` docs. **Fix this everywhere before anything else ships.**

---

## 🧩 Gap 1: We're Missing an Entire Phase (Phase 5)

The framework defines **5 phases**. The app only models 4.

### Phase 5: Continuous Safe Driver Development (NEW — not in app at all)

> "Road safety education should not end when a driver's licence is issued... the framework promotes lifelong learning through continued engagement with graduates."

**What needs to be added:**
- A 5th tab/section unlocked only after Phase 4 (licensing) is complete
- Framed as "Graduate Hub" or "Continuing Education" — not a locked/gated course, but an ongoing engagement space
- Content categories to build placeholders for:
  - Refresher learning modules
  - Road safety campaign participation (share/repost campaigns)
  - Advanced driving modules (e.g., highway mastery, eco-driving)
  - Electric vehicle awareness
  - Vehicle maintenance education
  - First aid refresher programmes
  - Insurance literacy
  - Safe mobility updates (news/announcements feed)
- Should reuse the existing module-card UI pattern but visually distinguished (e.g., a "Graduate" badge/theme) since it's post-licensing, not part of the pass/fail curriculum

**Why it matters:** This is the framework's core differentiator (see 7.3 table: "Focus on obtaining a licence" vs "Focus on lifelong safe mobility"). Without it, the app tells an incomplete story of the product's ambition.

---

## 🧩 Gap 2: Phase 1 Curriculum Content Needs Correction & Expansion

### 2a. Module descriptions need minor factual fixes

| Module | Current App Title | Framework Title |
|---|---|---|
| 5 | "Road Traffic Crashes: Causes & Prevention" | "Road Traffic Crashes: Causes, **Prevention & Responsibility**" |
| 11 | "Emergency Response & First Aid" | "Emergency Response, First Aid **& Fire Safety**" |
| 12 | (topics listed) | Add: **insurance fundamentals** as an explicit topic |

### 2b. "Core Learning Areas" framing (§7.1) doesn't fully match the 15-module table (§8.3)

The framework lists Phase 1 at a *thematic* level in Chapter 7 (10 areas, including "Sustainable & Responsible Mobility" and "Insurance & Risk Awareness (optional future module)") separately from the *module-by-module* breakdown in Chapter 8 (15 modules). The app currently only reflects the Chapter 8 module list. Consider:
- Adding "Insurance & Risk Awareness" as a visible **future module** placeholder (locked, "Coming Soon" badge) — this is explicitly called out as an optional future addition, so showing it (locked) sets accurate expectations.
- Module 13 currently reads "Digital Navigation & Responsible Mobility" — framework confirms this is Cubbes-original content (no FRSC alignment code), which the app already reflects correctly via the blank FRSC alignment. Good — no change needed there.

### 2c. Assessment philosophy isn't reflected in the UI

Framework §8.5 explicitly states: *"Assessment is designed to evaluate understanding, judgement, and application, not memorisation."* Currently every module has exactly **one** multiple-choice question. To align with the stated philosophy, the roadmap should include:
- **Scenario-based decision exercises** (not just MCQ) — e.g., "You're approaching a flooded junction at night, what do you do?" with branching outcomes
- **Hazard perception video exercises** — click/tap when a hazard appears (this is explicitly named in §8.2 and §9.4)
- Personalized recommendations after quiz failure via Ask Cubbes AI (see Gap 4)

---

## 🧩 Gap 3: Gamification Is Named But Not Built

Framework §7.1 and §8.2 explicitly list these engagement mechanics — the app only has a basic XP counter today.

| Feature | Framework Reference | Current State | Needed |
|---|---|---|---|
| XP / Points | §8.2 | ✅ Partially built (static "240 XP", +20 per quiz) | Persist across sessions, show XP history |
| **Learning streaks** | §7.1, §9.5 | ❌ Not built | Daily streak counter, "🔥 5 day streak" badge |
| **Achievement badges** | §7.1, §9.5 | ❌ Not built | Badge gallery (e.g., "Module Master", "Perfect Score", "Early Bird") |
| **Course completion milestones** | §7.1 | ❌ Not built | Milestone celebrations at 25%/50%/75%/100% |
| **University leaderboards** | §7.1 | ❌ Not built | Ranked list of students by XP within their institution |
| **"Sparks" or alternate reward currency** | §7.1 | ❌ Not built | Framework leaves this open — flag as a design decision, not urgent |

**Recommendation:** Build streaks + badges first (cheap, high engagement value); leaderboards require backend (see Gap 9).

---

## 🧩 Gap 4: "Ask Cubbes AI" Is a Toy Demo, Not What the Framework Describes

Current implementation: a text input that fires a `setTimeout` and always returns the same canned sentence.

Framework §9.4 describes **seven distinct AI capabilities**:

| Capability | In App Today? |
|---|---|
| Clarify road safety concepts | ⚠️ Fake (hardcoded response) |
| Explain traffic signs and regulations | ❌ No |
| Personalised study support | ❌ No |
| **Practice examination questions** | ❌ No — this implies an AI-generated practice quiz mode |
| **Review assessment performance** | ❌ No — AI should look at *your* quiz history and comment |
| Explore real-life driving scenarios | ❌ No |
| Recommended learning resources | ❌ No |

**What to build:**
1. Replace the fake `setTimeout` with a real LLM call (Claude API) — this is the single highest-leverage upgrade to the app's credibility
2. Feed the AI context: current module content + the student's quiz history + which modules they've struggled with
3. Add a distinct "Practice Exam" mode inside the AI panel — AI generates novel questions from module content instead of the single hardcoded quiz question
4. Add a "Review My Performance" button that summarizes strengths/weaknesses across completed modules

---

## 🧩 Gap 5: Digital Certification Is Not Actually Implemented

Framework §9.6 is specific about what a certificate must contain. The app currently only *mentions* a certificate name in text — there's no certificate object, generation, or display anywhere.

**Required certificate fields (§9.6):**
- [ ] Student identity (name)
- [ ] Institution
- [ ] Completion status
- [ ] Date of completion
- [ ] Verification reference (unique ID)
- [ ] QR code for authenticity *(explicitly flagged as future, so can stub this)*

**What to build:**
- A `view-certificate` screen, unlocked when Module 15 is passed at 80%+
- Renders as a printable/downloadable certificate (HTML → PDF via browser print, or canvas-to-image)
- Includes a mock verification reference (e.g., `CUBBES-2026-XXXXXX`)
- Placeholder QR code (can be a static styled div until real verification backend exists)

---

## 🧩 Gap 6: No Notification System

Framework §9.7 lists 7 notification triggers. The app has zero notification infrastructure — it's a single-session, no-persistence page.

**Notification triggers needed (§9.7):**
- Upcoming lessons
- Assessment deadlines
- Simulator bookings
- Practical driving schedules
- Learning milestones
- Certificate availability
- Programme announcements

**What to build (frontend-only approximation, since real push notifications need a backend + service worker):**
- An in-app notification bell icon in the header with a dropdown feed
- Simulate the 7 trigger types as static/generated in-app messages tied to state changes (e.g., completing module 15 → "🎓 Certificate available!" notification appears)
- This is a good "looks real" MVP before wiring actual email/SMS/push (which needs backend — see Gap 9)

---

## 🧩 Gap 7: Simulation & Driving School Sections Need to Move from "Static Info" to "Tracked State"

The last app update (Simulation & Practical Training content) added great *descriptive* content, but per §9.8–9.9 the platform is supposed to actually **track** state, not just display brochure copy.

| Framework Requirement (§9.8) | Current State |
|---|---|
| View available simulator locations | ✅ Static dropdown |
| Select preferred dates/times | ✅ Static dropdown |
| Receive booking confirmations | ⚠️ `alert()` only, not persisted |
| **Track simulator completion** | ❌ No state at all |
| **Access readiness assessments** | ❌ No assessment exists — just a line of text saying it's "included" |

| Framework Requirement (§9.9) | Current State |
|---|---|
| Search for nearby driving schools | ⚠️ Static list, no search/filter |
| Compare available training locations | ❌ No comparison view |
| View available schedules | ❌ No real schedule — just a "Select" button |
| Book practical training sessions | ⚠️ `alert()` only |
| **Track attendance** | ❌ Not built |
| **Monitor practical training progress** | ❌ Not built |

**What to build:**
- A `studentState` object tracking: `simulatorBooked`, `simulatorCompleted`, `readinessAssessmentScore`, `drivingSchoolSelected`, `attendanceLog[]`, `practicalHoursCompleted`
- A real (even if simulated) **Driving Readiness Assessment** — a 5–10 question hazard-perception mini quiz that produces a pass/fail + score, gating Phase 3 access
- An attendance log UI for practical training (date, hours, instructor sign-off checkbox) — even a manually-entered log is a big step up from nothing
- Progress bars for Phase 2 and Phase 3 (mirroring the Phase 1 progress bar already on Home)

---

## 🧩 Gap 8: Licensing Tracker Is Cosmetic, Not Functional

Framework §9.10 lists 6 things students should be able to track. The current `view-tracker` is a hardcoded, non-interactive timeline — it never changes regardless of what the student actually does in the app.

**What's needed:**
- Eligibility status → should be **computed** from `studentState` (e.g., "Not yet eligible — complete Module 15" vs "Eligible")
- Required documentation → convert the current static checklist into `localStorage`-backed checkboxes that persist
- Learner permit progress → new state field, currently doesn't exist anywhere
- Practical training completion → pull from Gap 7's `attendanceLog`
- Licensing application status → new state field (`not_started` / `documents_submitted` / `appointment_booked` / `interview_complete` / `licensed`)
- Outstanding requirements → a computed "what's left" list rather than a static checklist

This turns the Tracker tab from a marketing timeline into an actual product feature.

---

## 🧩 Gap 9: Everything Above Needs a Backend (This Is the Real Elephant in the Room)

The current app is a **single static HTML file with in-memory JavaScript state** — it resets on every page refresh. Almost every gap above (streaks, badges, leaderboards, certificates, notifications, attendance tracking, licensing status) fundamentally requires **persistence and, eventually, multi-user accounts**.

Framework §9.13 explicitly requires:
- Secure user authentication
- Encrypted data transmission
- **Role-based access controls** — 4 distinct roles are implied throughout Ch. 9: **Student**, **University**, **Driving School**, **FRSC** — each needs a different dashboard (§9.11, deferred to their Chapter 10)
- Student consent management
- Audit trails
- Nigerian data protection compliance

**Recommendation — pick one path:**
1. **Fast/cheap MVP path:** Use `localStorage` to fake persistence per-browser (no real accounts, no cross-device sync) — good enough to demo Gaps 3, 5, 6, 7, 8 without backend work
2. **Real path:** Stand up a lightweight backend (matches your stated preference for spreadsheet-backed MVPs — Google Sheets + Apps Script could model student records, attendance, and certificate issuance cheaply) with simple auth (magic link or student email + institution code)
3. **Production path:** Full auth + database + role-based dashboards for University/Driving School/FRSC per §9.11 (Chapter 10, not yet reviewed — request that chapter next if this path is chosen)

Given prior context that you generally prefer Sheets+Apps Script for quick MVPs over full backends, **path 2 is likely the right next step** once you're ready to move past the static demo.

---

## 🧩 Gap 10: Missing Interactive Learning Formats

Framework §8.2 names specific interaction types beyond video+text+quiz that the app doesn't have:

| Format | Framework Ref | Built? |
|---|---|---|
| Animated explainers | §8.2, §9.3 | ❌ (would need actual animation assets) |
| **Drag-and-drop traffic sign activities** | §8.2, §8.4 (Module 3) | ❌ Module 3 explicitly calls this out and it's missing |
| Interactive hazard perception videos | §8.2, §9.4 | ❌ (currently just a passive YouTube embed) |
| Mini games | §8.2 | ❌ |
| Adaptive learning recommendations | §9.3 | ❌ (needs AI, see Gap 4) |

**Highest-value pick:** Module 3 (Traffic Signs) explicitly requires drag-and-drop in the source doc — this is the one interactive format with a specific module citation, so it's the most defensible one to build first as a proof of concept for the "beyond video/quiz" interaction model.

---

## 📊 Priority Matrix — What to Build Next

### 🟢 Do immediately (content-only, no new engineering)
1. Fix certificate name everywhere ("Cubbes Certified Road Safety & Responsible Mobility Certificate")
2. Fix Module 5 and Module 11 titles to match framework exactly
3. Add "Insurance & Risk Awareness" as a visible locked/future module

### 🟡 Do next (frontend-only, `localStorage`, no backend needed)
4. Real Driving Readiness Assessment (mini quiz gating Phase 3)
5. Learning streaks + achievement badges
6. Persist quiz/progress state via `localStorage` so refresh doesn't wipe progress
7. Functional (computed, not static) Licensing Tracker
8. Certificate screen with mock verification reference
9. In-app notification feed (simulated triggers)
10. Drag-and-drop activity for Module 3

### 🟠 Do after (needs real backend / AI API)
11. Real Claude API integration for Ask Cubbes AI (biggest credibility upgrade)
12. AI-generated practice exam mode
13. AI performance review across quiz history
14. University leaderboard (needs multi-user data)
15. Attendance log with instructor sign-off (needs shared record between student + driving school)

### 🔴 Do last (major scope — needs Chapter 10 + stakeholder input)
16. Phase 5: Continuous Safe Driver Development section
17. Multi-role dashboards (University / Driving School / FRSC) per §9.11
18. Real user authentication & role-based access
19. FRSC/driving-school system integrations (§9.12)

---

## ❓ Open Question for You

Chapter 9 repeatedly references **"Chapter 10"** for dashboards/analytics (§9.11) — that content wasn't included in what you pasted. If you have it, sharing it would let me fold the University/Driving School/FRSC dashboard requirements into this same roadmap instead of guessing at scope.

---

**Next step:** Tell me which priority tier to start building, and I'll implement it directly in `index.html` (or spin up the `localStorage`/backend layer if you're ready to move off the single-file demo).
