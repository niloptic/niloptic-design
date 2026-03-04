# Internal Operations Templates

Last updated: 2026-03-04

---

## Overview

Internal operations templates define the detailed view layouts for admin-facing operational surfaces. These views power the day-to-day management of data pipelines, program coverage tracking, prediction governance, email operations, and presentation tooling. All views render within the Admin dashboard shell (`/admin`) and are restricted to `admin` and `designer` role scopes.

**Design system alignment:** Dark mode default, Inter (UI) + JetBrains Mono (data), Red `#DC2626` accent, WCAG AAA contrast compliance.

---

## Sync Operations Dashboard

Route: `/admin/sync`
Purpose: Centralized management of all data sync jobs executed through the external `/sync-server`. Provides job-level cards, live streaming progress, schedule configuration, and result inspection.

### Full Layout

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > SYNC OPERATIONS                                             │
│                                                                     │
│  Syncs run in /sync-server with live progress updates               │
│  and scheduled automation.                                          │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  AUTOMATION SCHEDULE                                                 │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                                                             │   │
│  │  ┌──────────────┐  ┌───────────────┐  ┌────────────────┐  │   │
│  │  │ Enabled      │  │ Run Time UTC  │  │ Range Days     │  │   │
│  │  │ [Yes ▼]      │  │ [03:00]       │  │ [1]            │  │   │
│  │  └──────────────┘  └───────────────┘  └────────────────┘  │   │
│  │                                                             │   │
│  │  ┌──────────────────────┐                                   │   │
│  │  │ Run Predictions After│                                   │   │
│  │  │ [Yes ▼]              │                                   │   │
│  │  └──────────────────────┘                                   │   │
│  │                                                             │   │
│  │  Last automated run: 2026-03-04 03:00 UTC                   │   │
│  │  Next scheduled run: 2026-03-05 03:00 UTC                   │   │
│  │                                                             │   │
│  │  [Save Schedule]                                            │   │
│  │                                                             │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  SYNC JOB CARDS                                                      │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌─────────────────────────────┐ ┌─────────────────────────────┐   │
│  │ ┌─ DIVISION I GAMES ──────┐│ │ ┌─ NET RANKINGS ───────────┐│   │
│  │ │                         ││ │ │                           ││   │
│  │ │ Status:  [✓ Completed]  ││ │ │ Status:  [✓ Completed]   ││   │
│  │ │ Last:    Mar 4, 05:14   ││ │ │ Last:    Mar 4, 04:42    ││   │
│  │ │ Duration: 3m 42s        ││ │ │ Duration: 1m 18s         ││   │
│  │ │ Records: 48 synced      ││ │ │ Records: 362 updated     ││   │
│  │ │                         ││ │ │                           ││   │
│  │ │ Parameters:             ││ │ │ Parameters:              ││   │
│  │ │ Start: [2026-03-03]     ││ │ │ Year: [2025]             ││   │
│  │ │ End:   [2026-03-04]     ││ │ │ Type: [REG ▼]            ││   │
│  │ │                         ││ │ │                           ││   │
│  │ │ [Sync Division I Games] ││ │ │ [Sync NET Rankings]      ││   │
│  │ └─────────────────────────┘│ │ └───────────────────────────┘│   │
│  └─────────────────────────────┘ └─────────────────────────────┘   │
│                                                                     │
│  ┌─────────────────────────────┐ ┌─────────────────────────────┐   │
│  │ ┌─ CONFERENCE LEADERS ────┐│ │ ┌─ STANDINGS ──────────────┐│   │
│  │ │                         ││ │ │                           ││   │
│  │ │ Status:  [✓ Completed]  ││ │ │ Status:  [✓ Completed]   ││   │
│  │ │ Last:    Mar 4, 04:38   ││ │ │ Last:    Mar 4, 03:48    ││   │
│  │ │ Duration: 2m 05s        ││ │ │ Duration: 1m 52s         ││   │
│  │ │ Records: 156 synced     ││ │ │ Records: 362 updated     ││   │
│  │ │                         ││ │ │                           ││   │
│  │ │ Parameters:             ││ │ │ Parameters:              ││   │
│  │ │ Year: [2025]            ││ │ │ Year: [2025]             ││   │
│  │ │ Type: [REG ▼]           ││ │ │ Type: [REG ▼]            ││   │
│  │ │                         ││ │ │                           ││   │
│  │ │ [Sync Conference Ldrs]  ││ │ │ [Sync Standings]         ││   │
│  │ └─────────────────────────┘│ │ └───────────────────────────┘│   │
│  └─────────────────────────────┘ └─────────────────────────────┘   │
│                                                                     │
│  ┌─────────────────────────────┐ ┌─────────────────────────────┐   │
│  │ ┌─ TRANSFER PORTAL ──────┐│ │ ┌─ VIEWS SYNC ─────────────┐│   │
│  │ │                         ││ │ │                           ││   │
│  │ │ Status:  [✓ Completed]  ││ │ │ Status:  [✓ Completed]   ││   │
│  │ │ Last:    Mar 3, 22:10   ││ │ │ Last:    Mar 4, 05:18    ││   │
│  │ │ Duration: 4m 31s        ││ │ │ Duration: 0m 48s         ││   │
│  │ │ Records: 214 persisted  ││ │ │                           ││   │
│  │ │                         ││ │ │ Refreshes dashboard       ││   │
│  │ │ Pulls latest transfer   ││ │ │ materialized views for    ││   │
│  │ │ portal feed and         ││ │ │ low-latency read          ││   │
│  │ │ persists to sync tables.││ │ │ performance.              ││   │
│  │ │                         ││ │ │                           ││   │
│  │ │ [Sync Transfer Portal]  ││ │ │ [Refresh Views]          ││   │
│  │ └─────────────────────────┘│ │ └───────────────────────────┘│   │
│  └─────────────────────────────┘ └─────────────────────────────┘   │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  FULL SYNC + PREDICTIONS (full-width card)                           │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Status:  [◉ Running]                                        │   │
│  │ Stage:   Syncing NET Rankings                               │   │
│  │ Progress: 142 / 362                                         │   │
│  │                                                             │   │
│  │ ████████████████████░░░░░░░░░░░░░░░░░░░░░░░░░░  39.2%     │   │
│  │                                                             │   │
│  │ Live Stage Log:                                             │   │
│  │ ┌─────────────────────────────────────────────────────┐    │   │
│  │ │ 05:26:14  142/362  Syncing NET Rankings...          │    │   │
│  │ │ 05:24:52   48/48   Division I games synced          │    │   │
│  │ │ 05:21:10    -/-    Starting full sync pipeline...   │    │   │
│  │ └─────────────────────────────────────────────────────┘    │   │
│  │ (auto-scrolling, max 15 visible entries)                    │   │
│  │                                                             │   │
│  │ [Run Full Sync + Predictions]  ← disabled while running    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  RESULT OUTPUT (rendered after job completion)                       │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ {                                                JetBrains  │   │
│  │   "games_synced": 48,                            Mono 12px  │   │
│  │   "rankings_updated": 362,                                  │   │
│  │   "leaders_updated": 156,                                   │   │
│  │   "standings_updated": 362,                                 │   │
│  │   "predictions_generated": 4218,                            │   │
│  │   "duration_ms": 184200                                     │   │
│  │ }                                                           │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Job Card Anatomy

