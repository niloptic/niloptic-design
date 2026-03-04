# Operations Playbook: Coach

> Last updated: 2026-03-04

---

## Role Overview

**Who:** Head coaches and assistant coaches managing the team NIL landscape, using NIL intelligence as a recruiting tool, and ensuring their roster composition maximizes both competitive performance and program NIL value.

**Organization category:** `athletic` (program-scoped)
**Role key:** `coach`
**Shell route:** `/coach`

Coaches sit at the operational center of the NIL ecosystem. They manage the day-to-day reality of how NIL impacts team dynamics, recruiting decisions, and roster construction. NIL Optic gives coaches the same executive dashboard composition as Athletic Directors -- team roster valuations, pipeline management, and budget tools -- with coach-specific labeling and player-level allocation detail.

### Core Responsibilities

- Monitor team roster valuations and individual player NIL trends
- Use NIL data as a recruiting tool for prospective student-athletes
- Manage player pipeline for recruiting and transfer portal activity
- Allocate per-player budgets within program NIL allocation
- Coordinate with Athletic Director on program-level NIL strategy
- Ensure player compliance awareness through communication
- Build roster composition strategies that optimize NIL + competitive value

---

## Daily Operations

**Time allocation:** 30--45 minutes

### Morning Check-in (`7:30 AM`)

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P0 | Review team roster valuations -- flag significant changes | `/coach` | 10 min |
| P1 | Check recruiting pipeline -- new prospects, stage changes | `/dashboard/pipelines` | 10 min |
| P1 | Monitor player compliance status -- any flags from AD | `/dashboard/messages` | 5 min |
| P2 | Review transfer portal activity -- departures and targets | `/transfer-portal` | 5 min |
| P2 | Check messages from AD, agents, or recruits | `/dashboard/messages` | 5 min |

### Daily KPI Glance

| Metric | Source | Format |
|---|---|---|
| Team Total NIL Value | `/coach` Team Cap Table | `$XX.XM` |
| Team Value Change (24h) | `/coach` trend indicator | `+/- $X.XK` |
| Roster Size | `/coach` roster section | `#/##` (filled/max) |
| Recruiting Pipeline Count | `/dashboard/pipelines` | `#` |
| Unread Messages | `/dashboard/messages` badge | `#` |

### Player Valuation Alert Protocol

```
IF player valuation change > +10% in 24h
  THEN note as positive -- potential agent activity or viral moment
  AND check social media / news context

IF player valuation change > -10% in 24h
  THEN flag for review -- injury? controversy? portal rumors?
  AND schedule 1:1 check-in with player

IF starter valuation drops > 5% for 3 consecutive days
  THEN escalate to AD awareness
  AND coordinate with player's agent if applicable
```

---

## Weekly Cadence

**Day:** Monday (team NIL meeting prep) + Wednesday (recruiting)

### Monday: Team NIL Review

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 8:00 AM | Team NIL meeting prep -- compile roster valuation summary | `/coach` | Coach solo |
| 8:30 AM | Recruiting outreach -- contact top 3 pipeline prospects | `/dashboard/messages` | Coach solo |
| 9:00 AM | Budget allocation review -- per-player allocation accuracy | `/coach/settings` | Coach + Assistant Coaches |
| 9:30 AM | AD check-in -- program NIL status alignment | `/dashboard/messages` | Coach + AD |

### Wednesday: Recruiting and Planning

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 8:00 AM | Transfer portal pipeline review -- rank targets by NIL fit | `/transfer-portal` | Coach + Recruiting Coordinator |
| 8:30 AM | Roster Builder scenario modeling -- test roster compositions | `/dashboard/roster-builder` | Coach solo |
| 9:00 AM | Pipeline stage progression -- advance recruiting prospects | `/dashboard/pipelines` | Coach solo |
| 9:30 AM | Agent coordination for represented roster players | `/dashboard/messages` | Coach + Agent contacts |

### Weekly Team NIL Meeting Agenda

