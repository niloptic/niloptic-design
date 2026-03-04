# Tournament Intelligence Feature Spec

Last updated: 2026-03-04

---

## Overview

NCAA tournament tracking with NIL valuation overlays. March Madness is the primary focus — the biggest NIL value event of the year. Tournament Intelligence transforms bracket data into actionable NIL insights: which matchups generate the most exposure value, which athletes spike during tournament play, and how advancement impacts valuations in real time.

Basketball-first by design. The NCAA Men's and Women's Basketball Tournaments are the default surface. Football bowl season, College World Series, and conference tournaments are supported but secondary.

---

## Tournament Bracket View

```
┌──────────────────────────────────────────────────────────────────────┐
│  MARCH MADNESS 2026                    [Men's ▼]  [Live ●]         │
│  NCAA Tournament Bracket · NIL Value Overlay                        │
│  ────────────────────────────────────────────────────────────────── │
│                                                                      │
│  ROUND OF 64          ROUND OF 32        SWEET 16       FINAL FOUR │
│                                                                      │
│  ┌────────────┐                                                      │
│  │ (1) Duke   │───┐                                                  │
│  │ $42.1M NIL │   │  ┌────────────┐                                  │
│  ├────────────┤   ├──│ Duke       │───┐                              │
│  │(16) FGCU   │───┘  │ $42.1M     │   │                              │
│  │ $1.2M NIL  │      └────────────┘   │  ┌────────────┐             │
│  └────────────┘                       ├──│ Duke       │──┐          │
│  ┌────────────┐                       │  │ $42.1M     │  │          │
│  │ (8) Iowa   │───┐  ┌────────────┐  │  └────────────┘  │          │
│  │ $18.7M NIL │   ├──│ Iowa       │──┘                   │          │
│  ├────────────┤   │  │ $18.7M     │                      │          │
│  │ (9) Baylor │───┘  └────────────┘                      │          │
│  │ $12.3M NIL │                                          │          │
│  └────────────┘                                   ┌──────────────┐  │
│                                                   │ CHAMPIONSHIP │  │
│  ┌────────────┐                                   │              │  │
│  │ (4) UConn  │───┐                              │  TBD         │  │
│  │ $35.8M NIL │   │  ┌────────────┐              │              │  │
│  ├────────────┤   ├──│ UConn      │──┐           └──────────────┘  │
│  │(13) Vermont│───┘  │ $35.8M     │  │                              │
│  │ $0.8M NIL  │      └────────────┘  │  ┌────────────┐             │
│  └────────────┘                      ├──│ UConn      │──┘          │
│  ┌────────────┐                      │  │ $35.8M     │             │
│  │ (5) Kansas │───┐  ┌────────────┐  │  └────────────┘             │
│  │ $28.4M NIL │   ├──│ Kansas     │──┘                              │
│  ├────────────┤   │  │ $28.4M     │                                  │
│  │(12) Drake  │───┘  └────────────┘                                  │
│  │ $3.1M NIL  │                                                      │
│  └────────────┘                                                      │
│                                                                      │
│  ━━ Team NIL values in JetBrains Mono  ● Live game indicator        │
│  Click any team card for full roster valuations                      │
└──────────────────────────────────────────────────────────────────────┘
```

### Team Card (Within Bracket)

| Element          | Token / Style                          |
|------------------|----------------------------------------|
| Card             | zinc-800 bg, 8px radius, 120px width   |
| Seed number      | JetBrains Mono 12, zinc-400            |
| School name      | Inter Semi-Bold 13, white              |
| NIL value        | JetBrains Mono 12, `--color-brand-red` |
| Live indicator   | 8px circle, green pulse animation      |
| Winner connector | 2px solid, `--color-brand-red`         |
| Loser card       | 50% opacity, zinc-600 text             |

---

## Money Fight Card

