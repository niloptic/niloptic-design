# Extended Role Dashboard Templates

Last updated: 2026-03-04

---

## Overview

This document defines the seven missing role-specific dashboard templates that extend the core templates library (`templates.md`). Each template follows the shared Dashboard Shell composition and uses NIL Optic design tokens for surfaces, typography, spacing, and motion.

All templates inherit:
- Dark mode default (`--ui-surface-1`, `--ui-surface-2`)
- Inter for UI text, JetBrains Mono for data/numeric values
- Brand accent `#DC2626` for active states and CTAs
- 12-column responsive grid (`--layout-columns`)
- Shared top navigation with role-aware context title
- Ghost/skeleton loading states for data-heavy sections

---

## Coach Dashboard Template

Primary user: Head coaches, assistant coaches
Route: `/coach`
Status: `planned`

### Layout Composition

Reuses the Athletic Director dashboard layout composition with coach-specific labeling:
- "Team Cap Table" replaces "Org Cap Table"
- "Team/Conf." and "Team/Div." copy replaces "Org/Conf." and "Org/Div."
- Player-level allocation replaces sport/team-level allocation
- Conference rankings scoped to coach's conference only

### Left Navigation

```
NAV

  OVERVIEW
  [ ] Dashboard
  [ ] Roster Builder

  TEAM
  [ ] Team Roster
  [ ] Recruiting Pipeline
  [ ] Valuations
  [ ] Predictions

  TOOLS
  [ ] Favorites
  [ ] Pipelines
  [ ] Tournaments

  DIRECTORIES
  [ ] Agent Directory
  [ ] Affiliate Directory

  COMMUNICATE
  [ ] Messages
  [ ] Huddles

  [Coach Settings]
```

### Role Label Conventions

| AD Label | Coach Label |
| --- | --- |
| Org Cap Table | Team Cap Table |
| Org/Conf. | Team/Conf. |
| Org/Div. | Team/Div. |
| Sport allocation | Player allocation |
| Organization Settings | Coach Settings |
| Department Overview | Team Overview |

### KPI Strip

```
┌────────────────┐ ┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│ TEAM NIL VALUE │ │ ACTIVE PLAYERS │ │ PIPELINE       │ │ BUDGET UTIL.   │
│                │ │                │ │                │ │                │
│ $8.6M         │ │ 13             │ │ 5 prospects    │ │ 72%            │
│ ▲ +6.1%       │ │ ▲ +2           │ │ $1.4M est.     │ │ $620K / $860K  │
│ font: mono    │ │ font: mono     │ │ font: mono     │ │ font: mono     │
└────────────────┘ └────────────────┘ └────────────────┘ └────────────────┘
```

Tokens: `--ui-surface-1` card bg, `--ui-border-default` border, `--font-mono-data` values, `--color-positive-verified` positive deltas, `--color-priority-delta` negative deltas.

### ASCII Wireframe

```
┌──────────────────────────────────────────────────────────────────┐
│  [Logo]   [Team Name]  Search ________   [Huddles] [Msgs] [Av] │
├────────────┬─────────────────────────────────────────────────────┤
│            │                                                     │
│  NAV       │  TEAM OVERVIEW                                      │
│            │                                                     │
│  ■ Dash    │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐│
│  □ Roster  │  │ Team NIL │ │ Active   │ │ Pipeline │ │ Budget ││
│  □ Recruit │  │ $8.6M    │ │ Players  │ │ 5 pros.  │ │ 72%    ││
│  □ Value   │  │ ▲ +6.1%  │ │ 13       │ │ $1.4M    │ │ 620/860││
│  □ Predict │  └──────────┘ └──────────┘ └──────────┘ └────────┘│
│            │                                                     │
│  ─ TOOLS   │  ┌─────────────────────────┐ ┌─────────────────────┐│
│  □ Favs    │  │ TEAM CAP TABLE           │ │ TOP ATHLETES        ││
│  □ Pipes   │  │                          │ │                     ││
│  □ Tourney │  │ [Actual Budget] [EST Cap]│ │ 1. K. Carter  $1.9M││
│            │  │ [Roster]                 │ │ 2. D. Walton  $1.4M││
│  ─ COMMS   │  │                          │ │ 3. J. Monroe  $1.1M││
│  □ Msgs    │  │ #  Player    Alloc  Est  │ │ 4. T. Hughes  $890K││
│  □ Huddle  │  │ 1  K.Carter  $180K $1.9M│ │ 5. R. James   $720K││
│            │  │ 2  D.Walton  $140K $1.4M│ │                     ││
│            │  │ 3  J.Monroe  $120K $1.1M│ │ [View Full Roster]  ││
│  [Profile] │  │ ...                      │ │                     ││
│            │  └─────────────────────────┘ └─────────────────────┘│
│            │                                                     │
│            │  ┌─────────────────────────┐ ┌─────────────────────┐│
│            │  │ RECRUITING PIPELINE      │ │ CONFERENCE RANK     ││
│            │  │                          │ │                     ││
│            │  │ Tracked:    8            │ │ Team/Conf. Rankings ││
│            │  │ Contacted:  4            │ │                     ││
│            │  │ Visited:    2            │ │ 1. Alabama   $24.1M ││
│            │  │ Committed:  1            │ │ 2. Georgia   $22.8M ││
│            │  │                          │ │ 3. LSU       $19.4M ││
│            │  │ [View Pipeline]          │ │ ■ 4. [You]   $8.6M ││
│            │  └─────────────────────────┘ └─────────────────────┘│
│            │                                                     │
│            │  ┌──────────────────────────────────────────────────┐│
│            │  │ COMPLIANCE TRACKER                                ││
│            │  │                                                   ││
│            │  │ ✓ 11 compliant  |  ⚠ 1 review needed  |  ✗ 1 exp││
│            │  │                                                   ││
│            │  │ [View All]                                        ││
│            │  └──────────────────────────────────────────────────┘│
└────────────┴─────────────────────────────────────────────────────┘
```