Each sync job card follows a consistent structure:

```
┌─ JOB TITLE ──────────────────┐
│                               │
│  Status:   [Badge]            │  ← color-coded status badge
│  Last:     Timestamp          │  ← JetBrains Mono, relative or absolute
│  Duration: Xm XXs            │  ← JetBrains Mono
│  Records:  ###/### or ###     │  ← JetBrains Mono
│                               │
│  Parameters:                  │  ← job-specific input controls
│  [input fields]               │
│                               │
│  [Action Button]              │  ← brand-red primary button
│                               │
└───────────────────────────────┘
```

### Status Badge Specifications

| Status    | Background         | Text Color | Icon      | Border            |
|-----------|--------------------|------------|-----------|-------------------|
| Completed | `#22C55E/10`       | `#22C55E`  | CheckCircle | `#22C55E/20`    |
| Running   | `#3B82F6/10`       | `#3B82F6`  | Loader    | `#3B82F6/20`      |
| Failed    | `#EF4444/10`       | `#EF4444`  | XCircle   | `#EF4444/20`      |
| Queued    | `#71717A/10`       | `#71717A`  | Clock     | `#71717A/20`      |
| Stale     | `#F59E0B/10`       | `#F59E0B`  | AlertTriangle | `#F59E0B/20` |

### Progress Stream Behavior

- Uses Server-Sent Events (SSE) via `EventSource` at `/api/admin/sync/jobs/{jobId}/events`
- Each event carries: `stage`, `message`, `current`, `total`, `percent`
- Stage log auto-scrolls showing last 15 entries
- Terminal events (`complete`, `error`) close the SSE connection
- Polling fallback at 2.5s interval checks terminal job status via REST
- Progress bar uses `role="progressbar"` with `aria-valuenow` and `aria-valuemax`

### Schedule Configuration

| Field                   | Type    | Default  | Persistence              |
|-------------------------|---------|----------|--------------------------|
| Enabled                 | Boolean | `false`  | Supabase automation table |
| Run Time (UTC)          | Time    | `03:00`  | Supabase automation table |
| Division Range Days     | Number  | `1`      | Supabase automation table |
| Run Predictions After   | Boolean | `true`   | Supabase automation table |

---

## Battle Board Admin View

Route: Rendered as panel within `/admin` home or dedicated `/admin/battle-board`
Purpose: Strategic war room for tracking NCAA basketball program onboarding across all conferences. Power 4 conferences are the primary focus with expansion through high-major, mid-major, D2/D3/NAIA tiers.

