# Sports Directory Feature Spec

Last updated: 2026-03-04

---

## Overview

Searchable, browsable directory of athletes, teams, conferences, and divisions. The Sports Directory is the discovery layer for NIL Optic — the entry point for exploring the NIL landscape. Basketball is the default sport view. The directory connects to every other feature surface: valuations, predictions, pipelines, compliance, transfer portal, and tournament intelligence. Every entity in the directory (athlete, team, conference) is a click-through to deeper NIL data.

---

## Directory Landing

```
┌──────────────────────────────────────────────────┐
│  SPORTS DIRECTORY                                │
│  ──────────────────────────────────────────────  │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  [Search athletes, teams, conferences...]    ││  ← Typeahead search
│  └──────────────────────────────────────────────┘│
│                                                  │
│  SPORT SELECTOR                                  │
│  ┌──────────────────────────────────────────────┐│
│  │ [Basketball]  [Football]  [Baseball]         ││  ← Horizontal rail
│  │  ● Active                                    ││     Basketball default
│  │ [Soccer]  [Softball]  [Track]  [More ▼]     ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  FEATURED ATHLETES          Top NIL Valuations   │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐     │
│  │ [Photo]   │ │ [Photo]   │ │ [Photo]   │     │
│  │           │ │           │ │           │     │
│  │ K.Williams│ │ C. Clark  │ │ A. Reaves │     │
│  │ Duke      │ │ Iowa      │ │ Kentucky  │     │
│  │ Guard     │ │ Guard     │ │ Guard     │     │
│  │           │ │           │ │           │     │
│  │ $8.2M    │ │ $6.1M    │ │ $4.7M    │     │
│  │ ▲ +12.3% │ │ ▲ +8.7%  │ │ ▲ +5.1%  │     │
│  │           │ │           │ │           │     │
│  │ [Profile] │ │ [Profile] │ │ [Profile] │     │
│  └───────────┘ └───────────┘ └───────────┘     │
│                                                  │
│  BROWSE BY CONFERENCE                            │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐        │
│  │ [Logo]   │ │ [Logo]   │ │ [Logo]   │        │
│  │ SEC      │ │ Big Ten  │ │ Big 12   │        │
│  │ $312.4M  │ │ $287.1M  │ │ $198.6M  │        │
│  │ 16 teams │ │ 18 teams │ │ 16 teams │        │
│  └──────────┘ └──────────┘ └──────────┘        │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐        │
│  │ [Logo]   │ │ [Logo]   │ │ [Logo]   │        │
│  │ ACC      │ │ Big East │ │ Pac-12   │        │
│  │ $176.2M  │ │ $142.8M  │ │ $89.4M   │        │
│  │ 18 teams │ │ 11 teams │ │ 12 teams │        │
│  └──────────┘ └──────────┘ └──────────┘        │
│                                                  │
│  [View All Conferences]                          │
└──────────────────────────────────────────────────┘
```

### Landing Anatomy

| Element              | Token / Style                          |
|----------------------|----------------------------------------|
| Search bar           | zinc-800 bg, `--radius-md`, 48px h     |
| Search icon          | zinc-500, 20px                         |
| Sport pill (default) | `--color-brand-red` bg, white text     |
| Sport pill (inactive)| zinc-700 bg, zinc-400 text             |
| Featured card        | zinc-800 bg, `--radius-lg`, 200px w    |
| Athlete photo        | 64px circle, `--radius-pill`           |
| Athlete name         | Inter Bold 14, white                   |
| School name          | Inter Regular 12, zinc-400             |
| NIL value            | JetBrains Mono 18, `--color-brand-red` |
| Trend delta          | JetBrains Mono 12, green (up) / red    |
| Conference card      | zinc-800 bg, `--radius-md`, 160px w    |
| Conference logo      | 48px square                            |
| Conference name      | Inter Semi-Bold 14, white              |
| Conference NIL       | JetBrains Mono 14, zinc-300            |

### Typeahead Search