### Content Sections

| Section | Span | Data Source | Notes |
| --- | --- | --- | --- |
| KPI Strip | Full width, 4 cards | Team aggregate + budget | JetBrains Mono values |
| Team Cap Table | 7 col | Player-level allocations | Tabs: Actual Budget, EST Cap, Roster |
| Top Athletes | 5 col | Team roster by valuation | Ranked list with delta indicators |
| Recruiting Pipeline | 7 col | Coach pipeline stages | Funnel counts |
| Conference Rank | 5 col | Conference standings | Highlight coach's team row |
| Compliance Tracker | Full width | Team compliance status | Status bar with counts |

### Token References

- Card surfaces: `--ui-surface-1`
- Card borders: `--ui-border-default`
- KPI values: `--font-mono-data`
- Active tab: `--ad-tab-active-bg`, `--ad-tab-active-border`, `--ad-tab-active-text`
- Highlighted row (own team): `--ad-selection-bg`, `--ad-selection-border`
- Conference rank bars: `--ad-rank-track`, `--ad-rank-fill`

---

## Fan Dashboard Template

Primary user: Sports fans (public signup, no org)
Route: `/fan`
Status: `planned`

### Layout Composition

Simplified shell with no sidebar on desktop. Uses horizontal card-based navigation for core tools. No Messages or Huddles in top nav. Fan routes stay inside `/fan` segment. Upgrade CTAs positioned prominently.

### Left Navigation

Fan shell does NOT use a traditional left sidebar. Navigation is handled via:
- Simplified top nav (logo, search, notifications, avatar)
- Core Tools cards on the overview page
- Compact horizontal tab bar on mobile

Fan nav items (rendered as top-level cards or compact tabs):
```
  [Overview]  [Roster Builder]  [Favorites]  [Tournaments]
```

Routes:
- `/fan` (overview)
- `/fan/roster-builder`
- `/fan/favorites`
- `/fan/tournaments`

Top nav exclusions: No Huddles icon, no Messages icon, no keyboard shortcuts.

### KPI Strip

Fan dashboard does not use a traditional KPI strip. Instead, it uses a welcome banner with contextual stats.

### ASCII Wireframe

```
┌──────────────────────────────────────────────────────────────────┐
│  [Logo]   NIL OPTIC          Search ________     [Notif] [Av]   │
│                                                                  │
│  No [Huddles] or [Messages] controls                             │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │    Welcome to NIL Optic                                      ││
│  │    Your hub for college athlete NIL intelligence.            ││
│  │                                                              ││
│  │    145 Teams tracked  |  3,200+ Athletes  |  $2.1B+ NIL     ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  CORE TOOLS                                                      │
│                                                                  │
│  ┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐ │
│  │ [Icon]           │ │ [Icon]           │ │ [Icon]           │ │
│  │ ROSTER BUILDER   │ │ FAVORITES        │ │ TOURNAMENTS      │ │
│  │                  │ │                  │ │                  │ │
│  │ Build & compare  │ │ 0 players saved  │ │ March Madness    │ │
│  │ custom rosters   │ │ 0 teams saved    │ │ bracket intel    │ │
│  │                  │ │                  │ │                  │ │
│  │ [Open ->]        │ │ [Open ->]        │ │ [Open ->]        │ │
│  └──────────────────┘ └──────────────────┘ └──────────────────┘ │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │  TRENDING ATHLETES                         [ticker scroll->] ││
│  │                                                              ││
│  │  J. Smith ▲+8%  |  A. Jones ▲+5%  |  M. Davis ▼-2%  | ... ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  FAN-LITE VALUATION PREVIEW                                      │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │  Top 3 Athletes by Estimated NIL                             ││
│  │                                                              ││
│  │  [Team Logo] University of Georgia                           ││
│  │  1. J. Smith    FB  WR   $3.1M  ▲ +16.7%                   ││
│  │  2. A. Johnson  FB  QB   $2.8M  ▲ +9.3%                    ││
│  │  3. T. Williams BK  PG   $1.6M  ▲ +4.1%                   ││
│  │                                                              ││
│  │  + 281 more athletes  [Locked]                               ││
│  │                                                              ││
│  │  [Team Logo] Louisiana State University                      ││
│  │  1. D. Carter   FB  RB   $2.4M  ▲ +11.2%                  ││
│  │  2. K. Brown    FB  WR   $1.9M  ▲ +6.8%                   ││
│  │  3. R. Lewis    BK  SG   $1.2M  ▼ -1.4%                   ││
│  │                                                              ││
│  │  + 274 more athletes  [Locked]                               ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │    UPGRADE TO NIL OPTIC PRO                                  ││
│  │                                                              ││
│  │    Get full valuations, predictions, and organizational      ││
│  │    tools. Unlock unlimited athlete data.                     ││
│  │                                                              ││
│  │    [Contact Sales]              [Org Version ->]             ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │  COMING SOON                                                  ││
│  │  Sports Portfolio selection for personalized team feeds.      ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Content Sections

| Section | Span | Data Source | Notes |
| --- | --- | --- | --- |
| Welcome Banner | Full width | Static + aggregate stats | No KPI strip; conversational welcome |
| Core Tools | 3 equal cards | Fan activity status | Live counts (favorites, rosters) |
| Trending Athletes | Full width ticker | Valuation delta feed | Horizontal scroll, auto-advance |
| Fan-Lite Preview | Full width | Top 3 per team | Capped valuation window; locked indicator |
| Upgrade CTA | Full width | Static | Brand gradient bg, two actions |
| Coming Soon | Full width | Static | Roadmap callout |

### Token References

- Welcome banner: `--ui-surface-1`, `--ui-border-default`
- Core Tools cards: `--ui-surface-1`, `--ui-border-default`, hover: `--ui-accent-hover-border`
- Trending ticker: `--ui-surface-2` bg, `--font-mono-data` values
- Upgrade CTA: `--auth-accent-primary` (`#DC2626`) gradient, `--auth-accent-glow`
- Locked indicator: `--ui-text-muted`, lock icon in `--color-risk-uncertainty`
- Coming Soon chip: `--ui-surface-2`, `--ui-text-muted`

