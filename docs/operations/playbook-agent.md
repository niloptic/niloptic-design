# Operations Playbook: NIL Agent

> Last updated: 2026-03-04

---

## Role Overview

**Who:** Sports agents managing athlete NIL deals, brand partnerships, and client portfolio growth. Agents are the deal-makers of the NIL ecosystem -- they identify market opportunities, negotiate brand contracts, and maximize the earning potential of their represented athletes.

**Organization category:** `agency`
**Role key:** `agent`
**Shell route:** `/agent`

Agents operate across multiple athletes and programs simultaneously. Their daily workflow centers on pipeline velocity: moving deals through stages, responding to brand inquiries, and proactively positioning clients for high-value opportunities. NIL Optic gives agents real-time portfolio valuation, deal pipeline management, and market intelligence to outperform competing agencies.

### Core Responsibilities

- Manage and grow client athlete portfolios
- Negotiate and close NIL brand partnership deals
- Monitor market opportunities across the NIL landscape
- Maintain pipeline discipline with clear stage progression
- Coordinate with Athletic Directors on deal compliance
- Track client valuations and social reach metrics
- Prospect new athlete clients via transfer portal and recruitment data

---

## Daily Operations

**Time allocation:** 60--90 minutes

### Morning Pipeline Sweep (`8:00 AM`)

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P0 | Review client valuation changes -- flag any drops > 5% | `/agent` KPI strip | 10 min |
| P0 | Check pipeline deals -- new inbound, stage changes, deadlines | `/dashboard/pipelines` | 15 min |
| P1 | Respond to brand inquiries and partnership proposals | `/dashboard/messages` | 15 min |
| P1 | Monitor market opportunities -- trending athletes, viral moments | `/predictions` | 10 min |
| P2 | Review transfer portal for prospecting opportunities | `/transfer-portal` | 10 min |

### Afternoon Deal Work (`2:00 PM`)

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P0 | Advance active deals through pipeline stages | `/dashboard/pipelines` | 15 min |
| P1 | Update client notes and deal documentation | `/dashboard/pipelines` | 10 min |
| P2 | Outreach to prospective new clients | `/dashboard/messages` | 10 min |

### Daily KPI Glance

| Metric | Source | Format |
|---|---|---|
| Portfolio Total Value | `/agent` KPI strip -- Total Est. Athlete NIL | `$XX.XM` |
| Actual Budget | `/agent` KPI strip -- Actual | `$XX.XK` |
| Budget vs. Estimate | `/agent` KPI strip -- Budget Vs Estimate | `+/- $XX.XK` |
| Active Pipeline Deals | `/dashboard/pipelines` count | `#` |
| Unread Messages | `/dashboard/messages` badge | `#` |
| Managed Athletes | `/agent` KPI strip -- Athletes | `#` |

---

## Weekly Cadence

**Day:** Tuesday (pipeline review) + Friday (portfolio strategy)

### Tuesday: Pipeline Review

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Full pipeline audit -- every deal reviewed for stage accuracy | `/dashboard/pipelines` | Agent solo |
| 9:45 AM | Client portfolio valuation update -- capture week-over-week deltas | `/agent` | Agent solo |
| 10:15 AM | New prospect outreach -- identify 3--5 potential new clients | `/dashboard/roster-builder` | Agent solo |
| 10:45 AM | Deal stage progression -- move deals that hit milestones | `/dashboard/pipelines` | Agent solo |

### Friday: Portfolio Strategy

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 9:00 AM | Weekly revenue summary -- deals closed, revenue recognized | `/agent` | Agent + Agency Admin |
| 9:30 AM | Client communication -- send weekly update to top 5 clients | `/dashboard/messages` | Agent solo |
| 10:00 AM | Market trend review -- conference/division valuation movements | `/predictions` | Agent solo |
| 10:30 AM | Competitive intelligence -- benchmark portfolio vs. rival agents | `/agent` | Agent solo |

### Weekly Pipeline Health Check

```
DEAL STAGE AUDIT:
  For each deal in pipeline:
    1. Is the deal in the correct stage? (Prospect → Outreach → Negotiation → Close)
    2. Has the deal been stagnant > 7 days? → Flag for action
    3. Is deal documentation complete? → Notes, terms, contacts
    4. Is AD/compliance awareness confirmed? → Check message thread
    5. Is the brand responsive? → Escalate if no response > 5 business days
```

### Weekly Report Outputs

- Pipeline velocity report: deals advanced, stagnant, closed, lost
- Portfolio valuation summary: total value, top movers, risk flags
- Prospect pipeline: new athletes identified, outreach status
- Revenue tracker: closed deal revenue vs. weekly/monthly target

---

## Monthly Cadence

**Timing:** Last week of each month

### Revenue Tracking

