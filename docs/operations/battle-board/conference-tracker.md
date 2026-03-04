# Conference Tracker Design Spec

> **Last Updated:** 2026-03-04
> **Owner:** Design / Operations
> **Classification:** Internal — Design Specification

---

## Overview

The Conference Tracker is the primary navigation layer of the Battle Board. It provides conference-level aggregation of onboarding progress, enabling sales leadership to assess territorial coverage, identify gaps, and prioritize resources. Every view in this spec is basketball-first, with multi-sport expansion visible only within onboarded programs.

---

## Conference Summary Card

The summary card is the atomic unit of the conference tracker. Each conference gets one card. Cards are displayed in a grid (3-up on desktop, 1-up on mobile) and are sortable by coverage %, priority tier, or last activity.

### ASCII Wireframe

```
+------------------------------------------------------------------------+
|                                                                        |
|  [ LOGO ]   SEC                                    Tier A  |  Power 4  |
|             Southeastern Conference                                    |
|                                                                        |
|  +------------------------------------------------------------------+  |
|  |  Schools: 16 total                                               |  |
|  |  Onboarded: 3    In Pipeline: 5    Uncontacted: 8                |  |
|  +------------------------------------------------------------------+  |
|                                                                        |
|  Coverage  [=======>................]  19%                              |
|                                                                        |
|  +--------------------------+  +------------------------------------+  |
|  |  Priority Sport          |  |  Pipeline Breakdown                |  |
|  |  1. Basketball    16/16  |  |  Outreach:       3                 |  |
|  |  2. Football      0/16   |  |  Demo Sched:     1                 |  |
|  |  3. Baseball      0/14   |  |  Trial Active:   1                 |  |
|  +--------------------------+  |  Onboarded:      3                 |  |
|                                +------------------------------------+  |
|                                                                        |
|  Last Activity: 2026-03-02       Assigned AEs: J. Smith, K. Davis      |
|                                                                        |
|  [ View Conference Detail ]                        [ Log Activity ]    |
|                                                                        |
+------------------------------------------------------------------------+
```

### Card Data Fields

| Field | Source | Update Frequency |
|-------|--------|------------------|
| Conference name | Registry (static) | On realignment |
| Logo placeholder | Asset library | Static |
| Total schools | Registry count | On realignment |
| Onboarded count | Pipeline status rollup | Real-time |
| Pipeline count | Status = Outreach + Demo + Trial | Real-time |
| Uncontacted count | Total - Onboarded - Pipeline | Real-time |
| Coverage % | (Onboarded / Total) x 100 | Real-time |
| Priority sport | Basketball always #1 | Static |
| Pipeline breakdown | Count per stage | Real-time |
| Last activity date | Most recent touchpoint across all schools | Real-time |
| Assigned AEs | AEs with schools in this conference | Real-time |

### Card States

| Coverage % | Visual Treatment |
|-----------|------------------|
| 0% | Red border, red coverage bar, "UNSTARTED" badge |
| 1-24% | Orange border, orange coverage bar |
| 25-49% | Yellow border, yellow coverage bar |
| 50-74% | Light green border, light green coverage bar |
| 75-99% | Green border, green coverage bar |
| 100% | Green border, green coverage bar, "COMPLETE" badge |

### Card Interactions

- **Click card:** Navigate to Conference Detail View
- **Click "View Conference Detail":** Same as card click
- **Click "Log Activity":** Opens activity log modal for the conference
- **Hover on coverage bar:** Tooltip shows exact counts per stage
- **Sort controls:** Coverage %, Tier, Last Activity, Alphabetical

---

## Conference Detail View

The detail view is the deep-dive into a single conference. It shows school-by-school status, sport coverage matrix, and revenue potential.

### ASCII Wireframe — Header

```
+========================================================================+
|                                                                        |
|  <-- Back to All Conferences                                           |
|                                                                        |
|  [ LOGO ]   SEC — Southeastern Conference                              |
|             Division I  |  Power 4  |  Tier A                          |
|                                                                        |
|  +--------------------+  +--------------------+  +------------------+  |
|  |  COVERAGE          |  |  PIPELINE          |  |  REVENUE         |  |
|  |                    |  |                    |  |                  |  |
|  |      19%           |  |   5 programs       |  |  $36,000         |  |
|  |   3 of 16          |  |   in pipeline      |  |  active ARR      |  |
|  |   onboarded        |  |   (31% of conf)    |  |  $192K potential |  |
|  +--------------------+  +--------------------+  +------------------+  |
|                                                                        |
|  Status Breakdown:                                                     |
|  Uncontacted [========]  8    Onboarded   [===]  3                     |
|  Outreach    [===]       3    Churned     []     0                     |
|  Demo Sched  [=]         1                                             |
|  Trial       [=]         1                                             |
|                                                                        |
+========================================================================+
```