### Fan-Specific Constraints

- No sidebar navigation (card-based tool access only)
- No keyboard shortcuts (`L`, `D`, `H`, `M`, `0-9` all disabled)
- No `View` deep-links to `/athletes/[playerId]` or team detail routes from favorites
- No `Stats`/`Share` analytics tabs on favorites
- Roster Builder shows full player list but masks NIL values beyond top 3
- Tournaments show capped valuation lists (top 3 preview depth)

---

## Agency Admin Dashboard Template

Primary user: Agency owners, administrators
Route: `/agency-admin`
Status: `planned`

### Layout Composition

Multi-agent operations overview. Shows aggregate agency performance with drill-down to individual agent metrics. Pipeline and revenue tracking at agency level.

### Left Navigation

```
NAV

  OFFICE
  [ ] Dashboard
  [ ] Office Overview
  [ ] Agency Settings

  AGENTS
  [ ] Agent Roster
  [ ] Performance
  [ ] Client Distribution

  COMPLIANCE
  [ ] Deal Compliance
  [ ] Contract Review
  [ ] Audit Log

  TOOLS
  [ ] Favorites
  [ ] Pipelines
  [ ] Tournaments

  DIRECTORIES
  [ ] Agent Directory
  [ ] Affiliate Directory

  COMMUNICATE
  [ ] Messages
  [ ] Huddles

  [Profile]
```

### KPI Strip

```
┌────────────────┐ ┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│ AGENCY REVENUE │ │ TOTAL CLIENTS  │ │ ACTIVE DEALS   │ │ AGENT COUNT    │
│                │ │                │ │                │ │                │
│ $4.2M         │ │ 47             │ │ 23             │ │ 6              │
│ ▲ +18% YTD    │ │ ▲ +8           │ │ $6.8M pipeline │ │ 2 top perform. │
│ font: mono    │ │ font: mono     │ │ font: mono     │ │ font: mono     │
└────────────────┘ └────────────────┘ └────────────────┘ └────────────────┘
```

### ASCII Wireframe

```
┌──────────────────────────────────────────────────────────────────┐
│  [Logo]   [Agency Name]  Search ________  [Huddles] [Msgs] [Av] │
├────────────┬─────────────────────────────────────────────────────┤
│            │                                                     │
│  NAV       │  AGENCY OPERATIONS                                  │
│            │                                                     │
│  ■ Dash    │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐│
│  □ Office  │  │ Agency   │ │ Total    │ │ Active   │ │ Agent  ││
│  □ Config  │  │ Revenue  │ │ Clients  │ │ Deals    │ │ Count  ││
│            │  │ $4.2M    │ │ 47       │ │ 23       │ │ 6      ││
│  ─ AGENTS  │  │ ▲ +18%   │ │ ▲ +8     │ │ $6.8M    │ │        ││
│  □ Roster  │  └──────────┘ └──────────┘ └──────────┘ └────────┘│
│  □ Perform │                                                     │
│  □ Distrib │  ┌──────────────────────────────────────────────────┐│
│            │  │ AGENT PERFORMANCE TABLE                           ││
│  ─ COMPLY  │  │                                                   ││
│  □ Deals   │  │ Agent         Clients  Deals   Revenue   Trend   ││
│  □ Contrac │  │ ─────────────────────────────────────────────── ││
│  □ Audit   │  │ M. Rodriguez    12       8     $1.4M     ▲ +22% ││
│            │  │ S. Chen          9       6     $980K     ▲ +15% ││
│  ─ TOOLS   │  │ J. Williams      8       4     $720K     ▲ +8%  ││
│  □ Favs    │  │ A. Thompson      7       3     $540K     ▼ -3%  ││
│  □ Pipes   │  │ D. Martinez      6       1     $340K     ▲ +4%  ││
│  □ Tourney │  │ K. Davis         5       1     $220K     ─  0%  ││
│            │  │                                                   ││
│  ─ COMMS   │  │ [View All Agents]                                 ││
│  □ Msgs    │  └──────────────────────────────────────────────────┘│
│  □ Huddle  │                                                     │
│            │  ┌─────────────────────────┐ ┌─────────────────────┐│
│  [Profile] │  │ CLIENT DISTRIBUTION     │ │ REVENUE TREND       ││
│            │  │                          │ │                     ││
│            │  │ [Donut Chart]            │ │ [Line Chart - 12mo] ││
│            │  │                          │ │                     ││
│            │  │ Football:  58%           │ │ Jan  $280K          ││
│            │  │ Basketball: 24%          │ │ Feb  $340K          ││
│            │  │ Baseball:  12%           │ │ Mar  $410K          ││
│            │  │ Other:      6%           │ │ ...                 ││
│            │  │                          │ │                     ││
│            │  │ SEC: 42%  B12: 28%      │ │ [Full Report]       ││
│            │  │ B10: 18%  ACC: 12%      │ │                     ││
│            │  └─────────────────────────┘ └─────────────────────┘│
│            │                                                     │
│            │  ┌──────────────────────────────────────────────────┐│
│            │  │ AGENCY PIPELINE SUMMARY                           ││
│            │  │                                                   ││
│            │  │ Prospect: 14  |  Outreach: 9  |  Negotiate: 6    ││
│            │  │ Signed: 23    |  Total Value: $6.8M               ││
│            │  │                                                   ││
│            │  │ [View Pipeline]                                   ││
│            │  └──────────────────────────────────────────────────┘│
└────────────┴─────────────────────────────────────────────────────┘
```

