# Operations Playbook: Platform Admin

> Last updated: 2026-03-04

---

## Role Overview

**Who:** NIL Optic internal team members responsible for managing the platform infrastructure, user operations, data quality, prediction accuracy, sync pipelines, and overall system health. Platform Admins are the operational backbone that ensures every external persona -- from Athletic Directors to Fans -- has a reliable, accurate, and performant experience.

**Organization category:** NIL Optic internal (not an external organization category)
**Role key:** `admin`
**Shell route:** `/admin`

Platform Admins have the broadest system access and the highest operational accountability. They own user onboarding pipelines, prediction model governance, data sync orchestration, and the battle board that tracks NCAA program coverage and conference penetration.

### Core Responsibilities

- Monitor system health, uptime, and performance metrics
- Manage user support queue and resolve escalated issues
- Oversee data sync pipelines and SportsRadar integration health
- Govern prediction accuracy and model calibration
- Manage user onboarding and organization/program setup
- Track platform adoption metrics and feature usage
- Maintain battle board for NCAA program coverage tracking
- Manage admin-level user accounts and permissions

---

## Daily Operations

**Time allocation:** 60--90 minutes

### Morning System Health Check (`7:00 AM`)

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P0 | System health monitoring -- uptime, error rates, response times | `/admin` | 10 min |
| P0 | User support queue -- triage and assign tickets | `/admin/users` | 15 min |
| P0 | Sync status check -- verify overnight data syncs completed | `/admin/sync` | 10 min |
| P1 | Prediction accuracy spot check -- flag any anomalies | `/admin/predictions` | 10 min |
| P1 | Transfer portal data freshness -- verify portal data is current | `/admin/transfer-portal` | 5 min |
| P2 | Review admin messages and internal escalations | `/dashboard/messages` | 10 min |

### Afternoon Operations (`2:00 PM`)

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P0 | Support queue follow-up -- resolve pending tickets | `/admin/users` | 15 min |
| P1 | Onboarding pipeline check -- pending invites, stuck onboarding flows | `/admin/onboarding` | 10 min |
| P2 | Feature usage analytics spot check | `/admin` | 10 min |

### Daily KPI Glance

| Metric | Source | Format |
|---|---|---|
| System Uptime | Infrastructure monitoring | `XX.XX%` |
| Active Users (24h) | `/admin` metrics | `#,###` |
| Open Support Tickets | `/admin/users` | `#` |
| Sync Job Status | `/admin/sync` | Pass / Fail / Stale |
| Prediction Jobs (Last Run) | `/admin/predictions` | Timestamp + status |
| Pending Onboarding | `/admin/onboarding` | `#` |

### Sync Status Assessment

```
SYNC HEALTH PROTOCOL:

  CHECK 1: Did all overnight sync jobs complete?
    → /admin/sync -- verify last run timestamp < 12 hours ago
    → If FAILED: check error logs, retry manual sync

  CHECK 2: Is game data current?
    → Division I game sync should reflect yesterday's games
    → If STALE: trigger manual date-range sync

  CHECK 3: Are rankings updated?
    → NET rankings sync should reflect latest release
    → Conference leaders and standings should match source

  CHECK 4: Is prediction data fresh?
    → Full sync + predictions should complete within SLA
    → If STALE: trigger manual full sync + predictions run

  SYNC JOBS (via /sync-server):
    - Division I game sync (date range)
    - NET rankings
    - Conference leaders
    - Standings
    - Full sync + predictions
```

---

## Weekly Cadence

**Day:** Monday (operational review) + Wednesday (data quality) + Friday (growth)

### Monday: Operational Review

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Onboarding pipeline review -- new orgs, pending invites, blockers | `/admin/onboarding` | Admin team |
| 9:30 AM | Prediction accuracy audit -- compare predictions to actuals | `/admin/predictions` | Admin + Data team |
| 10:00 AM | Data quality sweep -- missing data, stale records, anomalies | `/admin/sync` | Admin + Data team |
| 10:30 AM | User management review -- new accounts, role assignments, issues | `/admin/users` | Admin team |

### Wednesday: Data Quality Deep-Dive

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | SportsRadar data integrity check | `/admin/sync` | Admin + Engineering |
| 9:30 AM | Tournament data freshness verification | `/admin/transfer-portal` | Admin solo |
| 10:00 AM | Prediction model calibration review | `/admin/predictions` | Admin + Data Science |

### Friday: Growth and Adoption

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Platform metrics review -- WAU, feature adoption, session duration | `/admin` | Admin + Product |
| 9:30 AM | Battle board update -- program coverage, conference penetration | Internal tracking | Admin + Growth |
| 10:00 AM | New organization onboarding status -- pipeline health | `/admin/onboarding` | Admin + Sales |