### ASCII Wireframe — School Status Table

```
+========================================================================+
|  SCHOOL STATUS — SEC Basketball                                        |
|  Sort: [Status v]  Filter: [All Stages v]  Search: [___________]      |
+========================================================================+
|                                                                        |
|  School          | Status       | Contact        | Last Touch | AE    |
|  ————————————————+——————————————+————————————————+————————————+———————|
|  Alabama         | Onboarded    | J. Williams    | 2026-02-28 | Smith |
|  Arkansas        | Outreach     | M. Anderson    | 2026-03-01 | Smith |
|  Auburn          | Trial Active | D. Greene      | 2026-03-02 | Davis |
|  Florida         | Demo Sched   | R. Palmer      | 2026-02-25 | Smith |
|  Georgia         | Uncontacted  | —              | —          | —     |
|  Kentucky        | Onboarded    | K. Mitchell    | 2026-02-20 | Davis |
|  LSU             | Outreach     | T. Brooks      | 2026-03-01 | Smith |
|  Mississippi St  | Uncontacted  | —              | —          | —     |
|  Missouri        | Uncontacted  | —              | —          | —     |
|  Oklahoma        | Outreach     | B. Hawkins     | 2026-02-27 | Davis |
|  Ole Miss        | Uncontacted  | —              | —          | —     |
|  South Carolina  | Uncontacted  | —              | —          | —     |
|  Tennessee       | Onboarded    | C. Foster      | 2026-02-15 | Davis |
|  Texas           | Uncontacted  | —              | —          | —     |
|  Texas A&M       | Uncontacted  | —              | —          | —     |
|  Vanderbilt      | Uncontacted  | —              | —          | —     |
|                                                                        |
+========================================================================+
|  Showing 16 of 16 programs  |  Bulk Actions: [Assign AE] [Export]     |
+========================================================================+
```

### School Status Table Columns

| Column | Description | Sortable | Filterable |
|--------|-------------|----------|------------|
| School | Institution name | Yes (A-Z) | Yes (search) |
| Status | Current pipeline stage | Yes | Yes (dropdown) |
| Contact | Primary contact name | Yes (A-Z) | No |
| Last Touch | Date of most recent activity | Yes (date) | Yes (range) |
| AE | Assigned Account Executive | Yes (A-Z) | Yes (dropdown) |
| Priority | Within-conference priority | Yes | Yes |
| Notes | Truncated latest note | No | No |

### Row Interactions

- **Click row:** Navigate to School Detail View
- **Hover row:** Highlight with subtle background change
- **Status badge:** Color-coded per stage (see pipeline design)
- **Inline actions:** Quick-log activity, reassign AE, add note

---

### ASCII Wireframe — Sport Coverage Matrix

```
+========================================================================+
|  SPORT COVERAGE MATRIX — SEC                                           |
|  (Showing onboarding status per school per sport)                      |
+========================================================================+
|                                                                        |
|  School          | MBB  | WBB  | FB   | BSB  | SB   | T&F  | SOC  |  |
|  ————————————————+——————+——————+——————+——————+——————+——————+——————+  |
|  Alabama         |  ●   |  ○   |  ○   |  ○   |  ○   |  —   |  —   |  |
|  Arkansas        |  ◐   |  —   |  —   |  —   |  —   |  —   |  —   |  |
|  Auburn          |  ◐   |  —   |  —   |  —   |  —   |  —   |  —   |  |
|  Florida         |  ◐   |  —   |  —   |  —   |  —   |  —   |  —   |  |
|  Georgia         |  ○   |  —   |  —   |  —   |  —   |  —   |  —   |  |
|  Kentucky        |  ●   |  ○   |  ○   |  —   |  —   |  —   |  —   |  |
|  LSU             |  ◐   |  —   |  —   |  —   |  —   |  —   |  —   |  |
|  Tennessee       |  ●   |  ◐   |  ○   |  —   |  —   |  —   |  —   |  |
|  ...             |  ..  |  ..  |  ..  |  ..  |  ..  |  ..  |  ..  |  |
|                                                                        |
|  Legend: ● Onboarded  ◐ In Pipeline  ○ Targeted  — Not Applicable      |
|                                                                        |
+========================================================================+
```