### Content Sections

| Section | Span | Data Source | Notes |
| --- | --- | --- | --- |
| KPI Strip | Full width, 4 cards | Agency aggregate metrics | JetBrains Mono values |
| Agent Performance | Full width table | Agent roster + deal data | Sortable columns |
| Client Distribution | 6 col | Client sport/conf breakdown | Donut chart + conf breakdown |
| Revenue Trend | 6 col | Monthly revenue series | 12-month line chart |
| Pipeline Summary | Full width | Agency-wide deal stages | Stage counts + total value |

### Token References

- Card surfaces: `--ui-surface-1`
- Table rows: `--ui-surface-2`, `--ad-row-bg`
- Chart donut: `--ad-donut-track`, `--ad-donut-fill`
- Revenue line: `--ad-chart-line`, `--ad-chart-dot`
- Pipeline stage bars: `--ad-bar-track`, `--ad-bar-fill`

---

## Affiliate Admin Dashboard Template

Primary user: Affiliate firm administrators
Route: `/affiliate-admin`
Status: `planned`

### Layout Composition

Office and account management for affiliate firms (tax, wealth, legal). Service catalog overview with client satisfaction tracking. Maps to office/account/service nav emphasis.

### Left Navigation

```
NAV

  OFFICE
  [ ] Dashboard
  [ ] Office Overview
  [ ] Firm Settings

  ACCOUNTS
  [ ] Active Accounts
  [ ] Account Onboarding
  [ ] Client Health

  SERVICES
  [ ] Service Catalog
  [ ] Delivery Tracking
  [ ] Workshop Calendar

  TOOLS
  [ ] Favorites
  [ ] Pipelines
  [ ] Tournaments

  DIRECTORIES
  [ ] Agent Directory
  [ ] Affiliate Directory

  COMMUNICATE
  [ ] Messages
  [ ] Huddles

  [Profile]
```

### KPI Strip

```
┌────────────────┐ ┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│ ACTIVE ACCTS   │ │ SERVICES DELIV │ │ REVENUE        │ │ CLIENT SAT.    │
│                │ │                │ │                │ │                │
│ 34             │ │ 127            │ │ $1.8M          │ │ 4.7 / 5.0      │
│ ▲ +5 this mo.  │ │ ▲ +18 this mo. │ │ ▲ +12% YTD     │ │ ▲ +0.2         │
│ font: mono    │ │ font: mono     │ │ font: mono     │ │ font: mono     │
└────────────────┘ └────────────────┘ └────────────────┘ └────────────────┘
```

### ASCII Wireframe

```
┌──────────────────────────────────────────────────────────────────┐
│  [Logo]   [Firm Name]   Search ________   [Huddles] [Msgs] [Av] │
├────────────┬─────────────────────────────────────────────────────┤
│            │                                                     │
│  NAV       │  AFFILIATE FIRM OVERVIEW                            │
│            │                                                     │
│  ■ Dash    │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐│
│  □ Office  │  │ Active   │ │ Services │ │ Revenue  │ │ Client ││
│  □ Config  │  │ Accounts │ │ Delivered│ │          │ │ Sat.   ││
│            │  │ 34       │ │ 127      │ │ $1.8M    │ │ 4.7/5  ││
│  ─ ACCTS   │  │ ▲ +5     │ │ ▲ +18    │ │ ▲ +12%   │ │ ▲ +0.2 ││
│  □ Active  │  └──────────┘ └──────────┘ └──────────┘ └────────┘│
│  □ Onboard │                                                     │
│  □ Health  │  ┌──────────────────────────────────────────────────┐│
│            │  │ SERVICE CATALOG OVERVIEW                          ││
│  ─ SERVICE │  │                                                   ││
│  □ Catalog │  │ Category         Active   Completed   Pipeline   ││
│  □ Deliver │  │ ──────────────────────────────────────────────── ││
│  □ Workshp │  │ Wealth Mgmt        14        42          8      ││
│            │  │ Tax Planning        11        56          5      ││
│  ─ TOOLS   │  │ Legal Advisory       9        29          3      ││
│  □ Favs    │  │                                                   ││
│  □ Pipes   │  │ [Manage Catalog]                                  ││
│  □ Tourney │  └──────────────────────────────────────────────────┘│
│            │                                                     │
│  ─ COMMS   │  ┌──────────────────────────────────────────────────┐│
│  □ Msgs    │  │ ACCOUNT STATUS TABLE                              ││
│  □ Huddle  │  │                                                   ││
│            │  │ Account          Type      Status    Health  Rev  ││
│  [Profile] │  │ ──────────────────────────────────────────────── ││
│            │  │ UGA Athletics    Wealth    Active    ●●●○   $84K ││
│            │  │ LSU Athletics    Tax       Active    ●●●●   $62K ││
│            │  │ UCLA Athletics   Legal     Pending   ●●○○   --   ││
│            │  │ Vandy Athletics  Wealth    Active    ●●●○   $41K ││
│            │  │                                                   ││
│            │  │ [View All Accounts]                                ││
│            │  └──────────────────────────────────────────────────┘│
│            │                                                     │
│            │  ┌─────────────────────────┐ ┌─────────────────────┐│
│            │  │ OFFICE MANAGEMENT       │ │ UPCOMING WORKSHOPS  ││
│            │  │                          │ │                     ││
│            │  │ Affiliates:  4           │ │ Mar 12  NIL Tax 101││
│            │  │ Pending invites: 2       │ │ Mar 19  Wealth Wksp││
│            │  │ Active regions: 3        │ │ Apr 02  Legal Q&A  ││
│            │  │                          │ │                     ││
│            │  │ [Manage Office]          │ │ [View Calendar]     ││
│            │  └─────────────────────────┘ └─────────────────────┘│
└────────────┴─────────────────────────────────────────────────────┘
```