### Weekly Report Outputs

- System health summary: uptime, incidents, resolution times
- Sync pipeline status: all jobs, last run, success/failure
- Prediction accuracy report: accuracy %, drift indicators
- Onboarding pipeline: new orgs in funnel, conversion rate
- Support metrics: tickets opened, resolved, average resolution time

---

## Monthly Cadence

**Timing:** First week of each month

### Platform Metrics Review

| Task | Description | Screen |
|---|---|---|
| Active Users Analysis | MAU, WAU, DAU breakdown by role and organization | `/admin` |
| Feature Usage Analytics | Adoption rates for key features: Pipelines, Roster Builder, Predictions, Messages | `/admin` |
| Growth Reporting | New organizations onboarded, new users, churn analysis | `/admin/onboarding` |
| Prediction Accuracy Monthly | Aggregate prediction accuracy; identify systematic bias | `/admin/predictions` |
| Data Quality Report | Missing data %, stale records %, sync failure rate | `/admin/sync` |
| Support Resolution Metrics | Average resolution time, ticket volume by category, satisfaction | `/admin/users` |

### Monthly Meeting Cadence

| Meeting | Audience | Deliverable |
|---|---|---|
| Platform Health Review | Engineering + Admin | System reliability report |
| Data Quality Standup | Data + Admin | Data integrity scorecard |
| Growth Review | Sales + Admin + Product | Onboarding funnel and adoption metrics |
| Prediction Governance | Data Science + Admin | Model accuracy and calibration report |
| Support Retrospective | Customer Success + Admin | Support trends and improvement plan |

### Monthly KPI Scorecard

| KPI | Target | Measurement |
|---|---|---|
| System Uptime | 99.9%+ | % from monitoring |
| Active Users (MAU) | Growth MoM | `#,###` from analytics |
| Program Onboarding Rate | 5+ new programs/month | `#` from `/admin/onboarding` |
| Prediction Accuracy | 85%+ | `%` from `/admin/predictions` |
| Support Resolution Time | < 24 hours average | Hours from ticket data |
| Sync Success Rate | 99%+ | `%` from `/admin/sync` |

---

## Key Screens

| Screen | Route | Primary Use |
|---|---|---|
| Admin Home | `/admin` | Control center overview, system metrics |
| Users | `/admin/users` | User management, org/program membership, invite management |
| Admins | `/admin/admins` | Platform admin account management |
| Onboarding | `/admin/onboarding` | Onboarding question/flow management (admin-internal only) |
| Predictions | `/admin/predictions` | Prediction run management, accuracy settings |
| Tournaments | `/admin/tournaments` | Tournament data management |
| Transfer Portal | `/admin/transfer-portal` | Transfer portal override controls |
| Presentation Tools | `/admin/presentations` | Admin presentation workspace |
| Capability Matrix | `/admin/capability-matrix` | Role capability matrix viewer |
| Emails | Via admin tools | SendGrid email template management |
| Sync | `/admin/sync` | Data sync job management and scheduling |

### Admin Left Navigation

```
ADMIN NAV ITEMS:
  - Admin Home (/admin)
  - Onboarding (/admin/onboarding)
  - Users (/admin/users)
  - Admins (/admin/admins)
  - Capability Matrix (/admin/capability-matrix)
  - Predictions (/admin/predictions)
  - Tournaments (/admin/tournaments)  -- Note: links to /admin/tournaments
  - Transfer Portal (/admin/transfer-portal)
  - Presentation Tools (/admin/presentations)
  - Emails (admin email tooling)
  - Sync (/admin/sync)

GLOBAL NAV (all authenticated users):
  - Agent Directory (/agent-directory)
  - Affiliate Directory (/affiliate-directory)
  - Favorites (/dashboard/favorites)
  - Pipelines (/dashboard/pipelines)
  - Roster Builder (/dashboard/roster-builder)
  - Tournaments (/dashboard/tournaments)
```

### Navigation Context

- Admin shell renders through shared `DashboardShell` with admin role context
- Cross-shell link to `/designer` if user has designer scope
- Role switcher visible in top nav (lists all possessed roles + Fan preview)
- Top nav shows context title with `Huddles` and `Messages` controls
- Keyboard shortcuts: `L` light / `D` dark / `H` huddles / `M` messages / `1-9` sidebar pages

---

## KPIs

### Primary KPIs

| KPI | Definition | Target | Font |
|---|---|---|---|
| Active Users (MAU) | Unique users with at least one session in rolling 30 days | Growth MoM | `JetBrains Mono` `#,###` |
| Program Onboarding Rate | New programs completing full onboarding per month | 5+ | `JetBrains Mono` `##` |
| Prediction Accuracy | % of athlete valuations within confidence interval of actual market | 85%+ | `JetBrains Mono` `XX.X%` |
| System Uptime | % of time platform is available and responsive | 99.9%+ | `JetBrains Mono` `XX.XX%` |
| Support Resolution Time | Average hours from ticket open to resolution | < 24 hours | `JetBrains Mono` `XX.Xh` |