### Sport Abbreviations

| Code | Sport | Priority Order |
|------|-------|---------------|
| MBB | Men's Basketball | 1 (always first) |
| WBB | Women's Basketball | 2 |
| FB | Football | 3 |
| BSB | Baseball | 4 |
| SB | Softball | 5 |
| T&F | Track & Field | 6 |
| SOC | Soccer | 7 |

---

### Revenue Potential Calculator

```
+========================================================================+
|  REVENUE POTENTIAL — SEC                                               |
+========================================================================+
|                                                                        |
|  Calculation Model:                                                    |
|                                                                        |
|  Total Schools in Conference:           16                             |
|  Average Contract Value (Tier A):       $12,000 / year                 |
|  ——————————————————————————————————————————————————                    |
|  Max Conference Revenue:                $192,000 / year                |
|                                                                        |
|  Current Active Revenue:                $36,000 / year  (3 schools)    |
|  Pipeline Projected Revenue:            $60,000 / year  (5 schools)    |
|  ——————————————————————————————————————————————————                    |
|  Projected Total (if pipeline closes):  $96,000 / year                 |
|  Revenue Coverage:                      50% of max potential           |
|                                                                        |
|  +------------------------------------------------------------------+ |
|  |  Revenue Waterfall                                                | |
|  |                                                                   | |
|  |  Max Potential  ████████████████████████████████  $192K           | |
|  |  Active         ████████████                      $36K            | |
|  |  + Pipeline     ████████████████████              $96K            | |
|  |  Gap            ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  $96K            | |
|  +------------------------------------------------------------------+ |
|                                                                        |
+========================================================================+
```

---

## Heat Map View

The heat map provides a visual overview of conference coverage across the entire NCAA landscape. It is the default landing view of the Battle Board.

### Description

The heat map displays all conferences as colored blocks arranged by division and geography. Color intensity represents onboarding coverage percentage. The map is interactive — clicking a conference block navigates to its detail view.

### Color Scale

```
Coverage Color Scale:

  0%          25%         50%         75%         100%
  |           |           |           |            |
  ████████    ████████    ████████    ████████    ████████
  #DC2626     #F59E0B     #EAB308     #22C55E     #16A34A
  (Red)       (Orange)    (Yellow)    (Lt Green)  (Green)
```

| Coverage Range | Color | Hex | Meaning |
|---------------|-------|-----|---------|
| 0% | Red | `#DC2626` | No programs onboarded — immediate attention required |
| 1-24% | Orange | `#F59E0B` | Early stage — outreach in progress |
| 25-49% | Yellow | `#EAB308` | Building momentum — pipeline active |
| 50-74% | Light Green | `#22C55E` | Strong presence — more than half onboarded |
| 75-100% | Green | `#16A34A` | Dominant coverage — conference nearly or fully captured |

### Heat Map Layout

