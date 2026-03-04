# Operations Playbook: Agency Admin

> Last updated: 2026-03-04

---

## Role Overview

**Who:** Agency owners and administrators managing multi-agent operations, overseeing agency-wide deal flow, revenue performance, and agent productivity across all represented athlete portfolios.

**Organization category:** `agency`
**Role key:** `agency_admin`
**Shell route:** `/agency-admin`

Agency Admins are the operational executives of NIL agencies. They own the business-level view: total agency revenue, agent headcount and productivity, client distribution across agents, deal volume trends, and P&L performance. While individual agents manage client relationships and deals, Agency Admins ensure the agency as a whole operates profitably and scales strategically.

### Core Responsibilities

- Oversee agency-wide deal activity and revenue performance
- Monitor and optimize agent productivity and client distribution
- Manage agency organization settings, budgets, and compliance
- Conduct weekly agent 1:1s and pipeline audits
- Drive agency growth through strategic client acquisition
- Manage athlete roster linking and payment operations
- Coordinate with Athletic Directors on multi-athlete deals

---

## Daily Operations

**Time allocation:** 30--45 minutes

### Morning Command Post (`8:00 AM`)

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P0 | Agency-wide deal activity scan -- new deals, stage changes, closings | `/agency-admin` | 10 min |
| P0 | Agent performance check -- deals per agent, pipeline movement | `/agency-admin` | 10 min |
| P1 | Review critical messages -- AD escalations, brand partner issues | `/dashboard/messages` | 10 min |
| P2 | Payment operations -- pending payments, schedule updates | `/agency-admin` | 5 min |
| P2 | Check athlete link requests and opponent snapshots | `/agency-admin` | 5 min |

### Daily KPI Glance

| Metric | Source | Format |
|---|---|---|
| Agency Total Deal Volume | `/agency-admin` | `#` |
| Deals Closed (Today/Week) | `/agency-admin` | `#` |
| Agency Revenue MTD | `/agency-admin` | `$XXX.XK` |
| Agent Count (Active) | `/agency-admin` | `#` |
| Total Managed Athletes | `/agency-admin` | `#` |
| Unread Messages | `/dashboard/messages` badge | `#` |

---

## Weekly Cadence

**Day:** Monday (revenue review) + Thursday (agent 1:1s)

### Monday: Revenue and Pipeline Review

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Agency revenue review -- week-over-week, MTD, target tracking | `/agency-admin` | Agency Admin solo |
| 9:30 AM | Pipeline audit -- deals by stage, stagnant deals, conversion rates | `/dashboard/pipelines` | Agency Admin solo |
| 10:00 AM | Client distribution analysis -- agents with too many/few clients | `/agency-admin` | Agency Admin solo |
| 10:30 AM | Compliance review -- any flagged deals or AD escalations | `/dashboard/messages` | Agency Admin + compliance liaison |

### Thursday: Agent 1:1 Block

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Agent 1:1 (Agent A) -- pipeline review, deals, blockers | `/dashboard/pipelines` | Agency Admin + Agent |
| 9:30 AM | Agent 1:1 (Agent B) -- pipeline review, deals, blockers | `/dashboard/pipelines` | Agency Admin + Agent |
| 10:00 AM | Agent 1:1 (Agent C) -- pipeline review, deals, blockers | `/dashboard/pipelines` | Agency Admin + Agent |
| 10:30 AM | Staff sync -- aggregate learnings, resource allocation | `/agency-admin` | Agency Admin + all agents |

### Agent 1:1 Agenda Template

```
AGENT 1:1 WEEKLY (30 minutes):

  1. Pipeline Health (10 min)
     - Deals in each stage
     - Stagnant deals (>7 days no movement)
     - Expected closings this week

  2. Client Portfolio (10 min)
     - New clients added
     - Client valuation trends
     - At-risk clients (valuation decline, contract expiry)

  3. Revenue and Targets (5 min)
     - MTD revenue vs. target
     - Commission tracking
     - Forecast for remainder of month

  4. Blockers and Support (5 min)
     - Brand partner issues
     - AD coordination needs
     - Platform or data issues
```

### Weekly Report Outputs