### Content Sections

| Section | Span | Data Source | Notes |
| --- | --- | --- | --- |
| KPI Strip | Full width, 4 cards | Firm aggregate metrics | JetBrains Mono values |
| Service Catalog | Full width table | Service categories | Active/completed/pipeline counts |
| Account Status | Full width table | Client accounts | Health dots, revenue per acct |
| Office Management | 6 col | Affiliate user admin | Invite/region management |
| Upcoming Workshops | 6 col | Workshop calendar | Date + title list |

### Token References

- Health indicators: `--color-positive-verified` (full), `--color-risk-uncertainty` (partial), `--ui-text-muted` (empty)
- Account rows: `--ui-surface-2`, `--ad-row-bg`
- Workshop dates: `--font-mono-data`

---

## Affiliate Dashboard Template

Primary user: Individual affiliate advisors
Route: `/affiliate`
Status: `planned`

### Layout Composition

Account and advisory focused view for individual affiliate advisors. Inbound-first messaging policy: affiliates cannot initiate outbound contact; they can only compose when a prior message thread already exists.

### Left Navigation

```
NAV

  ACCOUNT
  [ ] Dashboard
  [ ] My Accounts
  [ ] Account Health

  ADVISORY
  [ ] Services Active
  [ ] Workshops
  [ ] Resources

  ACTIVITY
  [ ] Activity Feed
  [ ] Delivery Log
  [ ] Upcoming Tasks

  TOOLS
  [ ] Favorites
  [ ] Pipelines
  [ ] Tournaments

  DIRECTORIES
  [ ] Agent Directory
  [ ] Affiliate Directory

  COMMUNICATE
  [ ] Messages (inbound-first)
  [ ] Huddles

  [Profile]
```

### KPI Strip

```
┌────────────────┐ ┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│ ACTIVE CLIENTS │ │ SERVICES COMP. │ │ REVENUE YTD    │ │ NEXT TASK      │
│                │ │                │ │                │ │                │
│ 8              │ │ 24             │ │ $186K          │ │ Mar 06         │
│ ▲ +2 this mo.  │ │ ▲ +6 this mo.  │ │ ▲ +22%         │ │ Tax Review     │
│ font: mono    │ │ font: mono     │ │ font: mono     │ │ font: mono     │
└────────────────┘ └────────────────┘ └────────────────┘ └────────────────┘
```

### ASCII Wireframe

```
┌──────────────────────────────────────────────────────────────────┐
│  [Logo]   [Firm Name]   Search ________   [Huddles] [Msgs] [Av] │
├────────────┬─────────────────────────────────────────────────────┤
│            │                                                     │
│  NAV       │  MY ADVISORY OVERVIEW                               │
│            │                                                     │
│  ■ Dash    │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐│
│  □ Accts   │  │ Active   │ │ Services │ │ Revenue  │ │ Next   ││
│  □ Health  │  │ Clients  │ │ Compl.   │ │ YTD      │ │ Task   ││
│            │  │ 8        │ │ 24       │ │ $186K    │ │ Mar 06 ││
│  ─ ADVISE  │  │ ▲ +2     │ │ ▲ +6     │ │ ▲ +22%   │ │ Tax Rev││
│  □ Active  │  └──────────┘ └──────────┘ └──────────┘ └────────┘│
│  □ Workshp │                                                     │
│  □ Resourc │  ┌──────────────────────────────────────────────────┐│
│            │  │ CLIENT ACCOUNT LIST                               ││
│  ─ ACTIV   │  │                                                   ││
│  □ Feed    │  │ Client           Type     Status   Last Contact  ││
│  □ Log     │  │ ──────────────────────────────────────────────── ││
│  □ Tasks   │  │ J. Smith (UGA)   Wealth   Active   2d ago        ││
│            │  │ A. Jones (LSU)   Tax      Active   5d ago        ││
│  ─ TOOLS   │  │ M. Davis (UCLA)  Wealth   Active   1w ago        ││
│  □ Favs    │  │ T. Brown (Vandy) Legal    Review   2w ago        ││
│  □ Pipes   │  │                                                   ││
│  □ Tourney │  │ [View All Accounts]                               ││
│            │  └──────────────────────────────────────────────────┘│
│  ─ COMMS   │                                                     │
│  □ Msgs    │  ┌─────────────────────────┐ ┌─────────────────────┐│
│  □ Huddle  │  │ UPCOMING ACTIVITIES     │ │ SERVICE DELIVERY    ││
│            │  │                          │ │                     ││
│  [Profile] │  │ Mar 06  Tax Review      │ │ This Month          ││
│            │  │         J. Smith (UGA)   │ │                     ││
│            │  │                          │ │ Completed:  6       ││
│            │  │ Mar 12  NIL Tax 101     │ │ In Progress: 3      ││
│            │  │         Workshop (8 att) │ │ Scheduled:  4       ││
│            │  │                          │ │                     ││
│            │  │ Mar 19  Wealth Review   │ │ ████████████░░ 69%  ││
│            │  │         A. Jones (LSU)   │ │                     ││
│            │  │                          │ │ [View Delivery Log] ││
│            │  │ [View Full Calendar]     │ │                     ││
│            │  └─────────────────────────┘ └─────────────────────┘│
│            │                                                     │
│            │  ┌──────────────────────────────────────────────────┐│
│            │  │ INBOUND MESSAGES                          [●  2] ││
│            │  │                                                   ││
│            │  │ You have 2 unread messages from existing threads. ││
│            │  │ Affiliates can reply to existing threads only.    ││
│            │  │                                                   ││
│            │  │ [Open Messages]                                   ││
│            │  └──────────────────────────────────────────────────┘│
└────────────┴─────────────────────────────────────────────────────┘
```