### Full Layout

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > BATTLE BOARD                                                │
│                                                                     │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐      │
│  │ PROGRAMS   │ │ POWER 4    │ │ PIPELINE   │ │ PROJECTED  │      │
│  │ TARGETED   │ │ COVERAGE   │ │ VELOCITY   │ │ REVENUE    │      │
│  │            │ │            │ │            │ │            │      │
│  │ 1,312      │ │ 52%        │ │ 18/mo      │ │ $1.4M      │      │
│  │ All tiers  │ │ 35/67      │ │ ▲ +4 MoM   │ │ ARR pipe   │      │
│  └────────────┘ └────────────┘ └────────────┘ └────────────┘      │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  CONFERENCE COVERAGE HEAT MAP                                        │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  Filter: [● Basketball] [○ Football] [○ All]   Tier: [All ▼]       │
│                                                                     │
│  TIER A — POWER 4                                                   │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │ SEC          ████████████████████████████████░░░░░░  75%      │ │
│  │              12/16 programs    ▲ +2 (30d)    $192K ARR        │ │
│  │                                                                │ │
│  │ Big Ten      ████████████████████████░░░░░░░░░░░░░░  61%      │ │
│  │              11/18 programs    ▲ +3 (30d)    $132K ARR        │ │
│  │                                                                │ │
│  │ ACC          ████████████████░░░░░░░░░░░░░░░░░░░░░░  41%      │ │
│  │              7/17 programs     ▲ +1 (30d)    $84K ARR         │ │
│  │                                                                │ │
│  │ Big 12       ██████████████░░░░░░░░░░░░░░░░░░░░░░░░  31%      │ │
│  │              5/16 programs     — (30d)       $60K ARR         │ │
│  │                                                                │ │
│  │ Power 4 Total: 35/67 programs  |  52% coverage  |  $468K ARR │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  TIER B — HIGH MAJOR                                                │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │ American     ██████████████████░░░░░░░░░░░░░░░░░░░░  36%      │ │
│  │              5/14 programs                                     │ │
│  │                                                                │ │
│  │ Mtn West     ████████████████░░░░░░░░░░░░░░░░░░░░░░  33%      │ │
│  │              4/12 programs                                     │ │
│  │                                                                │ │
│  │ WCC          █████████████░░░░░░░░░░░░░░░░░░░░░░░░░  27%      │ │
│  │              3/11 programs                                     │ │
│  │                                                                │ │
│  │ MVC          ████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  17%      │ │
│  │              2/12 programs                                     │ │
│  │                                                                │ │
│  │ High Major Total: 14/49 programs  |  29% coverage             │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  PIPELINE FUNNEL                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │                                                                │ │
│  │ Uncontacted  ████████████████████████████████████████  812     │ │
│  │              Target pool                                       │ │
│  │                                                                │ │
│  │ Outreach     ██████████████████████████░░░░░░░░░░░░░  286     │ │
│  │              35% of pool      Avg: 4d in stage                │ │
│  │                                                                │ │
│  │ Demo Sched   ████████████████░░░░░░░░░░░░░░░░░░░░░░   98     │ │
│  │              34% from outreach     Avg: 7d in stage           │ │
│  │                                                                │ │
│  │ Trial Active ████████████░░░░░░░░░░░░░░░░░░░░░░░░░░   62     │ │
│  │              63% from demo         Avg: 14d in stage          │ │
│  │                                                                │ │
│  │ Onboarded    █████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  142     │ │
│  │              68% from trial   Avg cycle: 38d                  │ │
│  │                                                                │ │
│  │ Churned      █░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░   12     │ │
│  │              Win-back target: 25%                              │ │
│  │                                                                │ │
│  │ Conversion: Outreach→Demo 34%  Demo→Trial 63%  Trial→Paid 68%│ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  PROGRAM STATUS TABLE                                                │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  [Search programs ________] [Conference ▼] [Tier ▼] [Status ▼]     │
│                                                                     │
│  ┌─────────────┬──────┬──────┬──────────┬────────┬──────┬────────┐ │
│  │ PROGRAM     │ CONF │ TIER │ STATUS   │ AE     │ LAST │ NEXT   │ │
│  ├─────────────┼──────┼──────┼──────────┼────────┼──────┼────────┤ │
│  │ Kentucky    │ SEC  │ A    │ ● Active │ M.Chen │ 1d   │ --     │ │
│  │ Duke        │ ACC  │ A    │ ● Trial  │ K.Patel│ 3d   │ Mar 8  │ │
│  │ Gonzaga     │ WCC  │ B    │ ◐ Demo   │ J.Lee  │ 5d   │ Mar 6  │ │
│  │ Memphis     │ AAC  │ B    │ ○ Outreach│ T.Wms │ 7d   │ Mar 10 │ │
│  │ Loyola-Chi  │ A-10 │ C    │ ○ Unctd  │ --     │ --   │ --     │ │
│  │ [more rows...]                                                 │ │
│  └─────────────┴──────┴──────┴──────────┴────────┴──────┴────────┘ │
│                                                                     │
│  Showing 1-25 of 1,312    [< Prev]  [1] [2] [3] ... [53]  [Next >]│
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  AE PERFORMANCE & REVENUE FORECAST                                   │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌─────────────────────────────────┐ ┌─────────────────────────┐   │
│  │ AE PERFORMANCE                  │ │ REVENUE FORECAST        │   │
│  │                                 │ │                         │   │
│  │ M. Chen    │ 42 accts │ $504K  │ │ Current ARR:   $468K    │   │
│  │ K. Patel   │ 38 accts │ $456K  │ │ Pipeline ARR:  $1.4M    │   │
│  │ J. Lee     │ 35 accts │ $420K  │ │ 90d Forecast:  $780K    │   │
│  │ T. Williams│ 27 accts │ $324K  │ │ Close rate:    68%      │   │
│  │                                 │ │                         │   │
│  │ Total accounts: 142             │ │ MRR:  $39K              │   │
│  │ Avg per AE: 35.5               │ │ Target MRR: $100K       │   │
│  └─────────────────────────────────┘ └─────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Coverage Bar Color Scale

