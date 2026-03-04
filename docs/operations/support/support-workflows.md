# Support Workflows — Ticket Routing, SLAs, and Escalation

Last updated: 2026-03-04

---

## Overview

This document defines NIL Optic's support operations: how tickets are categorized, routed, prioritized, escalated, and resolved. The system is designed around four tiers of support with basketball-season awareness, role-based priority boosting, and clear SLA commitments. Integration with Intercom/Zendesk, Slack, and Supabase provides the operational backbone.

---

## Support Tiers

### Tier Architecture

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                                                                              │
│  TIER 0: SELF-SERVICE                                                        │
│  ┌──────────────────────────────────────────────────────────────────────────┐│
│  │  Help Center KB  │  FAQ Accordion  │  Contextual Tooltips  │  Videos    ││
│  │  Search          │  Guided Tours   │  In-app education     │  Chatbot   ││
│  └──────────────────────────────────────────────────────────────────────────┘│
│           │ User cannot self-resolve                                         │
│           ▼                                                                  │
│  TIER 1: FRONTLINE SUPPORT                                                   │
│  ┌──────────────────────────────────────────────────────────────────────────┐│
│  │  Live chat  │  Email queue  │  Ticket triage  │  Canned responses       ││
│  │  First-contact resolution target: 60%                                   ││
│  │  Staffing: Support Agents (generalist)                                  ││
│  └──────────────────────────────────────────────────────────────────────────┘│
│           │ Requires specialist knowledge                                    │
│           ▼                                                                  │
│  TIER 2: SPECIALIST SUPPORT                                                  │
│  ┌──────────────────────────────────────────────────────────────────────────┐│
│  │  Valuation SME  │  Compliance SME  │  Billing SME  │  Data SME          ││
│  │  Deep investigation, cross-system troubleshooting                       ││
│  │  Staffing: Senior Support + Domain Specialists                          ││
│  └──────────────────────────────────────────────────────────────────────────┘│
│           │ Requires code change or infrastructure fix                        │
│           ▼                                                                  │
│  TIER 3: ENGINEERING                                                         │
│  ┌──────────────────────────────────────────────────────────────────────────┐│
│  │  Bug fixes  │  Data pipeline  │  Infrastructure  │  Security            ││
│  │  Feature implementation for blocking issues                             ││
│  │  Staffing: Engineering team, on-call rotation                           ││
│  └──────────────────────────────────────────────────────────────────────────┘│
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

### Tier Definitions

| Tier | Name           | Staffing                 | Scope                                          | FCR Target |
|------|----------------|--------------------------|------------------------------------------------|------------|
| T0   | Self-Service   | Automated / KB           | Articles, FAQ, tooltips, tours, chatbot        | 70%        |
| T1   | Frontline      | Support Agents           | General troubleshooting, account, billing      | 60%        |
| T2   | Specialist     | Senior Support + SMEs    | Valuation logic, compliance, data integrity    | 85%        |
| T3   | Engineering    | Engineers, on-call       | Bug fixes, infra, data pipeline, security      | 95%        |

---

## Ticket Categories and Routing Rules

### Category Matrix

| Category ID         | Display Name             | Default Tier | Default Priority | Auto-Route To               |
|---------------------|--------------------------|--------------|------------------|------------------------------|
| `billing`           | Billing & Account        | T1           | P3               | Billing Agent Queue          |
| `technical`         | Technical Issue           | T1           | P2               | Technical Agent Queue        |
| `compliance`        | Compliance               | T2           | P2               | Compliance SME               |
| `valuation`         | Valuation Question        | T1 → T2      | P3               | General → Valuation SME      |
| `data-issue`        | Data Issue               | T2           | P2               | Data SME                     |
| `feature-request`   | Feature Request          | T1           | P4               | Product Backlog              |
| `deal-management`   | Deal Management          | T1           | P2               | Deal Support Queue           |
| `transfer-portal`   | Transfer Portal          | T1           | P3               | General Agent Queue          |
| `messaging`         | Messaging                | T1           | P3               | Technical Agent Queue        |
| `security`          | Security / Access        | T2           | P1               | Security SME + Engineering   |
| `onboarding`        | Onboarding Help          | T1           | P3               | Onboarding Specialist        |

### Routing Decision Tree

```
Ticket Submitted
      │
      ├── Category = Security?
      │     └── YES → P1 + T2 Security SME + Slack #support-critical
      │
      ├── Category = Compliance?
      │     └── YES → T2 Compliance SME
      │
      ├── Category = Data Issue?
      │     └── YES → T2 Data SME
      │
      ├── Category = Billing?
      │     └── YES → T1 Billing Queue
      │
      ├── Category = Technical?
      │     ├── Error code present?
      │     │     └── YES → Auto-match known errors → T1 or T2
      │     └── NO → T1 Technical Queue
      │
      ├── Category = Valuation?
      │     ├── Involves specific athlete data?
      │     │     └── YES → T2 Valuation SME
      │     └── NO → T1 General Queue
      │
      ├── Category = Feature Request?
      │     └── YES → T1 Acknowledge → Route to Product Backlog
      │
      └── Default → T1 General Queue
```