```
┌──────────────────────────────────────────────────┐
│  [Search: "Mar"]                                 │
│  ──────────────────────────────────────────────  │
│                                                  │
│  ATHLETES                                        │
│  ┌──────────────────────────────────────────────┐│
│  │ [AV] Marcus Thompson   Guard · Kentucky     ││
│  │      $2.4M                                   ││
│  ├──────────────────────────────────────────────┤│
│  │ [AV] Mario Williams    Forward · UCLA       ││
│  │      $1.8M                                   ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  TEAMS                                           │
│  ┌──────────────────────────────────────────────┐│
│  │ [Logo] Maryland Terrapins    Big Ten         ││
│  │        Team NIL: $24.1M                      ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  CONFERENCES                                     │
│  ┌──────────────────────────────────────────────┐│
│  │ [Logo] MAAC (Metro Atlantic)                 ││
│  │        Total NIL: $8.2M                      ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [View all results for "Mar"]                    │
└──────────────────────────────────────────────────┘
```

---

## Conference Detail View

```
┌──────────────────────────────────────────────────┐
│  ← Directory                                     │
│                                                  │
│  [SEC Logo]  SOUTHEASTERN CONFERENCE             │
│  64px        Total NIL Value: $312.4M            │
│              16 Teams · Basketball                │
│  ──────────────────────────────────────────────  │
│                                                  │
│  CONFERENCE STANDINGS + NIL OVERLAY              │
│  ┌────┬──────────────┬───────┬──────────┬──────┐│
│  │ #  │ Team         │ W-L   │ NIL Value│ Top  ││
│  ├────┼──────────────┼───────┼──────────┼──────┤│
│  │ 1  │ Kentucky     │ 24-3  │ $42.1M   │ $4.7M││
│  │ 2  │ Tennessee    │ 22-5  │ $38.7M   │ $3.9M││
│  │ 3  │ Alabama      │ 21-6  │ $35.2M   │ $3.4M││
│  │ 4  │ Auburn       │ 20-7  │ $31.8M   │ $3.1M││
│  │ 5  │ Arkansas     │ 18-9  │ $28.4M   │ $2.8M││
│  │ 6  │ Florida      │ 17-10 │ $26.1M   │ $2.5M││
│  └────┴──────────────┴───────┴──────────┴──────┘│
│                                                  │
│  Sort: [NIL Value ▼] [Standings] [Alphabetical]  │
│                                                  │
│  TEAMS                                           │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐     │
│  │ [Mascot]  │ │ [Mascot]  │ │ [Mascot]  │     │
│  │ Kentucky  │ │ Tennessee │ │ Alabama   │     │
│  │ Wildcats  │ │ Volunteers│ │ Crimson T.│     │
│  │ $42.1M    │ │ $38.7M    │ │ $35.2M    │     │
│  │ Top: Reav.│ │ Top: Jack.│ │ Top: Mill.│     │
│  │ [View]    │ │ [View]    │ │ [View]    │     │
│  └───────────┘ └───────────┘ └───────────┘     │
│                                                  │
│  [Load More Teams]                               │
└──────────────────────────────────────────────────┘
```

### Conference Detail Anatomy

| Element              | Token / Style                          |
|----------------------|----------------------------------------|
| Conference logo      | 64px square, `--radius-md`             |
| Conference name      | Inter Bold 24, white                   |
| Total NIL value      | JetBrains Mono 20, `--color-brand-red` |
| Team count           | Inter Regular 14, zinc-400             |
| Standings table      | zinc-800 bg, alternating row shading   |
| Table header         | Inter Semi-Bold 12, zinc-400, uppercase|
| Rank number          | JetBrains Mono 14, zinc-300            |
| Team name            | Inter Semi-Bold 14, white              |
| W-L record           | JetBrains Mono 14, white               |
| NIL value            | JetBrains Mono 14, `--color-brand-red` |
| Sort controls        | Pill buttons, active = red bg          |
| Team card            | zinc-800 bg, `--radius-lg`, 180px w    |

---

## Team Detail View