```
+========================================================================+
|  NCAA BASKETBALL CONFERENCE HEAT MAP                                   |
|  Filter: [All Divisions v] [Basketball v] [All Tiers v] [All Status v] |
+========================================================================+
|                                                                        |
|  POWER 4 (Tier A)                                                      |
|  +----------+  +----------+  +----------+  +----------+               |
|  |   SEC    |  | Big Ten  |  |   ACC    |  |  Big 12  |               |
|  |  19%  ██ |  |  11%  ██ |  |   6%  ██ |  |   0%  ██ |               |
|  |  3/16    |  |  2/18    |  |  1/18    |  |  0/16    |               |
|  +----------+  +----------+  +----------+  +----------+               |
|                                                                        |
|  HIGH MAJOR (Tier B)                                                   |
|  +----------+  +----------+  +----------+  +----------+  +----------+ |
|  |   AAC    |  |   MWC    |  |   WCC    |  |   A-10   |  |   MVC    | |
|  |   0%  ██ |  |   0%  ██ |  |   0%  ██ |  |   0%  ██ |  |   0%  ██ | |
|  |  0/13    |  |  0/11    |  |  0/10    |  |  0/15    |  |  0/12    | |
|  +----------+  +----------+  +----------+  +----------+  +----------+ |
|                                                                        |
|  MID-MAJOR (Tier C)                                                    |
|  +------+ +------+ +------+ +------+ +------+ +------+ +------+      |
|  |B.East| | CAA  | |C-USA | | Horz | | Ivy  | | MAAC | | MAC  |      |
|  | 0% ██| | 0% ██| | 0% ██| | 0% ██| | 0% ██| | 0% ██| | 0% ██|      |
|  +------+ +------+ +------+ +------+ +------+ +------+ +------+      |
|  +------+ +------+ +------+ +------+ +------+ +------+ +------+      |
|  | Pat  | |SoCon | |SunBt | | WAC  | |B.Sky | |B.Sth | |B.Wst |      |
|  | 0% ██| | 0% ██| | 0% ██| | 0% ██| | 0% ██| | 0% ██| | 0% ██|      |
|  +------+ +------+ +------+ +------+ +------+ +------+ +------+      |
|  +------+ +------+ +------+ +------+ +------+ +------+ +------+      |
|  | OVC  | | NEC  | |Sthlnd| |Summt | | SWAC | | MEAC | | AEC  |      |
|  | 0% ██| | 0% ██| | 0% ██| | 0% ██| | 0% ██| | 0% ██| | 0% ██|      |
|  +------+ +------+ +------+ +------+ +------+ +------+ +------+      |
|  +------+                                                              |
|  | ASUN |                                                              |
|  | 0% ██|                                                              |
|  +------+                                                              |
|                                                                        |
|  LOWER DIVISIONS (Tier D)                                              |
|  +------------------+  +------------------+  +------------------+     |
|  |  Division II     |  |  Division III    |  |  NAIA            |     |
|  |  0% of ~300      |  |  0% of ~400      |  |  0% of ~250      |     |
|  |  Expansion phase |  |  Expansion phase |  |  Long-term       |     |
|  +------------------+  +------------------+  +------------------+     |
|                                                                        |
+========================================================================+
```

### Filter Controls

| Filter | Options | Default |
|--------|---------|---------|
| Division | All, D1, D2, D3, NAIA | All |
| Sport | Basketball, Football, All Sports | Basketball |
| Priority Tier | All, A, B, C, D, E | All |
| Status | All, Active Pipeline, Uncontacted, Onboarded | All |

### Heat Map Interactions

- **Click conference block:** Navigate to Conference Detail View
- **Hover conference block:** Tooltip with school count, pipeline summary, top AE
- **Filter change:** Animate color transitions as data updates
- **Zoom controls:** Toggle between compact (all conferences) and expanded (one tier)

---

## Division Rollup View

The Division Rollup provides executive-level progress tracking across the entire NCAA landscape.

### ASCII Wireframe

```
+========================================================================+
|  DIVISION ROLLUP — NCAA Basketball Coverage                            |
|  As of: 2026-03-04                                                     |
+========================================================================+
|                                                                        |
|  OVERALL PROGRESS                                                      |
|  [=>...........................................]  6 / 360 D1  (1.7%)   |
|                                                                        |
+------------------------------------------------------------------------+
|                                                                        |
|  DIVISION I BREAKDOWN                                                  |
|                                                                        |
|  Power 4 (67 programs)  — Tier A                                       |
|  [=====>.............................]  6/67 onboarded  (9.0%)         |
|  Pipeline: 12 programs | Uncontacted: 49 programs                      |
|  Revenue: $72K active | $192K pipeline | $804K max potential           |
|                                                                        |
|  +--------------+  +--------------+  +--------------+  +-----------+  |
|  | SEC    19%   |  | B10    11%   |  | ACC     6%   |  | B12   0%  |  |
|  | 3/16 active  |  | 2/18 active  |  | 1/18 active  |  | 0/16      |  |
|  +--------------+  +--------------+  +--------------+  +-----------+  |
|                                                                        |
|  High Major (61 programs) — Tier B                                     |
|  [>..............................................]  0/61  (0%)         |
|  Pipeline: 0 programs | Uncontacted: 61 programs                       |
|  Revenue: $0 active | $0 pipeline | $488K max potential                |
|                                                                        |
|  +--------+  +--------+  +--------+  +--------+  +--------+          |
|  |AAC  0% |  |MWC  0% |  |WCC  0% |  |A10  0% |  |MVC  0% |          |
|  | 0/13   |  | 0/11   |  | 0/10   |  | 0/15   |  | 0/12   |          |
|  +--------+  +--------+  +--------+  +--------+  +--------+          |
|                                                                        |
|  Mid-Major (~230 programs) — Tier C                                    |
|  [>..............................................]  0/~230  (0%)       |
|  Pipeline: 0 programs | Uncontacted: ~230 programs                     |
|  Revenue: $0 active | $0 pipeline | $1.38M max potential               |
|                                                                        |
|  22 conferences — all at 0% coverage                                   |
|  Activation target: Q3 2026                                            |
|                                                                        |
+------------------------------------------------------------------------+
|                                                                        |
|  LOWER DIVISIONS                                                       |
|                                                                        |
|  Division II (~300 programs) — Tier D                                  |
|  [>..............................................]  0/~300  (0%)       |
|  Status: Expansion phase — not yet activated                           |
|  Target activation: Q1 2027                                            |
|                                                                        |
|  Division III (~400 programs) — Tier D                                 |
|  [>..............................................]  0/~400  (0%)       |
|  Status: Expansion phase — self-serve model planned                    |
|  Target activation: Q3 2027                                            |
|                                                                        |
|  NAIA (~250 programs) — Tier D                                         |
|  [>..............................................]  0/~250  (0%)       |
|  Status: Long-term — not yet planned                                   |
|  Target activation: 2028                                               |
|                                                                        |
+========================================================================+
```