```
┌──────────────────────────────────────────────────┐
│  MONEY FIGHT                    Round of 32      │
│  ──────────────────────────────────────────────  │
│                                                  │
│  ┌─────────────────┐    VS    ┌─────────────────┐│
│  │                 │          │                 ││
│  │   (1) DUKE      │          │   (8) IOWA      ││
│  │   Blue Devils   │          │   Hawkeyes      ││
│  │                 │          │                 ││
│  │   TEAM NIL      │          │   TEAM NIL      ││
│  │   $42.1M        │          │   $18.7M        ││
│  │                 │          │                 ││
│  │   TOP 3:        │          │   TOP 3:        ││
│  │   K. Williams   │          │   C. Clark      ││
│  │    $8.2M        │          │    $6.1M        ││
│  │   J. Proctor    │          │   A. Reaves     ││
│  │    $5.4M        │          │    $3.8M        ││
│  │   T. McCain     │          │   D. Murray     ││
│  │    $4.1M        │          │    $2.9M        ││
│  │                 │          │                 ││
│  └─────────────────┘          └─────────────────┘│
│                                                  │
│  ──────────────────────────────────────────────  │
│                                                  │
│  COMBINED NIL VALUE                              │
│  $60.8M                                         │  ← Display LG, red
│                                                  │
│  NIL IMPACT SCORE                                │
│  ████████████████░░░░  82/100                   │  ← Exposure value
│                                                  │
│  Matchup generates est. $2.4M in brand exposure  │
│                                                  │
│  [View Full Rosters]    [Compare Head-to-Head]   │
└──────────────────────────────────────────────────┘
```

### Money Fight Card Anatomy

| Element             | Token / Style                          |
|---------------------|----------------------------------------|
| Card                | zinc-900 bg, `--radius-lg`, 16px pad   |
| "VS" divider        | Inter Bold 24, `--color-brand-red`     |
| Team name           | Inter Bold 16, white                   |
| Team NIL value      | JetBrains Mono 20, `--color-brand-red` |
| Athlete name        | Inter Medium 13, white                 |
| Athlete value       | JetBrains Mono 13, zinc-300            |
| Combined value      | JetBrains Mono 28, `--color-brand-red` |
| Impact score bar    | `--color-brand-red` fill, zinc-700 bg  |
| Impact label        | Inter Medium 14, zinc-400              |

---

## Conference Value Clash

```
┌──────────────────────────────────────────────────┐
│  CONFERENCE PERFORMANCE              [2026 ▼]   │
│  ──────────────────────────────────────────────  │
│                                                  │
│  ┌────┬──────────┬──────────┬──────┬───────────┐│
│  │ #  │ Conf     │ NIL Value│ W-L  │ Rev Impact││
│  ├────┼──────────┼──────────┼──────┼───────────┤│
│  │ 1  │ SEC      │ $312.4M  │ 14-4 │ +$18.2M  ││
│  │ 2  │ Big Ten  │ $287.1M  │ 12-5 │ +$14.7M  ││
│  │ 3  │ Big 12   │ $198.6M  │ 10-6 │ +$9.3M   ││
│  │ 4  │ ACC      │ $176.2M  │ 8-7  │ +$6.1M   ││
│  │ 5  │ Big East │ $142.8M  │ 7-4  │ +$5.8M   ││
│  │ 6  │ Pac-12   │ $89.4M   │ 4-5  │ +$2.1M   ││
│  └────┴──────────┴──────────┴──────┴───────────┘│
│                                                  │
│  Revenue Impact = est. additional brand value    │
│  from tournament exposure based on round reached │
│                                                  │
│  [View Conference Detail]                        │
└──────────────────────────────────────────────────┘
```

### Conference Table Anatomy

| Element            | Token / Style                          |
|--------------------|----------------------------------------|
| Table header       | Inter Semi-Bold 12, zinc-400, uppercase|
| Rank number        | JetBrains Mono 14, zinc-300            |
| Conference name    | Inter Semi-Bold 14, white              |
| NIL value          | JetBrains Mono 14, `--color-brand-red` |
| W-L record         | JetBrains Mono 14, white               |
| Revenue impact     | JetBrains Mono 14, green               |
| Row hover          | zinc-800 bg                            |

---

## Tier Board