### Auto-Routing Intelligence

| Signal                    | Action                                             |
|---------------------------|----------------------------------------------------|
| Error code in description | Match against known error DB, tag with bug ID      |
| Athlete name mentioned    | Link to athlete profile in Supabase for context    |
| "March Madness" keyword   | Tag as seasonal-priority, boost during tournament   |
| "transfer portal" keyword | Tag as transfer-related, route to portal specialists|
| Repeat ticket (same user) | Flag for priority review, link to prior tickets     |
| Role = AD or Agency Admin | Apply priority boost (see below)                   |

---

## SLA Matrix

### SLA by Priority Level

| Priority  | Label      | First Response | Resolution Target | Escalation Trigger        |
|-----------|------------|----------------|-------------------|---------------------------|
| P1        | Critical   | 1 hour         | 4 hours           | No response in 30 min     |
| P2        | High       | 4 hours        | 24 hours          | No response in 2 hours    |
| P3        | Medium     | 24 hours       | 72 hours          | No response in 12 hours   |
| P4        | Low        | 72 hours       | 1 week            | No response in 48 hours   |

### Priority Definitions

| Priority  | Criteria                                                              | Examples                                    |
|-----------|-----------------------------------------------------------------------|---------------------------------------------|
| P1        | Platform down, data breach, compliance violation, cannot access       | Login failure for all users, data leak      |
| P2        | Major feature broken, data incorrect, workflow blocked                | Roster not loading, deal stuck in pipeline  |
| P3        | Minor feature issue, general question, non-blocking                  | Chart rendering glitch, valuation question  |
| P4        | Feature request, cosmetic issue, nice-to-have                        | UI suggestion, color preference, typo       |

### SLA by Tier Breakdown

| Tier | P1 Response | P2 Response | P3 Response | P4 Response |
|------|-------------|-------------|-------------|-------------|
| T1   | 1 hr        | 4 hr        | 24 hr       | 72 hr       |
| T2   | 1 hr        | 4 hr        | 24 hr       | 72 hr       |
| T3   | 30 min      | 2 hr        | 8 hr        | 48 hr       |

---

## Role-Based Priority Boosting

Certain user roles receive automatic priority upgrades due to business impact and organizational scope.

### Boost Rules

| User Role              | Default Boost | Rationale                                          |
|------------------------|---------------|----------------------------------------------------|
| Athletic Director      | +1 priority   | Manages entire program NIL; org-level impact       |
| Agency Admin           | +1 priority   | Manages multiple agents and deals                  |
| Agent (Enterprise plan)| +1 priority   | High-value subscriber, deal-critical workflows     |
| Athlete (during deal)  | +1 priority   | Active deal in progress, time-sensitive            |
| Coach                  | No boost      | Standard priority                                  |
| Fan                    | No boost      | Standard priority                                  |

### Boost Logic

```
incoming_priority = user_selected_priority

IF user.role IN ["athletic_director", "agency_admin"]:
    boosted_priority = max(P1, incoming_priority - 1)
ELIF user.role == "agent" AND user.plan == "enterprise":
    boosted_priority = max(P1, incoming_priority - 1)
ELIF user.role == "athlete" AND user.has_active_deal:
    boosted_priority = max(P1, incoming_priority - 1)
ELSE:
    boosted_priority = incoming_priority

final_priority = boosted_priority
```

### Boost Visibility

- Boosted tickets display a "Priority Boost" badge in the agent dashboard.
- Boost reason is logged in ticket metadata (e.g., "Boosted: AD role").
- Boost does not affect user-facing priority display (users see their selected priority).

---

## Escalation Paths

### Escalation Matrix

