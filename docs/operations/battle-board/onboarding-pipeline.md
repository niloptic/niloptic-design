# Program Onboarding Pipeline

> **Last Updated:** 2026-03-04
> **Owner:** Operations / Customer Success
> **Classification:** Internal — Confidential

---

## Overview

This document defines the complete onboarding pipeline for NCAA programs entering the NIL Optic platform. Every program — regardless of division, conference, or sport — follows this pipeline. Basketball programs follow an accelerated track with sport-specific onboarding steps.

The pipeline is linear by default. Programs must progress through each stage sequentially. Reverse transitions are allowed (e.g., Demo Scheduled back to Outreach if a demo is cancelled), but stage-skipping is not permitted.

---

## Pipeline Stages

```
  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
  │              │    │              │    │              │
  │ UNCONTACTED  │───>│  OUTREACH    │───>│    DEMO      │
  │              │    │              │    │  SCHEDULED   │
  └──────────────┘    └──────────────┘    └──────────────┘
                                                │
                                                v
  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
  │              │    │              │    │              │
  │   CHURNED    │<───│  ONBOARDED   │<───│    TRIAL     │
  │              │    │   (ACTIVE)   │    │   ACTIVE     │
  └──────────────┘    └──────────────┘    └──────────────┘
         │                                       │
         │            ┌──────────────┐           │
         └───────────>│   WIN-BACK   │<──────────┘
                      │  (Re-entry)  │  (if trial fails)
                      └──────────────┘
```

---

### Stage 1: Uncontacted

**Definition:** Program exists in the NCAA registry but no outreach has been attempted.

| Attribute | Detail |
|-----------|--------|
| **Stage Code** | `UNCONTACTED` |
| **Entry Criteria** | Program exists in NCAA basketball registry |
| **Required Data** | School name, conference, division, sport, estimated NIL potential |
| **Owner** | Sales Team (pooled) |
| **SLA** | None — this is the backlog |
| **Exit Criteria** | First outreach touchpoint logged (email, call, or referral) |
| **Automated Actions** | None |
| **Dashboard Color** | Gray (`#6B7280`) |

**Data Requirements at Entry:**

| Field | Required | Source |
|-------|----------|--------|
| School name | Yes | Registry |
| Conference | Yes | Registry |
| Division | Yes | Registry |
| Sport (Basketball) | Yes | Registry |
| Estimated NIL budget | Yes | Market research / SportsRadar |
| Primary contact | No | To be researched |
| AD name | No | Public directory |

**Notes:**
- All programs enter the system at this stage via the NCAA Basketball Registry
- Programs remain here until an AE is assigned and makes first contact
- Priority tier determines when a program gets activated from this stage
- Tier A programs should not remain Uncontacted for more than 2 weeks after system launch

---

### Stage 2: Outreach

**Definition:** Initial contact has been made with the program's Athletic Director, compliance officer, or other decision-maker.

| Attribute | Detail |
|-----------|--------|
| **Stage Code** | `OUTREACH` |
| **Entry Criteria** | First email, call, or referral sent to AD or compliance officer |
| **Required Data** | Primary contact name, email, phone, title |
| **Owner** | Account Executive (assigned) |
| **SLA** | Follow up within 3 business days of initial contact |
| **Exit Criteria** | Demo meeting scheduled with decision-maker |
| **Automated Actions** | Email sequence triggered; CRM task created for follow-up |
| **Dashboard Color** | Orange (`#F59E0B`) |

**Data Requirements at Entry:**

| Field | Required | Source |
|-------|----------|--------|
| Primary contact name | Yes | Research / referral |
| Primary contact email | Yes | Research / referral |
| Primary contact phone | Preferred | Research / referral |
| Primary contact title | Yes | Research / referral |
| Assigned AE | Yes | Assignment engine |
| Outreach channel | Yes | AE logs (email/call/referral) |
| First contact date | Yes | Auto-logged |

**Outreach Cadence by Tier:**

| Tier | Initial Outreach | Follow-up 1 | Follow-up 2 | Follow-up 3 | Escalation |
|------|-----------------|-------------|-------------|-------------|------------|
| A | Day 0 | Day 3 | Day 7 | Day 14 | Day 21 (VP level) |
| B | Day 0 | Day 5 | Day 12 | Day 21 | Day 30 (VP level) |
| C | Day 0 | Day 7 | Day 21 | Day 45 | Archive after 60 |
| D | Day 0 | Day 14 | Day 45 | — | Archive after 60 |

