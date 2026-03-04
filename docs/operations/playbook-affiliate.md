# Operations Playbook: Affiliate

> Last updated: 2026-03-04

---

## Role Overview

**Who:** Tax advisors, wealth management professionals, and legal partners who are affiliated with NIL Optic to provide specialized financial, tax, and legal services to college athletes navigating NIL income and contracts.

**Organization category:** `affiliate`
**Role key:** `affiliate` (program-scoped) / `affiliate_admin` (organization-scoped)
**Shell routes:** `/affiliate` (advisor), `/affiliate-admin` (admin)

Affiliates are the support infrastructure of the NIL ecosystem. As athletes earn NIL income -- often for the first time -- they need professional guidance on tax obligations, wealth management, contract review, and financial planning. NIL Optic connects affiliate partners with athletes and athletic programs, creating a marketplace where advisors can serve the unique needs of student-athletes.

### Core Responsibilities

- Manage active client accounts and service delivery
- Provide tax, wealth, or legal advisory services to athletes
- Track service utilization and client engagement
- Plan and deliver educational workshops via huddles
- Maintain affiliate directory presence for discoverability
- Coordinate with agents and ADs on athlete financial needs
- Drive revenue through service delivery and client acquisition

---

## Daily Operations

**Time allocation:** 20--30 minutes

### Morning Client Review (`8:30 AM`)

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P0 | Client account review -- active accounts, pending actions | `/affiliate` | 10 min |
| P1 | Service delivery tracking -- open tasks, deadlines, deliverables | `/affiliate` | 5 min |
| P1 | Check messages -- respond to client inquiries (inbound-first) | `/dashboard/messages` | 10 min |
| P2 | Monitor affiliate directory listing for visibility | `/affiliate-directory` | 2 min |

### Daily KPI Glance

| Metric | Source | Format |
|---|---|---|
| Active Client Accounts | `/affiliate` | `#` |
| Pending Service Requests | `/affiliate` | `#` |
| Messages (Inbound) | `/dashboard/messages` badge | `#` |
| Monthly Revenue (MTD) | `/affiliate` | `$XX.XK` |

### Communication Policy Reminder

```
AFFILIATE MESSAGING POLICY:

  Affiliates follow an INBOUND-FIRST messaging policy:
    - Cannot initiate outbound contact to new users
    - Can only compose messages when a prior thread exists
    - Existing threads: full read/send capability
    - New contact: must wait for athlete/agent/AD to initiate

  This ensures:
    - Athletes are not spammed by service providers
    - Communication is athlete-driven and consent-based
    - Trust is built through quality service, not volume outreach
```

---

## Weekly Cadence

**Day:** Tuesday (client operations) + Friday (planning)

### Tuesday: Client Operations

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Client account status review -- all active accounts | `/affiliate` | Affiliate solo |
| 9:30 AM | Service delivery progress check -- deadlines, deliverables | `/affiliate` | Affiliate solo |
| 10:00 AM | Respond to pending client messages | `/dashboard/messages` | Affiliate solo |
| 10:30 AM | Workshop planning -- prepare upcoming huddle content | External prep | Affiliate solo |

### Friday: Business Planning

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Weekly revenue summary -- services delivered, revenue recognized | `/affiliate` | Affiliate + Affiliate Admin |
| 9:30 AM | Client outreach planning -- identify re-engagement opportunities | `/affiliate` | Affiliate solo |
| 10:00 AM | Directory presence audit -- verify listing accuracy | `/affiliate-directory` | Affiliate solo |

### Workshop Planning Framework

```
AFFILIATE WORKSHOP CADENCE:

  Huddle Format: Affiliate Workshop
  Frequency: Monthly (or as demand warrants)
  Duration: 30-60 minutes
  Audience: Athletes, coaches, ADs within scope

  WORKSHOP TOPICS (Rotating):
    Month 1: NIL Income Tax Basics for Student-Athletes
    Month 2: Wealth Management 101 -- What to Do with Your First NIL Check
    Month 3: Contract Review Essentials -- Know What You're Signing
    Month 4: Tax Filing Season Prep for NIL Earners
    Month 5: Long-Term Financial Planning for Athletes
    Month 6: Legal Protections for Your Name, Image, and Likeness

  WORKSHOP EXECUTION:
    1. Plan content and agenda (2 weeks prior)
    2. Coordinate with AD or agent for audience invite
    3. Create huddle session with format: affiliate_workshop
    4. Deliver workshop via huddle room
    5. Follow up with attendees via existing message threads
```

---

## Monthly Cadence

**Timing:** Last week of each month

### Monthly Business Review