```
┌──────────────────────────────────────────────────────────────────────┐
│                                                                      │
│  T1 → T2 ESCALATION                                                 │
│  ┌──────────────────────────────────────────────────────────────────┐│
│  │  Trigger:                                                       ││
│  │  - Agent cannot resolve within 2 interactions                   ││
│  │  - Requires domain expertise (valuation, compliance, data)      ││
│  │  - Customer requests escalation                                 ││
│  │  - SLA breach imminent                                          ││
│  │                                                                 ││
│  │  Owner: T2 Specialist takes primary ownership                   ││
│  │  SLA: Specialist must acknowledge within 1 hour                 ││
│  │  Handoff: Full ticket context + prior conversation + user data  ││
│  └──────────────────────────────────────────────────────────────────┘│
│                                                                      │
│  T2 → T3 ESCALATION                                                 │
│  ┌──────────────────────────────────────────────────────────────────┐│
│  │  Trigger:                                                       ││
│  │  - Confirmed bug requiring code change                          ││
│  │  - Data pipeline or infrastructure issue                        ││
│  │  - Security vulnerability                                      ││
│  │  - Specialist cannot resolve with config/data fixes             ││
│  │                                                                 ││
│  │  Owner: Engineering on-call takes ownership                     ││
│  │  SLA: Engineer must acknowledge within 30 min (P1) / 2hr (P2)  ││
│  │  Handoff: Bug report format with repro steps + logs + context   ││
│  └──────────────────────────────────────────────────────────────────┘│
│                                                                      │
│  MANAGEMENT ESCALATION                                               │
│  ┌──────────────────────────────────────────────────────────────────┐│
│  │  Trigger:                                                       ││
│  │  - Customer threatens churn (AD/Agency Admin)                   ││
│  │  - SLA breached by > 2x resolution target                      ││
│  │  - Compliance or legal concern                                  ││
│  │  - 3+ tickets from same user in 7 days                         ││
│  │                                                                 ││
│  │  Owner: Support Lead + Account Manager                          ││
│  │  Action: Personal outreach, root cause analysis, retention plan ││
│  └──────────────────────────────────────────────────────────────────┘│
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

### Escalation Handoff Protocol

| Step | Action                                                          |
|------|-----------------------------------------------------------------|
| 1    | Escalating agent writes internal note summarizing issue         |
| 2    | Escalating agent tags the ticket with escalation reason         |
| 3    | Escalating agent assigns to appropriate T2/T3 queue            |
| 4    | Receiving party acknowledges within SLA window                  |
| 5    | Receiving party updates customer with estimated resolution time |
| 6    | Original agent remains CC'd and monitors for resolution         |
| 7    | Resolution is documented in ticket and KB article if recurring  |

### Engineering Bug Report Template

```
## Bug Report — Support Escalation

**Ticket ID:** #NIL-20260304-XXXX
**Priority:** P2 — High
**Reporter Role:** Athletic Director
**Affected Feature:** Roster Builder

### Description
Basketball roster fails to load for the 2026 season. All other sports
load correctly. Affects Kentucky basketball program.

### Steps to Reproduce
1. Log in as AD for University of Kentucky
2. Navigate to Roster Builder
3. Select "Basketball" from the sport dropdown
4. Observe empty roster with loading spinner that never resolves

### Expected Behavior
Basketball roster should display all rostered players with NIL valuations.

### Actual Behavior
Infinite loading spinner. No error message. Console shows 504 timeout
on /api/roster/basketball endpoint.

### Environment
- Browser: Chrome 120
- OS: macOS 14.2
- Account ID: usr_abc123
- Organization: University of Kentucky

### Impact
- Affected users: All Kentucky AD accounts
- Business impact: Cannot view roster NIL data during March Madness prep
- Workaround: None identified

### Supporting Data
- Screenshot: [attached]
- Console logs: [attached]
- Network trace: [attached]
```

---

## Basketball Season Awareness

NIL Optic support operations adjust staffing, routing, and SLAs based on basketball calendar events.

### Season Calendar and Staffing Adjustments

| Period                    | Dates (Approx.)      | Staffing Level | Notes                              |
|---------------------------|----------------------|----------------|------------------------------------|
| Pre-season                | Oct 1 - Nov 14       | Normal         | Baseline staffing                  |
| Regular Season            | Nov 15 - Feb 28      | Normal + 20%   | Increased basketball activity      |
| Conference Tournaments    | Mar 1 - Mar 14       | Normal + 30%   | Peak conference play               |
| March Madness             | Mar 15 - Apr 7       | Normal + 50%   | Highest traffic period             |
| Spring Transfer Portal    | Apr 15 - May 15      | Normal + 30%   | Heavy portal tracking activity     |
| Off-season                | May 16 - Sep 30      | Normal         | Baseline, content catch-up         |

### March Madness Support Protocol

```
┌──────────────────────────────────────────────────────────────────────┐
│  MARCH MADNESS SUPPORT PROTOCOL (Mar 15 - Apr 7)                    │
│                                                                      │
│  Staffing:                                                           │
│  ├── T1: +50% headcount (temp + overtime)                           │
│  ├── T2: Valuation SME on extended hours (8 AM - 10 PM ET)         │
│  ├── T3: Engineering on-call 24/7 with 15-min pager response       │
│  └── Management: Support Lead on-call for management escalations    │
│                                                                      │
│  SLA Adjustments:                                                    │
│  ├── P1: Response within 30 min (down from 1 hr)                   │
│  ├── P2: Response within 2 hr (down from 4 hr)                     │
│  └── P3/P4: Standard SLA maintained                                │
│                                                                      │
│  Proactive Actions:                                                  │
│  ├── Daily status page update for known issues                      │
│  ├── Pre-game day system health check (morning of game days)        │
│  ├── Real-time Slack monitoring of #support-critical                │
│  └── Post-round debrief: review ticket spike patterns               │
│                                                                      │
│  Common March Madness Issues:                                        │
│  ├── Valuation spikes/drops after upset games                       │
│  ├── Traffic surges causing slow load times                         │
│  ├── Predictor score confusion after unexpected results             │
│  ├── Compliance questions on tournament-related deals               │
│  └── Transfer portal speculation generating data inquiries          │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