```
┌──────────────────────────────────────────────────┐
│  ← SEC                                           │
│                                                  │
│  [Team Logo]  KENTUCKY WILDCATS                  │
│  64px         SEC · Division I · Basketball      │
│  ──────────────────────────────────────────────  │
│                                                  │
│  TEAM NIL VALUE                                  │
│  $42.1M                          ▲ +8.4% (30d)  │  ← Display XL, red
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐      │
│  │ Budget   │  │ Avg/Plyr │  │ Roster   │      │
│  │ $4.2M    │  │ $2.8M    │  │ 15       │      │
│  │ NIL Alloc│  │ Valuation│  │ Athletes │      │
│  └──────────┘  └──────────┘  └──────────┘      │
│                                                  │
│  TOP PERFORMERS                                  │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐     │
│  │ [Photo]   │ │ [Photo]   │ │ [Photo]   │     │
│  │ A. Reaves │ │ D. Murray │ │ J. Taylor │     │
│  │ Guard     │ │ Forward   │ │ Center    │     │
│  │ $4.7M     │ │ $3.8M     │ │ $2.9M     │     │
│  │ ▲ +5.1%   │ │ ▲ +3.2%   │ │ ▲ +1.8%   │     │
│  └───────────┘ └───────────┘ └───────────┘     │
│                                                  │
│  FULL ROSTER                                     │
│  ┌────┬──────────┬──────┬──────────┬─────┬─────┐│
│  │ #  │ Athlete  │ Pos  │ NIL Value│ Conf│Trend││
│  ├────┼──────────┼──────┼──────────┼─────┼─────┤│
│  │ 1  │ A.Reaves │ G    │ $4.7M    │ 92% │ ▲   ││
│  │ 2  │ D.Murray │ F    │ $3.8M    │ 88% │ ▲   ││
│  │ 3  │ J.Taylor │ C    │ $2.9M    │ 85% │ ▲   ││
│  │ 4  │ R.Brooks │ G    │ $2.1M    │ 81% │ ─   ││
│  │ 5  │ K.Lewis  │ F    │ $1.9M    │ 78% │ ▼   ││
│  │ ...│          │      │          │     │     ││
│  └────┴──────────┴──────┴──────────┴─────┴─────┘│
│                                                  │
│  BUDGET VS. VALUATION                            │
│  ┌──────────────────────────────────────────────┐│
│  │  NIL Budget:      $4.2M                      ││
│  │  Team Valuation:  $42.1M                     ││
│  │  Budget/Value:    10.0%                      ││
│  │                                              ││
│  │  Budget   ████░░░░░░░░░░░░░░░░  10%         ││
│  │  Value    ████████████████████  100%         ││
│  └──────────────────────────────────────────────┘│
│                                                  │
└──────────────────────────────────────────────────┘
```

### Team Detail Anatomy

| Element              | Token / Style                          |
|----------------------|----------------------------------------|
| Team logo            | 64px square, `--radius-md`             |
| Team name            | Inter Bold 24, white                   |
| Conference / division| Inter Regular 14, zinc-400             |
| Team NIL value       | JetBrains Mono 32, `--color-brand-red` |
| Trend delta          | JetBrains Mono 14, green/red           |
| KPI card             | zinc-800 bg, `--radius-md`, 120px      |
| KPI value            | JetBrains Mono 20, white               |
| KPI label            | Inter Regular 12, zinc-400             |
| Top performer card   | zinc-800 bg, `--radius-lg`, 160px w    |
| Roster table         | Full-width, zinc-800 bg, striped rows  |
| Confidence column    | JetBrains Mono 13, white               |
| Trend indicator      | ▲ green, ─ zinc-500, ▼ red             |
| Budget bar           | zinc-700 bg, `--color-brand-red` fill  |

---

## Athlete Profile View

References the **Valuation Hero Card** defined in `features.md`. The profile view wraps the hero card with additional context sections.

```
┌──────────────────────────────────────────────────┐
│  ← Kentucky Wildcats                             │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │          [VALUATION HERO CARD]               ││  ← From features.md
│  │          See features.md for spec            ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  PERFORMANCE STATS (Basketball)                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐        │
│  │  22.4    │ │  5.8     │ │  6.2     │        │
│  │  PPG     │ │  RPG     │ │  APG     │        │
│  └──────────┘ └──────────┘ └──────────┘        │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐        │
│  │  48.2%   │ │  38.1%   │ │  1.4     │        │
│  │  FG%     │ │  3PT%    │ │  SPG     │        │
│  └──────────┘ └──────────┘ └──────────┘        │
│                                                  │
│  SOCIAL MEDIA METRICS                            │
│  ┌──────────────────────────────────────────────┐│
│  │  Instagram: 1.2M  │  TikTok: 2.8M          ││
│  │  Twitter: 540K     │  YouTube: 180K          ││
│  │                                              ││
│  │  Engagement Rate: 4.2% (above avg)           ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  DEAL HISTORY                                    │
│  ┌────┬────────────┬──────────┬────────┬───────┐│
│  │ #  │ Brand      │ Value    │ Status │ Date  ││
│  ├────┼────────────┼──────────┼────────┼───────┤│
│  │ 1  │ Nike       │ $50,000  │●Active │ Feb 26││
│  │ 2  │ Gatorade   │ $25,000  │●Active │ Jan 26││
│  │ 3  │ Beats      │ $15,000  │●Ended  │ Dec 25││
│  └────┴────────────┴──────────┴────────┴───────┘│
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │          [PREDICTION CARD]                   ││  ← From features.md
│  │          See features.md for spec            ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [Compare Athlete]  [Add to Pipeline]            │
│                                                  │
└──────────────────────────────────────────────────┘
```

