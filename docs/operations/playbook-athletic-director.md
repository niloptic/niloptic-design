# Operations Playbook: Athletic Director

> Last updated: 2026-03-04

---

## Role Overview

**Who:** Athletic Directors at D1, D2, and D3 programs responsible for managing NIL compliance, program valuation, budget allocation, and the strategic positioning of their athletic department in the NIL marketplace.

**Organization category:** `athletic`
**Role key:** `athletic_director`
**Shell route:** `/athletic-director`

Athletic Directors operate at the intersection of compliance, finance, and competitive strategy. They own the holistic NIL health of their program -- from ensuring every deal passes compliance review to presenting board-ready NIL valuations that justify budget decisions. NIL Optic gives ADs executive-grade visibility into the full NIL landscape of their program across every sport, with basketball as the highest-value anchor.

### Core Responsibilities

- Own total program NIL valuation and trend direction
- Ensure 100% compliance across all active athlete deals
- Manage and allocate NIL budgets across sports programs
- Report NIL performance to university leadership and boards
- Coordinate with coaches, agents, and affiliate partners
- Monitor transfer portal activity for roster impact on valuations
- Benchmark program NIL position against conference and division peers

---

## Daily Operations

**Time allocation:** 30--45 minutes

### Morning Check-in (`8:00 AM`)

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P0 | Review compliance alert queue | `/athletic-director` | 5 min |
| P0 | Check program NIL value dashboard -- value change vs. prior day | `/athletic-director` | 5 min |
| P1 | Scan active deals for status changes (new, pending, closed) | `/dashboard/pipelines` | 10 min |
| P1 | Review inbound messages from coaches, agents, affiliates | `/dashboard/messages` | 10 min |
| P2 | Check transfer portal activity for roster-impact alerts | `/transfer-portal` | 5 min |

### Compliance Alert Response Protocol

```
IF compliance alert severity = CRITICAL
  THEN escalate to General Counsel within 1 hour
  AND flag athlete + deal in pipeline as HOLD

IF compliance alert severity = WARNING
  THEN review deal terms within 24 hours
  AND schedule coach check-in if athlete is flagged

IF compliance alert severity = INFO
  THEN batch review during weekly compliance audit
```

### Daily KPI Glance

| Metric | Source | Format |
|---|---|---|
| Program NIL Value | `/athletic-director` KPI strip | `$XX.XM` |
| Value Change (24h) | `/athletic-director` trend indicator | `+/- $X.XK` |
| Active Deals | `/dashboard/pipelines` count | `#` |
| Compliance Rate | `/athletic-director` compliance widget | `XX.X%` |
| Unread Messages | `/dashboard/messages` badge | `#` |

---

## Weekly Cadence

**Day:** Monday (operational review) + Thursday (forward planning)

### Monday: Operational Review

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Roster valuation review -- all sports, basketball priority | `/athletic-director` | AD + Assistant ADs |
| 9:30 AM | Compliance audit sweep -- flag any open issues | `/athletic-director` | AD + Compliance staff |
| 10:00 AM | Budget vs. actual review -- Actual Budget and EST Cap tabs | `/dashboard/org-settings` | AD + CFO liaison |
| 10:30 AM | Coach check-ins -- basketball HC, then by sport priority | `/dashboard/messages` | AD + Head Coaches |

### Thursday: Forward Planning

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Transfer portal pipeline review -- incoming/outgoing athletes | `/transfer-portal` | AD + Recruiting Coordinator |
| 9:30 AM | Agent coordination -- review pending deal terms | `/dashboard/pipelines` | AD + Agent contacts |
| 10:00 AM | Conference positioning review -- rank within conference | `/athletic-director` | AD solo |

### Weekly Report Outputs

- Roster valuation summary by sport (basketball highlighted)
- Compliance status report: clean / flagged / escalated
- Budget utilization snapshot: allocated vs. spent vs. remaining
- Transfer portal impact assessment