| Task | Description | Screen |
|---|---|---|
| Revenue Reconciliation | Match closed deals to revenue recognition; calculate commission | `/agent` |
| Client Performance Reviews | Rank clients by deal count, total value, and growth trajectory | `/agent` |
| Market Trend Analysis | Identify rising sports, conferences, or athlete archetypes | `/predictions` |
| Brand Relationship Mapping | Catalog active brand partners; identify cross-sell opportunities | `/dashboard/pipelines` |
| Agent Settings Audit | Verify represented player list accuracy; update allocation table | `/agent/settings` |

### Monthly Meeting Cadence

| Meeting | Audience | Deliverable |
|---|---|---|
| Agency Revenue Review | Agency Admin + all agents | Monthly P&L contribution report |
| Top Client Check-in | Top 5 clients by value | Personalized valuation trend + deal status |
| AD Coordination Call | Athletic Directors of represented programs | Compliance sync + deal calendar |
| Brand Partner Review | Active brand contacts | Partnership performance + renewal pipeline |

### Monthly KPI Scorecard

| KPI | Target | Measurement |
|---|---|---|
| Deals Closed | 5+ per month | Count from `/dashboard/pipelines` |
| Revenue Recognized | Agency-defined target | `$XX.XK` from deal close data |
| Pipeline Conversion Rate | 25%+ (prospect to close) | `%` from pipeline stage analysis |
| New Clients Added | 1--2 per month | Count from `/agent/settings` |
| Client Retention Rate | 95%+ | % of clients maintained month-over-month |

---

## Key Screens

| Screen | Route | Primary Use |
|---|---|---|
| Agent Dashboard | `/agent` | Portfolio overview, KPI strip, represented athletes, budget impact cards |
| Agent Settings | `/agent/settings` | Profile management, represented player search/add, allocation table, avatar |
| Pipelines | `/dashboard/pipelines` | Deal pipeline management with Kanban stages |
| Roster Builder | `/dashboard/roster-builder` | Prospect identification and roster modeling |
| Messages | `/dashboard/messages` | Client, AD, and brand communication |
| Predictions | `/predictions` | Athlete valuation forecasting |
| Transfer Portal | `/transfer-portal` | Transfer portal athlete prospecting |
| Agent Directory | `/agent-directory` | Public agent profile visibility |
| NIL Report | `/nil-report` | Market intelligence and trend data |

### Navigation Context

- Left nav includes: `Roster Builder`, `Favorites`, `Pipelines`, `Agent Directory`, `Affiliate Directory`
- Profile menu exposes `Agent Settings` for profile and represented player management
- Top nav shows agency organization context with `Huddles` and `Messages` controls
- Agent KPI strip: `Team Members`, `Programs`, `Pipelines` (active boards), `Athletes` (managed)

---

## KPIs

### Primary KPIs

| KPI | Definition | Target | Font |
|---|---|---|---|
| Portfolio Total Value | Sum of estimated NIL values for all represented athletes | Growth MoM | `JetBrains Mono` `$XX.XM` |
| Deals Closed / Month | Count of deals reaching CLOSED stage in calendar month | 5+ | `JetBrains Mono` `##` |
| Pipeline Conversion Rate | % of prospects that convert to closed deals | 25%+ | `JetBrains Mono` `XX.X%` |
| Revenue YTD | Total commission revenue recognized year-to-date | Agency target | `JetBrains Mono` `$XXX.XK` |
| Client Count | Total represented athletes under active agreement | Growth trend | `JetBrains Mono` `##` |

### Secondary KPIs

| KPI | Definition | Target |
|---|---|---|
| Average Deal Size | Total deal value / number of closed deals | Growth trend |
| Pipeline Velocity | Average days from prospect to close | Decreasing trend |
| Brand Diversity Index | Unique brands in portfolio / total deals | 50%+ unique brands |
| Client Satisfaction | % of clients with active engagement in last 30 days | 80%+ |
| Social Reach Portfolio | Aggregate social followers of represented athletes | Growth trend |

---

## Escalation Paths

| Trigger | Severity | Escalation Target | SLA |
|---|---|---|---|
| Client valuation drops > 20% in 7 days | HIGH | Agent immediate review + client communication | 24 hours |
| Deal stagnant > 14 days in negotiation stage | MEDIUM | Agency Admin review + brand re-engagement | 48 hours |
| Compliance flag on active deal | CRITICAL | AD notification + legal review | 4 hours |
| Brand partnership dispute | HIGH | Agency Admin + legal counsel | 24 hours |
| Client departure (agent switch) | CRITICAL | Agency Admin immediate + retention strategy | 4 hours |
| Platform data sync issue | MEDIUM | NIL Optic support | 4 hours |

### Escalation Flow

```
LEVEL 1: Agent Self-Service
  - Review pipeline and deal status
  - Message brand or AD directly
  - Update deal notes and stage

LEVEL 2: Agent + Agency Admin
  - Escalate stagnant or at-risk deals
  - Request agency-level brand relationship leverage
  - Coordinate multi-agent deal if applicable

LEVEL 3: Agent + External
  - Engage legal for contract disputes
  - Engage AD for compliance issues
  - Contact NIL Optic support for platform issues
```