### Athlete Profile Anatomy

| Element              | Token / Style                          |
|----------------------|----------------------------------------|
| Stat card            | zinc-800 bg, `--radius-md`, 100px w    |
| Stat value           | JetBrains Mono 24, white               |
| Stat label           | Inter Regular 11, zinc-400             |
| Social platform      | Inter Medium 13, zinc-300              |
| Social count         | JetBrains Mono 14, white               |
| Engagement rate      | JetBrains Mono 13, green (above avg)   |
| Deal table           | zinc-800 bg, striped rows              |
| Deal status (active) | green dot + "Active"                   |
| Deal status (ended)  | zinc-500 dot + "Ended"                 |
| Compare button       | Secondary, zinc-700 bg                 |
| Pipeline button      | Primary, `--color-brand-red` bg        |

---

## Role-Aware Guidance

| Capability                    | AD               | Agent              | Coach              | Fan               | Public (unauth)    |
|-------------------------------|------------------|--------------------|--------------------|-------------------|--------------------|
| Browse directory              | Full             | Full               | Full               | Limited           | Teaser only        |
| View athlete valuations       | Conference-wide  | Full market        | Team context       | Top-3 per team    | Top-3 preview      |
| View team detail              | Full             | Full               | Team + conference  | Summary only      | Name + record      |
| Add to pipeline               | Yes (recruiting) | Yes (client roster)| Yes (recruiting)   | No                | No                 |
| Add to program                | Yes              | No                 | No                 | No                | No                 |
| Compare athletes              | Yes              | Yes                | Yes                | No                | No                 |
| View deal history             | Yes              | Client only        | No                 | No                | No                 |
| View predictions              | Yes              | Yes                | Team only          | No                | No                 |
| See social metrics            | Yes              | Yes                | Yes                | Limited           | No                 |
| Upgrade CTA shown             | No               | No                 | No                 | Yes               | Yes                |
| Sign-up prompt                | No               | No                 | No                 | No                | Yes                |

### Fan View Restrictions

```
┌──────────────────────────────────────────────────┐
│  [Athlete Profile — Fan View]                    │
│                                                  │
│  A. Reaves · Kentucky · Guard                    │
│  NIL Valuation: $4.7M                            │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  🔒 Full valuation breakdown, predictions,   ││
│  │     deal history, and comparison tools        ││
│  │     require NIL Optic Pro.                    ││
│  │                                              ││
│  │  [Upgrade to Pro]                            ││
│  └──────────────────────────────────────────────┘│
│                                                  │
└──────────────────────────────────────────────────┘
```

### Public (Unauthenticated) View

```
┌──────────────────────────────────────────────────┐
│  [Directory — Public View]                       │
│                                                  │
│  TOP BASKETBALL ATHLETES BY NIL VALUE            │
│                                                  │
│  1. K. Williams (Duke)           $8.2M           │
│  2. C. Clark (Iowa)              $6.1M           │
│  3. A. Reaves (Kentucky)         $4.7M           │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  Sign up for NIL Optic to access full        ││
│  │  athlete profiles, team valuations, and       ││
│  │  conference intelligence.                     ││
│  │                                              ││
│  │  [Create Free Account]  [Learn More]         ││
│  └──────────────────────────────────────────────┘│
│                                                  │
└──────────────────────────────────────────────────┘
```

---

## Filter System

```
┌──────────────────────────────────────────────────┐
│  FILTERS                            [Clear All] │
│  ──────────────────────────────────────────────  │
│                                                  │
│  Sport:       [Basketball ▼]                     │
│  Conference:  [All Conferences ▼]                │
│  Division:    [Division I ▼]                     │
│  Position:    [All Positions ▼]                  │
│  Valuation:   [$0 ━━━━━━━━●━━ $10M+]           │  ← Range slider
│  Class Year:  [All ▼]                            │
│                                                  │
│  SORT BY                                         │
│  [NIL Value (desc)]  [Trending]  [Alphabetical]  │
│                                                  │
│  VIEW MODE                                       │
│  [Grid]  [List]  [Table]                         │
│    ●                                             │
│                                                  │
│  Showing 247 results                             │
│  [Apply Filters]                                 │
└──────────────────────────────────────────────────┘
```