### Transfer Portal Window Protocol

```
┌──────────────────────────────────────────────────────────────────────┐
│  TRANSFER PORTAL WINDOW SUPPORT (Apr 15 - May 15)                   │
│                                                                      │
│  Staffing:                                                           │
│  ├── T1: +30% headcount                                            │
│  ├── T2: Data SME on extended hours for portal data issues          │
│  └── T3: Engineering standby for data pipeline monitoring           │
│                                                                      │
│  Common Portal Issues:                                               │
│  ├── Player not appearing in portal feed                            │
│  ├── NIL valuation not updating after portal entry                  │
│  ├── Watchlist sync delays                                          │
│  ├── Transfer destination not reflecting in athlete profile         │
│  └── Compliance questions about portal-related deals                │
│                                                                      │
│  Proactive Actions:                                                  │
│  ├── Daily portal data pipeline health check                        │
│  ├── Pre-built canned responses for common portal questions         │
│  └── Escalation fast-track for data pipeline issues                 │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

---

## Canned Responses / Macro Library

Pre-written response templates for common issues. Agents customize with specific details before sending.

### Macro Inventory

| Macro ID            | Category    | Title                                           | Usage Frequency |
|---------------------|-------------|-------------------------------------------------|-----------------|
| `m-welcome`         | General     | Welcome and acknowledgment                      | Very High       |
| `m-more-info`       | General     | Requesting additional information               | Very High       |
| `m-escalation`      | General     | Escalation notification to customer             | High            |
| `m-resolution`      | General     | Issue resolved confirmation                     | Very High       |
| `m-roster-empty`    | Technical   | Basketball roster not loading                   | High (seasonal) |
| `m-valuation-delay` | Valuation   | Valuation data delayed / processing             | High            |
| `m-valuation-method`| Valuation   | How NIL valuation is calculated                 | Medium          |
| `m-deal-stuck`      | Deals       | Deal stuck in workflow stage                    | Medium          |
| `m-compliance-check`| Compliance  | Compliance review status update                 | Medium          |
| `m-portal-missing`  | Portal      | Player not appearing in transfer portal         | High (seasonal) |
| `m-portal-nil`      | Portal      | NIL value update after portal entry             | High (seasonal) |
| `m-billing-plan`    | Billing     | Plan comparison and upgrade guidance            | Medium          |
| `m-billing-invoice` | Billing     | Invoice and billing cycle explanation            | Low             |
| `m-feature-request` | General     | Feature request acknowledgment and tracking     | Medium          |
| `m-mm-valuation`    | Seasonal    | March Madness valuation fluctuation explanation | High (Mar only) |
| `m-mm-predictor`    | Seasonal    | Predictor score changes during tournament       | High (Mar only) |
| `m-password-reset`  | Account     | Password reset instructions                     | Medium          |
| `m-2fa-setup`       | Account     | Two-factor authentication setup help            | Low             |

### Example Macros

**m-welcome — Welcome and Acknowledgment**
```
Hi {customer_name},

Thank you for reaching out to NIL Optic Support. I've received your
request and I'm looking into it now.

Ticket: {ticket_id}
Priority: {priority}
Expected response time: {sla_time}

I'll follow up with an update as soon as I have more information.

Best,
{agent_name}
NIL Optic Support
```

**m-roster-empty — Basketball Roster Not Loading**
```
Hi {customer_name},

I understand your basketball roster is not displaying data.
Here are a few things to check:

1. Confirm you're viewing the correct season (use the season
   dropdown in the top-right of Roster Builder).
2. Try refreshing the page (Cmd+Shift+R / Ctrl+Shift+R).
3. Check if other sports rosters load correctly.

If the issue persists after these steps, I'll escalate this to
our technical team. Could you share:
- A screenshot of what you see
- Your browser and OS version
- The time you first noticed the issue

We'll get this resolved quickly — I know roster data is critical
during basketball season.

Best,
{agent_name}
NIL Optic Support
```

**m-mm-valuation — March Madness Valuation Fluctuation**
```
Hi {customer_name},