**Automated Email Sequence:**

1. **Email 1 (Day 0):** Introduction to NIL Optic — personalized to school and conference
2. **Email 2 (Day 3-5):** Case study from peer institution in same conference
3. **Email 3 (Day 7-12):** NIL market data specific to their conference and division
4. **Email 4 (Day 14-21):** Direct ask for 15-minute demo with conference-specific deck
5. **Email 5 (Day 21-30):** Final follow-up with limited-time pilot offer

---

### Stage 3: Demo Scheduled

**Definition:** The Athletic Director or other decision-maker has agreed to see the NIL Optic platform in a live demonstration.

| Attribute | Detail |
|-----------|--------|
| **Stage Code** | `DEMO_SCHEDULED` |
| **Entry Criteria** | AD or decision-maker agreed to a product demonstration |
| **Required Data** | Demo date/time, attendee list, program priorities, conference context |
| **Owner** | Account Executive + Solutions Engineer |
| **SLA** | Demo within 5 business days of scheduling |
| **Exit Criteria** | Demo completed and trial agreed upon |
| **Automated Actions** | Calendar invite sent; demo prep checklist triggered; conference deck generated |
| **Dashboard Color** | Blue (`#3B82F6`) |

**Data Requirements at Entry:**

| Field | Required | Source |
|-------|----------|--------|
| Demo date/time | Yes | AE scheduling |
| Attendee list | Yes | AE confirmed with contact |
| Program priorities | Preferred | Pre-demo questionnaire |
| Decision timeline | Preferred | AE discovery call |
| Budget authority | Preferred | AE discovery call |
| Conference context | Yes | Auto-generated from registry |

**Demo Preparation Checklist:**

- [ ] Conference-specific slide deck prepared
- [ ] School branding applied to demo environment
- [ ] Sample roster data loaded (from SportsRadar)
- [ ] NIL valuation examples generated for top players
- [ ] Competitor analysis for their conference prepared
- [ ] Pricing proposal drafted based on tier
- [ ] Solutions Engineer briefed on school-specific needs
- [ ] Calendar invite sent with agenda and video link
- [ ] Pre-demo questionnaire sent to attendees
- [ ] Demo recording setup confirmed

**Demo Structure (45 minutes):**

| Segment | Duration | Content |
|---------|----------|---------|
| Introduction | 5 min | Team intros, agenda, school-specific context |
| Platform Overview | 10 min | Dashboard tour with their conference data |
| Basketball Deep-Dive | 15 min | Roster valuations, transfer portal, compliance |
| ROI Discussion | 10 min | Cost-benefit analysis, peer benchmarks |
| Next Steps | 5 min | Trial setup, timeline, decision process |

---

### Stage 4: Trial Active

**Definition:** A pilot account has been created for the program. Data is loaded, users are invited, and the program is actively evaluating the platform.

| Attribute | Detail |
|-----------|--------|
| **Stage Code** | `TRIAL_ACTIVE` |
| **Entry Criteria** | Account created, initial data loaded, users invited |
| **Required Data** | Trial start date, end date, success criteria, assigned CSM |
| **Owner** | Customer Success Manager |
| **SLA** | Check-in at Day 3, Day 7, Day 14, Day 21 |
| **Exit Criteria** | Contract signed and payment processed |
| **Automated Actions** | Account provisioned; onboarding email sequence; usage tracking enabled |
| **Dashboard Color** | Yellow (`#EAB308`) |

**Data Requirements at Entry:**

| Field | Required | Source |
|-------|----------|--------|
| Trial start date | Yes | Auto on account creation |
| Trial end date | Yes | Start + 30 days (default) |
| Success criteria | Yes | CSM defined with AD |
| Assigned CSM | Yes | Assignment engine |
| Primary users (names/emails) | Yes | AD provides |
| Basketball roster loaded | Yes | SportsRadar sync |
| Initial valuations generated | Yes | Auto on roster load |

**Trial Timeline:**