### Secondary KPIs

| KPI | Definition | Target |
|---|---|---|
| Sync Success Rate | % of scheduled sync jobs completing without error | 99%+ |
| Feature Adoption Rate | % of active users engaging with key features per month | 60%+ |
| Onboarding Completion Rate | % of invited users completing full onboarding | 80%+ |
| Data Freshness | Average age of SportsRadar data (hours since last sync) | < 12 hours |
| Conference Penetration | % of D1 conferences with at least one program on platform | Growth QoQ |

---

## Escalation Paths

| Trigger | Severity | Escalation Target | SLA |
|---|---|---|---|
| System outage / service unavailable | CRITICAL | Engineering on-call + CTO | 15 minutes |
| Data sync failure (all jobs) | CRITICAL | Engineering + Data team | 1 hour |
| Prediction model producing invalid results | HIGH | Data Science + Engineering | 4 hours |
| User unable to access platform (auth issue) | HIGH | Admin immediate + Engineering if code issue | 2 hours |
| Compliance-sensitive data exposed | CRITICAL | Security + Legal + CTO | Immediate |
| High-priority user support request (D1 AD) | HIGH | Admin + Customer Success lead | 4 hours |
| Onboarding stuck for new organization | MEDIUM | Admin + Sales | 24 hours |
| Minor UI bug reported | LOW | Engineering backlog | 1 week |

### Escalation Flow

```
LEVEL 1: Admin Self-Service
  - Check system dashboards
  - Retry sync jobs manually
  - Resolve user account issues
  - Reset onboarding states

LEVEL 2: Admin + Engineering
  - Escalate sync failures
  - Debug auth/access issues
  - Investigate prediction anomalies
  - Address performance degradation

LEVEL 3: Admin + Leadership
  - Report outages to CTO
  - Security incidents to Security + Legal
  - Data breaches to full incident response team
  - Major customer escalations to CEO/COO
```

---

## Battle Board Integration

The battle board is the strategic tool that tracks NIL Optic's penetration across the NCAA landscape. Platform Admins own the data that feeds the battle board.

### NCAA Program Coverage Tracking

| Metric | Definition | Current Target |
|---|---|---|
| Total Programs Onboarded | Count of programs with active organization setup | Growth MoM |
| D1 Program Coverage | % of D1 programs on platform | 25% by EOY |
| D2 Program Coverage | % of D2 programs on platform | 10% by EOY |
| D3 Program Coverage | % of D3 programs on platform | 5% by EOY |
| Conference Penetration | % of conferences with 2+ programs | 50% of Power 4 |

### Conference Penetration Metrics

```
CONFERENCE PENETRATION TIERS:

  TIER 1 - POWER 4 (Priority):
    SEC:          ##/16 programs onboarded
    Big Ten:      ##/18 programs onboarded
    Big 12:       ##/16 programs onboarded
    ACC:          ##/17 programs onboarded

  TIER 2 - HIGH MAJOR:
    American:     ##/14 programs
    Mountain West: ##/12 programs
    WCC:          ##/11 programs
    MVC:          ##/12 programs

  TIER 3 - MID-MAJOR:
    [Additional conferences tracked in battle-board/]

  PENETRATION SCORE:
    Conference Penetration % = Programs Onboarded / Total Conference Programs * 100
    Target: 50%+ for Power 4 conferences within 12 months
```

### Battle Board Data Sources

| Data Point | Source | Update Frequency |
|---|---|---|
| Program count by conference | SportsRadar via `/admin/sync` | Weekly |
| Onboarded program count | `/admin/onboarding` | Real-time |
| Active user count per program | `/admin/users` analytics | Daily |
| Revenue per program | Business systems | Monthly |
| Feature adoption per program | Platform analytics | Weekly |

---

## Sync Operations

### Sync Job Management (`/admin/sync`)

All sync jobs execute through the external `/sync-server` (not Next.js server actions) and stream live per-stage progress.

| Sync Job | Description | Frequency |
|---|---|---|
| Division I Game Sync | Sync game data for specified date range | Daily (overnight) |
| NET Rankings | Sync latest NET ranking data | Daily |
| Conference Leaders | Sync conference statistical leaders | Daily |
| Standings | Sync team standings data | Daily |
| Full Sync + Predictions | Complete data refresh and prediction model run | Daily (overnight) |

### Sync Schedule Management