### Content Sections

| Section | Span | Data Source | Notes |
| --- | --- | --- | --- |
| KPI Strip | Full width, 4 cards | Advisor personal metrics | JetBrains Mono values |
| Client Account List | Full width table | Assigned client accounts | Last contact timestamp |
| Upcoming Activities | 6 col | Calendar + tasks | Date + client context |
| Service Delivery | 6 col | Delivery log aggregate | Progress bar + counts |
| Inbound Messages | Full width | Thread inbox | Badge count, inbound-first note |

### Inbound-First Messaging Indicator

Affiliate dashboard includes a persistent messaging context indicator:
- Badge shows unread count from existing threads only
- "Reply to existing threads only" helper text
- No "New Message" or "Compose" primary action
- Messages icon in top nav links to inbox (read + reply only)

### Token References

- Progress bar track: `--ad-bar-track`
- Progress bar fill: `--ad-bar-fill`
- Inbound badge: `--dash-nav-badge-bg` (`#DC2626`), `--dash-nav-badge-text`
- Last contact muted text: `--ui-text-muted`

---

## Assistant Athletic Director Dashboard Template

Primary user: Assistant ADs
Route: `/assistant-athletic-director`
Status: `planned`

### Layout Composition

Operations and event focused with a subset of Athletic Director capabilities. Shares `athletic` org category with AD and GM. Has full thread access (read/send) for messaging. Can compose outbound messages. Includes read-level compliance overview.

### Left Navigation

```
NAV

  OVERVIEW
  [ ] Dashboard
  [ ] Program Summary

  OPERATIONS
  [ ] Task Manager
  [ ] Workflow Queue
  [ ] Resource Allocation

  EVENTS
  [ ] Event Calendar
  [ ] Game Day Ops
  [ ] Scheduling

  COMPLIANCE
  [ ] Compliance Overview
  [ ] Audit Status
  [ ] Report Archive

  TOOLS
  [ ] Roster Builder
  [ ] Favorites
  [ ] Pipelines
  [ ] Tournaments

  DIRECTORIES
  [ ] Agent Directory
  [ ] Affiliate Directory

  COMMUNICATE
  [ ] Messages
  [ ] Huddles

  [Profile]
```

### KPI Strip

```
┌────────────────┐ ┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│ PROGRAM EVENTS │ │ COMPLIANCE     │ │ ACTIVE OPS     │ │ OPEN TASKS     │
│                │ │                │ │                │ │                │
│ 12 this month  │ │ 94% compliant  │ │ 7 in progress  │ │ 18             │
│ 3 upcoming     │ │ 16 reviews due │ │ 2 urgent       │ │ 5 due today    │
│ font: mono    │ │ font: mono     │ │ font: mono     │ │ font: mono     │
└────────────────┘ └────────────────┘ └────────────────┘ └────────────────┘
```

### ASCII Wireframe

```
┌──────────────────────────────────────────────────────────────────┐
│  [Logo]   [Org Name]    Search ________   [Huddles] [Msgs] [Av] │
├────────────┬─────────────────────────────────────────────────────┤
│            │                                                     │
│  NAV       │  ASSISTANT AD OPERATIONS                            │
│            │                                                     │
│  ■ Dash    │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐│
│  □ Program │  │ Program  │ │ Compli-  │ │ Active   │ │ Open   ││
│            │  │ Events   │ │ ance     │ │ Ops      │ │ Tasks  ││
│  ─ OPS     │  │ 12       │ │ 94%      │ │ 7        │ │ 18     ││
│  □ Tasks   │  │ 3 next   │ │ 16 rev.  │ │ 2 urgent │ │ 5 today││
│  □ Queue   │  └──────────┘ └──────────┘ └──────────┘ └────────┘│
│  □ Resourc │                                                     │
│            │  ┌──────────────────────────────────────────────────┐│
│  ─ EVENTS  │  │ OPERATIONS TASK LIST                              ││
│  □ Calenda │  │                                                   ││
│  □ GameDay │  │ Priority  Task                    Due     Status  ││
│  □ Sched   │  │ ──────────────────────────────────────────────── ││
│            │  │ ●  High   Budget reconciliation   Today   In Prog ││
│  ─ COMPLY  │  │ ●  High   Vendor contract review  Today   Open    ││
│  □ Overvie │  │ ○  Med    Facility scheduling     Mar 06  Open    ││
│  □ Audit   │  │ ○  Med    Travel coordination     Mar 08  Open    ││
│  □ Reports │  │ ○  Low    Equipment inventory     Mar 12  Open    ││
│            │  │                                                   ││
│  ─ TOOLS   │  │ [View All Tasks]                                  ││
│  □ Roster  │  └──────────────────────────────────────────────────┘│
│  □ Favs    │                                                     │
│  □ Pipes   │  ┌─────────────────────────┐ ┌─────────────────────┐│
│  □ Tourney │  │ EVENT CALENDAR           │ │ COMPLIANCE OVERVIEW ││
│            │  │                          │ │ (read-level)        ││
│  ─ COMMS   │  │ March 2026              │ │                     ││
│  □ Msgs    │  │ ┌─┬─┬─┬─┬─┬─┬─┐       │ │ ✓ 247 compliant     ││
│  □ Huddle  │  │ │ │ │ │ │ │●│ │       │ │ ⚠  28 review needed ││
│            │  │ ├─┼─┼─┼─┼─┼─┼─┤       │ │ ✗   9 expired       ││
│  [Profile] │  │ │ │●│ │ │ │ │●│       │ │                     ││
│            │  │ ├─┼─┼─┼─┼─┼─┼─┤       │ │ Status: Read Only   ││
│            │  │ │ │ │ │●│ │ │ │       │ │                     ││
│            │  │ └─┴─┴─┴─┴─┴─┴─┘       │ │ [View Details]      ││
│            │  │                          │ │                     ││
│            │  │ [View Full Calendar]     │ │                     ││
│            │  └─────────────────────────┘ └─────────────────────┘│
│            │                                                     │
│            │  TEAM QUICK-LINKS                                   │
│            │                                                     │
│            │  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐      │
│            │  │Football│ │Basketb.│ │Baseball │ │Soccer  │      │
│            │  │ 96 ath │ │ 15 ath │ │ 35 ath  │ │ 28 ath │      │
│            │  └────────┘ └────────┘ └────────┘ └────────┘      │
└────────────┴─────────────────────────────────────────────────────┘
```