| Coverage % | Bar Fill Color            | Semantic               |
|------------|---------------------------|------------------------|
| 0-19%      | `#EF4444` (red)           | Critical gap           |
| 20-39%     | `#F59E0B` (amber)         | Below target           |
| 40-59%     | `#FACC15` (yellow)        | Approaching target     |
| 60-79%     | `#22C55E` (green)         | On target              |
| 80-100%    | `#22C55E` (green, bright) | Exceeding target       |

### Priority Tier Definitions

| Tier | Segment                | AE Ratio | Outreach Cadence | Icon Color      |
|------|------------------------|----------|------------------|-----------------|
| A    | Power 4 Basketball     | 1:8      | Weekly           | `#DC2626` (red) |
| B    | High-Major Basketball  | 1:12     | Bi-weekly        | `#F97316` (orange)|
| C    | Mid-Major D1           | 1:20     | Monthly          | `#FACC15` (yellow)|
| D    | D2/D3/NAIA Basketball  | 1:50     | Quarterly        | `#71717A` (zinc) |
| E    | Other Sports Expansion | 1:30     | As capacity allows| `#3F3F46` (zinc-700)|

### Pipeline Status Badges

| Status        | Code               | Badge Style                        |
|---------------|--------------------|------------------------------------|
| Uncontacted   | `UNCONTACTED`      | Zinc outline, no fill              |
| Outreach      | `OUTREACH`         | Blue outline, light blue fill      |
| Demo Scheduled| `DEMO_SCHEDULED`   | Amber outline, light amber fill    |
| Trial Active  | `TRIAL_ACTIVE`     | Green outline, light green fill    |
| Onboarded     | `ONBOARDED`        | Green solid, white text            |
| Churned       | `CHURNED`          | Red outline, light red fill        |

---

## Predictions Admin Workspace

Route: `/admin/predictions`
Purpose: Prediction model governance, run management, accuracy monitoring, confidence distribution analysis, and model drift detection.