| Setting | Description |
|---|---|
| Enable/Disable Schedule | Toggle automated sync on/off |
| UTC Run Time | Configure when scheduled syncs execute |
| Persistence | Schedule config stored in Supabase automation config tables |
| Manual Override | Support manual runs for any sync job at any time |

### Sync Monitoring

```
SYNC HEALTH DASHBOARD:

  For each job:
    - Last run timestamp
    - Duration (minutes)
    - Status: SUCCESS / FAILED / IN_PROGRESS / STALE
    - Records processed: current/total (live streaming during execution)
    - Error count and details (if failed)

  ALERT THRESHOLDS:
    - Job not completed within 2x expected duration → WARNING
    - Job failed → ALERT to admin team
    - Data not refreshed in 24 hours → CRITICAL
```

---

## User and Onboarding Management

### User Management (`/admin/users`)

| Operation | Description |
|---|---|
| Organization User Management | View/manage org memberships across all organizations |
| Program User Management | View/manage program memberships per organization |
| Invite Email Preview | Preview branded invite email templates |
| SendGrid Test-Send | Test invite emails (Org/Program/Athlete scopes) |
| Role Assignment | Manage user role metadata |
| Account Status | View account status, last login, activity |

### Onboarding Pipeline (`/admin/onboarding`)

| Stage | Description | Admin Action |
|---|---|---|
| Invite Sent | Organization invite dispatched | Monitor delivery |
| Invite Accepted | User accepted invite and created account | Verify role setup |
| Onboarding Started | User began onboarding flow | Monitor progress |
| Onboarding Complete | User completed all onboarding steps | Confirm data quality |
| Active User | User regularly accessing platform | Track engagement |

### Onboarding Governance

- Onboarding question/flow management is admin-internal only (`/admin/onboarding`)
- Non-admin users must not see onboarding management UI in dashboard navigation
- User onboarding does not include role-selection prompts
- Role context is derived from authenticated role/profile state, not manual selection
- If no org/program context exists, onboarding does not auto-launch

---

## Prediction Governance

### Prediction Operations (`/admin/predictions`)

| Task | Frequency | Description |
|---|---|---|
| Prediction Run Trigger | Daily (automated) + manual as needed | Execute prediction model against current data |
| Accuracy Audit | Weekly | Compare predicted valuations to market actuals |
| Model Calibration Review | Monthly | Assess systematic bias and drift |
| Confidence Interval Check | Weekly | Verify confidence bands are well-calibrated |
| Fan-Lite Prediction Scope | Ongoing | Ensure limited users see only top-3 valuation windows |

### Prediction Accuracy Framework

```
ACCURACY MEASUREMENT:

  METRIC 1: Mean Absolute Error (MAE)
    → Average absolute difference between predicted and actual valuation
    → Target: < 15% of average valuation

  METRIC 2: Directional Accuracy
    → % of predictions that correctly predict up/down/flat direction
    → Target: 80%+

  METRIC 3: Confidence Calibration
    → % of actual values falling within stated confidence interval
    → Target: 85%+ within 90% CI

  METRIC 4: Bias Check
    → Average signed error (positive = overestimating, negative = underestimating)
    → Target: Near zero (< 3% bias)
```

---

## Access and Permissions

| Capability | Allowed |
|---|---|
| View all platform data | Yes |
| Manage all user accounts | Yes |
| Manage admin accounts | Yes |
| Run and configure sync jobs | Yes |
| Run and configure predictions | Yes |
| Manage onboarding flows | Yes |
| Manage transfer portal overrides | Yes |
| Access capability matrix viewer | Yes |
| Access presentation tools | Yes |
| Manage invite emails and SendGrid templates | Yes |
| Cross-shell link to designer (if designer scope) | Yes |
| Create NIL payments | No (agent-scoped) |

---

## Seasonal Calendar

| Month | Focus Area | Key Action |
|---|---|---|
| August | Pre-season data prep | Verify all roster data synced; test prediction models |
| September | Season launch | Monitor system load; ensure sync stability |
| October | Q4 operational review | Platform metrics; onboarding funnel health |
| November | Tournament data surge | MTE game data sync; prediction accuracy check |
| December | Year-end review | Annual metrics compilation; system maintenance window |
| January | Conference play data load | Elevated sync monitoring; prediction recalibration |
| February | Pre-tournament prep | Tournament bracket data prep; system load testing |
| March | March Madness peak | Maximum operational intensity; 24/7 monitoring |
| April | Post-season transition | Transfer portal data activation; system recovery |
| May | Portal data peak | Portal sync monitoring; prediction model updates |
| June | Platform maintenance | Feature deployment; infrastructure upgrades |
| July | Pre-season preparation | Data pipeline validation; onboarding pipeline prep |

---

*NIL Optic -- The engine behind the intelligence.*