### Content Sections

| Section | Span | Data Source | Notes |
| --- | --- | --- | --- |
| KPI Strip | Full width, 4 cards | Ops aggregate metrics | JetBrains Mono values |
| Operations Task List | Full width table | Task manager | Priority dot, due date, status |
| Event Calendar | 6 col | Program calendar | Mini month view with event dots |
| Compliance Overview | 6 col | Compliance data (read) | Status counts, read-only badge |
| Team Quick-Links | Full width, 4 cards | Program teams | Sport name + athlete count |

### Role Constraints

- Compliance overview is read-level only (no edit/approve actions)
- Cannot create NIL payments (restricted to agent scope)
- Can compose outbound messages to any user
- Shares organization scope with AD and GM roles
- Profile menu shows no `Organization Settings` (AD-exclusive)

### Token References

- Priority high dot: `--color-priority-delta`
- Priority medium dot: `--color-risk-uncertainty`
- Priority low dot: `--ui-text-muted`
- Compliance status bar: same pattern as AD compliance tracker
- Calendar event dots: `--dash-nav-badge-bg` (`#DC2626`)
- Read-only badge: `--ad-chip-bg`, `--ad-chip-border`, `--ad-chip-text`

---

## General Manager Dashboard Template

Primary user: General managers
Route: `/general-manager`
Status: `planned`

### Layout Composition

Roster, valuation, and contract focused. GMs operate within the `athletic` org category alongside ADs and Assistant ADs. Full messaging access with outbound compose. Roster management is the primary workflow.

### Left Navigation

```
NAV

  OVERVIEW
  [ ] Dashboard
  [ ] Program Summary

  ROSTER
  [ ] Active Roster
  [ ] Roster Builder
  [ ] Player Search
  [ ] Add to Pipeline

  VALUATION
  [ ] Team Valuations
  [ ] Player Comparisons
  [ ] Predictions

  CONTRACTS
  [ ] Active Contracts
  [ ] Contract Pipeline
  [ ] Payment Schedule

  TOOLS
  [ ] Favorites
  [ ] Pipelines
  [ ] Tournaments

  DIRECTORIES
  [ ] Agent Directory
  [ ] Affiliate Directory

  COMMUNICATE
  [ ] Messages
  [ ] Huddles

  [Profile]
```

### KPI Strip

```
┌────────────────┐ ┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│ ROSTER VALUE   │ │ ACTIVE DEALS   │ │ BUDGET REMAIN. │ │ TOP PROSPECT   │
│                │ │                │ │                │ │                │
│ $14.2M         │ │ 9              │ │ $2.1M          │ │ D. Carter      │
│ ▲ +11.4%       │ │ $3.8M total    │ │ of $5.0M alloc │ │ $1.9M est.     │
│ font: mono    │ │ font: mono     │ │ font: mono     │ │ font: mono     │
└────────────────┘ └────────────────┘ └────────────────┘ └────────────────┘
```

### ASCII Wireframe

```
┌──────────────────────────────────────────────────────────────────┐
│  [Logo]   [Org Name]    Search ________   [Huddles] [Msgs] [Av] │
├────────────┬─────────────────────────────────────────────────────┤
│            │                                                     │
│  NAV       │  GENERAL MANAGER OVERVIEW                           │
│            │                                                     │
│  ■ Dash    │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐│
│  □ Program │  │ Roster   │ │ Active   │ │ Budget   │ │ Top    ││
│            │  │ Value    │ │ Deals    │ │ Remain.  │ │ Prosp. ││
│  ─ ROSTER  │  │ $14.2M   │ │ 9        │ │ $2.1M    │ │D.Carter││
│  □ Active  │  │ ▲ +11.4% │ │ $3.8M    │ │ of $5.0M │ │ $1.9M  ││
│  □ Builder │  └──────────┘ └──────────┘ └──────────┘ └────────┘│
│  □ Search  │                                                     │
│  □ Pipelin │  ┌──────────────────────────────────────────────────┐│
│            │  │ ROSTER MANAGEMENT TABLE                           ││
│  ─ VALUE   │  │                                                   ││
│  □ Team V  │  │ #   Player        Pos  Est NIL   Contract  Stat  ││
│  □ Compare │  │ ──────────────────────────────────────────────── ││
│  □ Predict │  │ 1   D. Carter     RB   $1.9M    $180K     ▲+14% ││
│            │  │ 5   K. Mitchell   WR   $1.6M    $150K     ▲+8%  ││
│  ─ CONTRAC │  │ 12  J. Thomas     QB   $1.4M    $200K     ▲+22% ││
│  □ Active  │  │ 23  R. Anderson   CB   $1.1M    $90K      ▼-3%  ││
│  □ Pipelin │  │ 3   T. Williams   PG   $980K    $85K      ▲+5%  ││
│  □ Payment │  │ 44  M. Johnson    C    $720K    $60K      ─ 0%  ││
│            │  │                                                   ││
│  ─ TOOLS   │  │ Showing 6 of 15  [View Full Roster]              ││
│  □ Favs    │  └──────────────────────────────────────────────────┘│
│  □ Pipes   │                                                     │
│  □ Tourney │  ┌─────────────────────────┐ ┌─────────────────────┐│
│            │  │ CONTRACT TRACKING        │ │ VALUATION COMPARE   ││
│  ─ COMMS   │  │                          │ │                     ││
│  □ Msgs    │  │ Active:      9           │ │ [Bar Chart]         ││
│  □ Huddle  │  │ Expiring:    3 (30d)     │ │                     ││
│            │  │ Pending:     4           │ │ D.Carter    ████ 1.9││
│  [Profile] │  │ Total Value: $3.8M      │ │ K.Mitchell  ███  1.6││
│            │  │                          │ │ J.Thomas    ███  1.4││
│            │  │ Next Expiry:             │ │ R.Anderson  ██   1.1││
│            │  │ R. Anderson  Apr 15      │ │ T.Williams  ██   .98││
│            │  │ T. Williams  May 01      │ │                     ││
│            │  │ M. Johnson   May 22      │ │ [Full Comparison]   ││
│            │  │                          │ │                     ││
│            │  │ [Manage Contracts]       │ │                     ││
│            │  └─────────────────────────┘ └─────────────────────┘│
│            │                                                     │
│            │  ┌──────────────────────────────────────────────────┐│
│            │  │ PIPELINE PREVIEW                                  ││
│            │  │                                                   ││
│            │  │ Scouted: 12  |  Contacted: 6  |  Offered: 3      ││
│            │  │ Committed: 1 |  Est Pipeline Value: $4.2M         ││
│            │  │                                                   ││
│            │  │ [View Pipeline]    [Add to Pipeline]              ││
│            │  └──────────────────────────────────────────────────┘│
└────────────┴─────────────────────────────────────────────────────┘
```