### Filter Anatomy

| Element              | Token / Style                          |
|----------------------|----------------------------------------|
| Filter dropdown      | zinc-700 bg, `--radius-sm`, 40px h     |
| Range slider track   | zinc-600, 4px height                   |
| Range slider thumb   | `--color-brand-red`, 16px circle       |
| Sort pill (active)   | `--color-brand-red` bg, white text     |
| Sort pill (inactive) | zinc-700 bg, zinc-400 text             |
| View mode icon       | 20px, active = white, inactive = zinc-500 |
| Results count        | Inter Regular 13, zinc-400             |

---

## Routes

| Route                             | Description                |
|-----------------------------------|----------------------------|
| `/directory`                      | Directory landing          |
| `/basketball`                     | Basketball directory       |
| `/football`                       | Football directory         |
| `/conferences/[conferenceId]`     | Conference detail          |
| `/teams/[teamId]`                 | Team detail                |
| `/athletes/[playerId]`           | Athlete profile            |
| `/fan/directory`                  | Fan view (limited)         |

---

## States

### Loading (Skeleton)
```
┌──────────────────────────────────────────────────┐
│  SPORTS DIRECTORY                                │
│                                                  │
│  [░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░] │  ← Search skeleton
│                                                  │
│  [░░░░░] [░░░░░] [░░░░░] [░░░░░]               │  ← Sport pills
│                                                  │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐     │
│  │ ░░░░░░░░  │ │ ░░░░░░░░  │ │ ░░░░░░░░  │     │  ← Card skeletons
│  │ ░░░░░░    │ │ ░░░░░░    │ │ ░░░░░░    │     │     Shimmer animation
│  │ ░░░░      │ │ ░░░░      │ │ ░░░░      │     │
│  └───────────┘ └───────────┘ └───────────┘     │
└──────────────────────────────────────────────────┘
```

### Empty Search Results
```
┌──────────────────────────────────────────────────┐
│  SPORTS DIRECTORY                                │
│                                                  │
│  Search: "Xyzzy University"                      │
│                                                  │
│              [Search icon, 48px, zinc-600]       │
│                                                  │
│              No results found                    │
│              Try adjusting your search or         │
│              browse by conference instead.        │
│                                                  │
│              [Browse Conferences]                 │
└──────────────────────────────────────────────────┘
```

### Error
```
┌──────────────────────────────────────────────────┐
│  SPORTS DIRECTORY                                │
│                                                  │
│              [Warning icon, 48px, red]           │
│                                                  │
│              Unable to load directory             │
│              Check your connection and try again. │
│                                                  │
│              [Retry]                             │
└──────────────────────────────────────────────────┘
```

### First-Visit Education
```
┌──────────────────────────────────────────────────┐
│  WELCOME TO THE SPORTS DIRECTORY                 │
│                                                  │
│  Step 1 of 3                 [●  ○  ○]          │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  [Illustration: search + browse preview]     ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  Discover NIL Valuations                         │
│  Browse athletes, teams, and conferences.        │
│  Every entity links to deep NIL intelligence.    │
│                                                  │
│  [Next →]                           [Skip]       │
└──────────────────────────────────────────────────┘
```

---

## Design Tokens

| Token Family          | Example Tokens                                       |
|-----------------------|------------------------------------------------------|
| `--directory-*`       | `--directory-search-height`, `--directory-card-gap`   |
| `--directory-sport-*` | `--directory-sport-pill-height`, `--directory-sport-active` |
| `--directory-filter-*`| `--directory-filter-dropdown-bg`, `--directory-filter-slider` |
| `--directory-card-*`  | `--directory-card-width`, `--directory-card-radius`   |
| `--conference-*`      | `--conference-logo-size`, `--conference-header-height`|
| `--team-*`            | `--team-roster-row-height`, `--team-budget-bar-fill`  |

---

## Accessibility

- Search typeahead results announced via `aria-live="polite"` as they update
- Sport selector rail is keyboard-navigable with arrow keys
- All cards have descriptive `aria-label` (e.g., "Kentucky Wildcats, SEC, NIL value 42.1 million")
- Filter dropdowns support keyboard selection
- Grid/List/Table views are equivalent in content — no view-mode-exclusive information
- Upgrade gates include descriptive text for screen readers
