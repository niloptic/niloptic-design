# Operations Playbook: Fan

> Last updated: 2026-03-04

---

## Role Overview

**Who:** Sports fans who explore NIL data, track athlete valuations, engage with roster building tools, and follow tournament intelligence on the NIL Optic platform. Fans represent the broadest entry point into the NIL Optic ecosystem and are the primary conversion funnel for paid organizational upgrades.

**Organization category:** None (public / limited-access persona)
**Role key:** `fan`
**Shell route:** `/fan`

Fans are not an organization or program role. The fan persona is a limited-access shell that provides curated NIL intelligence tools without the full operational depth available to Athletic Directors, Agents, Coaches, or Athletes. The fan experience is designed to demonstrate platform value, build engagement habits, and drive upgrade conversions to paid organizational accounts.

### Core Engagement Model

- Browse athlete NIL valuations with fan-lite depth (top-3 valuation windows)
- Explore roster builder with full player list but capped NIL value visibility
- Build and manage a favorites watchlist (players and teams)
- Engage with tournament intelligence previews
- Experience the NIL Optic data surface enough to justify upgrade consideration

---

## Daily Operations

**Time allocation:** 5--15 minutes (engagement-driven, not obligation-driven)

### Casual Check-in

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P1 | Browse athlete valuations -- check top movers and trending players | `/fan` | 3 min |
| P1 | Check tournament brackets and matchup intelligence | `/fan/tournaments` | 3 min |
| P2 | Explore roster builder -- model fantasy roster compositions | `/fan/roster-builder` | 5 min |
| P2 | Review favorites watchlist -- check valuation movements | `/fan/favorites` | 3 min |

### Daily Engagement Patterns

```
FAN ENGAGEMENT TRIGGERS:

  GAME DAY:
    - Pre-game: Check matchup valuations
    - Post-game: Review valuation changes from game performance
    - Tournament: Bracket and valuation movement

  NON-GAME DAY:
    - Trending: Browse trending athletes and top movers
    - Roster Builder: Model hypothetical rosters
    - Favorites: Check watchlist updates

  SEASONAL PEAKS:
    - November: MTE tournament brackets
    - February: Conference tournament positioning
    - March: March Madness (peak fan engagement)
    - April-May: Transfer portal activity
```

---

## Weekly Cadence

**Day:** Flexible (fan engagement is habit-driven, not calendar-driven)

### Weekly Engagement Rhythm

| Activity | Screen | Frequency | Purpose |
|---|---|---|---|
| Review favorites watchlist | `/fan/favorites` | 2--3x per week | Track valuation movements for followed athletes/teams |
| Check valuation movements | `/fan` | 2--3x per week | Browse top movers and trending players |
| Explore roster builder | `/fan/roster-builder` | 1--2x per week | Model roster compositions, compare players |
| Tournament intelligence | `/fan/tournaments` | During tournament weeks | Bracket analysis and valuation matchup data |

### Favorites Watchlist Management

```
FAN FAVORITES FUNCTIONALITY:

  ALLOWED:
    - Add players to favorites via quick-add search (Add Player)
    - Add teams to favorites via quick-add search (Add Team)
    - View favorites watchlist with player/team names and basic data
    - Remove favorites from watchlist

  NOT AVAILABLE (Fan-Lite Restrictions):
    - No deep-link View actions to /athletes/[playerId] or team detail routes
    - No Stats or Share analytics tabs
    - No Locked status affordances
    - No private profile access

  ENGAGEMENT GOAL:
    Build a personalized watchlist that creates habitual return visits
    and demonstrates enough value to motivate upgrade consideration.
```

---

## Key Screens

| Screen | Route | Primary Use |
|---|---|---|
| Fan Overview | `/fan` | Core tools grid, fan activity status, roadmap callout |
| Roster Builder | `/fan/roster-builder` | Full player list with capped NIL value visibility |
| Favorites | `/fan/favorites` | Player and team watchlist with quick-add search |
| Tournaments | `/fan/tournaments` | Tournament snapshot previews with capped valuation lists |