### Content Sections

| Section | Span | Data Source | Notes |
| --- | --- | --- | --- |
| KPI Strip | Full width, 4 cards | Roster + budget aggregate | Top Prospect shows name + est |
| Roster Management | Full width table | Active roster | Jersey #, position, NIL, contract, trend |
| Contract Tracking | 6 col | Contract data | Expiry countdown, total value |
| Valuation Compare | 6 col | Player valuations | Horizontal bar chart |
| Pipeline Preview | Full width | Recruiting pipeline | Stage counts + total est value |

### Role-Specific Actions

- `Add to Pipeline` button on pipeline section and player search (lightbox selector)
- Roster table supports inline sort by Est NIL, Contract Value, or Trend
- Contract tracking highlights expiring deals within 30 days
- No NIL payment creation (restricted to agent scope)
- Can compose outbound messages to any user

### Token References

- Roster table rows: `--ui-surface-2`, `--ad-row-bg`
- Jersey number column: `--font-mono-data`
- Valuation bars: `--ad-compare-track`, `--ad-compare-fill`, `--ad-compare-focus-fill`
- Expiry warning: `--color-risk-uncertainty`
- Pipeline stage bars: `--ad-bar-track`, `--ad-bar-fill`
- Top Prospect card accent: `--ui-accent-solid`

---

## Cross-Template Conventions

### Shared Navigation Rules

All role templates (except Fan) include these global nav items:
- Agent Directory (`/agent-directory`)
- Affiliate Directory (`/affiliate-directory`)
- Favorites (route varies by shell)
- Pipelines (`/dashboard/pipelines`)

### Shared Top Navigation

All role templates (except Fan) include:
- Logo + org/program context title (skeleton while loading)
- Search input
- Huddles icon + label
- Messages icon + label
- Notification bell
- Avatar dropdown with role-specific settings

Fan template excludes: Huddles, Messages, Notifications, keyboard shortcuts.

### Messaging Access Matrix (Template Impact)

| Template | Outbound Compose | Inbound Reply | Thread Access |
| --- | --- | --- | --- |
| Coach | Program-scoped + listed agents | Full | Full |
| Fan | None | None | None |
| Agency Admin | Any user | Full | Full |
| Affiliate Admin | Existing threads only | Full | Full |
| Affiliate | Existing threads only | Full | Full |
| Assistant AD | Any user | Full | Full |
| General Manager | Any user | Full | Full |

### KPI Card Pattern

All KPI strips follow this token composition:
- Surface: `--ui-surface-1`
- Border: `--ui-border-default`
- Primary value: `--font-mono-data`, `--ui-text-primary`
- Label: `--font-body-operational`, `--ui-text-muted`
- Positive delta: `--color-positive-verified`
- Negative delta: `--color-priority-delta`
- Neutral delta: `--ui-text-muted`
- Card padding: `--ui-card-padding-default`
- Card radius: `--ui-radius-lg`

### Loading States

All templates use ghost/skeleton loading for:
- KPI strip cards (4 ghost blocks at card dimensions)
- Table rows (shimmer rows matching column layout)
- Chart areas (ghost block at chart dimensions)
- Nav context title (skeleton text while role context resolves)

Ghost tokens: `--ui-ghost-start`, `--ui-ghost-mid`, `--ui-ghost-end`, `--ui-ghost-duration`.

### Responsive Behavior

| Breakpoint | Layout Change |
| --- | --- |
| >= 1280px (desktop) | Full sidebar + 12-col content grid |
| 768-1279px (tablet) | Collapsed sidebar + 8-col content, KPI cards wrap to 2x2 |
| < 768px (mobile) | Bottom tab bar, stacked single-column, horizontal scroll KPI cards |

### Dark/Light Theme Support

All templates must support both themes through tokenized surfaces. No hardcoded color utilities. Light mode keeps sidebar dark for X parity (`--dash-nav-bg` stays slate-900 in light mode).