### Division Rollup Data

| Metric | Power 4 | High Major | Mid-Major | D2 | D3 | NAIA |
|--------|---------|------------|-----------|-----|-----|------|
| Programs | 67 | 61 | ~230 | ~300 | ~400 | ~250 |
| Avg Contract Value | $12,000 | $8,000 | $6,000 | $3,000 | $1,500 | $1,200 |
| Max Revenue Potential | $804K | $488K | $1.38M | $900K | $600K | $300K |
| AE Assignment | Dedicated | Dedicated | Pooled | Self-serve | Self-serve | Self-serve |
| Outreach Cadence | Weekly | Bi-weekly | Monthly | Quarterly | None | None |
| Target Start | Q1 2026 | Q1 2026 | Q3 2026 | Q1 2027 | Q3 2027 | 2028 |

---

## Pipeline Funnel Dashboard

The Pipeline Funnel shows the health and velocity of the entire sales pipeline across all conferences and divisions.

### ASCII Wireframe

```
+========================================================================+
|  PIPELINE FUNNEL — NCAA Basketball Programs                            |
|  Period: Last 30 Days  |  Filter: [All Tiers v]  [Basketball v]        |
+========================================================================+
|                                                                        |
|  +------------------------------------------------------------------+  |
|  |                                                                  |  |
|  |  UNCONTACTED                                                     |  |
|  |  ████████████████████████████████████████████████████████  310    |  |
|  |                                                                  |  |
|  |           ↓  Conversion: 8.4%  |  Avg: 0 days                   |  |
|  |                                                                  |  |
|  |  OUTREACH                                                        |  |
|  |  ██████████████████████████                               26     |  |
|  |                                                                  |  |
|  |           ↓  Conversion: 38.5%  |  Avg: 7.2 days                |  |
|  |                                                                  |  |
|  |  DEMO SCHEDULED                                                  |  |
|  |  ██████████████████                                       10     |  |
|  |                                                                  |  |
|  |           ↓  Conversion: 60%  |  Avg: 4.1 days                  |  |
|  |                                                                  |  |
|  |  TRIAL ACTIVE                                                    |  |
|  |  ████████████                                             6      |  |
|  |                                                                  |  |
|  |           ↓  Conversion: 50%  |  Avg: 21 days                   |  |
|  |                                                                  |  |
|  |  ONBOARDED (ACTIVE)                                              |  |
|  |  ████████                                                 6      |  |
|  |                                                                  |  |
|  |  CHURNED                                                         |  |
|  |  ██                                                       0      |  |
|  |                                                                  |  |
|  +------------------------------------------------------------------+  |
|                                                                        |
+------------------------------------------------------------------------+
|                                                                        |
|  PIPELINE VELOCITY                                                     |
|                                                                        |
|  Programs entering pipeline this month:    12                          |
|  Programs completing onboarding this month: 2                          |
|  Average full-cycle time (Outreach → Onboarded): 32.4 days            |
|  Pipeline acceleration vs last month: +15%                             |
|                                                                        |
+------------------------------------------------------------------------+
|                                                                        |
|  REVENUE PROJECTION                                                    |
|                                                                        |
|  Active Revenue (6 programs):               $62,000 ARR               |
|  Trial Pipeline (at 50% close):             +$24,000 projected        |
|  Demo Pipeline (at 30% close):              +$24,000 projected        |
|  Outreach Pipeline (at 12% close):          +$24,960 projected        |
|  ——————————————————————————————————————————                           |
|  Total Revenue Forecast:                    $134,960 ARR              |
|                                                                        |
+========================================================================+
```