```
TEAM NIL WEEKLY (Monday or Tuesday, 15 minutes):

  1. Team valuation update (2 min)
     - Total team NIL value
     - Week-over-week change
     - Conference rank movement

  2. Individual standouts (3 min)
     - Top 3 valuation gainers
     - Any valuation concerns

  3. Recruiting pipeline (5 min)
     - New prospects added
     - Pipeline stage movement
     - Portal targets update

  4. Budget check (3 min)
     - Allocation vs. actual
     - Any adjustment needs

  5. Action items (2 min)
     - Assign follow-ups to staff
```

### Weekly Report Outputs

- Team roster valuation summary with player-level detail
- Recruiting pipeline status: new, advanced, stalled, committed
- Budget allocation accuracy check
- Conference rank context: position and delta

---

## Monthly Cadence

**Timing:** First Monday of each month

### Monthly Review

| Task | Description | Screen |
|---|---|---|
| Team Valuation Trend Analysis | 30-day team valuation chart; identify drivers (performance, portal, social) | `/coach` |
| Recruiting Funnel Review | Full pipeline audit: top-of-funnel, conversion rate, time-to-commit | `/dashboard/pipelines` |
| Agent Coordination | Monthly sync with agents representing team players; deal awareness | `/dashboard/messages` |
| Budget Reconciliation | Per-player allocation review; adjust for roster changes | `/coach/settings` |
| Competitor Analysis | Compare team NIL position to conference rivals via directory | `/directory` |

### Monthly Meeting Cadence

| Meeting | Audience | Deliverable |
|---|---|---|
| Coach Monthly Review | AD + Head Coach | Team NIL health report |
| Staff Sync | Head Coach + Assistants | Recruiting strategy alignment |
| Player Group Meeting | Entire roster | NIL awareness and compliance reminder |
| Agent Roundtable | Agents of represented players | Collaborative deal awareness |

### Monthly KPI Scorecard

| KPI | Target | Measurement |
|---|---|---|
| Team Total NIL Value | Growth MoM | `$XX.XM` from `/coach` |
| Roster Coverage % | 50%+ players with active NIL deals | `%` from roster analysis |
| Recruiting Pipeline Health | 10+ active prospects in pipeline | `#` from `/dashboard/pipelines` |
| Budget Allocation Accuracy | < 5% variance from planned | `%` from `/coach/settings` |
| Player Retention Rate | 90%+ (no unplanned portal entries) | `%` from roster tracking |

---

## Key Screens

| Screen | Route | Primary Use |
|---|---|---|
| Coach Dashboard | `/coach` | Team roster valuations, Team Cap Table, conference rank |
| Coach Settings | `/coach/settings` | Budget allocation (player-level), org user management |
| Pipelines | `/dashboard/pipelines` | Recruiting pipeline management |
| Roster Builder | `/dashboard/roster-builder` | Roster composition modeling and budget scenarios |
| Messages | `/dashboard/messages` | AD, agent, recruit, and player communication |
| Org Settings | `/dashboard/org-settings` | Budget and org user management (shared entry) |
| Transfer Portal | `/transfer-portal` | Transfer portal athlete workspace |
| Predictions | `/predictions` | Player valuation forecasting |
| Sports Directory | `/directory` | Conference/team/player drill-down analytics |
| Favorites | `/dashboard/favorites` | Track players, teams, and recruiting targets |

### Coach Dashboard Composition

The `/coach` shell renders the same Athletic Director dashboard template/layout composition used on `/athletic-director`, with coach workspace labeling:

- **Team Cap Table** (not Org Cap Table): `Actual Budget`, `EST Cap`, and `Roster` tabs
- **Team/Conf.** and **Team/Div.** share copy (not Org/Conf. and Org/Div.)
- Player-level allocation detail (not sport/team-level like AD)
- Conference rankings show teams within the conference

### Navigation Context

- Left nav includes: `Roster Builder`, `Favorites`, `Pipelines`, `Agent Directory`, `Affiliate Directory`
- Profile menu exposes `Coach Settings` (not Organization Settings)
- Top nav shows program context with `Huddles` and `Messages` controls
- Keyboard shortcuts: `L` light / `D` dark / `H` huddles / `M` messages / `1-9` sidebar pages