During March Madness, NIL valuations can shift more rapidly
than usual due to:

- Tournament performance (wins/losses, individual highlights)
- Increased media exposure and social media engagement
- Brand interest spikes following breakout performances
- Bracket advancement multiplier effects

These fluctuations are expected and reflect real-time market
dynamics. Valuations typically stabilize within 48-72 hours
after a team's tournament run concludes.

If you believe a specific valuation is incorrect, please share
the athlete name and what you're seeing, and I'll have our
valuation team review.

Best,
{agent_name}
NIL Optic Support
```

**m-portal-missing — Player Not in Transfer Portal**
```
Hi {customer_name},

Transfer portal data is sourced from official NCAA feeds and may
take up to 24 hours to appear on NIL Optic after a player
officially enters the portal.

If it has been more than 24 hours:
1. Search for the player by name in the Transfer Portal section.
2. Check the athlete's profile page for a "Transfer Status" badge.
3. Confirm the player has officially entered (not just reported
   by media).

If the player is confirmed in the portal and still not showing,
please share the player's name and school, and I'll escalate to
our data team for investigation.

Best,
{agent_name}
NIL Optic Support
```

---

## Quality Assurance

### CSAT Survey

Sent after every ticket resolution. Simple 2-question survey.

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  How was your support experience?                    │
│                                                      │
│  ★ ★ ★ ★ ★                                          │  ← 1-5 star rating
│                                                      │
│  Any additional feedback? (optional)                 │
│  ┌──────────────────────────────────────────────────┐│
│  │                                                  ││
│  └──────────────────────────────────────────────────┘│
│                                                      │
│  [Submit]                                            │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### QA Scoring Rubric

| Criteria                | Weight | 5 (Excellent)                  | 3 (Acceptable)               | 1 (Needs Improvement)         |
|-------------------------|--------|--------------------------------|------------------------------|-------------------------------|
| Accuracy                | 30%    | Correct solution, no errors    | Mostly correct, minor gaps   | Wrong solution provided       |
| Tone & Empathy          | 20%    | Warm, professional, empathetic | Professional but neutral     | Cold, robotic, dismissive     |
| Resolution Speed        | 20%    | Resolved first contact         | Resolved within SLA          | Breached SLA                  |
| Knowledge Demonstrated  | 15%    | Deep product understanding     | Adequate understanding       | Needed excessive assistance   |
| Documentation           | 15%    | Thorough internal notes        | Basic notes recorded         | No internal notes             |

### QA Schedule

| Review Type        | Frequency  | Sample Size | Reviewer              |
|--------------------|------------|-------------|-----------------------|
| Random QA review   | Weekly     | 10% of tickets | Support Lead        |
| New agent review   | Daily      | 100% for first 30 days | Senior Agent   |
| Escalated ticket review | Per-ticket | 100% of escalations | Support Lead |
| CSAT < 3 review    | Per-ticket | 100% of low-rated | Support Lead       |
| Monthly calibration| Monthly    | 20 tickets cross-reviewed | Full team    |

### Agent Performance Metrics

| Metric                     | Target          | Measurement Period |
|----------------------------|-----------------|--------------------|
| Average CSAT               | > 4.5 / 5       | Rolling 30 days   |
| First Contact Resolution   | > 60%            | Rolling 30 days   |
| Average Response Time      | < SLA by 20%    | Rolling 7 days    |
| Average Resolution Time    | < SLA by 10%    | Rolling 30 days   |
| QA Score                   | > 4.0 / 5       | Rolling 30 days   |
| Tickets Handled / Day      | 15-25            | Daily average     |
| Escalation Rate            | < 20%            | Rolling 30 days   |
| Knowledge Article Created  | 2+ / month       | Monthly           |

---

## Integration Points

### System Integration Architecture

```
┌──────────────────────────────────────────────────────────────────────┐
│                                                                      │
│  ┌────────────┐    ┌────────────┐    ┌────────────┐                 │
│  │ NIL Optic  │    │ Intercom / │    │  Supabase  │                 │
│  │ Help Widget│───▶│  Zendesk   │◀──▶│  User DB   │                 │
│  │            │    │            │    │            │                 │
│  │ In-app     │    │ Ticket     │    │ User role  │                 │
│  │ support    │    │ management │    │ Org data   │                 │
│  │ launcher   │    │ Agent UI   │    │ Sub plan   │                 │
│  └────────────┘    └─────┬──────┘    └────────────┘                 │
│                          │                                           │
│                    ┌─────┴──────┐                                    │
│                    │   Slack    │                                    │
│                    │            │                                    │
│                    │ #support-  │                                    │
│                    │  critical  │                                    │
│                    │ #support-  │                                    │
│                    │  general   │                                    │
│                    │ #eng-      │                                    │
│                    │  oncall    │                                    │
│                    └────────────┘                                    │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