### Fan Overview Composition (`/fan`)

The `/fan` overview presents functional Core Tools cards (not static links) with live fan activity status:

| Card | Description | Status Display |
|---|---|---|
| Roster Builder | Model hypothetical rosters from full player lists | Active roster count, last session |
| Favorites | Track players and teams you follow | Favorites count, recent additions |
| Tournaments | Tournament bracket intelligence | Active tournament status |
| Roadmap Callout | Future sports-portfolio selection preview | Coming soon indicator |

### Fan Shell Navigation

```
FAN LEFT NAV (Limited):
  - Overview (/fan)
  - Roster Builder (/fan/roster-builder)
  - Favorites (/fan/favorites)
  - Tournaments (/fan/tournaments)

NOT AVAILABLE IN FAN SHELL:
  - Pipelines
  - Predictions (full depth)
  - Transfer Portal
  - Directory tooling
  - Messages / Huddles (no top-nav communication controls)
  - Keyboard shortcuts (L, D, H, M, 0-9 all ignored)
  - Notifications
```

### Navigation Context

- Fan shell is limited: no `Huddles`, `Messages`, or `Notifications` in top nav
- No keyboard shortcuts exposed or active in fan shell
- Profile settings menu hides keyboard shortcut references
- Fan tool routing stays inside fan segment (`/fan/roster-builder`, `/fan/favorites`, `/fan/tournaments`)
- No cross-shell navigation to private role dashboards

---

## Fan-Lite Data Visibility

The fan experience intentionally caps data depth to create upgrade motivation while providing enough value to sustain engagement.

### Roster Builder (`/fan/roster-builder`)

| Data Element | Visibility | Notes |
|---|---|---|
| Player List | Full coverage | All players available for exploration |
| Player Name | Visible | Full name displayed |
| Team | Visible | Team affiliation shown |
| Position | Visible | Position displayed |
| Core Box Stats (PTS/AST/REB) | Visible | Basic stat line available |
| Est. NIL Value | Top 3 only | Fan-lite capped at top-3 valuation window |
| Remaining Player NIL Values | Masked | Upgrade incentive |

### Favorites (`/fan/favorites`)

| Feature | Available | Notes |
|---|---|---|
| Add Player (quick-add search) | Yes | Self-service watchlist growth |
| Add Team (quick-add search) | Yes | Self-service watchlist growth |
| Player/Team Names | Visible | Basic identification |
| View Action (deep-link to profile) | No | Privacy-scoped restriction |
| Stats Tab | No | Suppressed for fan-lite |
| Share Tab | No | Suppressed for fan-lite |
| Locked Status Affordance | No | Removed from fan experience |

### Tournaments (`/fan/tournaments`)

| Data Element | Visibility | Notes |
|---|---|---|
| Tournament Bracket Structure | Visible | Full bracket layout |
| Team Names and Seeds | Visible | Standard bracket data |
| Top Valuation List | Top 3 per matchup | Fan-lite capped depth |
| Deeper Intelligence | Locked / Upgrade Framing | Upgrade incentive |

---

## KPIs

### Primary KPIs (Fan Engagement)

| KPI | Definition | Target | Font |
|---|---|---|---|
| Session Frequency | Average sessions per fan per week | 3+ | `JetBrains Mono` `#.#` |
| Feature Engagement | % of fans using 2+ features per session | 40%+ | `JetBrains Mono` `XX%` |
| Upgrade Conversion Rate | % of fans who convert to paid organizational account | 5--10% | `JetBrains Mono` `X.X%` |

### Secondary KPIs

