# Notifications System Feature Spec

Last updated: 2026-03-04

---

## Overview

In-app and push notification system for NIL events, deal updates, valuation changes, and platform activity. Notifications are the real-time awareness layer — they surface the most important changes across the NIL Optic platform without requiring users to poll individual features. Every notification is actionable: it routes to the relevant feature surface on tap/click. Role-based filtering ensures each user only receives notifications relevant to their scope.

---

## Notification Bell

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  [Logo]  Dashboard  Pipeline  Directory   [🔔]  │  ← Top nav bar
│                                            (7)  │  ← Unread count badge
│                                                  │
└──────────────────────────────────────────────────┘
```

### Bell Anatomy

| Element          | Token / Style                           |
|------------------|-----------------------------------------|
| Bell icon        | 24px, white, `--z-index-header`         |
| Unread badge     | 18px min-width, `--color-brand-red` bg  |
| Badge text       | JetBrains Mono 10, white, bold          |
| Badge position   | Top-right of bell, -4px offset          |
| Bell hover       | zinc-700 circle bg, 36px                |
| Bell active      | `--color-brand-red` circle bg           |

### Badge Behavior

| Count    | Display  | Notes                              |
|----------|----------|------------------------------------|
| 0        | Hidden   | No badge shown                     |
| 1-99     | Number   | Exact count displayed              |
| 100+     | "99+"    | Capped display with overflow       |

---

## Notification Drawer

```
┌──────────────────────────────────────────────────┐
│                                    ┌─────────────┤
│                                    │NOTIFICATIONS│
│                                    │             │
│                                    │ [All] [Deals│
│                                    │ [Valuations]│
│                                    │ [Messages]  │
│                                    │ [System]    │
│                                    │             │
│                                    │ Mark all rea│
│  ┌─────────────────────────────────┤             │
│  │  (Main page content dimmed)     │─────────────│
│  │                                 │             │
│  │                                 │ ● Deal Stag │  ← Unread (bold)
│  │                                 │   M.Thompson│
│  │                                 │   deal moved│
│  │                                 │   to Negotia│
│  │                                 │   2h ago    │
│  │                                 │   [View Dea]│
│  │                                 │─────────────│
│  │                                 │   Valuation │  ← Read (regular)
│  │                                 │   K.Williams│
│  │                                 │   valuation │
│  │                                 │   up 12.4%  │
│  │                                 │   5h ago    │
│  │                                 │─────────────│
│  │                                 │ ● New Messag│
│  │                                 │   Coach Will│
│  │                                 │   sent a    │
│  │                                 │   message   │
│  │                                 │   6h ago    │
│  │                                 │─────────────│
│  │                                 │             │
│  │                                 │ [View All]  │
│  └─────────────────────────────────┴─────────────┘
└──────────────────────────────────────────────────┘
```

### Full Drawer (Expanded View)

```
┌──────────────────────────────────────────────────┐
│  NOTIFICATIONS                    [Mark All Read]│
│  ──────────────────────────────────────────────  │
│                                                  │
│  [All]  [Deals]  [Valuations]  [Messages]  [Sys]│  ← Filter tabs
│   ●                                              │
│                                                  │
│  TODAY                                           │
│  ┌──────────────────────────────────────────────┐│
│  │ ● [📊]  Deal Stage Change           2h ago  ││  ← Unread indicator
│  │         M. Thompson deal moved to            ││
│  │         "Negotiation" stage                   ││
│  │         [View Deal →]                        ││
│  ├──────────────────────────────────────────────┤│
│  │ ● [📈]  Valuation Spike              5h ago  ││
│  │         K. Williams valuation up 12.4%       ││
│  │         in the last 24 hours                  ││
│  │         [View Athlete →]                     ││
│  ├──────────────────────────────────────────────┤│
│  │ ● [💬]  New Message                  6h ago  ││
│  │         New message from Coach Williams      ││
│  │         in "Nike Deal Discussion"             ││
│  │         [Open Thread →]                      ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  YESTERDAY                                       │
│  ┌──────────────────────────────────────────────┐│
│  │   [🏀]  Tournament Update          18h ago  ││  ← Read (no dot)
│  │         Kentucky advances to Sweet 16 —      ││
│  │         NIL impact: +8.2%                     ││
│  │         [View Tournament →]                  ││
│  ├──────────────────────────────────────────────┤│
│  │   [🔄]  Transfer Portal              1d ago  ││
│  │         J. Proctor entered the transfer      ││
│  │         portal from UConn                     ││
│  │         [View in Portal →]                   ││
│  ├──────────────────────────────────────────────┤│
│  │   [⚠]   Compliance Alert            1d ago  ││
│  │         Compliance review needed:             ││
│  │         Nike deal for M. Thompson             ││
│  │         [Review Compliance →]                ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [Load More]                                     │
└──────────────────────────────────────────────────┘
```

### Drawer Anatomy

| Element                 | Token / Style                          |
|-------------------------|----------------------------------------|
| Drawer panel            | zinc-900 bg, 360px width, right-slide  |
| Drawer overlay          | black at 50% opacity                   |
| Filter tab (active)     | `--color-brand-red` underline, white   |
| Filter tab (inactive)   | zinc-400 text, no underline            |
| Section header ("Today")| Inter Semi-Bold 11, zinc-500, uppercase|
| Mark all read           | Inter Medium 13, zinc-400, underline   |
| View all link           | Inter Medium 13, `--color-brand-red`   |
| Notification divider    | zinc-800, 1px height                   |

---

## Notification Card Anatomy

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  ● [📊]  Deal Stage Change              2h ago  │
│                                                  │
│     M. Thompson deal moved to                    │
│     "Negotiation" stage                          │
│                                                  │
│     [View Deal →]                                │
│                                                  │
└──────────────────────────────────────────────────┘
```

### Card Element Map

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  [A] [B]  [C]                            [D]    │
│                                                  │
│       [E]                                        │
│       [E continued, 2 lines max]                 │
│                                                  │
│       [F]                                        │
│                                                  │
└──────────────────────────────────────────────────┘

A = Unread indicator (red dot, 8px)
B = Category icon (20px, category color)
C = Title (Inter Semi-Bold 14, white)
D = Timestamp (JetBrains Mono 11, zinc-500)
E = Body (Inter Regular 13, zinc-400, 2 lines max)
F = Action button (Inter Medium 12, --color-brand-red)
```

### Card Tokens

| Element              | Token / Style                          |
|----------------------|----------------------------------------|
| Card (unread)        | zinc-800 bg, white text                |
| Card (read)          | zinc-900 bg, zinc-400 text             |
| Unread dot           | 8px circle, `--color-brand-red`        |
| Category icon        | 20px, category-specific color          |
| Title (unread)       | Inter Semi-Bold 14, white              |
| Title (read)         | Inter Regular 14, zinc-400             |
| Body preview         | Inter Regular 13, zinc-400, 2-line clamp|
| Timestamp            | JetBrains Mono 11, zinc-500, relative  |
| Action button        | Inter Medium 12, `--color-brand-red`   |
| Card padding         | 12px horizontal, 10px vertical         |
| Card hover           | zinc-750 bg                            |

### Category Icons and Colors

| Category       | Icon  | Color              |
|----------------|-------|--------------------|
| Deals          | 📊    | `--color-brand-red`|
| Valuations     | 📈    | `#16A34A` (green)  |
| Messages       | 💬    | `#3B82F6` (blue)   |
| Compliance     | ⚠     | `#F59E0B` (amber)  |
| Tournaments    | 🏀    | `#8B5CF6` (purple) |
| Transfer Portal| 🔄    | `#06B6D4` (cyan)   |
| System         | ⚙     | zinc-400           |
| Predictions    | 🎯    | `#EC4899` (pink)   |

---

## Push Notifications (Mobile — NILWatch)

### Permission Prompt

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │         [NIL Optic Logo]                     ││
│  │                                              ││
│  │     Stay ahead of the NIL market             ││
│  │                                              ││
│  │     Get real-time alerts for deal updates,   ││
│  │     valuation spikes, and tournament news.   ││
│  │                                              ││
│  │     ┌──────────┐  ┌──────────┐              ││
│  │     │ Not Now  │  │ Enable   │              ││
│  │     └──────────┘  └──────────┘              ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
└──────────────────────────────────────────────────┘
```

### Lock Screen Notification

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  3:47 PM                                         │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │ [NIL Icon]  NIL Optic             now       ││
│  │                                              ││
│  │ Valuation Spike                              ││
│  │ K. Williams valuation up 12.4% — Duke       ││
│  │ advances to Sweet 16                         ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │ [NIL Icon]  NIL Optic             2m ago    ││
│  │                                              ││
│  │ Deal Update                                  ││
│  │ M. Thompson deal moved to Negotiation        ││
│  └──────────────────────────────────────────────┘│
│                                                  │
└──────────────────────────────────────────────────┘
```

### Deep-Link Routing

| Notification Type   | Deep-Link Target                       |
|---------------------|----------------------------------------|
| Deal stage change   | `/dashboard/pipelines`                 |
| Valuation spike     | `/athletes/[playerId]`                 |
| New message         | `/dashboard/messages/[threadId]`       |
| Invite received     | `/dashboard/notifications`             |
| Compliance alert    | `/dashboard/compliance/deal/[dealId]`  |
| Tournament update   | `/dashboard/tournaments`               |
| Transfer portal     | `/dashboard/transfer-portal/[id]`      |
| Prediction alert    | `/predictions`                         |
| System              | N/A (informational only)               |

### Push Categories (iOS/Android)

| Category       | Badge | Sound   | Priority   |
|----------------|-------|---------|------------|
| Deals          | Yes   | Default | High       |
| Valuations     | Yes   | Default | High       |
| Messages       | Yes   | Chime   | Medium     |
| Compliance     | Yes   | Alert   | High       |
| Tournaments    | Yes   | Default | Medium     |
| Transfer Portal| Yes   | Default | High       |
| Predictions    | No    | Silent  | Low        |
| System         | No    | Silent  | Low        |

---

## Notification Types

| Type                | Trigger                      | Title Pattern                           | Route                          | Priority |
|---------------------|------------------------------|-----------------------------------------|--------------------------------|----------|
| Deal stage change   | Pipeline record moves        | "{Athlete} deal moved to {Stage}"       | `/dashboard/pipelines`         | High     |
| Valuation spike     | >10% change in 24h           | "{Athlete} valuation up {X}%"           | `/athletes/[id]`               | High     |
| Valuation drop      | >10% decline in 24h          | "{Athlete} valuation down {X}%"         | `/athletes/[id]`               | High     |
| New message         | Thread message received      | "New message from {Sender}"             | `/dashboard/messages/[id]`     | Medium   |
| Invite received     | Org/program invite           | "You've been invited to {Org}"          | `/dashboard/notifications`     | High     |
| Compliance alert    | Deal flagged                 | "Compliance review needed: {Deal}"      | `/dashboard/compliance`        | High     |
| Compliance cleared  | Deal passes review           | "{Deal} compliance approved"            | `/dashboard/compliance`        | Low      |
| Tournament update   | March Madness game result    | "{Team} advances — NIL impact: +{X}%"  | `/dashboard/tournaments`       | Medium   |
| Tournament elim     | Team eliminated              | "{Team} eliminated — impact: -{X}%"     | `/dashboard/tournaments`       | Medium   |
| Transfer portal     | Athlete enters portal        | "{Athlete} entered transfer portal"     | `/dashboard/transfer-portal`   | High     |
| Transfer committed  | Portal athlete commits       | "{Athlete} committed to {School}"       | `/dashboard/transfer-portal`   | Medium   |
| Prediction alert    | New prediction available     | "New prediction: {Athlete}"             | `/predictions`                 | Low      |
| System maintenance  | Scheduled maintenance        | "Scheduled maintenance: {Date}"         | N/A                            | Low      |
| System update       | Feature release              | "New feature: {Feature Name}"           | N/A                            | Low      |

---

## Role-Based Notification Filtering

| Notification Type        | AD                | Agent               | Athlete            | Coach              | Fan                |
|--------------------------|-------------------|----------------------|--------------------|--------------------|--------------------|
| Deal stage change        | All program deals | Client deals only    | Own deals only     | No                 | No                 |
| Valuation spike/drop     | Program athletes  | Client athletes      | Personal only      | Team athletes      | Favorites only     |
| New message              | All threads       | All threads          | Own threads        | Program threads    | No                 |
| Invite received          | Yes               | Yes                  | Yes                | Yes                | No                 |
| Compliance alert         | All program       | Client deals         | Own deals          | Team overview      | No                 |
| Tournament update        | Conference teams  | Client impact        | Personal impact    | Team impact        | All teams          |
| Transfer portal          | Conference-wide   | Market-wide          | Own status         | Team roster impact | No                 |
| Prediction alert         | Program athletes  | Client athletes      | Personal only      | Team athletes      | No                 |
| System                   | Yes               | Yes                  | Yes                | Yes                | Yes                |

---

## Notification Preferences

```
┌──────────────────────────────────────────────────┐
│  NOTIFICATION PREFERENCES                        │
│  ──────────────────────────────────────────────  │
│                                                  │
│  CATEGORIES                                      │
│  ┌──────────────────────────────────────────────┐│
│  │                  In-App    Push     Email    ││
│  │  Deals           [●]       [●]      [○]     ││
│  │  Valuations      [●]       [●]      [●]     ││
│  │  Messages        [●]       [●]      [○]     ││
│  │  Compliance      [●]       [●]      [●]     ││
│  │  Tournaments     [●]       [○]      [○]     ││
│  │  Transfer Portal [●]       [●]      [○]     ││
│  │  Predictions     [●]       [○]      [○]     ││
│  │  System          [●]       [○]      [○]     ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [●] = Enabled    [○] = Disabled                │
│                                                  │
│  ──────────────────────────────────────────────  │
│                                                  │
│  QUIET HOURS                                     │
│  ┌──────────────────────────────────────────────┐│
│  │  Enable quiet hours:     [●━━━━━━━━━━] On   ││
│  │                                              ││
│  │  Start time:  [10:00 PM  ▼]                  ││
│  │  End time:    [7:00 AM   ▼]                  ││
│  │                                              ││
│  │  During quiet hours:                         ││
│  │  • Push notifications silenced               ││
│  │  • In-app notifications still collected      ││
│  │  • High-priority alerts bypass quiet hours   ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [Save Preferences]                              │
└──────────────────────────────────────────────────┘
```

### Preferences Anatomy

| Element              | Token / Style                          |
|----------------------|----------------------------------------|
| Category row         | zinc-800 bg, 48px height, 12px pad     |
| Category label       | Inter Medium 14, white                 |
| Toggle (enabled)     | `--color-brand-red` bg, white circle   |
| Toggle (disabled)    | zinc-600 bg, zinc-400 circle           |
| Column header        | Inter Semi-Bold 11, zinc-500, uppercase|
| Quiet hours toggle   | Same as category toggles               |
| Time dropdown        | zinc-700 bg, `--radius-sm`, 40px h     |
| Save button          | Primary, `--color-brand-red` bg        |

---

## Route

| Route                          | Description                      |
|--------------------------------|----------------------------------|
| `/dashboard/notifications`     | Full notifications inbox         |
| `/dashboard/notifications/preferences` | Notification preferences  |

---

## States

### No Notifications (Empty)
```
┌──────────────────────────────────────────────────┐
│  NOTIFICATIONS                                   │
│                                                  │
│              [Bell icon, 48px, zinc-600]         │
│                                                  │
│              No notifications yet                │
│              You'll see updates here when         │
│              deals move, valuations change,       │
│              or teammates send messages.          │
│                                                  │
│              [Explore Dashboard]                  │
└──────────────────────────────────────────────────┘
```

### Has Unread
- Bell badge shows count
- Unread notifications have bold titles and red dot indicator
- Drawer opens to unread section by default
- "Mark all read" action visible at top

### All Read
- No bell badge
- All notification cards in regular weight
- Section headers still visible (Today, Yesterday, etc.)

### Notification Loading
```
┌──────────────────────────────────────────────────┐
│  NOTIFICATIONS                                   │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ││
│  │  ░░░░░░░░░░░░░░░░░░░░░░░░                   ││
│  ├──────────────────────────────────────────────┤│
│  │  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ││
│  │  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░              ││
│  ├──────────────────────────────────────────────┤│
│  │  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ││
│  │  ░░░░░░░░░░░░░░░░                           ││
│  └──────────────────────────────────────────────┘│
└──────────────────────────────────────────────────┘
```

---

## Design Tokens

| Token Family            | Example Tokens                                       |
|-------------------------|------------------------------------------------------|
| `--notification-*`      | `--notification-drawer-width`, `--notification-card-padding` |
| `--notification-bell-*` | `--notification-bell-size`, `--notification-bell-badge-size` |
| `--notification-card-*` | `--notification-card-unread-bg`, `--notification-card-read-bg` |
| `--notification-cat-*`  | `--notification-cat-deals`, `--notification-cat-valuations` |
| `--notification-pref-*` | `--notification-pref-toggle-size`, `--notification-pref-row-height` |

---

## Accessibility

- Bell icon has `aria-label="Notifications, {count} unread"` with dynamic count
- Drawer panel has `role="dialog"` with `aria-label="Notification drawer"`
- Filter tabs use `role="tablist"` with `aria-selected` state
- Each notification card is a focusable region with full text read by screen reader
- Unread status announced: "Unread notification: {title}"
- Mark all read action confirmed with `aria-live="assertive"` announcement
- Push notification permission prompt is keyboard-navigable
- Quiet hours toggle announces state change
- Preference toggles have explicit `aria-label` including category and channel