### Intercom / Zendesk Integration

| Integration Point       | Direction       | Data                                          |
|-------------------------|-----------------|-----------------------------------------------|
| Ticket creation         | App → Helpdesk  | Category, priority, description, context       |
| User context            | Supabase → Helpdesk | Role, org, plan, sport, recent activity   |
| Ticket status sync      | Helpdesk → App  | Status updates reflected in in-app tracker     |
| CSAT collection         | Helpdesk → App  | Survey responses stored for analytics          |
| Agent assignment        | Helpdesk internal| Auto-route by category, skills-based routing  |
| Article suggestions     | Helpdesk → App  | Auto-suggest KB articles based on ticket text  |

### Slack Alerting Configuration

| Channel               | Trigger                                             | Format                         |
|-----------------------|-----------------------------------------------------|--------------------------------|
| `#support-critical`   | Any P1 ticket created                               | Full ticket summary + link     |
| `#support-critical`   | SLA breach on any P1/P2 ticket                      | Warning with time remaining    |
| `#support-critical`   | Management escalation triggered                     | Escalation reason + context    |
| `#support-general`    | Daily ticket summary (EOD)                           | Volume, resolution, CSAT       |
| `#support-general`    | Weekly CSAT report                                   | Trends, low-rated tickets      |
| `#eng-oncall`         | T3 escalation ticket created                         | Bug report format + link       |
| `#eng-oncall`         | P1 infrastructure / security alert                   | Immediate page to on-call      |

### Slack Alert Format — P1 Example