```
┌──────────────────────────────────────────────────┐
│  BRACKET REGIONS                                 │
│  ──────────────────────────────────────────────  │
│                                                  │
│  ┌──────────────────────┐ ┌──────────────────────┐
│  │  EAST REGION          │ │  WEST REGION          │
│  │                       │ │                       │
│  │  Total NIL: $284.1M   │ │  Total NIL: $312.7M   │
│  │  Teams: 16            │ │  Teams: 16            │
│  │                       │ │                       │
│  │  Top Athlete:         │ │  Top Athlete:         │
│  │  K. Williams (Duke)   │ │  C. Clark (Iowa)      │
│  │  $8.2M               │ │  $6.1M               │
│  │                       │ │                       │
│  │  Upset Potential: 3   │ │  Upset Potential: 5   │  ← Seed vs value
│  │  ████░░░░░░ Low      │ │  ████████░░ High     │     mismatch count
│  │                       │ │                       │
│  │  [View Region]        │ │  [View Region]        │
│  └──────────────────────┘ └──────────────────────┘
│                                                  │
│  ┌──────────────────────┐ ┌──────────────────────┐
│  │  SOUTH REGION         │ │  MIDWEST REGION       │
│  │                       │ │                       │
│  │  Total NIL: $298.3M   │ │  Total NIL: $267.9M   │
│  │  Teams: 16            │ │  Teams: 16            │
│  │                       │ │                       │
│  │  Top Athlete:         │ │  Top Athlete:         │
│  │  J. Proctor (UConn)   │ │  A. Reaves (Kentucky) │
│  │  $5.4M               │ │  $4.7M               │
│  │                       │ │                       │
│  │  Upset Potential: 2   │ │  Upset Potential: 4   │
│  │  ███░░░░░░░ Low      │ │  ██████░░░░ Medium   │
│  │                       │ │                       │
│  │  [View Region]        │ │  [View Region]        │
│  └──────────────────────┘ └──────────────────────┘
│                                                  │
│  Upset Potential = seed rank vs NIL valuation    │
│  rank mismatch (higher = more likely upsets)     │
└──────────────────────────────────────────────────┘
```

### Tier Board Anatomy

| Element             | Token / Style                          |
|---------------------|----------------------------------------|
| Region card         | zinc-800 bg, `--radius-lg`, 16px pad   |
| Region title        | Inter Bold 16, white                   |
| Total NIL           | JetBrains Mono 18, `--color-brand-red` |
| Top athlete name    | Inter Medium 14, white                 |
| Top athlete value   | JetBrains Mono 14, zinc-300            |
| Upset bar (low)     | green fill                             |
| Upset bar (medium)  | yellow fill                            |
| Upset bar (high)    | `--color-brand-red` fill               |

---

## Fan View (Public)

```
┌──────────────────────────────────────────────────┐
│  🏀 MARCH MADNESS 2026              [Sign Up]   │
│  ──────────────────────────────────────────────  │
│                                                  │
│  See the NIL value behind every matchup          │
│                                                  │
│  FEATURED MATCHUP                                │
│  ┌──────────────────────────────────────────────┐│
│  │  (1) Duke $42.1M  vs  (8) Iowa $18.7M       ││
│  │                                              ││
│  │  Top 3 Athletes (Duke):                      ││
│  │  K. Williams $8.2M · J. Proctor $5.4M       ││
│  │  T. McCain $4.1M                             ││
│  │                                              ││
│  │  ┌──────────────────────────────────────┐    ││
│  │  │  🔒 See full roster valuations       │    ││  ← Upgrade gate
│  │  │  [Upgrade to NIL Optic Pro]          │    ││
│  │  └──────────────────────────────────────┘    ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  BRACKET PREVIEW (Top 3 per team only)           │
│  ┌──────────────────────────────────────────────┐│
│  │  [Simplified bracket — team names + seeds]   ││
│  │  NIL values shown for top-3 athletes only    ││
│  │  Full valuations, predictions, and deal data ││
│  │  require Pro account                         ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  No messaging or huddle controls in fan view     │
│                                                  │
│  Route: /fan/tournaments                         │
└──────────────────────────────────────────────────┘
```

---

## Role-Based Behavior

| Capability                     | AD              | Agent                | Athlete             | Coach              | Fan                |
|--------------------------------|-----------------|----------------------|---------------------|--------------------|--------------------|
| Full bracket data              | Yes             | Yes                  | Yes                 | Yes                | Top-3 per team     |
| Roster valuations              | Conference-wide | Client + market      | Personal only       | Team only          | Preview only       |
| Compliance tracking            | Full            | Client deals         | Own deals           | Read-only          | No                 |
| Brand opportunity matching     | No              | Yes (during games)   | No                  | No                 | No                 |
| Tournament exposure metrics    | Program-wide    | Client-focused       | Personal            | Team-focused       | No                 |
| Money Fight cards              | Yes             | Yes                  | Yes                 | Yes                | Featured only      |
| Predictions overlay            | Yes             | Yes                  | Personal only       | Team only          | No                 |
| Export tournament data         | Yes             | Yes                  | No                  | No                 | No                 |

---

## March Madness Calendar Integration

### Pre-Tournament: Selection Sunday