```
Day 0          Day 3         Day 7          Day 14         Day 21        Day 30
  │              │             │              │              │              │
  ▼              ▼             ▼              ▼              ▼              ▼
Account       Check-in 1    Check-in 2     Check-in 3    Check-in 4    Trial Ends
Created       (Adoption)    (Value Demo)   (Expansion)   (Close Prep)  (Decision)
  │              │             │              │              │              │
  │  Roster      │  Feature    │  Report      │  Contract    │  Final       │
  │  loaded      │  training   │  delivered   │  discussion  │  proposal    │
  │  Users       │  Q&A        │  ROI review  │  Objection   │  sent        │
  │  invited     │  session    │              │  handling    │              │
```

**Trial Check-in Schedule:**

| Check-in | Timing | Purpose | Owner | Deliverable |
|----------|--------|---------|-------|-------------|
| Check-in 1 | Day 3 | Confirm adoption — are users logging in? | CSM | Usage report |
| Check-in 2 | Day 7 | Demonstrate value — walkthrough of first week's data | CSM | Insight report |
| Check-in 3 | Day 14 | Expand use case — show additional features | CSM + AE | Expansion proposal |
| Check-in 4 | Day 21 | Close preparation — discuss contract terms | AE + CSM | Contract draft |

**Trial Success Metrics:**

| Metric | Target | Measurement |
|--------|--------|-------------|
| DAU (Daily Active Users) | 3+ users per week | Platform analytics |
| Logins per week | 5+ total | Platform analytics |
| Features explored | 4+ feature areas | Platform analytics |
| Reports generated | 2+ valuation reports | Platform analytics |
| Stakeholder NPS | 7+ (out of 10) | Day 14 survey |

---

### Stage 5: Onboarded (Active)

**Definition:** The program has signed a contract, processed payment, and is a fully active paying customer on the NIL Optic platform.

| Attribute | Detail |
|-----------|--------|
| **Stage Code** | `ONBOARDED` |
| **Entry Criteria** | Contract signed, payment processed, full team access granted |
| **Required Data** | Contract value, term, renewal date, primary users, billing info |
| **Owner** | Customer Success Manager |
| **SLA** | QBR (Quarterly Business Review) every 90 days |
| **Exit Criteria** | Contract expiration or cancellation (transitions to Churned) |
| **Automated Actions** | Billing activated; full feature access; QBR scheduling; health scoring |
| **Dashboard Color** | Green (`#16A34A`) |

**Data Requirements at Entry:**

| Field | Required | Source |
|-------|----------|--------|
| Contract value (ACV) | Yes | Signed contract |
| Contract term | Yes | Signed contract |
| Contract start date | Yes | Signed contract |
| Renewal date | Yes | Calculated from term |
| Payment method | Yes | Billing system |
| Full user list | Yes | AD provides |
| Success criteria (ongoing) | Yes | QBR defined |
| Executive sponsor | Yes | CSM identifies |

**Active Account Health Score:**

| Factor | Weight | Measurement | Healthy | At Risk | Critical |
|--------|--------|-------------|---------|---------|----------|
| Login frequency | 25% | Weekly logins / expected | 80%+ | 50-79% | <50% |
| Feature adoption | 25% | Features used / available | 60%+ | 40-59% | <40% |
| Support tickets | 15% | Tickets per month | 0-2 | 3-5 | 6+ |
| NPS score | 20% | Latest survey | 8-10 | 6-7 | 1-5 |
| Engagement trend | 15% | 30-day usage trend | Increasing | Flat | Declining |

**QBR Agenda:**

1. Usage metrics review (30-day, 90-day trends)
2. ROI analysis (NIL deals facilitated, compliance events prevented)
3. Feature adoption gaps and training opportunities
4. Product roadmap preview and feedback collection
5. Renewal discussion and expansion opportunities
6. Multi-sport cross-sell (if basketball-only)

---

### Stage 6: Churned

**Definition:** The program was previously an active paying customer but has let their contract expire or actively cancelled.

| Attribute | Detail |
|-----------|--------|
| **Stage Code** | `CHURNED` |
| **Entry Criteria** | Contract expired without renewal, or cancellation processed |
| **Required Data** | Churn reason, last activity date, win-back potential score, churn date |
| **Owner** | Account Executive (win-back assignment) |
| **SLA** | Win-back attempt within 30 days of churn |
| **Exit Criteria** | Re-enters at Outreach (win-back) or permanently archived |
| **Automated Actions** | Churn survey sent; win-back sequence triggered; health score archived |
| **Dashboard Color** | Red (`#DC2626`) |

**Data Requirements at Entry:**