---

## Monthly Cadence

**Timing:** First full week of each month

### Board Reporting Prep

| Task | Description | Screen |
|---|---|---|
| NIL Trend Analysis | Pull 30-day program valuation trend; compare to conference average | `/athletic-director` |
| Conference Comparison | Rank program against all conference peers by total NIL value | `/athletic-director` conference rankings |
| Budget Forecast | Project remaining budget based on current deal pipeline velocity | `/dashboard/org-settings` |
| Compliance Summary | Aggregate compliance incidents -- resolved, pending, escalated | `/athletic-director` |
| Athlete Coverage Report | Calculate % of roster with active NIL deals by sport | `/dashboard/pipelines` |

### Monthly Meeting Cadence

| Meeting | Audience | Deliverable |
|---|---|---|
| AD Monthly Review | University President / Provost | 1-page NIL health summary |
| Coach Roundtable | All head coaches | Sport-by-sport NIL landscape briefing |
| Agent Coordination | Primary agents | Deal pipeline status and forecast |
| Affiliate Partner Check-in | Tax/wealth affiliates | Service utilization and athlete engagement |

### NIL Trend Analysis Framework

```
MONTHLY TREND DIMENSIONS:
  1. Total program valuation: direction + magnitude
  2. Per-athlete average valuation: rising / flat / declining
  3. Deal volume: new deals opened vs. closed vs. expired
  4. Social reach aggregate: total follower growth across roster
  5. Conference relative position: rank movement + gap to #1
```

---

## Quarterly Business Review (QBR)

**Timing:** End of each academic quarter (Oct, Jan, Apr, Jul)

### QBR Deliverables

| Deliverable | Format | Audience |
|---|---|---|
| Full Program NIL Report | Executive deck, 10--15 slides | Board of Trustees |
| Budget Forecasting Model | Spreadsheet + dashboard export | CFO + Budget Committee |
| Competitive Benchmarking | Conference and division comparison tables | President + AD staff |
| Compliance Audit Results | Formal compliance report | General Counsel + NCAA liaison |
| Transfer Portal Impact Analysis | Roster valuation delta report | Coaches + Recruiting |

### QBR Preparation Timeline

| Week | Activity |
|---|---|
| QBR -3 weeks | Begin data collection; export NIL report from `/nil-report` |
| QBR -2 weeks | Draft executive summary; pull prediction accuracy metrics from `/predictions` |
| QBR -1 week | Internal review with Assistant ADs; finalize slide deck |
| QBR week | Present to Board; distribute digital report |

### QBR KPI Scorecard

| KPI | Target | Measurement |
|---|---|---|
| Total Program NIL Value | Quarter-over-quarter growth | `$XX.XM` from `/athletic-director` |
| Compliance Rate | 100% | Zero unresolved violations |
| Active Deals Count | Sport-proportional targets | `#` from `/dashboard/pipelines` |
| Budget Utilization | 85--95% allocation | `%` from `/dashboard/org-settings` |
| Athlete Coverage | 60%+ roster with active deals | `%` from roster vs. pipeline cross-reference |
| Conference Rank | Top quartile | Ordinal rank from conference comparison |

---

## Key Screens

| Screen | Route | Primary Use |
|---|---|---|
| AD Dashboard | `/athletic-director` | NIL value overview, compliance, conference rank |
| AD Settings | `/athletic-director/settings` | Budget allocation, org user management |
| Pipelines | `/dashboard/pipelines` | Deal tracking across all sports |
| Org Settings | `/dashboard/org-settings` | Budget vs. actual, Org Cap Table (Actual Budget / EST Cap / Roster tabs) |
| Messages | `/dashboard/messages` | Coach, agent, and affiliate communication |
| NIL Report | `/nil-report` | Program NIL trend summaries and top-10 lists |
| Predictions | `/predictions` | Athlete valuation forecasting |
| Transfer Portal | `/transfer-portal` | Transfer portal athlete monitoring |
| Sports Directory | `/directory` | Conference/division/team drill-down analytics |
| Roster Builder | `/dashboard/roster-builder` | Roster planning and budget modeling |