```
┌──────────────────────────────────────────────────┐
│  SELECTION SUNDAY IMPACT            Mar 15, 2026 │
│  ──────────────────────────────────────────────  │
│                                                  │
│  VALUATION SPIKES (24h post-selection)           │
│                                                  │
│  ▲ +12.4%  #1 Seeds (avg)                       │
│  ▲ +8.1%   #2-4 Seeds (avg)                     │
│  ▲ +3.2%   #5-8 Seeds (avg)                     │
│  ▼ -2.1%   Bubble teams (not selected)           │
│                                                  │
│  TOP MOVERS                                      │
│  K. Williams (Duke)     $7.8M → $8.2M   ▲+5.1% │
│  C. Clark (Iowa)        $5.6M → $6.1M   ▲+8.9% │
│                                                  │
└──────────────────────────────────────────────────┘
```

### During Tournament: Real-Time Updates

- Valuation recalculation triggers after each game result
- Win = valuation boost (magnitude scales with seed differential)
- Loss = valuation impact (eliminated teams show projected decline)
- Buzzer-beater / highlight plays trigger social spike tracking

### Post-Tournament: Impact Reports

```
┌──────────────────────────────────────────────────┐
│  POST-TOURNAMENT REPORT             Apr 10, 2026 │
│  ──────────────────────────────────────────────  │
│                                                  │
│  TOURNAMENT NIL IMPACT SUMMARY                   │
│                                                  │
│  Total NIL value created:     $847.2M           │
│  Avg valuation change:        +14.3%            │
│  Athletes with 10%+ spike:    142               │
│                                                  │
│  Transfer portal entries (post-tourney):  87     │
│  Projected portal surge window:  Mar 28 – Apr 15│
│                                                  │
│  [Download Full Report]   [View Portal Surge]    │
└──────────────────────────────────────────────────┘
```

---

## States

### Pre-Season (No Active Tournament)
```
┌──────────────────────────────────────────────────┐
│  TOURNAMENT INTELLIGENCE                         │
│                                                  │
│              [🏀 Icon, 48px, zinc-600]           │
│                                                  │
│              No active tournament                │
│              March Madness tips off in 42 days.  │
│              View last year's impact report       │
│              or explore conference previews.      │
│                                                  │
│              [2025 Report]  [Conference Preview]  │
└──────────────────────────────────────────────────┘
```

### Selection Week
- Bracket reveal countdown timer
- Bubble team watchlist with valuation sensitivity analysis
- Auto-seed projection overlay

### Tournament Active
- Live game indicators on bracket
- Real-time valuation recalculation badges
- Push notification triggers for valuation spikes

### Post-Tournament
- Final impact report generation
- Transfer portal surge tracking crosslink
- Year-over-year comparison data

---

## Routes

| Route                              | Description                        |
|------------------------------------|------------------------------------|
| `/dashboard/tournaments`           | Tournament bracket (role-filtered) |
| `/dashboard/tournaments/bracket`   | Full bracket view                  |
| `/dashboard/tournaments/matchup/[id]` | Money Fight card detail         |
| `/dashboard/tournaments/regions`   | Tier Board                         |
| `/dashboard/tournaments/conference`| Conference Value Clash             |
| `/fan/tournaments`                 | Fan view (public, limited)         |

---

## Design Tokens

| Token Family           | Example Tokens                                        |
|------------------------|-------------------------------------------------------|
| `--bracket-*`          | `--bracket-connector-width`, `--bracket-card-width`   |
| `--seed-*`             | `--seed-1-color`, `--seed-5-color`, `--seed-16-color` |
| `--tournament-*`       | `--tournament-live-pulse`, `--tournament-header-bg`   |
| `--matchup-*`          | `--matchup-card-gap`, `--matchup-vs-size`             |
| `--region-*`           | `--region-card-padding`, `--region-bar-height`        |

### Seed Color Scale

| Seed Range | Color                          | Usage                |
|------------|--------------------------------|----------------------|
| 1-4        | `--color-brand-red`            | Championship tier    |
| 5-8        | `#F59E0B` (amber)              | Contender tier       |
| 9-12       | `#3B82F6` (blue)               | Upset watch tier     |
| 13-16      | zinc-500                       | Long shot tier       |

---

## Accessibility

- Bracket navigation via keyboard (arrow keys between rounds, Tab between teams)
- Screen reader announces team name, seed, NIL value, and game status
- Color is not the sole indicator of seed tier (number labels always present)
- Live game updates announced via `aria-live="polite"` region
- High contrast mode inverts bracket connectors to white