---

## KPIs

### Primary KPIs

| KPI | Definition | Target | Font |
|---|---|---|---|
| Team Total NIL Value | Aggregate estimated NIL value for entire team roster | Top 5 in conference | `JetBrains Mono` `$XX.XM` |
| Roster Coverage % | % of rostered players with at least one active NIL deal | 50%+ | `JetBrains Mono` `XX.X%` |
| Recruiting Pipeline Health | Count of active prospects in recruiting pipeline | 10+ | `JetBrains Mono` `##` |
| Budget Allocation Accuracy | Variance between planned and actual per-player allocation | < 5% variance | `JetBrains Mono` `XX.X%` |

### Secondary KPIs

| KPI | Definition | Target |
|---|---|---|
| Player Retention Rate | % of roster retained through season (no unplanned portal entries) | 90%+ |
| Conference NIL Rank | Team rank within conference by total NIL value | Top quartile |
| Recruiting Conversion Rate | % of pipeline prospects that commit | 15%+ |
| Average Player Valuation | Team total NIL value / roster size | Growth trend |
| Starter Concentration | % of team NIL value held by starters | Awareness metric |

---

## Escalation Paths

| Trigger | Severity | Escalation Target | SLA |
|---|---|---|---|
| Player enters transfer portal (unplanned) | CRITICAL | AD immediate notification + player meeting | 4 hours |
| Player compliance flag from AD | HIGH | Coach + player conversation + AD loop-back | 24 hours |
| Budget overage on player allocation | MEDIUM | AD review + budget adjustment | 48 hours |
| Recruiting target commits elsewhere | MEDIUM | Adjust pipeline; identify replacement targets | 1 week |
| Agent conflict with player deal terms | HIGH | Coach mediates + AD awareness | 24 hours |
| Team valuation drops > 10% in 1 week | HIGH | AD meeting + root cause analysis | 48 hours |
| Data sync issue affecting roster data | MEDIUM | NIL Optic support | 4 hours |

### Escalation Flow

```
LEVEL 1: Coach Self-Service
  - Review dashboard and roster data
  - Message player, agent, or AD directly
  - Adjust pipeline and budget allocations

LEVEL 2: Coach + AD
  - Escalate compliance or budget issues to AD
  - Coordinate on program-level NIL strategy
  - Joint recruiting strategy for high-value targets

LEVEL 3: Coach + External
  - Agent coordination for player deal issues
  - AD + Compliance for regulatory concerns
  - NIL Optic support for platform issues
```

---

## Basketball Focus

Basketball coaches have the most concentrated NIL management challenge: a 13-scholarship roster where individual player valuations can swing dramatically based on game performance, tournament exposure, and portal activity.

### Roster Construction Around March Madness

| Roster Slot | NIL Consideration | Strategy |
|---|---|---|
| Starting 5 | Highest individual valuations; most exposure-sensitive | Maximize exposure opportunities; protect brand value |
| 6th Man | Swing player; valuation upside if role expands | Position for increased minutes and visibility |
| Key Reserves (7--9) | Moderate NIL value; role-dependent | Maintain deal flow; social media consistency |
| Development (10--13) | Lower current value; high future upside | Invest in brand building for future seasons |
| Incoming Recruits | Projected value based on ranking and social reach | Use NIL projections in recruiting pitch |

### Transfer Portal Recruiting with NIL

```
NIL AS RECRUITING TOOL:

  For Portal Targets:
    1. Pull target's current NIL valuation from predictions
    2. Model projected valuation at YOUR program
       (factor in: conference exposure, media market, brand partnerships)
    3. Show the delta: "Your valuation could grow from $X to $Y here"
    4. Back it up: share program NIL infrastructure, agent access, brand network
    5. Use Roster Builder to model team impact of addition

  For High School Recruits:
    1. Show program's total NIL value and conference rank
    2. Demonstrate NIL support infrastructure (AD, agents, affiliates)
    3. Reference comparable player trajectories at your program
    4. Highlight March Madness exposure multiplier effect
```