### Navigation Context

- Left nav includes: `Roster Builder`, `Favorites`, `Pipelines`, `Agent Directory`, `Affiliate Directory`
- Profile menu exposes `Organization Settings` (not Coach Settings)
- Top nav shows organization/program context title with `Huddles` and `Messages` controls
- Keyboard shortcuts: `L` light / `D` dark / `H` huddles / `M` messages / `1-9` sidebar pages

---

## KPIs

### Primary KPIs

| KPI | Definition | Target | Font |
|---|---|---|---|
| Total Program NIL Value | Aggregate estimated NIL value across all rostered athletes | Growth QoQ | `JetBrains Mono` `$XX.XM` |
| Compliance Rate | % of active deals passing compliance review | 100% | `JetBrains Mono` `XX.X%` |
| Active Deals Count | Total deals in pipeline with status != closed/expired | Sport-proportional | `JetBrains Mono` `###` |
| Budget Utilization % | Allocated budget spent / total budget | 85--95% | `JetBrains Mono` `XX.X%` |
| Athlete Coverage % | Athletes with 1+ active NIL deal / total roster size | 60%+ | `JetBrains Mono` `XX.X%` |

### Secondary KPIs

| KPI | Definition | Target |
|---|---|---|
| Conference Rank | Program NIL value rank within conference | Top quartile |
| Transfer Portal Net Value | NIL value gained - lost via portal movement | Positive delta |
| Average Deal Size | Total deal value / number of deals | Growth trend |
| Social Reach Aggregate | Total social followers across rostered athletes | Growth trend |
| Agent Coordination Score | % of deals with agent-AD communication in last 30 days | 80%+ |

---

## Escalation Paths

| Trigger | Severity | Escalation Target | SLA |
|---|---|---|---|
| Compliance violation detected | CRITICAL | General Counsel + NCAA Compliance Officer | 1 hour |
| Budget overage > 5% | HIGH | CFO + University Budget Committee | 24 hours |
| Athlete dispute (deal terms) | HIGH | AD direct resolution + legal if needed | 24 hours |
| Agent non-responsiveness on active deal | MEDIUM | AD outreach + agency admin escalation | 48 hours |
| Transfer portal high-value departure | MEDIUM | AD + Head Coach immediate review | 24 hours |
| Data sync failure (valuations stale) | MEDIUM | Platform Admin + NIL Optic support | 4 hours |
| Prediction accuracy below threshold | LOW | AD awareness + data team review | 1 week |

### Escalation Flow

```
LEVEL 1: AD Self-Service
  - Review dashboard alerts
  - Check deal pipeline status
  - Message coach or agent directly

LEVEL 2: AD + Staff
  - Loop in Assistant AD or General Manager
  - Schedule huddle for real-time coordination
  - Document issue in pipeline notes

LEVEL 3: AD + External
  - Engage General Counsel (compliance)
  - Engage CFO (budget)
  - Contact NIL Optic support (platform issues)
```

---

## Basketball-First Focus

Basketball is the highest-value sport in the NIL landscape for the majority of D1 programs. The Athletic Director playbook prioritizes basketball operations accordingly.

### Basketball Roster as Value Anchor

- Basketball roster typically represents 30--50% of total program NIL value
- Starting five often account for 60--70% of basketball team value
- Point guard and center positions carry disproportionate NIL premium
- One-and-done / transfer portal players create acute valuation volatility

### March Madness Tournament Prep

