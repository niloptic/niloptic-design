# NIL Optic Battle Board

> **Last Updated:** 2026-03-04
> **Owner:** Operations / Growth Team
> **Classification:** Internal — Confidential

---

## Purpose

The NIL Optic Battle Board is the centralized war room for tracking program onboarding across all of college sports. It provides real-time visibility into every NCAA program's status in the sales pipeline, measures territorial coverage by conference and division, and drives prioritized outreach strategy.

**Basketball is the #1 priority sport.** Every metric, view, and workflow in the Battle Board is optimized around basketball program acquisition first, with expansion paths to football and other sports built on top of basketball infrastructure.

### Strategic Objective

Achieve dominant market coverage across NCAA basketball — starting with Power 4, expanding through high-major and mid-major D1, then scaling to D2/D3/NAIA — before broadening to multi-sport coverage within onboarded programs.

---

## Data Model

### Program Entity

Every NCAA program tracked in the Battle Board conforms to the following data model:

| Field | Type | Description |
|-------|------|-------------|
| `school_name` | String | Official institution name |
| `school_id` | UUID | Unique internal identifier |
| `conference` | String | Current conference affiliation |
| `division` | Enum | D1, D2, D3, NAIA |
| `sport` | Enum | Basketball (primary), Football, Baseball, etc. |
| `onboarding_status` | Enum | Current pipeline stage (see Status Stages) |
| `priority_tier` | Enum | A through E (see Priority Tiers) |
| `primary_contact` | Object | Name, title, email, phone of AD or decision-maker |
| `secondary_contact` | Object | Compliance officer or assistant AD |
| `estimated_nil_budget` | Currency | Estimated annual NIL budget potential |
| `contract_value` | Currency | Actual or projected contract value |
| `last_contact_date` | Date | Most recent outreach touchpoint |
| `next_action_date` | Date | Scheduled next touchpoint |
| `assigned_ae` | String | Account Executive responsible |
| `assigned_csm` | String | Customer Success Manager (post-onboarding) |
| `notes` | Text | Free-form notes and activity log |
| `created_at` | Timestamp | Record creation date |
| `updated_at` | Timestamp | Last modification timestamp |

### Status Stages

Programs move through a linear pipeline with defined entry/exit criteria:

```
Uncontacted → Outreach → Demo Scheduled → Trial Active → Onboarded → Churned
```

| Stage | Code | Description | Owner |
|-------|------|-------------|-------|
| **Uncontacted** | `UNCONTACTED` | Program exists in registry, no outreach attempted | Sales Team |
| **Outreach** | `OUTREACH` | Initial contact made — email, call, or referral sent | Account Executive |
| **Demo Scheduled** | `DEMO_SCHEDULED` | Decision-maker has agreed to a product demonstration | AE + Solutions Engineer |
| **Trial Active** | `TRIAL_ACTIVE` | Pilot account created, data loaded, users invited | Customer Success Manager |
| **Onboarded** | `ONBOARDED` | Contract signed, payment processed, fully active | Customer Success Manager |
| **Churned** | `CHURNED` | Previously active, contract expired or cancelled | AE (win-back) |

### Priority Tiers

Tiers determine resource allocation, outreach cadence, and AE assignment density:

| Tier | Segment | Description | AE Ratio | Outreach Cadence |
|------|---------|-------------|----------|------------------|
| **A** | Power 4 Basketball | SEC, Big Ten, ACC, Big 12 basketball programs | 1:8 | Weekly |
| **B** | High-Major Basketball | AAC, Mountain West, WCC, A-10, MVC basketball | 1:12 | Bi-weekly |
| **C** | Mid-Major D1 Basketball | All remaining D1 conference basketball programs | 1:20 | Monthly |
| **D** | D2/D3/NAIA Basketball | Lower division basketball programs | 1:50 | Quarterly |
| **E** | Other Sports Expansion | Football, baseball, softball, etc. at any division | 1:30 | As capacity allows |

---

## Views

The Battle Board is composed of five primary views, each designed for a specific operational context.

### 1. Conference Heat Map

**Purpose:** Geographic and organizational visualization of coverage density across all conferences.

- Color-coded conference regions: Red (0% coverage) to Green (75%+ coverage)
- Filterable by division, sport, priority tier, and status
- Click-through to conference detail view
- Real-time update as programs move through pipeline
- Default view shows basketball-only coverage

### 2. Division Breakdown

**Purpose:** Top-level progress tracking across D1/D2/D3/NAIA.

- Progress bars for each division showing percentage onboarded
- D1 sub-breakdown: Power 4 vs High-Major vs Mid-Major
- Program counts per stage within each division
- Revenue potential and actual revenue comparison
- Trend lines showing week-over-week progress

### 3. Sport Drilldown

**Purpose:** Multi-sport coverage analysis within onboarded programs.

- Basketball as primary column (always visible)
- Expansion sports shown per program once basketball is active
- Cross-sell opportunity identification
- Sport-specific onboarding checklists
- Revenue per sport per program

### 4. Pipeline Funnel