### Funnel Metrics Table

| Stage | Count | % of Total | Conversion to Next | Avg Days in Stage | Target Days |
|-------|-------|-----------|-------------------|------------------|------------|
| Uncontacted | 310 | 86.1% | 8.4% → Outreach | — | — |
| Outreach | 26 | 7.2% | 38.5% → Demo | 7.2 | <5 |
| Demo Scheduled | 10 | 2.8% | 60% → Trial | 4.1 | <5 |
| Trial Active | 6 | 1.7% | 50% → Onboarded | 21.0 | <21 |
| Onboarded | 6 | 1.7% | — (retain) | — | — |
| Churned | 0 | 0% | — (win-back) | — | — |

### Funnel Interactions

- **Click stage bar:** Expand to show list of programs in that stage
- **Click conversion arrow:** Show programs that converted in this period
- **Hover revenue projection:** Breakdown by tier and conference
- **Period selector:** Last 7 days, 30 days, 90 days, YTD, All time
- **Tier filter:** Show funnel for specific priority tier only

---

## Component Design Tokens

All conference tracker components use the NIL Optic design system tokens.

### Colors

| Token | Value | Usage |
|-------|-------|-------|
| `--color-coverage-0` | `#DC2626` | 0% coverage (red) |
| `--color-coverage-25` | `#F59E0B` | 1-24% coverage (orange) |
| `--color-coverage-50` | `#EAB308` | 25-49% coverage (yellow) |
| `--color-coverage-75` | `#22C55E` | 50-74% coverage (light green) |
| `--color-coverage-100` | `#16A34A` | 75-100% coverage (green) |
| `--color-tier-a` | `#DC2626` | Tier A badge (brand red) |
| `--color-tier-b` | `#F59E0B` | Tier B badge (amber) |
| `--color-tier-c` | `#3B82F6` | Tier C badge (blue) |
| `--color-tier-d` | `#6B7280` | Tier D badge (gray) |
| `--color-tier-e` | `#8B5CF6` | Tier E badge (purple) |
| `--color-bg-card` | `#111111` | Card background (dark mode) |
| `--color-bg-surface` | `#1A1A1A` | Surface background |
| `--color-border` | `#333333` | Default border |
| `--color-text-primary` | `#FFFFFF` | Primary text |
| `--color-text-secondary` | `#9CA3AF` | Secondary text |

### Typography

| Element | Font | Size | Weight |
|---------|------|------|--------|
| Conference name (card) | Inter | 18px | 700 (Bold) |
| Conference name (detail) | Inter | 28px | 700 (Bold) |
| Stat label | Inter | 12px | 500 (Medium) |
| Stat value | JetBrains Mono | 24px | 700 (Bold) |
| Table header | Inter | 11px | 600 (Semibold) |
| Table body | Inter | 13px | 400 (Regular) |
| Coverage % | JetBrains Mono | 14px | 600 (Semibold) |
| Badge text | Inter | 10px | 700 (Bold) |

### Spacing

| Token | Value | Usage |
|-------|-------|-------|
| `--space-card-padding` | 24px | Internal card padding |
| `--space-card-gap` | 16px | Gap between cards in grid |
| `--space-section-gap` | 32px | Gap between major sections |
| `--space-table-row-height` | 48px | Table row height |
| `--space-table-cell-padding` | 12px | Table cell padding |

### Elevation

| Token | Value | Usage |
|-------|-------|-------|
| `--shadow-card` | `0 1px 3px rgba(0,0,0,0.3)` | Card resting state |
| `--shadow-card-hover` | `0 4px 12px rgba(0,0,0,0.5)` | Card hover state |
| `--shadow-modal` | `0 8px 32px rgba(0,0,0,0.6)` | Modal/overlay |

---

## Responsive Behavior

| Breakpoint | Layout | Cards Per Row | Table Behavior |
|-----------|--------|---------------|----------------|
| Desktop (1280px+) | Full grid | 3 cards | Full table with all columns |
| Tablet (768-1279px) | Reduced grid | 2 cards | Scrollable table, priority columns visible |
| Mobile (< 768px) | Stack | 1 card | Card-based table rows |

---

## Related Documents

- [Battle Board Overview](./README.md)
- [NCAA Basketball Registry](./ncaa-basketball-registry.md)
- [Onboarding Pipeline](./onboarding-pipeline.md)
- [Design Tokens](../../design/design-tokens.md)

---

*NIL Optic — The operating system for college athletics NIL management.*