### Full Layout

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > PREDICTIONS WORKSPACE                                       │
│                                                                     │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐      │
│  │ MAE        │ │ DIRECTIONAL│ │ CONFIDENCE │ │ BIAS       │      │
│  │            │ │ ACCURACY   │ │ CALIBR.    │ │            │      │
│  │ 12.4%      │ │ 83.2%      │ │ 87.1%      │ │ +1.8%      │      │
│  │ Tgt: <15%  │ │ Tgt: 80%+  │ │ Tgt: 85%+  │ │ Tgt: <3%   │      │
│  │ [✓ Pass]   │ │ [✓ Pass]   │ │ [✓ Pass]   │ │ [✓ Pass]   │      │
│  └────────────┘ └────────────┘ └────────────┘ └────────────┘      │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  RUN CONTROLS                                                        │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                                                             │   │
│  │ Last Run:         Mar 4, 2026 03:14 UTC                     │   │
│  │ Duration:         12m 38s                                   │   │
│  │ Athletes Scored:  4,218                                     │   │
│  │ Model Version:    v2.4.1                                    │   │
│  │                                                             │   │
│  │ ┌────────────────────┐ ┌────────────────────────┐          │   │
│  │ │ Season Year        │ │ Season Type            │          │   │
│  │ │ [2025]             │ │ [Regular Season ▼]     │          │   │
│  │ └────────────────────┘ └────────────────────────┘          │   │
│  │                                                             │   │
│  │ [Trigger Prediction Run]          [View Run History]        │   │
│  │                                                             │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  RESULTS PREVIEW                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌──────────────────────────────┐ ┌────────────────────────────┐   │
│  │ CONFIDENCE DISTRIBUTION      │ │ ACCURACY TREND (30d)       │   │
│  │                              │ │                            │   │
│  │ 90-100%  ████████████████ 42%│ │ 90%─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │   │
│  │ 80-89%   ████████████░░░ 31% │ │      ╱‾‾╲    ╱‾╲         │   │
│  │ 70-79%   ████████░░░░░░ 18%  │ │ 85%─ ──── ── ── ── ── ─  │   │
│  │ 60-69%   ████░░░░░░░░░  7%   │ │   ──╱     ╲╱    ╲──      │   │
│  │ <60%     █░░░░░░░░░░░░  2%   │ │ 80%                      │   │
│  │                              │ │                            │   │
│  │ Median: 88.4%                │ │   W1   W2   W3   W4  Now  │   │
│  │ Mean:   84.2%                │ │                            │   │
│  │ Std Dev: 9.1%                │ │ ─ MAE  ── Target           │   │
│  └──────────────────────────────┘ └────────────────────────────┘   │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  MODEL DRIFT INDICATORS                                              │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌───────────┬──────────┬──────────┬──────────┬─────────────────┐  │
│  │ SPORT     │ 7d MAE   │ 30d MAE  │ DRIFT    │ STATUS          │  │
│  ├───────────┼──────────┼──────────┼──────────┼─────────────────┤  │
│  │ Basketball│ 11.8%    │ 12.4%    │ -0.6%    │ [✓ Stable]      │  │
│  │ Football  │ 14.2%    │ 13.8%    │ +0.4%    │ [✓ Stable]      │  │
│  │ Baseball  │ 16.1%    │ 14.9%    │ +1.2%    │ [⚠ Monitor]     │  │
│  │ Soccer    │ 15.4%    │ 15.0%    │ +0.4%    │ [✓ Stable]      │  │
│  │ Softball  │ 17.2%    │ 16.8%    │ +0.4%    │ [✓ Stable]      │  │
│  └───────────┴──────────┴──────────┴──────────┴─────────────────┘  │
│                                                                     │
│  Drift threshold: ±1.0% = Stable, ±1.0-2.0% = Monitor, >2.0% = Alert│
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  HISTORICAL ACCURACY                                                 │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ PREDICTION ACCURACY BY WEEK (last 12 weeks)                 │   │
│  │                                                             │   │
│  │ 95% ─┤                                                      │   │
│  │ 90% ─┤       ■                     ■                        │   │
│  │ 85% ─┤  ■  ■   ■  ■  ■  ■  ■  ■     ■  ■  ■              │   │
│  │ 80% ─┤──────────────────── target line ──────────────       │   │
│  │ 75% ─┤                                                      │   │
│  │      └──┬──┬──┬──┬──┬──┬──┬──┬──┬──┬──┬──┬──              │   │
│  │         W1 W2 W3 W4 W5 W6 W7 W8 W9 W10W11W12              │   │
│  │                                                             │   │
│  │ Avg: 87.4%    Min: 84.1% (W3)    Max: 91.2% (W7)          │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  FAN-LITE PREDICTION SCOPE                                          │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Limited users (fan persona) see only top-3 valuation        │   │
│  │ windows. Verify scope enforcement:                          │   │
│  │                                                             │   │
│  │ Fan prediction depth: [Top 3 ▼]                             │   │
│  │ Upgrade chip visible: [✓ Yes]                               │   │
│  │ Full access requires: Organization membership               │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Accuracy Metric Definitions

| Metric                  | Calculation                                            | Target   | Font           |
|-------------------------|--------------------------------------------------------|----------|----------------|
| Mean Absolute Error     | avg(abs(predicted - actual)) / avg(valuation) * 100    | < 15%    | JetBrains Mono |
| Directional Accuracy    | correct_direction_count / total_predictions * 100      | 80%+     | JetBrains Mono |
| Confidence Calibration  | actuals_in_CI / total_predictions * 100                | 85%+ (90% CI) | JetBrains Mono |
| Bias Check              | avg(predicted - actual) / avg(valuation) * 100         | < 3%     | JetBrains Mono |

### Drift Status Thresholds

| Drift Range     | Status    | Badge Color                    | Action              |
|-----------------|-----------|--------------------------------|---------------------|
| < 1.0%          | Stable    | `--status-success` (green)     | No action needed    |
| 1.0% - 2.0%    | Monitor   | `--status-warning` (amber)     | Increase monitoring |
| > 2.0%          | Alert     | `--status-error` (red)         | Recalibration needed|

---

## Email Operations

Route: `/admin/invite-email-preview`
Purpose: Preview branded invite email templates by scope (Org, Program, Athlete), manage SendGrid test-send workflows, and track delivery metrics.