| Task | Description | Screen |
|---|---|---|
| Service Utilization Review | Audit % of active accounts with service activity this month | `/affiliate` |
| Revenue Tracking | Total revenue from advisory services; compare to target | `/affiliate` |
| Client Satisfaction Assessment | Review communication quality; identify at-risk accounts | `/dashboard/messages` |
| Affiliate Admin Sync | Report to admin on performance metrics and growth needs | `/affiliate-admin` |
| Directory Optimization | Update listing details; ensure service descriptions are current | `/affiliate-directory` |

### Monthly Meeting Cadence

| Meeting | Audience | Deliverable |
|---|---|---|
| Affiliate Team Sync | Affiliate Admin + all affiliates | Performance review, service delivery quality |
| Client Re-engagement Review | Affiliate solo | Identify dormant accounts for re-engagement |
| AD/Agent Coordination | Athletic Directors and agents (existing threads) | Service awareness, referral pipeline |
| Workshop Retrospective | Post-workshop review | Attendance data, feedback, follow-up actions |

### Monthly KPI Scorecard

| KPI | Target | Measurement |
|---|---|---|
| Active Accounts | Growth MoM | `#` from `/affiliate` |
| Service Utilization Rate | 70%+ of accounts with monthly activity | `%` |
| Monthly Revenue | Affiliate-defined target | `$XX.XK` |
| Client Satisfaction | 90%+ positive engagement | Qualitative assessment |
| Workshop Attendance | 10+ attendees per session | `#` from huddle data |

---

## Key Screens

| Screen | Route | Primary Use |
|---|---|---|
| Affiliate Dashboard | `/affiliate` | Client accounts, service delivery, activity tracking |
| Affiliate Admin | `/affiliate-admin` | Organization-level management, affiliate team oversight |
| Affiliate Directory | `/affiliate-directory` | Public listing for discoverability |
| Affiliate Directory Category | `/affiliate-directory/[category]` | Category-specific service pages |
| Messages | `/dashboard/messages` | Client communication (inbound-first) |
| Favorites | `/dashboard/favorites` | Track athletes and programs of interest |

### Affiliate Directory Presence

The `/affiliate-directory` is the public-facing marketplace where athletes, coaches, and ADs discover affiliate partners:

| Directory Field | Description |
|---|---|
| Company Name | Affiliate organization name |
| Category | `Wealth Management`, `Tax`, or `Legal` |
| City / State | Physical location for local service matching |
| Email | Public contact email |
| Phone | Public contact phone |
| Partner List | Named partners / advisors |
| Message Action | In-app message button (routes to compose if linked user exists) |

### Category Dropdown Options

| Category | Description |
|---|---|
| All | Show all affiliate partners across categories |
| Wealth Management | Financial planning, investment advisory, wealth preservation |
| Tax | NIL income tax preparation, filing, estimated payments |
| Legal | Contract review, NIL rights protection, compliance advisory |

### Directory Filters

- **State filter** -- narrow by state (e.g., Texas)
- **City filter** -- narrow by city (e.g., Dallas)
- **Clear filters** -- remove all active filters with one action

---

## KPIs

### Primary KPIs

| KPI | Definition | Target | Font |
|---|---|---|---|
| Active Accounts | Total client accounts with current service agreement | Growth MoM | `JetBrains Mono` `##` |
| Service Utilization | % of active accounts with service activity in rolling 30 days | 70%+ | `JetBrains Mono` `XX.X%` |
| Revenue | Total advisory service revenue | Monthly target | `JetBrains Mono` `$XX.XK` |
| Client Satisfaction | % of clients with positive engagement indicators | 90%+ | `JetBrains Mono` `XX%` |

### Secondary KPIs

| KPI | Definition | Target |
|---|---|---|
| Workshop Attendance | Average attendees per affiliate workshop huddle | 10+ |
| Referral Rate | New clients acquired through AD/agent referrals | Growth trend |
| Response Time | Average response time to inbound client messages | < 4 hours business hours |
| Service Completion Rate | % of contracted services delivered on time | 95%+ |
| Directory Engagement | Views/contacts from affiliate directory listing | Growth trend |

---

## Escalation Paths

| Trigger | Severity | Escalation Target | SLA |
|---|---|---|---|
| Client tax filing deadline at risk | CRITICAL | Affiliate Admin + client direct communication | 24 hours |
| Client dispute on service quality | HIGH | Affiliate Admin mediation | 48 hours |
| Compliance question on NIL contract | HIGH | Legal affiliate or external counsel | 24 hours |
| Client account dormant > 60 days | MEDIUM | Re-engagement outreach via existing thread | 1 week |
| Directory listing inaccuracy reported | LOW | Affiliate Admin correction | 48 hours |
| Platform access or data issue | MEDIUM | NIL Optic support | 4 hours |

---

## Basketball Focus