- Agency revenue summary: closed, pipeline, forecast
- Agent productivity scorecard: deals per agent, conversion rate
- Client distribution balance: clients per agent, value per agent
- Pipeline health report: stage velocity, stagnation flags

---

## Monthly Cadence

**Timing:** First Monday of each month

### Monthly Business Review

| Task | Description | Screen |
|---|---|---|
| P&L Review | Full agency P&L -- revenue, commissions, operating costs | `/agency-admin` |
| Client Distribution Analysis | Agent-to-client ratio; identify rebalancing needs | `/agency-admin` |
| Growth Planning | Identify expansion opportunities -- new sports, conferences, athlete tiers | `/agency-admin` |
| Agent Performance Ranking | Stack-rank agents by revenue, deal count, client growth | `/agency-admin` |
| Payment Reconciliation | Verify all athlete payments processed and on schedule | API: `/api/agency-admin/payments` |

### Monthly Meeting Cadence

| Meeting | Audience | Deliverable |
|---|---|---|
| Agency All-Hands | All agents + admin | Monthly performance summary + strategy direction |
| Executive Review | Agency ownership | P&L, growth metrics, strategic decisions |
| AD Partnership Review | Key Athletic Directors | Multi-athlete deal coordination, compliance status |
| Brand Partner Roundtable | Top brand partners | Partnership performance, renewal pipeline |

### Monthly KPI Scorecard

| KPI | Target | Measurement |
|---|---|---|
| Agency Revenue | Monthly target | `$XXX.XK` |
| Agent Productivity (avg. deals/agent) | 5+ deals/agent/month | Average from agent data |
| Client Distribution Balance | Max 2:1 ratio between highest/lowest loaded agents | Ratio |
| Deal Volume | Growth MoM | `#` total deals across agency |
| Client Retention | 95%+ | % clients retained month-over-month |

---

## Key Screens

| Screen | Route | Primary Use |
|---|---|---|
| Agency Admin Dashboard | `/agency-admin` | Agency-wide overview, agent performance, deal activity |
| Org Settings | `/dashboard/org-settings` | Agency organization settings, user management, budget |
| Pipelines | `/dashboard/pipelines` | Deal pipeline management across all agents |
| Messages | `/dashboard/messages` | Communication with agents, ADs, brand partners |
| Predictions | `/predictions` | Athlete valuation forecasting for strategic planning |
| Agent Directory | `/agent-directory` | Agency public presence and agent listings |

### Navigation Context

- Left nav includes: `Roster Builder`, `Favorites`, `Pipelines`, `Agent Directory`, `Affiliate Directory`
- Office/agent/compliance nav links in agency admin shell
- Top nav shows agency organization context with `Huddles` and `Messages` controls

---

## KPIs

### Primary KPIs

| KPI | Definition | Target | Font |
|---|---|---|---|
| Agency Revenue | Total commission revenue across all agents | Growth MoM | `JetBrains Mono` `$XXX.XK` |
| Agent Productivity | Average deals closed per agent per month | 5+ | `JetBrains Mono` `#.#` |
| Client Distribution | Standard deviation of client count per agent | Low variance | `JetBrains Mono` `#.#` |
| Deal Volume | Total deals across agency (all stages) | Growth trend | `JetBrains Mono` `###` |

### Secondary KPIs

| KPI | Definition | Target |
|---|---|---|
| Portfolio Total Value | Sum of all represented athlete NIL values | Growth QoQ |
| Agency Deal Conversion Rate | Prospect to close across all agents | 25%+ |
| Average Deal Size | Total deal value / number of deals | Growth trend |
| Agent Headcount | Total active agents in agency | Aligned with growth plan |
| Client Acquisition Rate | New clients per month across agency | 3--5 per month |

---

## Escalation Paths

| Trigger | Severity | Escalation Target | SLA |
|---|---|---|---|
| Agent revenue below 50% of monthly target at mid-month | HIGH | Agency Admin + Agent 1:1 | 24 hours |
| Client dispute escalation from agent | HIGH | Agency Admin direct involvement | 24 hours |
| Compliance violation on agency deal | CRITICAL | Legal counsel + AD notification | 4 hours |
| Agent departure / poaching | CRITICAL | Immediate client redistribution plan | 4 hours |
| Brand partner contract dispute | HIGH | Agency Admin + legal | 24 hours |
| Payment processing failure | MEDIUM | Operations + NIL Optic support | 48 hours |