```
┌──────────────────────────────────────────────────────┐
│  :rotating_light: P1 CRITICAL TICKET                 │
│                                                      │
│  #NIL-20260315-1823                                  │
│  "Platform login failure — all Kentucky AD accounts" │
│                                                      │
│  Category: Security / Access                         │
│  Role: Athletic Director                             │
│  Org: University of Kentucky                         │
│  Priority: P1 Critical (boosted from P2)             │
│  SLA: First response due in 30 min                   │
│                                                      │
│  [View Ticket]  [Assign to Me]                       │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### Supabase User Context

When a ticket is created, the following user context is automatically attached from Supabase:

| Field                 | Source                    | Usage                              |
|-----------------------|---------------------------|------------------------------------|
| `user_id`             | `auth.users`              | Unique user identifier             |
| `role`                | `profiles.role`           | Priority boost calculation          |
| `organization`        | `organizations.name`      | Org context for agent              |
| `plan`                | `subscriptions.plan`      | Enterprise boost eligibility        |
| `primary_sport`       | `profiles.primary_sport`  | Sport-specific routing              |
| `last_active`         | `profiles.last_sign_in`   | Recency context                    |
| `current_page`        | Client-side capture       | Where the issue occurred           |
| `browser`             | Client-side capture       | Technical debugging context        |
| `open_tickets`        | `tickets.count`           | Repeat issue detection              |

---

## On-Call Rotation

### On-Call Structure

| Level              | Coverage         | Rotation        | Pager Response      |
|--------------------|------------------|-----------------|---------------------|
| T1 On-Call         | 7 AM - 11 PM ET | Weekly          | 15 min              |
| T2 On-Call         | 8 AM - 8 PM ET  | Weekly          | 30 min              |
| T3 Engineering     | 24/7             | Weekly          | 15 min (P1), 1 hr (P2) |
| Support Lead       | Business hours   | N/A (permanent) | 30 min              |

### High-Traffic On-Call (March Madness / Transfer Portal / Signing Day)

| Level              | Coverage         | Rotation        | Pager Response      |
|--------------------|------------------|-----------------|---------------------|
| T1 On-Call         | 24/7             | 12-hr shifts    | 10 min              |
| T2 On-Call         | 7 AM - 12 AM ET | 8-hr shifts     | 15 min              |
| T3 Engineering     | 24/7             | 8-hr shifts     | 10 min (P1), 30 min (P2) |
| Support Lead       | 7 AM - 11 PM ET | N/A             | 15 min              |

### On-Call Handoff Protocol

| Step | Action                                                          |
|------|-----------------------------------------------------------------|
| 1    | Outgoing on-call writes shift summary in #support-handoff       |
| 2    | Open P1/P2 tickets transferred to incoming on-call              |
| 3    | Incoming on-call acknowledges in Slack within 15 minutes        |
| 4    | Any in-progress customer conversations are re-introduced        |
| 5    | Pager tool updated with incoming on-call contact                |

---

## Support Analytics Dashboard

### Dashboard Wireframe

```
┌──────────────────────────────────────────────────────────────────────┐
│  SUPPORT ANALYTICS                            [Today] [7d] [30d]    │
│                                                                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────┐│
│  │     127      │  │    4.6/5     │  │    2.3 hr    │  │   64%    ││
│  │   Tickets    │  │    CSAT      │  │  Avg Resolve │  │   FCR    ││
│  │   Today      │  │   Score      │  │   Time       │  │   Rate   ││
│  │   ▲ +12%     │  │   ▲ +0.2     │  │   ▼ -0.5hr   │  │   ▲ +3%  ││
│  └──────────────┘  └──────────────┘  └──────────────┘  └──────────┘│
│                                                                      │
│  TICKET VOLUME (30 DAY)                                              │
│  ┌──────────────────────────────────────────────────────────────────┐│
│  │  150 ┤                                                          ││
│  │      │                        ╭──╮                              ││
│  │  100 ┤    ╭──╮   ╭──╮  ╭──╮ │  │ ╭──╮                        ││
│  │      │╭──╮│  │╭──╮│  │╭╯  ╰─╯  ╰─╯  ╰──╮                    ││
│  │   50 ┤│  ╰╯  ╰╯  ╰╯  ╰╯                  ╰──╮                ││
│  │      │╯                                        ╰───            ││
│  │    0 ┤                                                          ││
│  │      └──────────────────────────────────────────────────────    ││
│  │       Mar 1        Mar 8        Mar 15 (MM)    Mar 22          ││
│  └──────────────────────────────────────────────────────────────────┘│
│                                                                      │
│  BY CATEGORY                    BY PRIORITY                          │
│  ┌─────────────────────────┐   ┌─────────────────────────┐          │
│  │ Technical    ████████ 34│   │ P1 Critical  ██ 5       │          │
│  │ Valuation   ██████ 28   │   │ P2 High      ████████ 38│          │
│  │ Deals       █████ 22    │   │ P3 Medium    █████████ 52│         │
│  │ Billing     ███ 15      │   │ P4 Low       ██████ 32   │         │
│  │ Compliance  ███ 14      │   │                          │         │
│  │ Portal      ██ 8        │   │                          │         │
│  │ Other       ██ 6        │   │                          │         │
│  └─────────────────────────┘   └─────────────────────────┘          │
│                                                                      │
│  SLA COMPLIANCE                 DEFLECTION RATE                      │
│  ┌─────────────────────────┐   ┌─────────────────────────┐          │
│  │ P1: 96% within SLA      │   │  Self-Service: 72%      │          │
│  │ P2: 91% within SLA      │   │  T0→T1 deflected: 68%   │          │
│  │ P3: 94% within SLA      │   │  Search resolved: 75%   │          │
│  │ P4: 98% within SLA      │   │  KB article helpful: 82%│          │
│  │                          │   │                          │         │
│  │ Overall: 94.2%           │   │  Overall deflection:    │         │
│  │ Target: > 95%            │   │  72.4% (target: 70%)    │         │
│  └─────────────────────────┘   └─────────────────────────┘          │
│                                                                      │
│  AGENT PERFORMANCE              TOP ISSUES THIS WEEK                 │
│  ┌─────────────────────────┐   ┌─────────────────────────────────┐  │
│  │ Agent       CSAT  FCR   │   │ 1. BB roster load timeout (18) │  │
│  │ ─────────────────────── │   │ 2. Valuation spike confusion    │  │
│  │ S. Johnson  4.8   72%   │   │    after March Madness (14)     │  │
│  │ M. Chen     4.7   68%   │   │ 3. Deal compliance stuck (11)  │  │
│  │ A. Kumar    4.5   65%   │   │ 4. Transfer portal sync (9)    │  │
│  │ J. Williams 4.4   61%   │   │ 5. Plan upgrade questions (7)  │  │
│  └─────────────────────────┘   └─────────────────────────────────┘  │
│                                                                      │
│  OPEN P1/P2 TICKETS (REQUIRES ATTENTION)                             │
│  ┌──────────────────────────────────────────────────────────────────┐│
│  │ ● P1  #NIL-0315-1823  Platform login failure — Kentucky    12m ││
│  │ ● P2  #NIL-0315-1756  Roster timeout — Duke basketball    45m ││
│  │ ● P2  #NIL-0315-1690  Deal stuck in compliance review     2h  ││
│  └──────────────────────────────────────────────────────────────────┘│
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

### Dashboard Tokens