| Field | Required | Source |
|-------|----------|--------|
| Churn date | Yes | Auto on contract expiration/cancel |
| Churn reason (primary) | Yes | Exit survey / CSM notes |
| Churn reason (secondary) | Preferred | Exit survey / CSM notes |
| Last activity date | Yes | Platform analytics |
| Contract value at churn | Yes | Billing records |
| Win-back potential | Yes | Scored by CSM (1-10) |
| Competitor switch | Preferred | Exit survey / intel |

**Churn Reason Categories:**

| Code | Reason | Win-Back Likelihood |
|------|--------|-------------------|
| `BUDGET` | Budget constraints or cuts | High — revisit at fiscal year |
| `VALUE` | Didn't see enough value | Medium — needs re-demo with updates |
| `CHAMPION_LEFT` | Key champion left the program | Medium — find new champion |
| `COMPETITOR` | Switched to competitor | Low — needs competitive displacement |
| `COMPLIANCE` | Compliance or institutional policy | Low — institutional barrier |
| `REORGANIZATION` | Staff/department reorganization | Medium — wait for stability |
| `FEATURE_GAP` | Missing critical features | High — address in roadmap |
| `SUPPORT` | Poor support experience | High — escalate and resolve |

**Win-Back Sequence:**

| Step | Timing | Action | Owner |
|------|--------|--------|-------|
| 1 | Day 0 (churn) | Automated exit survey sent | System |
| 2 | Day 7 | Personal outreach from VP of CS | VP CS |
| 3 | Day 14 | Win-back offer with updated features | AE |
| 4 | Day 30 | Final win-back attempt | AE |
| 5 | Day 60 | Move to quarterly nurture cadence | Marketing |
| 6 | Day 90+ | Quarterly check-in with platform updates | Marketing |

---

## Stage Transition Rules

### Forward Transitions

| From | To | Required Actions | Approver |
|------|----|-----------------|----------|
| Uncontacted | Outreach | First contact logged, AE assigned | AE |
| Outreach | Demo Scheduled | Demo date confirmed with decision-maker | AE |
| Demo Scheduled | Trial Active | Demo completed, trial approved, account created | AE + CSM |
| Trial Active | Onboarded | Contract signed, payment processed | AE + Finance |

### Reverse Transitions

| From | To | Trigger | Required Actions |
|------|----|---------|-----------------|
| Demo Scheduled | Outreach | Demo cancelled or no-show | Reschedule attempted, reason logged |
| Trial Active | Outreach | Trial abandoned or declined | Exit survey, churn risk noted |
| Trial Active | Demo Scheduled | Trial paused, needs re-demo | New demo scheduled |
| Onboarded | Churned | Contract expired or cancelled | Churn survey, win-back initiated |
| Churned | Outreach | Win-back accepted | New AE assigned, fresh outreach |

### Rules

1. **No stage skipping.** A program cannot jump from Uncontacted to Trial Active. Every stage must be entered and exited properly.
2. **Reverse transitions require documentation.** Every backward move must include a reason and next-action plan.
3. **Churned programs re-enter at Outreach.** They do not return to their previous stage. Fresh pipeline, fresh approach.
4. **AE handoff to CSM occurs at Trial Active.** The AE remains involved through onboarding but CSM takes primary ownership.
5. **Finance approval required for Onboarded.** Contract must be countersigned and payment confirmed before marking Onboarded.

---

## Basketball-First Onboarding Checklist

When a basketball program enters the Trial Active stage, the following checklist must be completed within the first 7 days of the trial. This checklist is specific to basketball and is in addition to the standard platform onboarding.

### Checklist

| # | Task | Owner | Target | Verification |
|---|------|-------|--------|-------------|
| 1 | Basketball roster imported from SportsRadar | CSM | Day 0 | All players visible in roster view |
| 2 | Player NIL valuations generated | System | Day 0 | Valuation scores populated for 100% of roster |
| 3 | Conference standings connected | CSM | Day 1 | Live standings displayed in conference view |
| 4 | Tournament bracket data linked | CSM | Day 1 | Bracket position and seed visible (if in-season) |
| 5 | Transfer portal monitoring enabled | CSM | Day 2 | Portal alerts active, incoming/outgoing tracked |
| 6 | Compliance dashboard configured | CSM | Day 2 | State-specific NIL rules loaded, alerts active |
| 7 | Budget allocation set for basketball program | CSM + AD | Day 3 | NIL budget entered and allocation model active |
| 8 | Coaches and staff invited to platform | CSM | Day 3 | All users have active accounts with correct roles |
| 9 | First valuation report delivered | CSM | Day 5 | PDF/dashboard report shared with AD |
| 10 | 30-day check-in scheduled | CSM | Day 7 | Calendar invite confirmed with AD and key staff |