| KPI | Definition | Target |
|---|---|---|
| Favorites List Size | Average number of favorites per fan | 5+ |
| Roster Builder Sessions | % of fans who use roster builder weekly | 30%+ |
| Tournament Engagement | % of fans active during tournament windows | 60%+ |
| Time on Platform | Average session duration | 5+ minutes |
| Return Rate (7-day) | % of fans returning within 7 days | 50%+ |

### Conversion Funnel Metrics

| Funnel Stage | Definition | Target |
|---|---|---|
| Signup | Fan creates free account | Volume growth MoM |
| Activation | Fan uses at least one feature beyond overview | 70%+ of signups |
| Engagement | Fan returns 3+ times in first 14 days | 40%+ of activated |
| Consideration | Fan encounters upgrade prompt and engages | 20%+ of engaged |
| Conversion | Fan upgrades to paid organizational account | 5--10% of consideration |

---

## Conversion Focus: Fan to Paid User Upgrade Path

The fan experience is explicitly designed as a product-led growth (PLG) funnel. Every fan interaction should build toward upgrade consideration.

### Upgrade Trigger Points

| Trigger | Location | Mechanism |
|---|---|---|
| Masked NIL values in Roster Builder | `/fan/roster-builder` | "Unlock full valuations" prompt |
| Locked tournament intelligence | `/fan/tournaments` | "Upgrade for deeper analysis" framing |
| Capped prediction visibility | Fan-lite surfaces | Top-3 valuation window with upgrade CTA |
| Org Version chip | Prediction and valuation surfaces | Non-intrusive upgrade affordance |
| Feature discovery | `/fan` overview | Core Tools cards hint at full-depth capabilities |

### Upgrade Path Flow

```
FAN UPGRADE FUNNEL:

  1. FREE FAN ACCOUNT
     - Full roster builder player coverage
     - Top-3 NIL valuation windows
     - Favorites watchlist (basic)
     - Tournament snapshot previews

  2. ENCOUNTER UPGRADE PROMPT
     - Masked values trigger curiosity
     - "Org Version" chip appears on capped surfaces
     - Locked intelligence sections show preview of full depth

  3. UPGRADE CONSIDERATION
     - Org Version chip routes to sales lead capture
     - Lead capture collects email, role interest, program affiliation
     - Email workflow nurtures toward paid onboarding

  4. PAID ORGANIZATION ACCOUNT
     - Full NIL valuation depth
     - Pipeline management
     - Predictions engine
     - Messages and Huddles
     - Role-scoped dashboard (AD, Coach, Agent, etc.)
     - Full tournament and transfer portal intelligence
```

### Conversion Messaging Framework

| Surface | Message | Tone |
|---|---|---|
| Masked NIL value | "Full NIL valuations available with organization account" | Informative, not aggressive |
| Locked tournament data | "Upgrade for conference-level tournament intelligence" | Value-focused |
| Org Version chip | "See what your program is worth" | Curiosity-driven |
| Favorites limitation | "Track detailed analytics with a full account" | Aspiration-based |
| Overview roadmap callout | "More tools coming -- get early access with upgrade" | Forward-looking |

---

## Basketball Focus

Basketball is the highest-engagement sport for fans on NIL Optic. March Madness drives the single largest traffic spike of the year.

### Basketball Fan Engagement Calendar

| Month | Engagement Level | Driver |
|---|---|---|
| August | Low | Off-season; minimal basketball content |
| September | Low--Medium | Preseason rankings and preview content |
| October | Medium | Early season excitement; roster reveals |
| November | Medium--High | MTE tournaments; early season games |
| December | Medium | Non-conference play; holiday tournaments |
| January | High | Conference play begins; matchup interest |
| February | High | Conference race intensifies; tournament positioning |
| March | Peak | March Madness -- highest traffic month of year |
| April | Medium--High | Transfer portal activity; off-season buzz |
| May | Medium | Portal commitments; roster construction speculation |
| June | Low--Medium | Summer content; recruiting news |
| July | Low | Off-season minimum |

### March Madness Fan Experience