---

## Basketball Focus

Basketball represents the highest-revenue vertical for most NIL agencies. Agency Admins must ensure basketball-focused agents have the resources and support to capitalize on the sport's unique NIL dynamics.

### Basketball Revenue Concentration

| Metric | Typical Range | Action |
|---|---|---|
| Basketball % of agency revenue | 40--60% | Ensure adequate agent coverage |
| Basketball client count % | 25--40% | Monitor for over/under-indexing |
| Basketball average deal size vs. other sports | 2--3x | Factor into revenue forecasts |
| March Madness revenue surge | +30--50% of monthly average | Pre-position resources for March |

### Agency Staffing for Basketball Season

```
BASKETBALL SEASON STAFFING MODEL:

  Pre-Season (Aug-Oct):
    - Standard coverage (1 agent : 8-10 clients)
    - Focus: preseason brand partnerships

  Regular Season (Nov-Feb):
    - Elevated coverage (1 agent : 6-8 clients)
    - Focus: game performance deal activation

  March Madness (Mar):
    - Surge coverage (1 agent : 4-6 clients)
    - All hands on deck for tournament clients
    - Focus: real-time exposure capture, inbound brand response

  Post-Season + Portal (Apr-Jun):
    - Elevated coverage (1 agent : 6-8 clients)
    - Focus: portal client acquisition, deal close-out
```

---

## Payment and Athlete Operations

### Payment Management

Agency Admins have access to athlete payment operations through dedicated API endpoints:

| Operation | Endpoint | Description |
|---|---|---|
| Manage Payments | `/api/agency-admin/payments` | Create, update, and track athlete payment records |
| Payment Schedule | `/api/agency-admin/payments/schedule` | Manage recurring payment schedules |
| Link Athletes | `/api/agency-admin/athletes/link` | Link athletes to agency roster |
| Opponent Snapshot | `/api/agency-admin/opponent-snapshot` | Build comparison data for negotiations |

### Athlete Linking Workflow

```
ATHLETE LINKING PROCESS:

  1. Agent identifies new represented athlete
  2. Agent adds player via /agent/settings represented player search
  3. Agency Admin verifies and links athlete to agency roster
  4. Allocation table auto-populates with player data
  5. Budget summary tiles update with new athlete's estimated NIL
  6. Payment schedule can be configured for linked athlete
```

---

## Access and Permissions

| Capability | Allowed |
|---|---|
| View agency-wide deal activity | Yes |
| Manage agency organization settings | Yes |
| Create NIL payments | Yes |
| Link athletes to agency roster | Yes |
| Build opponent comparison snapshots | Yes |
| Manage payment schedules | Yes |
| Initiate messages to any authenticated user | Yes |
| Host huddles and meets | Yes |
| Invite agency-level users (Agency Admin, Agent) | Yes |
| Access athlete private dashboard | No (requires explicit athlete role) |

---

## Seasonal Calendar

| Month | Focus Area | Key Action |
|---|---|---|
| August | Pre-season deal pipeline build | Assign agents to client rosters; set revenue targets |
| September | Brand activation season begins | Monitor deal execution across agents |
| October | QBR preparation | Compile agency performance for ownership review |
| November | Tournament and early season deals | Allocate surge resources for basketball MTE clients |
| December | Year-end close | Revenue reconciliation; holiday brand campaigns |
| January | QBR #2; conference play revenue | Mid-year agent performance reviews |
| February | Pre-tournament positioning | Prepare March Madness operational plan |
| March | March Madness surge | Maximum agency operational intensity |
| April | Post-tournament close + portal | Deal close-out; portal client acquisition strategy |
| May | Portal peak | Support agents with portal target outreach |
| June | Off-season planning | Growth strategy; agent hiring; P&L review |
| July | QBR #4; fiscal year prep | Annual agency strategy; next-year targets |

---

*NIL Optic -- Scale your agency with intelligence.*