### Checklist Completion Tracking

```
+========================================================================+
|  BASKETBALL ONBOARDING — [School Name]                                 |
|  Trial Start: 2026-03-01  |  CSM: M. Johnson  |  AE: K. Davis         |
+========================================================================+
|                                                                        |
|  Progress: 7 of 10 complete  [===========>........]  70%               |
|                                                                        |
|  [x] 1. Basketball roster imported              Day 0  ✓              |
|  [x] 2. Player NIL valuations generated         Day 0  ✓              |
|  [x] 3. Conference standings connected          Day 1  ✓              |
|  [x] 4. Tournament bracket data linked          Day 1  ✓              |
|  [x] 5. Transfer portal monitoring enabled      Day 2  ✓              |
|  [x] 6. Compliance dashboard configured         Day 2  ✓              |
|  [x] 7. Budget allocation set                   Day 3  ✓              |
|  [ ] 8. Coaches and staff invited               Day 3  PENDING        |
|  [ ] 9. First valuation report delivered        Day 5  UPCOMING       |
|  [ ] 10. 30-day check-in scheduled             Day 7  UPCOMING       |
|                                                                        |
|  Blockers: Waiting on AD to provide staff email list (item 8)         |
|  Next Action: Follow up with AD for staff list by EOD 2026-03-04      |
|                                                                        |
+========================================================================+
```

---

## Metrics & KPIs

### Pipeline Performance Metrics

| Metric | Definition | Target | Measurement |
|--------|-----------|--------|-------------|
| **Outreach → Demo Conversion** | % of contacted programs that schedule a demo | 35%+ | Monthly |
| **Demo → Trial Conversion** | % of demos that convert to active trials | 50%+ | Monthly |
| **Trial → Onboard Conversion** | % of trials that convert to paying customers | 65%+ | Monthly |
| **Full Funnel Conversion** | % of Outreach that reach Onboarded | 12%+ | Quarterly |
| **Average Days in Outreach** | Mean days from first contact to demo scheduled | <10 days | Weekly |
| **Average Days in Demo** | Mean days from demo scheduled to trial start | <5 days | Weekly |
| **Average Days in Trial** | Mean days from trial start to contract signed | <25 days | Weekly |
| **Total Sales Cycle** | Mean days from first contact to onboarded | <40 days | Monthly |

### Revenue Metrics

| Metric | Definition | Target | Measurement |
|--------|-----------|--------|-------------|
| **Revenue Per Active Program (Tier A)** | ACV for Power 4 basketball programs | $12,000+ | Per contract |
| **Revenue Per Active Program (Tier B)** | ACV for high-major basketball programs | $8,000+ | Per contract |
| **Revenue Per Active Program (Tier C)** | ACV for mid-major basketball programs | $6,000+ | Per contract |
| **Revenue Per Active Program (Tier D)** | ACV for D2/D3/NAIA programs | $1,500-3,000 | Per contract |
| **Pipeline Revenue** | Total projected revenue in pipeline | Tracked weekly | CRM |
| **Monthly Recurring Revenue** | MRR from all active programs | Growth target | Billing |
| **Net Revenue Retention** | Revenue retained + expansion - churn | 110%+ | Quarterly |

### Operational Metrics

| Metric | Definition | Target | Measurement |
|--------|-----------|--------|-------------|
| **Pipeline Velocity** | Programs moving through full funnel per month | 15+/month | Monthly |
| **AE Productivity** | Demos scheduled per AE per week | 3+/week | Weekly |
| **CSM Health Score** | Average health score across active accounts | 7.5+ | Monthly |
| **Churn Rate** | % of onboarded programs lost per quarter | <5% | Quarterly |
| **Win-Back Success Rate** | % of churned programs re-activated | 20%+ | Quarterly |
| **Time to First Value** | Days from trial start to first report delivered | <5 days | Per trial |
| **Onboarding Checklist Completion** | % of checklist items complete within SLA | 90%+ | Per trial |