### NIL-Aware Practice and Game Strategy

| Decision | NIL Data Input | Screen |
|---|---|---|
| Starting lineup decisions | Player valuation trend + deal pipeline activity | `/coach` roster section |
| Minutes allocation | Exposure ROI per player per minute | `/predictions` |
| Transfer portal recruiting | Target valuation + projected program fit | `/transfer-portal` + `/dashboard/roster-builder` |
| Scholarship allocation | NIL value vs. budget allocation balance | `/coach/settings` |
| Conference game scheduling | Rivalry game exposure value for roster | `/directory` |

### Basketball Recruiting Calendar

| Month | Portal Activity | Coach Action |
|---|---|---|
| March--April | Post-season portal entries surge | Identify and prioritize targets immediately |
| April--May | Peak portal activity; commitment window | Aggressive outreach; close top targets |
| May--June | Portal winds down; late entries | Fill remaining roster needs |
| August--September | Fall portal window opens | Monitor for mid-year transfer opportunities |
| October--November | Limited portal activity | Focus on current roster; early scouting |
| December--February | Minimal portal; focus on current season | Pipeline maintenance; future target identification |

---

## Settings and Budget Management

### Coach Settings (`/coach/settings`)

| Tab | Description |
|---|---|
| Budget + Allocation | Total budget input + per-player allocation values |
| Org Users | Manage organization-level users within coach scope |
| Program Users | Manage program-level Coach and GM role users |
| Athlete User | Manage athlete role assignments for rostered players |

### Budget Allocation Workflow

```
COACH BUDGET SETUP (First-Time):

  1. Set total team budget in Coach Settings
  2. Roster auto-populates from SportsRadar team data
  3. For each player: review estimated NIL valuation
  4. Set allocated $ per player based on:
     - Estimated valuation
     - Scholarship value
     - Role / minutes projection
     - Recruiting commitment terms
  5. Monitor Budget vs. Estimate delta monthly
```

### Invite Management

Coaches can manage invites with lifecycle tracking:

| Invite Scope | Role Options | Status Tracking |
|---|---|---|
| Org Users | AD, AAD, GM | Pending, Accepted, Expired, Revoked |
| Program Users | Coach, GM | Pending, Accepted, Expired, Revoked |
| Athlete Users | Athlete | Pending, Accepted, Expired, Revoked |

---

## Access and Permissions

| Capability | Allowed |
|---|---|
| View team roster valuations | Yes |
| Manage per-player budget allocation | Yes (player-level) |
| Add prospects to pipeline (Add to Pipeline action) | Yes |
| Initiate messages (within active program scope + listed agents) | Yes |
| Host huddles and meets | Yes |
| Access Roster Builder | Yes |
| Add SportsRadar-backed sport/team programs | No (AD-family only) |
| Create NIL payments | No (agent-scoped only) |
| Access athlete private dashboard | No (requires explicit athlete role) |
| View Organization Settings as AD scope | No (coach sees Coach Settings only) |

---

## Seasonal Calendar

| Month | Focus Area | Key Action |
|---|---|---|
| August | Preseason roster lock | Finalize budget allocation; baseline team valuation |
| September | Non-conference prep | Early season recruiting pipeline activation |
| October | Season opener | Monitor early game performance impact on valuations |
| November | MTE / early tournaments | Exposure tracking; valuation movement monitoring |
| December | Conference play begins | Conference rank tracking; rival comparison |
| January | Peak conference season | Heavy recruiting outreach; mid-season valuation review |
| February | Tournament positioning | Bracket projection awareness; roster stability focus |
| March | March Madness | Tournament exposure management; portal prep |
| April | Post-season / portal opens | Immediate portal response; roster reconstruction begins |
| May | Peak portal activity | Close priority portal targets; finalize commitments |
| June | Off-season development | Summer workouts; brand building support |
| July | Pre-season planning | Finalize next-season budget; set recruiting targets |

---

*NIL Optic -- Build rosters that win and earn.*