Basketball athletes generate the highest individual NIL incomes, creating the most complex tax and wealth management needs. Affiliate partners serving basketball programs should be prepared for:

### Tax Complexity for Basketball Athletes

| Scenario | Tax Implication | Affiliate Service |
|---|---|---|
| Multi-state game appearances | State income tax nexus in each state played | Multi-state filing preparation |
| Brand partnership income | 1099 reporting, quarterly estimated payments | Estimated payment calculation + filing |
| Tournament appearance bonuses | Additional income in tournament host state | Supplemental state filing |
| Transfer to new state | Residency change, dual-state filing | Tax residency analysis |
| International exhibition games | Foreign income reporting requirements | International tax advisory |

### Basketball Seasonal Tax Calendar

| Month | Tax Action | Priority |
|---|---|---|
| January | Q4 estimated payment due (Jan 15) | P0 |
| February | 1099 forms arriving; begin tax prep | P0 |
| March | Tournament income tracking (multi-state) | P1 |
| April | Tax filing deadline (Apr 15) or extension filing | P0 |
| June | Q2 estimated payment due (Jun 15) | P0 |
| September | Q3 estimated payment due (Sep 15) | P0 |
| October | Extension deadline (Oct 15) if filed | P0 |
| November | Year-end tax planning session | P1 |
| December | Year-end wealth management review; charitable giving strategy | P1 |

### Wealth Management for High-Value Basketball Athletes

```
WEALTH MANAGEMENT TIERS:

  Tier 1: NIL Income > $500K/year
    - Full wealth management plan
    - Investment advisory
    - Tax optimization strategy
    - Estate planning introduction
    - Monthly check-ins

  Tier 2: NIL Income $100K-$500K/year
    - Basic financial planning
    - Tax preparation and filing
    - Savings and budgeting guidance
    - Quarterly check-ins

  Tier 3: NIL Income < $100K/year
    - Tax preparation
    - Financial literacy education
    - Workshop attendance
    - Semi-annual check-ins
```

---

## Affiliate Admin Operations

The `affiliate_admin` role manages the affiliate organization:

### Affiliate Admin Responsibilities

| Area | Description | Screen |
|---|---|---|
| Team Management | Manage affiliate team members, roles, and assignments | `/affiliate-admin` |
| Org Settings | Organization-level configuration and user management | `/dashboard/org-settings` |
| Performance Oversight | Monitor affiliate team revenue and service metrics | `/affiliate-admin` |
| Directory Management | Ensure accurate directory listings for all team members | `/affiliate-directory` |
| Workshop Coordination | Approve and schedule affiliate workshop huddles | `/affiliate-admin` |

### Admin KPIs

| KPI | Definition | Target |
|---|---|---|
| Team Revenue | Total revenue across all affiliate advisors | Growth MoM |
| Advisor Utilization | % of advisor capacity being utilized | 80%+ |
| Client Distribution | Balance of accounts across advisors | Even distribution |
| Workshop Delivery | Workshops delivered per month | 1+ per advisor |

---

## Access and Permissions

| Capability | Affiliate | Affiliate Admin |
|---|---|---|
| View client accounts | Yes (own clients) | Yes (all clients) |
| Manage service delivery | Yes | Yes |
| Initiate outbound messages | No (inbound-first only) | No (inbound-first only) |
| Reply to existing message threads | Yes | Yes |
| Host affiliate workshop huddles | Yes | Yes |
| Manage organization settings | No | Yes |
| Invite affiliate-level users | No | Yes |
| Access athlete private dashboard | No | No |
| Create NIL payments | No | No |
| Browse agent directory | Yes | Yes |

---

## Seasonal Calendar

| Month | Focus Area | Key Action |
|---|---|---|
| August | Preseason onboarding | Onboard new athlete clients; establish service agreements |
| September | Season kickoff | Activate advisory services; schedule Q4 estimated payments |
| October | Q3 estimated payment review | Ensure Q3 payments processed; begin Q4 planning |
| November | Year-end planning begins | Tax-loss harvesting; charitable giving strategy |
| December | Year-end close | Finalize year-end financial actions; holiday scheduling |
| January | Tax season prep begins | Q4 estimated payments; 1099 collection; prep for filing |
| February | Tax filing preparation | Full tax prep for basketball athletes (complex multi-state) |
| March | Tournament tax tracking | Track multi-state tournament income; support filing |
| April | Tax filing deadline | Filing deadline execution; extension management |
| May | Post-season financial review | Year-in-review with clients; summer planning |
| June | Q2 estimated payments | Process estimated payments; mid-year wealth review |
| July | Off-season advisory | Financial literacy workshops; new client onboarding |

---

*NIL Optic -- Professional advisory for the NIL generation.*