| Timeline | Action | Priority |
|---|---|---|
| Selection Sunday -4 weeks | Baseline all basketball player valuations; lock pre-tournament snapshot | P0 |
| Selection Sunday -2 weeks | Activate social media amplification strategy for key players | P1 |
| Selection Sunday | Capture tournament seed and matchup data; project exposure value | P0 |
| Tournament Week 1 | Monitor real-time valuation changes per game performance | P0 |
| Sweet 16 / Elite 8 | Assess brand partnership inbound surge; coordinate with agents | P0 |
| Final Four | Maximum valuation window -- lock favorable deal terms | P0 |
| Post-Tournament +1 week | Capture tournament valuation lift; compare to pre-tournament baseline | P0 |

### Transfer Portal Monitoring

```
BASKETBALL PORTAL PRIORITY MATRIX:

  HIGH IMPACT (monitor daily):
    - Starting five members entering portal
    - Top-50 ranked portal entrants in conference
    - Players with >$500K estimated NIL value

  MEDIUM IMPACT (monitor weekly):
    - Bench rotation players (6th--10th man)
    - Transfers from rival conference programs
    - International players with social reach >100K

  LOW IMPACT (monitor monthly):
    - Walk-on portal entries
    - Non-scholarship transfers
    - Redshirt players without NIL activity
```

### Basketball-Specific KPIs

| KPI | Definition | Target |
|---|---|---|
| Basketball Team NIL Value | Total estimated NIL for basketball roster | Top 5 in conference |
| Starting 5 Concentration | % of team value held by starters | Monitor (not a target -- awareness metric) |
| Tournament Valuation Lift | Post-tournament value minus pre-tournament baseline | Positive delta |
| Portal Net Value (Basketball) | NIL value gained minus lost from basketball portal activity | Positive delta |
| Basketball Deal Velocity | New basketball deals per month | 3+ per month during season |

---

## Seasonal Calendar

| Month | Focus Area | Key Action |
|---|---|---|
| August | Preseason preparation | Lock roster valuations; set season budget |
| September | Early season positioning | Conference preseason rankings; agent coordination |
| October | QBR #1 | Board reporting; budget check |
| November | Non-conference tournament play | Monitor valuation movement from early results |
| December | Finals + holiday scheduling | Reduced cadence; maintain compliance monitoring |
| January | QBR #2; conference play begins | Conference comparison deep-dive |
| February | Tournament positioning | Bracket projections; valuation forecasting |
| March | March Madness | Maximum operational intensity |
| April | QBR #3; post-season review | Tournament ROI analysis; portal monitoring |
| May | Transfer portal peak | Roster reconstruction planning |
| June | Off-season planning | Budget forecasting; recruiting strategy |
| July | QBR #4; fiscal year prep | Annual reporting; next-year budget submission |

---

## Tool Reference

| Tool | Purpose | Access |
|---|---|---|
| Org Cap Table | View Actual Budget, EST Cap, and Roster allocation tabs | `/athletic-director` |
| Conference Rankings | Rank teams within conference by NIL value | `/athletic-director` |
| Pipeline Board | Kanban-style deal tracking with stage progression | `/dashboard/pipelines` |
| Roster Builder | Model roster composition and budget scenarios | `/dashboard/roster-builder` |
| Predictions Engine | Forecast athlete valuations with confidence intervals | `/predictions` |
| NIL Report | Aggregated NIL trend data and top performer lists | `/nil-report` |
| Huddles | Live video coordination with coaches, agents, affiliates | `/dashboard/messages` > Start Meet |

---

## Access and Permissions

| Capability | Allowed |
|---|---|
| View all program athlete valuations | Yes |
| Manage organization budget and allocations | Yes (sport/team-level) |
| Invite org-level users (AD, AAD, GM roles) | Yes |
| Add SportsRadar-backed sport/team programs | Yes |
| Create NIL payments | No (agent-scoped only) |
| Access athlete private dashboard | No (requires explicit athlete role) |
| Initiate messages to any authenticated user | Yes |
| Host huddles and meets | Yes |

---

*NIL Optic -- Executive-grade NIL intelligence for Athletic Directors.*
