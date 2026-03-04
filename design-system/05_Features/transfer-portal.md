# Transfer Portal Feature Spec

Last updated: 2026-03-04

---

## Overview

Time-windowed workspace for tracking athletes entering and exiting the NCAA transfer portal. The basketball transfer portal is the highest-activity window and the default view. Transfer Portal intelligence connects directly to NIL valuations — every portal entry, commitment, and withdrawal triggers a valuation recalculation. For agents, ADs, and coaches, the portal is the primary talent acquisition surface during transfer windows.

---

## Portal Dashboard

```
┌──────────────────────────────────────────────────┐
│  TRANSFER PORTAL                  [● Window Open]│  ← Status indicator
│  ──────────────────────────────────────────────  │
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐      │
│  │   347    │  │    42    │  │   $1.2B  │      │
│  │ Active   │  │ New This │  │ Total    │      │
│  │ Entries  │  │ Week     │  │ NIL Value│      │
│  └──────────┘  └──────────┘  └──────────┘      │
│                                                  │
│  KPI STRIP                                       │
│  ┌──────────────────────────────────────────────┐│
│  │ Avg Valuation: $890K  │ Top Prospect: $8.2M ││
│  │ Avg Days in Portal: 18│ Commitments: 124    ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  FILTERS                                         │
│  ┌──────────────────────────────────────────────┐│
│  │ Sport: [Basketball ▼]  Position: [All ▼]     ││
│  │ Conf:  [All ▼]        Valuation: [$0 — $10M]││
│  │ Entry: [Last 7 days ▼] Status: [In Portal ▼]││
│  │                                              ││
│  │ [Apply Filters]              [Clear All]     ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  PORTAL ENTRIES                    [Grid] [List] │
│  ┌──────────────────────────────────────────────┐│
│  │  [Athlete Portal Cards — see below]          ││
│  └──────────────────────────────────────────────┘│
│                                                  │
└──────────────────────────────────────────────────┘
```

### Dashboard KPI Anatomy

| Element            | Token / Style                          |
|--------------------|----------------------------------------|
| KPI card           | zinc-800 bg, `--radius-md`, 120px      |
| KPI value          | JetBrains Mono 28, white               |
| KPI label          | Inter Regular 12, zinc-400             |
| Status indicator   | 8px circle, green (open) / red (closed)|
| KPI strip          | zinc-800 bg, 48px height, 16px padding |
| Filter bar         | zinc-900 bg, `--radius-md`, 12px pad   |
| Filter dropdown    | zinc-700 bg, `--radius-sm`             |

---

## Athlete Portal Card

```
┌──────────────────────────────────────────────────┐
│  ┌────────────────────────────────────────────┐  │
│  │                                            │  │
│  │  [Photo]   Marcus Thompson                 │  │
│  │   56px     Guard · Junior · 6'3"           │  │
│  │   circle                                   │  │
│  │            University of Kentucky          │  │  ← Current school
│  │                 ↓                          │  │
│  │            ● IN PORTAL                     │  │  ← Portal status badge
│  │                                            │  │
│  │  ──────────────────────────────────────── │  │
│  │                                            │  │
│  │  CURRENT NIL          PREDICTED POST-XFER  │  │
│  │  $2.4M                $2.8M – $3.6M       │  │
│  │                       ▲ +16% to +50%       │  │  ← Range based on
│  │                                            │  │     destination tier
│  │  DAYS IN PORTAL       ENTERED              │  │
│  │  12                   Feb 20, 2026         │  │
│  │                                            │  │
│  │  ──────────────────────────────────────── │  │
│  │                                            │  │
│  │  REPORTED INTEREST                         │  │
│  │  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐    │  │
│  │  │ Duke │ │UConn │ │Kansas│ │ +4   │    │  │  ← School pills
│  │  └──────┘ └──────┘ └──────┘ └──────┘    │  │
│  │                                            │  │
│  │  [View Profile]    [Add to Pipeline]       │  │
│  │                                            │  │
│  └────────────────────────────────────────────┘  │
│                                                  │
└──────────────────────────────────────────────────┘
```

### Portal Card Anatomy