### Full Layout

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > EMAIL OPERATIONS                                            │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  TEMPLATE PREVIEW                                                    │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  Scope: [● Org] [○ Program] [○ Athlete]                             │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                                                             │   │
│  │  ┌───────────────────────────────────────────────────────┐  │   │
│  │  │                                                       │  │   │
│  │  │              ┌───────────────┐                        │  │   │
│  │  │              │  NIL OPTIC    │  Logo, 120px           │  │   │
│  │  │              │  ████████████ │                        │  │   │
│  │  │              └───────────────┘                        │  │   │
│  │  │                                                       │  │   │
│  │  │  Hello {first_name},                                  │  │   │
│  │  │                                                       │  │   │
│  │  │  You've been invited to join                          │  │   │
│  │  │  {organization_name} on NIL Optic                     │  │   │
│  │  │  as {role_label}.                                     │  │   │
│  │  │                                                       │  │   │
│  │  │  NIL Optic is the intelligence platform               │  │   │
│  │  │  for college athletics NIL management.                │  │   │
│  │  │                                                       │  │   │
│  │  │         ┌──────────────────────┐                      │  │   │
│  │  │         │  ACCEPT INVITATION   │  ← #DC2626 bg       │  │   │
│  │  │         │                      │    white text        │  │   │
│  │  │         └──────────────────────┘    radius-sm         │  │   │
│  │  │                                                       │  │   │
│  │  │  This invitation expires in 7 days.                   │  │   │
│  │  │  If you didn't expect this, ignore                    │  │   │
│  │  │  this email.                                          │  │   │
│  │  │                                                       │  │   │
│  │  │  ─────────────────────────────────                    │  │   │
│  │  │  NIL Optic | Support@niloptic.com                     │  │   │
│  │  │  The intelligence platform for NIL.                   │  │   │
│  │  │                                                       │  │   │
│  │  └───────────────────────────────────────────────────────┘  │   │
│  │                                                             │   │
│  │  [Refresh Preview]                                          │   │
│  │                                                             │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  TEST SEND CONTROLS                                                  │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                                                             │   │
│  │ Recipient Email:  [________________________________]        │   │
│  │ Template Scope:   [Org ▼]                                   │   │
│  │ Org Name Preview: [SEC University__________________]        │   │
│  │ Role Preview:     [Athletic Director ▼]                     │   │
│  │                                                             │   │
│  │ [Send Test Email]                                           │   │
│  │                                                             │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  DELIVERY METRICS                                                    │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐      │
│  │ SENT       │ │ DELIVERED  │ │ OPENED     │ │ CLICKED    │      │
│  │            │ │            │ │            │ │            │      │
│  │ 847        │ │ 839        │ │ 612        │ │ 428        │      │
│  │ All time   │ │ 99.1%      │ │ 73.0%      │ │ 51.0%      │      │
│  └────────────┘ └────────────┘ └────────────┘ └────────────┘      │
│                                                                     │
│  RECENT TEST SENDS                                                  │
│  ┌────────┬──────────────────┬──────────┬────────┬────────────┐    │
│  │ STATUS │ RECIPIENT        │ SCOPE    │ SENT   │ RESULT     │    │
│  ├────────┼──────────────────┼──────────┼────────┼────────────┤    │
│  │ ✓      │ test@niloptic.com│ Org      │ 2h ago │ Delivered  │    │
│  │ ✓      │ dev@niloptic.com │ Program  │ 1d ago │ Delivered  │    │
│  │ ✗      │ qa@niloptic.com  │ Athlete  │ 2d ago │ Bounced    │    │
│  │ ✓      │ pm@niloptic.com  │ Org      │ 3d ago │ Delivered  │    │
│  └────────┴──────────────────┴──────────┴────────┴────────────┘    │
│                                                                     │
│  TEMPLATE VERSION MANAGEMENT                                        │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Active Version: v3.1    Last Updated: Mar 1, 2026           │   │
│  │                                                             │   │
│  │ v3.1  Mar 1   Added role-specific body copy     [Active]   │   │
│  │ v3.0  Feb 15  Redesigned CTA button             [Archive]  │   │
│  │ v2.8  Jan 20  Updated logo placement            [Archive]  │   │
│  │                                                             │   │
│  │ [Revert to Previous]                                        │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Email Template Variables

| Variable             | Source             | Scope           |
|----------------------|--------------------|-----------------|
| `{first_name}`       | Invite metadata    | All             |
| `{organization_name}`| Organization table | Org, Program    |
| `{program_name}`     | Program table      | Program         |
| `{role_label}`       | Role taxonomy      | All             |
| `{invite_link}`      | Generated URL      | All             |
| `{expiry_days}`      | Config (default 7) | All             |

### Delivery Status Colors

| Status    | Color Token              | Icon         |
|-----------|--------------------------|--------------|
| Delivered | `--status-success`       | CheckCircle  |
| Bounced   | `--status-error`         | XCircle      |
| Pending   | `--status-info`          | Clock        |
| Failed    | `--status-error`         | AlertTriangle|