### Churn Analysis

| Metric | Definition | Target | Measurement |
|--------|-----------|--------|-------------|
| **Gross Churn Rate** | Programs churned / total active (quarterly) | <5% | Quarterly |
| **Revenue Churn Rate** | Revenue lost to churn / total ARR (quarterly) | <3% | Quarterly |
| **Logo Churn by Tier** | Churn rate broken out by priority tier | Varies | Quarterly |
| **Top Churn Reasons** | Most common churn reason categories | Track top 3 | Quarterly |
| **Win-Back Pipeline** | Churned programs with active win-back attempts | 50%+ | Monthly |

---

## Admin Battle Board Dashboard

The admin dashboard is the single-pane-of-glass view for sales leadership. It combines pipeline status, activity tracking, conference penetration, AE performance, and revenue forecasting.

### ASCII Wireframe

```
+========================================================================+
|  NIL OPTIC BATTLE BOARD — ADMIN DASHBOARD                              |
|  Last Refresh: 2026-03-04 09:15 AM  |  User: VP Sales  |  [Refresh]  |
+========================================================================+
|                                                                        |
|  TOTAL PIPELINE SUMMARY                                                |
|  +----------+ +----------+ +----------+ +----------+ +----------+     |
|  |          | |          | |          | |          | |          |     |
|  | UNCONT.  | | OUTREACH | | DEMO     | | TRIAL    | | ACTIVE   |     |
|  |          | |          | |          | |          | |          |     |
|  |   310    | |    26    | |    10    | |     6    | |     6    |     |
|  |          | |          | |          | |          | |          |     |
|  | -------- | | -------- | | -------- | | -------- | | -------- |     |
|  | 86.1%    | |  7.2%    | |  2.8%    | |  1.7%    | |  1.7%    |     |
|  +----------+ +----------+ +----------+ +----------+ +----------+     |
|                                                                        |
|  Churned: 0  |  Total Registry: 360 D1 programs                       |
|  Pipeline Revenue: $134,960 projected ARR                              |
|                                                                        |
+------------------------------------------------------------------------+
|                                                                        |
|  THIS WEEK'S ACTIVITIES                            Week of 2026-03-02  |
|  +------------------------------------------------------------------+  |
|  |                                                                  |  |
|  |  Demos Scheduled This Week:     4                                |  |
|  |    - Auburn (SEC) — Tue 3/4 — AE: Davis                         |  |
|  |    - Florida (SEC) — Wed 3/5 — AE: Smith                        |  |
|  |    - Michigan (B10) — Thu 3/6 — AE: Chen                        |  |
|  |    - Duke (ACC) — Fri 3/7 — AE: Patel                           |  |
|  |                                                                  |  |
|  |  Trials Starting This Week:     2                                |  |
|  |    - Purdue (B10) — Started 3/3 — CSM: Johnson                  |  |
|  |    - Oregon (B10) — Starting 3/5 — CSM: Williams                |  |
|  |                                                                  |  |
|  |  Conversions This Week:         1                                |  |
|  |    - Tennessee (SEC) — Trial → Onboarded — $12,000 ACV          |  |
|  |                                                                  |  |
|  |  At-Risk Trials:                1                                |  |
|  |    - LSU (SEC) — Low adoption (2 logins in 7 days)              |  |
|  |                                                                  |  |
|  +------------------------------------------------------------------+  |
|                                                                        |
+------------------------------------------------------------------------+
|                                                                        |
|  CONFERENCE LEADERBOARD                  SPORT: Basketball             |
|  +------------------------------------------------------------------+  |
|  |  Rank | Conference | Coverage | Active | Pipeline | Potential     |  |
|  |  -----+------------+----------+--------+----------+----------     |  |
|  |    1  | SEC        |    19%   |    3   |     5    |  $192K        |  |
|  |    2  | Big Ten    |    11%   |    2   |     4    |  $216K        |  |
|  |    3  | ACC        |     6%   |    1   |     2    |  $216K        |  |
|  |    4  | Big 12     |     0%   |    0   |     1    |  $192K        |  |
|  |    5  | AAC        |     0%   |    0   |     0    |  $104K        |  |
|  |    6  | MWC        |     0%   |    0   |     0    |   $88K        |  |
|  |    7  | WCC        |     0%   |    0   |     0    |   $80K        |  |
|  |    8  | A-10       |     0%   |    0   |     0    |  $120K        |  |
|  |  ...  | ...        |    ...   |   ...  |    ...   |   ...         |  |
|  +------------------------------------------------------------------+  |
|  Sorted by: Coverage %  |  [Show All Conferences]                      |
|                                                                        |
+------------------------------------------------------------------------+
|                                                                        |
|  AE PERFORMANCE                                    Period: March 2026  |
|  +------------------------------------------------------------------+  |
|  |                                                                  |  |
|  |  AE Name    | Programs | Outreach | Demos  | Trials | Closed    |  |
|  |  -----------+----------+----------+--------+--------+--------   |  |
|  |  J. Smith   |    18    |    8     |   3    |   1    |   1       |  |
|  |  K. Davis   |    16    |    7     |   2    |   2    |   2       |  |
|  |  L. Chen    |    14    |    6     |   3    |   1    |   1       |  |
|  |  R. Patel   |    12    |    5     |   2    |   2    |   2       |  |
|  |  -----------+----------+----------+--------+--------+--------   |  |
|  |  TEAM TOTAL |    60    |   26     |  10    |   6    |   6       |  |
|  |                                                                  |  |
|  |  Top Performer: K. Davis (2 closed, $24K revenue)               |  |
|  |  Needs Attention: — (all AEs meeting minimum targets)           |  |
|  |                                                                  |  |
|  +------------------------------------------------------------------+  |
|                                                                        |
+------------------------------------------------------------------------+
|                                                                        |
|  REVENUE FORECAST                                                      |
|  +------------------------------------------------------------------+  |
|  |                                                                  |  |
|  |  Current Active ARR:                $62,000                      |  |
|  |                                                                  |  |
|  |  Pipeline Forecast (weighted):                                   |  |
|  |    Trials (6 × $10K avg × 65%):    +$39,000                     |  |
|  |    Demos (10 × $10K avg × 33%):    +$33,000                     |  |
|  |    Outreach (26 × $10K avg × 12%): +$31,200                     |  |
|  |    ——————————————————————————                                   |  |
|  |  Weighted Pipeline Total:           $103,200                     |  |
|  |                                                                  |  |
|  |  Best Case (all pipeline closes):   $482,000                    |  |
|  |  Expected Case (weighted):          $165,200                    |  |
|  |  Worst Case (active only):          $62,000                     |  |
|  |                                                                  |  |
|  |  Monthly Trend:                                                  |  |
|  |  Jan: $24K → Feb: $48K → Mar: $62K (projected $85K)            |  |
|  |  Growth Rate: +38% MoM                                          |  |
|  |                                                                  |  |
|  +------------------------------------------------------------------+  |
|                                                                        |
+========================================================================+
|                                                                        |
|  QUICK ACTIONS                                                         |
|  [ Export Pipeline CSV ]  [ Schedule Team Review ]  [ Generate Report ] |
|  [ Assign Uncontacted ]   [ View Churned ]          [ Settings ]       |
|                                                                        |
+========================================================================+
```