| Element                | Token / Style                          |
|------------------------|----------------------------------------|
| Card                   | zinc-800 bg, `--radius-lg`, 16px pad   |
| Athlete photo          | 56px circle, `--radius-pill`           |
| Name                   | Inter Bold 16, white                   |
| Position / class       | Inter Regular 13, zinc-400             |
| School name            | Inter Medium 14, zinc-300              |
| Portal status badge    | See status table below                 |
| Current NIL            | JetBrains Mono 20, `--color-brand-red` |
| Predicted range        | JetBrains Mono 16, zinc-300            |
| Prediction delta       | JetBrains Mono 13, green               |
| Days in portal         | JetBrains Mono 16, white               |
| Entry date             | JetBrains Mono 12, zinc-500            |
| Interest pill          | zinc-700 bg, `--radius-sm`, 28px h     |
| Overflow pill (+N)     | zinc-600 bg, zinc-300 text             |

### Portal Status Badges

| Status        | Background         | Text     | Icon   |
|---------------|--------------------|----------|--------|
| In Portal     | `#DC2626` (red)    | white    | ●      |
| Committed     | `#16A34A` (green)  | white    | ✓      |
| Withdrawn     | zinc-600           | zinc-300 | ←      |
| Entered Today | `#F59E0B` (amber)  | black    | ★      |

---

## Portal Timeline

```
┌──────────────────────────────────────────────────┐
│  PORTAL TIMELINE                  [2025-26 ▼]   │
│  ──────────────────────────────────────────────  │
│                                                  │
│  Basketball Transfer Windows                     │
│                                                  │
│       Window 1                    Window 2       │
│  ┌────────────────┐         ┌────────────────┐  │
│  │  Apr 15 – May 1 │         │  Mar 28 – Apr 15│  │
│  │  (Post-Season)  │         │  (Post-Tourney)  │  │
│  └────────────────┘         └────────────────┘  │
│                                                  │
│  ──●────────●────────────────●────────●──────── │
│   Apr 15   May 1           Mar 28   Apr 15      │
│                                                  │
│  ATHLETE ACTIVITY OVERLAY                        │
│                                                  │
│  $3M ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │
│       ╱╲         Avg valuation                   │
│  $2M ╱──╲─ ─ ─ ─of portal ─ ─ ─ ─ ─ ─ ╱╲─ ─  │
│     ╱    ╲       entrants           ╱╱╱╱  ╲     │
│  $1M ─ ─ ─╲─ ─ ─ ─ ─ ─ ─ ─ ─╱╱╱╱─ ─ ─ ─╲─  │
│             ╲╲╲╲╲╲╲╲╲╲╲╱╱╱╱                    │
│  $0 ─────────────────────────────────────────── │
│     Apr  May  Jun  Jul  ... Jan  Feb  Mar  Apr   │
│                                                  │
│  ━━ Avg Valuation    ░░ Portal Window            │
│  ● Entry Events      ○ Commitment Events         │
└──────────────────────────────────────────────────┘
```

### Timeline Anatomy

| Element             | Token / Style                          |
|---------------------|----------------------------------------|
| Window block        | `--color-brand-red` bg, 30% opacity    |
| Timeline track      | zinc-700, 2px height                   |
| Entry marker        | 8px circle, `--color-brand-red`        |
| Commitment marker   | 8px circle, green                      |
| Valuation line      | 2px solid, white                       |
| Date labels         | JetBrains Mono 11, zinc-500            |
| Legend               | Inter Regular 12, zinc-400             |

---

## Valuation Impact Model

```
┌──────────────────────────────────────────────────┐
│  TRANSFER DESTINATION IMPACT                     │
│  How destination affects NIL valuation            │
│  ──────────────────────────────────────────────  │
│                                                  │
│  Marcus Thompson · Current: $2.4M                │
│                                                  │
│  DESTINATION          PROJECTED NIL    DELTA     │
│  ┌────────────────────────────────────────────┐  │
│  │ Duke (ACC)          $3.6M           ▲ +50% │  │
│  │ UConn (Big East)    $3.2M           ▲ +33% │  │
│  │ Kansas (Big 12)     $3.0M           ▲ +25% │  │
│  │ Iowa (Big Ten)      $2.8M           ▲ +16% │  │
│  │ Baylor (Big 12)     $2.5M           ▲  +4% │  │
│  └────────────────────────────────────────────┘  │
│                                                  │
│  Factors: conference media deal, market size,    │
│  team brand strength, recent NIL collective      │
│  activity at destination school                  │
│                                                  │
└──────────────────────────────────────────────────┘
```