---

## Basketball Focus

Basketball drives the highest-value NIL deals in college athletics. Agents with basketball clients operate in the most competitive and time-sensitive segment of the market.

### Transfer Portal Opportunities

The transfer portal is the primary client acquisition channel for NIL agents. Basketball portal activity creates immediate opportunities:

| Portal Event | Agent Action | Timeline |
|---|---|---|
| Top-50 player enters portal | Immediate outreach; valuation analysis | Within 24 hours |
| Player commits to new program | Update representation status; re-value | Within 48 hours |
| Player withdraws from portal | Confirm representation continuity | Within 24 hours |
| Rival agent signs portal target | Competitive analysis; adjust prospect list | Within 1 week |

### March Madness Exposure Windows

```
TOURNAMENT VALUATION IMPACT MODEL:

  Round of 64:  +5-10% valuation lift for standout performers
  Round of 32:  +10-20% cumulative lift
  Sweet 16:     +20-35% cumulative lift
  Elite 8:      +35-50% cumulative lift
  Final Four:   +50-100% cumulative lift for breakout stars
  Championship: +100-200% for tournament MVP / standout

AGENT ACTIONS BY ROUND:
  Pre-Tournament: Lock all existing deal terms; prepare brand pitch decks
  Round 1-2:      Activate brand outreach for standout performers
  Sweet 16:       Begin inbound brand response protocol (volume surge expected)
  Final Four:     Negotiate premium terms; leverage maximum exposure window
  Post-Tournament: Close deals within 14-day exposure decay window
```

### Basketball Client Prioritization

| Client Tier | Criteria | Service Level |
|---|---|---|
| Tier 1 | Top 25 national rank, $500K+ valuation | Daily touchpoint, proactive deal sourcing |
| Tier 2 | Conference top 10, $100K--$500K valuation | 2x weekly check-in, reactive deal management |
| Tier 3 | Rostered starter, $50K--$100K valuation | Weekly check-in, pipeline inclusion |
| Tier 4 | Bench / role player, < $50K valuation | Monthly check-in, group communication |

---

## Agent Settings Management

### Represented Player Configuration

The `/agent/settings` screen is the agent's operational control center for client management:

| Setting | Description | Update Frequency |
|---|---|---|
| Profile Fields | First name, last name, agency, public email, phone, listed toggle | As needed |
| Avatar | Upload, crop/edit, save, delete (normalized to 500x500) | As needed |
| Represented Players | Search/add via pipeline-style modal; remove inactive clients | Weekly |
| Allocation Table | Auto-filled `#`, `Pos`, `Est. Athlete Valuation`; editable `Allocated $` | Weekly |
| Budget Summary | Total Budget (Actual), Total Est. Athlete NIL, Budget Vs Estimate (Remaining) | Auto-calculated |

### Agent Directory Visibility

- Agents with `listed: true` appear in the public `/agent-directory`
- Directory cards show: name, agency, public email, phone, represented athletes
- Represented athlete display is privacy-scoped: name + latest estimated NIL only
- No private agent profile detail page is linked from directory cards
- In-app `Message` action on directory cards routes to compose flow

---

## Access and Permissions

| Capability | Allowed |
|---|---|
| View represented athlete valuations | Yes |
| Create NIL payments | Yes |
| Manage represented player list | Yes |
| Manage pipeline deals | Yes |
| Initiate messages to any authenticated user | Yes |
| Create known-player relationships | Yes (agent-authored, no player confirmation required) |
| Access athlete private dashboard | No (requires explicit athlete role) |
| Manage organization budget | No (Agency Admin scoped) |
| Invite org-level users | No (Agency Admin scoped) |

---

## Seasonal Calendar

| Month | Focus Area | Key Action |
|---|---|---|
| August | Preseason deal pipeline | Lock preseason brand partnerships; finalize client roster |
| September | Early season brand activation | Activate sponsorship deliverables; content schedules |
| October | Mid-fall deal review | Pipeline audit; QBR prep with agency |
| November | Tournament season positioning | MTE and early tournament exposure tracking |
| December | Holiday brand campaigns | Holiday campaign execution; reduced cadence |
| January | Conference play | Conference matchup exposure opportunities |
| February | Tournament projection | Bracket modeling; pre-tournament brand pitches |
| March | March Madness peak | Maximum deal velocity; real-time exposure capture |
| April | Post-tournament close | Close tournament-driven deals; portal prep |
| May | Transfer portal peak | Aggressive client acquisition via portal |
| June | Off-season brand building | Long-term partnership development |
| July | Summer showcase events | AAU/showcase circuit exposure deals |

---

*NIL Optic -- Deal intelligence for NIL agents who close.*