### Dashboard Refresh Behavior

| Data Type | Refresh Rate | Method |
|-----------|-------------|--------|
| Pipeline counts | Real-time | WebSocket push from CRM |
| Revenue numbers | Every 15 minutes | Polling from billing system |
| AE performance | Every 30 minutes | Aggregated query |
| Conference leaderboard | Every 15 minutes | Aggregated query |
| Activity feed | Real-time | WebSocket push from activity log |

### Access Control

| Role | Pipeline View | AE Performance | Revenue | Edit Access |
|------|--------------|---------------|---------|-------------|
| Super Admin | All programs | All AEs | Full | Full write |
| VP Sales | All programs | All AEs | Full | Read + assign |
| Regional Manager | Assigned region | Assigned AEs | Regional | Read + assign |
| Account Executive | Assigned programs | Own only | Pipeline only | Own programs |
| CSM | Active + trial | None | None | Trial/active only |
| Viewer | Summary only | Summary only | Summary only | None |

---

## Related Documents

- [Battle Board Overview](./README.md)
- [NCAA Basketball Registry](./ncaa-basketball-registry.md)
- [Conference Tracker](./conference-tracker.md)
- [Design Tokens](../../design/design-tokens.md)
- [Component Contracts](../../design/contracts/component-contracts.md)

---

*NIL Optic — The operating system for college athletics NIL management.*