| Element              | Token / Style                                       |
|----------------------|-----------------------------------------------------|
| KPI metric value     | Inter Bold 28, `--ui-text-primary`                  |
| KPI label            | Inter Regular 12, `--ui-text-muted`, uppercase      |
| KPI delta (positive) | JetBrains Mono 12, `--ui-text-success`              |
| KPI delta (negative) | JetBrains Mono 12, `--ui-text-danger`               |
| Chart bar (primary)  | `--support-accent` (red-600)                        |
| Chart bar (secondary)| Zinc-600                                            |
| Chart grid           | `--ui-border-default`                               |
| Table header         | Inter Semi-Bold 11, `--ui-text-muted`, uppercase    |
| Table row            | Inter Regular 13, `--ui-text-primary`               |
| Ticket ID            | JetBrains Mono 12, `--ui-text-muted`                |
| Priority badge       | Same tokens as ticket status badges in support-system|
| Section title        | Inter Semi-Bold 14, `--ui-text-primary`             |
| Card surface         | `--ui-surface-1`, `--ui-border-default`, radius-lg  |

### Key Dashboard Metrics

| Metric                    | Definition                                         | Target         |
|---------------------------|----------------------------------------------------|----------------|
| Tickets / day             | Total new tickets created per day                  | Trend tracking |
| CSAT score                | Average customer satisfaction (1-5)                | > 4.5          |
| Average resolution time   | Mean time from ticket creation to resolution       | < 4 hrs (P2)  |
| First contact resolution  | % of tickets resolved without escalation           | > 60%          |
| SLA compliance            | % of tickets resolved within SLA targets           | > 95%          |
| Self-service deflection   | % of help sessions resolved without a ticket       | > 70%          |
| Search-to-ticket rate     | % of searches that lead to ticket creation         | < 10%          |
| Agent utilization         | Tickets handled per agent per day                  | 15-25          |
| Escalation rate           | % of tickets escalated beyond T1                   | < 20%          |
| Repeat contact rate       | % of users filing 2+ tickets in 7 days             | < 8%           |

---

## Handoff Protocols — Support to Product/Engineering

### Support-to-Product Handoff (Feature Requests / Recurring Pain Points)

```
┌──────────────────────────────────────────────────────────────────────┐
│  FEATURE REQUEST / PAIN POINT ESCALATION                             │
│                                                                      │
│  Trigger:                                                            │
│  ├── 5+ tickets on same topic in 30 days                            │
│  ├── Feature request from AD/Agency Admin (high-value account)      │
│  └── Support team identifies systematic workflow friction            │
│                                                                      │
│  Process:                                                            │
│  1. Support Lead compiles ticket summary report                      │
│  2. Report filed in Product Backlog (Linear/Jira)                   │
│  3. Product Manager reviews within 1 business day                   │
│  4. PM responds with: Accepted / Deferred / Won't Do + rationale   │
│  5. Support Lead updates affected customers with decision           │
│  6. If accepted, PM shares estimated timeline                        │
│  7. Support Lead creates placeholder KB article if relevant         │
│                                                                      │
│  Report Format:                                                      │
│  ├── Title: "Recurring: [Issue Description]"                        │
│  ├── Ticket count + ticket IDs                                      │
│  ├── Affected roles and segments                                    │
│  ├── Customer verbatim quotes (anonymized)                          │
│  ├── Proposed solution (if any from support perspective)             │
│  └── Business impact estimate                                       │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

### Engineering-to-Support Handoff (Bug Fix / Feature Deploy)

```
┌──────────────────────────────────────────────────────────────────────┐
│  DEPLOYMENT NOTIFICATION — SUPPORT TEAM                              │
│                                                                      │
│  When engineering deploys a fix or feature:                          │
│  1. Engineering posts in #support-releases with:                     │
│     - What changed (user-facing description)                        │
│     - Which tickets this resolves (ticket IDs)                      │
│     - Any known caveats or partial fixes                            │
│     - Rollback plan if issues emerge                                │
│                                                                      │
│  2. Support Lead:                                                    │
│     - Closes resolved tickets with resolution note                  │
│     - Updates relevant KB articles within 24 hours                  │
│     - Removes temporary workaround guidance                         │
│     - Notifies affected customers                                   │
│                                                                      │
│  3. Monitoring (first 24 hours post-deploy):                        │
│     - Watch for new tickets related to the change                   │
│     - Report any regressions to engineering immediately             │
│     - Track CSAT on resolved tickets for quality signal             │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

### Weekly Sync — Support + Product + Engineering

| Agenda Item                | Owner          | Time  |
|----------------------------|----------------|-------|
| Top 5 ticket themes        | Support Lead   | 10 min|
| Open P1/P2 status          | Engineering    | 5 min |
| Feature request pipeline   | Product Manager| 5 min |
| KB coverage gaps           | Support Lead   | 5 min |
| Upcoming releases impact   | Engineering    | 5 min |
| Action items review        | All            | 5 min |

**Cadence:** Weekly, 30 minutes, recorded
**Slack channel:** #support-product-sync
**Notes doc:** Living document updated each session