---

## Presentation Tools

Route: `/admin/presentations`
Purpose: Admin workspace for creating, editing, and exporting presentations. Supports slide management with 16:9 dark-theme default format.

### Full Layout

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > PRESENTATION TOOLS                                          │
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  PRESENTATIONS LIBRARY                                               │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  [Search presentations ___________]            [+ New Presentation] │
│                                                                     │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌────────────┐│
│  │ ┌──────────┐ │ │ ┌──────────┐ │ │ ┌──────────┐ │ │ ┌────────┐ ││
│  │ │          │ │ │ │          │ │ │ │          │ │ │ │        │ ││
│  │ │  Thumb   │ │ │ │  Thumb   │ │ │ │  Thumb   │ │ │ │ Thumb  │ ││
│  │ │  16:9    │ │ │ │  16:9    │ │ │ │  16:9    │ │ │ │ 16:9   │ ││
│  │ │          │ │ │ │          │ │ │ │          │ │ │ │        │ ││
│  │ └──────────┘ │ │ └──────────┘ │ │ └──────────┘ │ │ └────────┘ ││
│  │              │ │              │ │              │ │            ││
│  │ Q1 Pitch    │ │ SEC Demo    │ │ Board Update │ │ Investor   ││
│  │ Deck         │ │ Package     │ │              │ │ Deck       ││
│  │ 12 slides   │ │ 8 slides    │ │ 6 slides     │ │ 18 slides  ││
│  │ Mar 1, 2026 │ │ Feb 28      │ │ Feb 15       │ │ Jan 30     ││
│  │              │ │              │ │              │ │            ││
│  │ [Edit][Dup] │ │ [Edit][Dup] │ │ [Edit][Dup] │ │ [Edit][Dup]││
│  │ [Export]    │ │ [Export]    │ │ [Export]    │ │ [Export]   ││
│  └──────────────┘ └──────────────┘ └──────────────┘ └────────────┘│
│                                                                     │
│  ═══════════════════════════════════════════════════════════════════ │
│  PRESENTATION EDITOR (active when editing a deck)                    │
│  ═══════════════════════════════════════════════════════════════════ │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                                                             │   │
│  │ Q1 Pitch Deck            Slide 3 of 12        [Close ×]   │   │
│  │                                                             │   │
│  │ ┌──────────┐  ┌──────────────────────────────────────────┐ │   │
│  │ │ 1  [   ] │  │                                          │ │   │
│  │ │          │  │                                          │ │   │
│  │ │ 2  [   ] │  │         SLIDE CANVAS                     │ │   │
│  │ │          │  │                                          │ │   │
│  │ │ 3* [   ] │  │         16:9 aspect ratio                │ │   │
│  │ │          │  │         Dark theme (--surface-canvas)     │ │   │
│  │ │ 4  [   ] │  │         Brand red accent (#DC2626)       │ │   │
│  │ │          │  │                                          │ │   │
│  │ │ 5  [   ] │  │         Content area:                    │ │   │
│  │ │          │  │         - Text blocks                    │ │   │
│  │ │ 6  [   ] │  │         - Charts / data viz             │ │   │
│  │ │          │  │         - Image placeholders             │ │   │
│  │ │ ...      │  │         - Speaker notes (below fold)     │ │   │
│  │ │          │  │                                          │ │   │
│  │ │ 12 [   ] │  │                                          │ │   │
│  │ └──────────┘  └──────────────────────────────────────────┘ │   │
│  │                                                             │   │
│  │ Slide Actions:                                              │   │
│  │ [+ Add Slide] [Duplicate] [Delete Slide] [Move ↑] [Move ↓]│   │
│  │                                                             │   │
│  │ Export Options:                                              │   │
│  │ [Export PDF] [Export PNG (all slides)] [Export Keynote]      │   │
│  │                                                             │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  SPEAKER NOTES (below slide canvas)                                 │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Notes for Slide 3:                                          │   │
│  │                                                             │   │
│  │ Talk about Q1 growth metrics. Emphasize Power 4             │   │
│  │ conference penetration and the SEC momentum.                │   │
│  │ Reference battle board data.                                │   │
│  │                                                             │   │
│  │ [Save Notes]                                                │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Slide Format Specifications

| Property         | Value                                |
|------------------|--------------------------------------|
| Aspect ratio     | 16:9 (1920 x 1080 reference)        |
| Background       | `--surface-canvas` (`#000000`)       |
| Text color       | `--text-primary` (`#FFFFFF`)         |
| Accent color     | `#DC2626` (brand red)                |
| Heading font     | Inter, 600 weight                    |
| Body font        | Inter, 400 weight                    |
| Data font        | JetBrains Mono, 500 weight           |
| Grid             | 12-column with 24px gutters          |

### Export Formats

| Format    | Output          | Use Case                           |
|-----------|-----------------|------------------------------------|
| PDF       | Multi-page PDF  | External sharing, email attachment  |
| PNG       | Per-slide images| Social media, documentation         |
| Keynote   | .key file       | Editable deck for Apple Keynote     |

---

## Responsive Behavior

### Breakpoint Adaptations for Operations Views

| Breakpoint | Sync Cards       | Battle Board     | Predictions      | Email Preview   |
|------------|------------------|------------------|------------------|-----------------|
| `2xl`      | 2-col grid       | Full heat map    | 2-col charts     | Side-by-side    |
| `xl`       | 2-col grid       | Full heat map    | 2-col charts     | Side-by-side    |
| `lg`       | 2-col grid       | Stacked bars     | 2-col charts     | Stacked         |
| `md`       | 1-col stack      | Stacked bars     | 1-col stack      | Stacked         |
| `sm`       | 1-col stack      | Compact list     | 1-col stack      | Stacked         |

### Mobile Considerations

- Sync job cards stack vertically in single column
- Battle board heat map bars compress to percentage-only labels
- Pipeline funnel simplifies to horizontal bar chart
- Program status table converts to card-based list
- Email preview scales within viewport with pinch-to-zoom
- Presentation editor hides slide rail; uses carousel navigation

---

## Accessibility

### ARIA Requirements for Operations Views

| Element                 | ARIA Role        | Additional Attributes                         |
|-------------------------|------------------|-----------------------------------------------|
| Sync progress bar       | `progressbar`    | `aria-valuenow`, `aria-valuemax`, `aria-label` |
| Sync stage log          | `log`            | `aria-live="polite"`, `aria-relevant="additions"` |
| Coverage bars           | `meter`          | `aria-valuenow`, `aria-valuemin`, `aria-valuemax` |
| Pipeline funnel bars    | `meter`          | `aria-valuenow`, `aria-label="{stage name}"`  |
| Status badges           | `status`         | `aria-live="polite"`                          |
| Accuracy metric cards   | `region`         | `aria-label="{metric name}"`                 |
| Drift status table      | `table`          | Column headers with `scope="col"`             |
| Email template preview  | `article`        | `aria-label="Email template preview"`         |
| Slide navigation        | `tablist`        | `aria-label="Slide thumbnails"`               |
| Active slide            | `tabpanel`       | `aria-labelledby="slide-{n}"`                 |

### Screen Reader Announcements

| Event                      | Announcement                                         |
|----------------------------|------------------------------------------------------|
| Sync job started           | "{Job name} sync started"                            |
| Sync progress update       | "{current} of {total} records processed"             |
| Sync job completed         | "{Job name} sync completed. {count} records synced." |
| Sync job failed            | "{Job name} sync failed. Check error details."       |
| Prediction run started     | "Prediction run started for {count} athletes"        |
| Test email sent            | "Test email sent to {recipient}"                     |

### Color Contrast Compliance

All status indicators and data visualizations maintain WCAG AAA compliance:
- Status badge text on colored backgrounds: minimum 4.5:1
- Bar chart labels on dark canvas: minimum 7:1
- Table cell text on card surfaces: minimum 15.4:1
- Secondary/muted text meets 9.7:1 minimum on dark surfaces

---

## Design Token References

### Layout Tokens

| Token                          | Value    | Usage                              |
|--------------------------------|----------|------------------------------------|
| `--space-4` (16px)             | 1rem     | Card internal padding minimum      |
| `--space-6` (24px)             | 1.5rem   | Standard card padding              |
| `--space-8` (32px)             | 2rem     | Section margins between panels     |
| `--radius-lg` (12px)          | 12px     | Standard card border radius        |
| `--radius-md` (8px)           | 8px      | Small cards, dropdowns             |
| `--radius-sm` (6px)           | 6px      | Buttons, inputs, badges            |
| `--elevation-card`            | `0 1px 3px rgba(0,0,0,0.1)` | Light mode card shadow |

### Typography Tokens

| Context          | Font           | Size  | Weight | Token Reference          |
|------------------|----------------|-------|--------|--------------------------|
| Section heading  | Inter          | 18px  | 600    | `--text-lg` + semibold   |
| Card heading     | Inter          | 16px  | 600    | `--text-base` + semibold |
| Card label       | Inter          | 12px  | 500    | `--text-xs` + medium     |
| Metric value     | JetBrains Mono | 24px  | 600    | `--text-2xl` + semibold  |
| Metric delta     | JetBrains Mono | 14px  | 500    | `--text-sm` + medium     |
| Table cell       | Inter          | 14px  | 400    | `--text-sm` + normal     |
| Table cell data  | JetBrains Mono | 14px  | 400    | `--text-sm` + normal     |
| Status badge     | Inter          | 12px  | 500    | `--text-xs` + medium     |
| Code/JSON output | JetBrains Mono | 12px  | 400    | `--text-xs` + normal     |

---

*NIL Optic -- The engine behind the intelligence.*