---

## Conference Talent Flow

```
┌──────────────────────────────────────────────────┐
│  CONFERENCE TALENT FLOW           [2025-26 ▼]   │
│  ──────────────────────────────────────────────  │
│                                                  │
│                  NET FLOW (NIL VALUE)             │
│                                                  │
│  SEC         ████████████████   +$48.2M  (IN)   │
│  Big Ten     ██████████░░░░░   +$22.1M  (IN)   │
│  Big 12      ████░░░░░░░░░░    +$8.4M  (IN)   │
│  ACC         ░░░░░░░░░░░░░░   -$12.3M  (OUT)  │
│  Big East    ░░░░░░░░░░░░░░   -$18.7M  (OUT)  │
│  Pac-12      ░░░░░░░░░░░░░░   -$24.1M  (OUT)  │
│                                                  │
│  ━━ Inbound value    ░░ Outbound value           │
│  Green = net gain    Red = net loss              │
│                                                  │
│  [View Full Flow Detail]                         │
└──────────────────────────────────────────────────┘
```

---

## Admin Override Controls

Route: `/admin/transfer-portal`

```
┌──────────────────────────────────────────────────┐
│  PORTAL ADMIN                     [Admin Only]   │
│  ──────────────────────────────────────────────  │
│                                                  │
│  OVERRIDE ACTIONS                                │
│                                                  │
│  Athlete:    [Search athlete...]                 │
│                                                  │
│  Entry Date Override:                            │
│  [YYYY-MM-DD]          [Apply Override]          │
│                                                  │
│  Exit Date Override:                             │
│  [YYYY-MM-DD]          [Apply Override]          │
│                                                  │
│  Manual Status:                                  │
│  [In Portal ▼]         [Update Status]          │
│                                                  │
│  ──────────────────────────────────────────────  │
│                                                  │
│  DATA QUALITY FLAGS                              │
│  ┌────────────────────────────────────────────┐  │
│  │ ⚠ M. Thompson — Entry date unconfirmed    │  │
│  │   Source: unofficial, needs verification    │  │
│  │   [Confirm] [Flag for Review] [Dismiss]    │  │
│  ├────────────────────────────────────────────┤  │
│  │ ⚠ J. Proctor — Duplicate entry detected    │  │
│  │   [Merge Records] [Keep Both] [Dismiss]    │  │
│  └────────────────────────────────────────────┘  │
│                                                  │
│  AUDIT LOG                                       │
│  ┌────┬─────────┬──────────┬──────────────────┐ │
│  │ #  │ Admin   │ Action   │ Timestamp        │ │
│  ├────┼─────────┼──────────┼──────────────────┤ │
│  │ 1  │ abridge │ Override │ 2026-03-04 14:22 │ │
│  │ 2  │ abridge │ Flag     │ 2026-03-04 11:08 │ │
│  └────┴─────────┴──────────┴──────────────────┘ │
└──────────────────────────────────────────────────┘
```

---

## Role-Based Behavior

| Capability                    | AD                 | Agent                | Coach               | Athlete            |
|-------------------------------|--------------------|-----------------------|---------------------|--------------------|
| View portal entries           | Conference-wide    | Full market           | Conference-wide     | Own status only    |
| Valuation predictions         | Yes                | Yes                   | Team context        | Personal only      |
| Add to pipeline               | Yes (recruiting)   | Yes (representation)  | Yes (recruiting)    | No                 |
| Interest indicators           | Conference-scoped  | Full market           | Team-scoped         | No                 |
| Destination impact model      | Yes                | Yes                   | Read-only           | Personal only      |
| Conference talent flow        | Yes                | Yes                   | Read-only           | No                 |
| Admin overrides               | No                 | No                    | No                  | No                 |
| Export portal data            | Yes                | Yes                   | No                  | No                 |

### Admin Access