**Purpose:** Sales pipeline health and velocity metrics.

- Stage-by-stage program counts with conversion rates
- Average time in each stage (target vs actual)
- Bottleneck identification (stages with longest dwell time)
- Revenue projection based on current pipeline
- AE-level pipeline breakdown
- Week-over-week movement tracking

### 5. School Detail

**Purpose:** Deep-dive into individual program status and history.

- Full program entity data display
- Activity timeline (every touchpoint logged)
- Contact history with communication records
- Contract details (for onboarded programs)
- Usage metrics (for trial/active programs)
- Associated sports programs at same institution
- Conference context and peer comparison

---

## Key Performance Indicators (KPIs)

### Coverage Metrics

| KPI | Definition | Target |
|-----|-----------|--------|
| Total Programs Targeted | Programs in registry across all tiers | 1,300+ |
| Overall Coverage % | (Onboarded / Total Targeted) x 100 | 15% Year 1 |
| Power 4 Coverage % | Onboarded Power 4 basketball programs | 50% Year 1 |
| High-Major Coverage % | Onboarded high-major basketball programs | 30% Year 1 |
| Conference Penetration | Conferences with 50%+ schools onboarded | 8 conferences Year 1 |

### Pipeline Metrics

| KPI | Definition | Target |
|-----|-----------|--------|
| Pipeline Velocity | Programs moving through full funnel per month | 15/month |
| Stage Conversion Rate | % moving from one stage to the next | 40%+ per stage |
| Demo-to-Trial Rate | % of demos converting to active trials | 50%+ |
| Trial-to-Onboard Rate | % of trials converting to paying customers | 65%+ |
| Average Sales Cycle | Days from Outreach to Onboarded | <45 days |

### Revenue Metrics

| KPI | Definition | Target |
|-----|-----------|--------|
| Revenue Per Active Program | Annual contract value per onboarded program | $12,000+ (Tier A) |
| Pipeline Revenue | Projected revenue from current pipeline | Tracked weekly |
| Monthly Recurring Revenue | Total MRR from all active programs | Growth target TBD |
| Churn Rate | % of onboarded programs lost per quarter | <5% |
| Win-Back Rate | % of churned programs re-activated | 20%+ |

---

## Integration Architecture

### Data Sources

```
+------------------+       +------------------+       +------------------+
|   SportsRadar    |  -->  |   NIL Optic      |  -->  |   Battle Board   |
|   Data Feed      |       |   Core Platform  |       |   Admin View     |
+------------------+       +------------------+       +------------------+
        |                          |                          |
   Team rosters             Player valuations           Pipeline tracking
   Conference data          NIL analytics               Coverage metrics
   Division structure       Compliance tools            Revenue forecasting
   Schedule data            Transfer portal             AE assignments
```

### SportsRadar Integration

- **Team Registry:** Feeds school names, conference affiliations, division classifications
- **Roster Data:** Auto-populates player rosters during trial/onboarding
- **Conference Standings:** Provides real-time competitive context
- **Schedule Data:** Powers tournament and season tracking features
- **Update Frequency:** Daily sync for rosters, real-time for scores/standings

### Admin Access

The Battle Board is an admin-level view accessible at `/admin/battle-board`:

- **Super Admin:** Full read/write access to all programs, all tiers
- **Regional Manager:** Read/write for assigned conferences and divisions
- **Account Executive:** Read/write for assigned programs only
- **Viewer:** Read-only access for executive reporting

---

## Basketball-First Strategy

### Phase 1: Power 4 Blitz (Q1-Q2 2026)
- Target all 67 Power 4 basketball programs simultaneously
- Assign dedicated AEs to SEC, Big Ten, ACC, Big 12
- Goal: 30+ demos scheduled, 15+ trials active

### Phase 2: High-Major Expansion (Q2-Q3 2026)
- Activate outreach to AAC, Mountain West, WCC, A-10, MVC
- Leverage Power 4 case studies for credibility
- Goal: 25+ demos scheduled across high-major conferences

### Phase 3: Mid-Major Saturation (Q3-Q4 2026)
- Systematic outreach to remaining D1 conferences
- Introduce self-serve onboarding for lower-touch programs
- Goal: 50+ mid-major programs in pipeline

### Phase 4: Division Expansion (2027)
- D2 and D3 entry with scaled/self-serve product tier
- NAIA exploration for long-term market completeness
- Multi-sport cross-sell within onboarded institutions

---

## Related Documents

- [NCAA Basketball Program Registry](./ncaa-basketball-registry.md) — Master list of all target programs
- [Conference Tracker Design Spec](./conference-tracker.md) — UI/UX specifications for conference views
- [Onboarding Pipeline](./onboarding-pipeline.md) — Detailed pipeline stage documentation
- [Design System](../../../design-system/) — NIL Optic component library
- [Design Tokens](../../design/design-tokens.md) — Color, typography, spacing tokens

---

## Changelog

| Date | Author | Change |
|------|--------|--------|
| 2026-03-04 | Operations | Initial Battle Board specification created |

---

*NIL Optic — The operating system for college athletics NIL management.*