```
TOURNAMENT FAN ENGAGEMENT STRATEGY:

  Selection Sunday:
    - Bracket reveal with NIL value overlay
    - "Money Fight" matchup cards (public teaser content)
    - Seed vs. Value conflict highlights

  Round 1-2:
    - Daily bracket updates with valuation shifts
    - Top performer valuation movement tracking
    - Engagement spike: push notifications for favorites

  Sweet 16 / Elite 8:
    - Conference Value Clash analysis
    - Tier board updates (Power 4, High Major, Mid-Major)
    - Upgrade prompts for deeper bracket intelligence

  Final Four / Championship:
    - Peak traffic window
    - Money Up / Down movers (partial view)
    - Maximum conversion opportunity
```

### Public Teaser Content (Pre-Signup)

Anonymous users accessing marketing surfaces see NIL-first preview intelligence:

| Teaser Module | Location | Content |
|---|---|---|
| Money Fight Matchup Cards | `/tournaments` (public) | Seeded matchup with NIL value comparison |
| Conference Value Clash | `/tournaments` (public) | Conference vs. conference NIL aggregates |
| Seed vs. Value Conflict | `/tournaments` (public) | Where seed ranking diverges from NIL value |
| Tier Board | `/tournaments` (public) | Power 4, High Major, Mid-Major breakdown |
| Money Up / Down Movers | `/tournaments` (public) | Partial list of valuation movers |

All public teaser content serves as a conversion funnel: limited data depth with clear CTA to `Sign In` or `Create Account`.

---

## Signup and Onboarding

### Fan Account Creation

| Step | Action | Notes |
|---|---|---|
| 1 | Navigate to `/signup` | Public registration screen |
| 2 | Complete signup form | Profile fields are non-authoritative (no role assignment) |
| 3 | Email verification | Standard email verification flow |
| 4 | Automatic fan persona routing | No org/program context = fan preview path |
| 5 | Land on `/fan` | Fan overview with Core Tools |

### Fan Onboarding Expectations

- No org/program attachment required
- No role-selection prompt during onboarding
- Onboarding does not auto-launch without org/program context
- Fan users enter in preview-only mode with fan-lite NIL access
- Upgrade to organization access via separate workflow

---

## Access and Permissions

| Capability | Allowed |
|---|---|
| Browse athlete valuations (fan-lite depth) | Yes |
| Use Roster Builder (capped NIL values) | Yes |
| Manage Favorites watchlist | Yes (add/remove only, no deep-links) |
| View tournament snapshot previews | Yes (capped depth) |
| Access Messages / Huddles | No |
| Access Pipelines | No |
| Access full Predictions | No |
| Access Transfer Portal | No |
| Access Directory tooling | No |
| Use keyboard shortcuts | No (ignored in fan shell) |
| View other users' private dashboards | No |
| Create NIL payments | No |

---

## Engagement Optimization Tactics

### Retention Mechanisms

| Mechanism | Description | Implementation |
|---|---|---|
| Favorites-driven return visits | Push awareness of valuation changes for favorited players | `/fan/favorites` watchlist |
| Tournament event triggers | Peak engagement during tournament windows | `/fan/tournaments` |
| Content freshness | Daily valuation updates create reason to return | `/fan` overview |
| Roster Builder experimentation | Unlimited roster modeling encourages exploration | `/fan/roster-builder` |
| Roadmap teasing | Future features create forward-looking anticipation | `/fan` overview callout |

### Anti-Churn Signals

| Signal | Threshold | Action |
|---|---|---|
| No session in 7 days | At-risk | Re-engagement email with top movers |
| No session in 14 days | Churning | "What you missed" email with highlights |
| No session in 30 days | Churned | Win-back campaign with tournament preview |
| Empty favorites list | Low investment | Prompt to add first favorite during session |
| Single-feature usage | Low breadth | Cross-feature discovery prompts |

---

*NIL Optic -- Every fan deserves NIL intelligence.*