Admin override controls are restricted to platform administrators with the `admin` role. This route (`/admin/transfer-portal`) is not visible to any standard user role.

---

## Basketball Portal Focus

### Transfer Window Dates (2025-26 Season)

| Window                | Open          | Close         | Context                      |
|-----------------------|---------------|---------------|------------------------------|
| Spring Window         | Apr 15, 2025  | May 1, 2025   | Post-season, pre-NBA draft   |
| Post-Tournament       | Mar 28, 2026  | Apr 15, 2026  | March Madness fallout        |

### March Madness to Portal Surge

```
┌──────────────────────────────────────────────────┐
│  TOURNAMENT → PORTAL SURGE TRACKER               │
│  ──────────────────────────────────────────────  │
│                                                  │
│  Tournament Ends:    Mar 27, 2026                │
│  Portal Opens:       Mar 28, 2026                │
│  Expected Entries:   200+ (basketball)           │
│                                                  │
│  SURGE TIMELINE                                  │
│                                                  │
│  Entries ─                                       │
│  80 ─ ─ ─ ─ ─ ─ ─╱╲─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │
│  60 ─ ─ ─ ─ ─ ─╱─ ─╲─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │
│  40 ─ ─ ─ ─ ─╱─ ─ ─ ─╲─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │
│  20 ─ ─ ─ ─╱─ ─ ─ ─ ─ ─╲╲╲─ ─ ─ ─ ─ ─ ─ ─  │
│   0 ────────────────────────────────────────── │
│      Mar 28  Mar 31  Apr 3   Apr 7   Apr 15    │
│                                                  │
│  ━━ Entries/day    ░░ Portal window              │
└──────────────────────────────────────────────────┘
```

---

## States

### Portal Closed (Off-Season)
```
┌──────────────────────────────────────────────────┐
│  TRANSFER PORTAL                   [○ Closed]    │
│                                                  │
│              [Portal icon, 48px, zinc-600]       │
│                                                  │
│              Transfer window is closed            │
│              Next window opens: Mar 28, 2026     │
│              47 days remaining                    │
│                                                  │
│              View historical portal data or       │
│              set alerts for the next window.      │
│                                                  │
│              [View History]  [Set Alert]          │
└──────────────────────────────────────────────────┘
```

### Portal Open (Active Window)
- Green status indicator in header
- Real-time entry counter updates
- Push notifications for new entries matching saved filters
- Countdown to window close date

### Individual Athlete States

| State       | Badge           | Description                             |
|-------------|-----------------|------------------------------------------|
| Entered     | ● In Portal     | Athlete has entered the portal           |
| Committed   | ✓ Committed     | Athlete committed to new school          |
| Withdrawn   | ← Withdrawn     | Athlete withdrew from portal             |
| Signed      | ✓ Signed        | Transfer finalized, enrolled at new school|

---

## Routes

| Route                               | Description                      |
|-------------------------------------|----------------------------------|
| `/dashboard/transfer-portal`        | Portal dashboard (role-filtered) |
| `/dashboard/transfer-portal/[id]`   | Athlete portal detail            |
| `/dashboard/transfer-portal/timeline`| Portal timeline view            |
| `/dashboard/transfer-portal/flow`   | Conference talent flow           |
| `/admin/transfer-portal`            | Admin override controls          |

---

## Design Tokens

| Token Family         | Example Tokens                                        |
|----------------------|-------------------------------------------------------|
| `--portal-*`         | `--portal-card-width`, `--portal-status-height`       |
| `--portal-window-*`  | `--portal-window-open-color`, `--portal-window-closed`|
| `--portal-status-*`  | `--portal-status-entered`, `--portal-status-committed`|
| `--portal-timeline-*`| `--portal-timeline-track`, `--portal-timeline-marker` |
| `--portal-flow-*`    | `--portal-flow-inbound`, `--portal-flow-outbound`     |

---

## Accessibility

- Filter controls are keyboard-navigable with visible focus indicators
- Portal status badges include text labels, not color alone
- Timeline is navigable with arrow keys; screen reader announces dates and events
- Card grid supports keyboard navigation (arrow keys between cards, Enter to open)
- Status changes announced via `aria-live="assertive"` for real-time updates
