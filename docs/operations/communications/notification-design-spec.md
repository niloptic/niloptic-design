# TITAN IX: HERALD -- Notification Design Specification

Last updated: 2026-03-04

---

## Overview

Complete design specification for all in-app and push notification surfaces across the NIL Optic platform. This document extends the existing Notifications System Feature Spec (`design-system/05_Features/notifications.md`) with expanded notification types, the full role-based notification matrix, priority level definitions, preference UI specifications, basketball-specific notification patterns, and accessibility requirements.

**This is a design specification and operational document -- not code.**

**Reference routes:**
- `/dashboard/notifications` -- In-app notifications inbox
- `/dashboard/notifications/preferences` -- Notification preferences
- `/api/notifications` -- List in-app notifications
- `/api/notifications/read` -- Mark notifications as read

---

## 1. In-App Notification Types

The following table defines every notification type surfaced within the NIL Optic platform. Each type has a trigger condition, display pattern, routing behavior, and priority classification.

### 1.1 Complete Notification Type Registry

| # | Type | Trigger | Title Pattern | Body Pattern | Route | Priority | Category |
|---|---|---|---|---|---|---|---|
| 1 | Valuation spike | Athlete valuation increases > 10% in 24h | `{Athlete} valuation up {X}%` | `{Athlete} at {School} saw a {X}% increase driven by {Reason}` | `/athletes/[id]` | High | Valuations |
| 2 | Valuation drop | Athlete valuation decreases > 10% in 24h | `{Athlete} valuation down {X}%` | `{Athlete} at {School} declined {X}% due to {Reason}` | `/athletes/[id]` | High | Valuations |
| 3 | Deal stage change | Pipeline record moves to new stage | `{Athlete} deal moved to {Stage}` | `{Brand} deal for {Athlete} advanced to "{Stage}" stage` | `/dashboard/pipelines` | High | Deals |
| 4 | Deal signed | Deal reaches "Signed" stage | `Deal signed: {Athlete} x {Brand}` | `${Amount} deal between {Athlete} and {Brand} is now signed` | `/dashboard/pipelines` | High | Deals |
| 5 | Deal expired | Deal contract passes expiration date | `Deal expired: {Athlete} x {Brand}` | `The {Brand} deal for {Athlete} expired on {Date}. Action needed.` | `/dashboard/pipelines` | High | Deals |
| 6 | New message | Thread message received from another user | `New message from {Sender}` | `{Sender} in "{ThreadName}": "{Preview...}"` | `/dashboard/messages/[threadId]` | Medium | Messages |
| 7 | Meet invite | User invited to a 1:1 or group meet | `{Inviter} invited you to a meet` | `Join a meet about "{Topic}" with {Inviter} and {X} others` | `/dashboard/meet/[meetId]` | Medium | Messages |
| 8 | Huddle invite | User invited to a huddle room | `{Inviter} started a huddle: {Topic}` | `Join the huddle "{Topic}" with {ParticipantCount} participants` | `/dashboard/huddles/[huddleId]` | Medium | Messages |
| 9 | Pipeline prospect update | New prospect added or prospect status changes | `New prospect: {Athlete} added to pipeline` | `{Athlete} ({School}, {Position}) added to your recruiting pipeline` | `/dashboard/pipelines` | Medium | Deals |
| 10 | Compliance alert | Deal flagged for compliance review | `Compliance review needed: {Deal}` | `{Brand} deal for {Athlete} requires compliance review. Reason: {Flag}` | `/dashboard/compliance/deal/[dealId]` | Critical | Compliance |
| 11 | Compliance cleared | Deal passes compliance review | `{Deal} compliance approved` | `The {Brand} deal for {Athlete} has passed compliance review` | `/dashboard/compliance` | Low | Compliance |
| 12 | Compliance deadline | Compliance deadline approaching (72h) | `Compliance deadline in {X} days` | `{Deal} compliance review due by {Date}. Current status: {Status}` | `/dashboard/compliance` | High | Compliance |
| 13 | Prediction ready | New prediction model output available | `New prediction: {Athlete}` | `Updated NIL prediction for {Athlete}: projected {Direction} {X}% over {Period}` | `/predictions` | Low | System |
| 14 | Roster change | Athlete added/removed from program roster | `Roster update: {Athlete} {Action}` | `{Athlete} has been {added to/removed from} {Program} roster` | `/dashboard/roster` | Medium | System |
| 15 | Transfer portal entry | Athlete enters the NCAA transfer portal | `{Athlete} entered transfer portal` | `{Athlete} ({School}, {Position}) has entered the transfer portal` | `/dashboard/transfer-portal/[id]` | High | Transfer Portal |
| 16 | Transfer portal commit | Portal athlete commits to a school | `{Athlete} committed to {School}` | `{Athlete} has committed to {School} from the transfer portal` | `/dashboard/transfer-portal/[id]` | Medium | Transfer Portal |
| 17 | Tournament bracket update | March Madness game result with NIL impact | `{Team} advances -- NIL impact: +{X}%` | `{Team} defeated {Opponent} in {Round}. Program valuation impact: {X}%` | `/dashboard/tournaments` | Medium | Tournaments |
| 18 | Tournament elimination | Team eliminated from tournament | `{Team} eliminated -- impact: -{X}%` | `{Team} eliminated in {Round}. Program valuation impact: -{X}%` | `/dashboard/tournaments` | Medium | Tournaments |
| 19 | Team invite | User invited to join an organization/program | `You've been invited to {Org}` | `{Inviter} invited you to join {Org} as {Role}. Expires {Date}.` | `/dashboard/notifications` | High | System |
| 20 | System announcement | Platform-wide or role-specific announcement | `{AnnouncementTitle}` | `{AnnouncementBody}` | Varies or N/A | Low | System |
| 21 | System maintenance | Scheduled maintenance window approaching | `Scheduled maintenance: {Date}` | `NIL Optic will be unavailable {Date} from {Start} to {End} ET` | N/A | Low | System |
| 22 | Feature release | New platform feature deployed | `New feature: {FeatureName}` | `{Description}. Try it now.` | Feature route | Low | System |
| 23 | Budget threshold | Program NIL budget utilization exceeds threshold | `Budget alert: {X}% utilized` | `{Program} has used {X}% of the {Period} NIL budget (${Used} of ${Total})` | `/dashboard/budget` | High | Compliance |
| 24 | Conference tournament result | Conference tournament game outcome | `{ConferenceName}: {Team} {Outcome}` | `{Team} {won/lost} in {ConferenceName} tournament {Round}` | `/dashboard/tournaments` | Medium | Tournaments |

---

## 2. Notification Card Anatomy

### 2.1 Card Wireframe

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  [A] [B]  [C]                                  [D]  │
│           [E ──────────────────────── 2 lines max]  │
│                                                      │
│       [F]  [G]                                       │
│                                                      │
└──────────────────────────────────────────────────────┘

A = Unread indicator dot
    - 8px circle, --color-brand-red (#DC2626)
    - Hidden when notification is read

B = Category icon
    - 20px, category-specific color
    - See Category Icon Map (Section 2.2)

C = Title
    - Unread: Inter Semi-Bold 14, white (#FFFFFF)
    - Read: Inter Regular 14, zinc-400 (#A1A1AA)

D = Timestamp
    - JetBrains Mono 11, zinc-500 (#71717A)
    - Relative format: "2h ago", "1d ago", "Mar 4"
    - Switches to absolute date after 7 days

E = Body preview
    - Inter Regular 13, zinc-400 (#A1A1AA)
    - 2-line clamp with ellipsis overflow
    - Max 140 characters

F = Role badge (optional, shown in multi-role contexts)
    - 4px radius pill, zinc-600 bg, zinc-300 text
    - Inter Medium 10, uppercase
    - Examples: "AD", "AGENT", "COACH"

G = Action button
    - Inter Medium 12, --color-brand-red (#DC2626)
    - Text link style with arrow: "View Deal →"
    - Hover: underline
```

### 2.2 Category Icon Map

| Category | Icon | Color | Hex |
|---|---|---|---|
| Deals | Chart bar | `--color-brand-red` | `#DC2626` |
| Valuations | Trending up/down | Positive green / Negative red | `#16A34A` / `#DC2626` |
| Messages | Message bubble | Blue | `#3B82F6` |
| Compliance | Warning triangle | Amber | `#F59E0B` |
| Tournaments | Basketball | Purple | `#8B5CF6` |
| Transfer Portal | Refresh/cycle | Cyan | `#06B6D4` |
| System | Settings gear | Zinc | `#A1A1AA` |
| Predictions | Target/crosshair | Pink | `#EC4899` |

### 2.3 Card States

| State | Background | Title Weight | Indicator | Interaction |
|---|---|---|---|---|
| Unread | zinc-800 (`#27272A`) | Semi-Bold | Red dot visible | Click marks as read + navigates |
| Read | zinc-900 (`#18181B`) | Regular | No dot | Click navigates |
| Hover | zinc-750 (`#323238`) | Inherit | Inherit | Cursor pointer |
| Focused | zinc-800 + red outline 2px | Inherit | Inherit | Keyboard focus ring |
| Pressed | zinc-700 (`#3F3F46`) | Inherit | Inherit | 100ms feedback |

### 2.4 Card Design Tokens

| Token | Value | Usage |
|---|---|---|
| `--notification-card-unread-bg` | `#27272A` (zinc-800) | Unread card background |
| `--notification-card-read-bg` | `#18181B` (zinc-900) | Read card background |
| `--notification-card-hover-bg` | `#323238` (zinc-750) | Card hover state |
| `--notification-card-padding-x` | `12px` | Horizontal padding |
| `--notification-card-padding-y` | `10px` | Vertical padding |
| `--notification-card-min-height` | `72px` | Minimum card height |
| `--notification-card-gap` | `0px` | No gap between cards (divider only) |
| `--notification-card-divider` | `#27272A` (zinc-800), 1px | Separator between cards |
| `--notification-unread-dot` | `#DC2626`, 8px circle | Unread indicator |
| `--notification-icon-size` | `20px` | Category icon size |
| `--notification-title-unread` | Inter Semi-Bold 14, `#FFFFFF` | Unread title style |
| `--notification-title-read` | Inter Regular 14, `#A1A1AA` | Read title style |
| `--notification-body` | Inter Regular 13, `#A1A1AA` | Body preview style |
| `--notification-timestamp` | JetBrains Mono 11, `#71717A` | Timestamp style |
| `--notification-action` | Inter Medium 12, `#DC2626` | Action button text |

---

## 3. Notification Drawer

### 3.1 Drawer Wireframe (Collapsed -- Right Slide-Out)

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│  [Main Application Content]                   ┌─────────────────┤
│                                               │  NOTIFICATIONS  │
│  ┌────────────────────────────────────────────│                 │
│  │                                            │  [All] [Deals]  │
│  │  (Dimmed overlay, 50% black opacity)       │  [Compliance]   │
│  │                                            │  [System]       │
│  │                                            │                 │
│  │                                            │  Mark all read  │
│  │                                            │                 │
│  │                                            │─────────────────│
│  │                                            │  TODAY          │
│  │                                            │                 │
│  │                                            │  ● [D] Deal Sta.│
│  │                                            │    M.Thompson   │
│  │                                            │    deal moved   │
│  │                                            │    to Negotiat. │
│  │                                            │    2h ago       │
│  │                                            │    [View Deal→] │
│  │                                            │─────────────────│
│  │                                            │    [V] Valuat.  │
│  │                                            │    K.Williams   │
│  │                                            │    valuation    │
│  │                                            │    up 12.4%     │
│  │                                            │    5h ago       │
│  │                                            │─────────────────│
│  │                                            │  ● [M] New Msg  │
│  │                                            │    Coach Willi. │
│  │                                            │    sent a       │
│  │                                            │    message      │
│  │                                            │    6h ago       │
│  │                                            │─────────────────│
│  │                                            │                 │
│  │                                            │  YESTERDAY      │
│  │                                            │                 │
│  │                                            │    [B] Tourney  │
│  │                                            │    Kentucky adv │
│  │                                            │    NIL +8.2%    │
│  │                                            │─────────────────│
│  │                                            │                 │
│  │                                            │  [View All]     │
│  │                                            │  [Preferences]  │
│  └────────────────────────────────────────────┴─────────────────┘
└──────────────────────────────────────────────────────────────────┘
```

### 3.2 Drawer Specifications

| Property | Value |
|---|---|
| Width | 360px (desktop), 100vw (mobile) |
| Position | Fixed, right edge of viewport |
| Animation | Slide in from right, 200ms ease-out |
| Dismiss animation | Slide out to right, 150ms ease-in |
| Overlay | `rgba(0, 0, 0, 0.50)` -- click to dismiss |
| Z-index | `--z-index-overlay` (above content, below modals) |
| Max notifications shown | 20 per load, infinite scroll with "Load more" |
| Background | zinc-900 (`#18181B`) |

### 3.3 Drawer Header

```
┌──────────────────────────────────────────────────────┐
│  NOTIFICATIONS                      [Mark All Read]  │
│  ────────────────────────────────────────────────── │
│                                                      │
│  [All]  [Deals]  [Compliance]  [Messages]  [System]  │
│   ●                                                  │
└──────────────────────────────────────────────────────┘
```

| Element | Token / Style |
|---|---|
| Title "NOTIFICATIONS" | Inter Semi-Bold 16, white, uppercase |
| "Mark All Read" link | Inter Medium 13, zinc-400, underline on hover |
| Filter tab (active) | Inter Medium 13, white, `--color-brand-red` underline 2px |
| Filter tab (inactive) | Inter Medium 13, zinc-400, no underline |
| Tab bar | 48px height, zinc-800 bottom border 1px |
| Unread indicator on tab | 6px red dot, top-right of tab label |

### 3.4 Filter Tab Categories

| Tab | Includes Notification Types |
|---|---|
| All | Every notification type |
| Deals | Deal stage change, deal signed, deal expired, pipeline prospect update |
| Compliance | Compliance alert, compliance cleared, compliance deadline, budget threshold |
| Messages | New message, meet invite, huddle invite |
| System | Roster change, team invite, system announcement, maintenance, feature release, prediction ready |

**Note:** Tournament and Transfer Portal notifications appear under the "All" tab and are not given a dedicated tab unless the user's role has > 5 tournament/portal notifications in the last 30 days, in which case a dynamic "Basketball" tab surfaces.

### 3.5 Section Headers

Notifications are grouped by time period:

| Section | Criteria |
|---|---|
| Today | Notifications received in the current calendar day (user local time) |
| Yesterday | Notifications received in the previous calendar day |
| This Week | Notifications from the current week (Mon-Sun), excluding Today and Yesterday |
| Earlier | All notifications older than the current week |

Section header style: Inter Semi-Bold 11, zinc-500 (`#71717A`), uppercase, 8px bottom padding.

### 3.6 Drawer Footer

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  [View All Notifications]                            │
│  [Notification Preferences]                          │
│                                                      │
└──────────────────────────────────────────────────────┘
```

| Element | Route | Style |
|---|---|---|
| View All | `/dashboard/notifications` | Inter Medium 13, `--color-brand-red` |
| Preferences | `/dashboard/notifications/preferences` | Inter Medium 13, zinc-400 |

---

## 4. Notification Bell

### 4.1 Bell Wireframe

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│  [Logo]  Dashboard  Pipeline  Directory      [B]   │
│                                              (7)   │
│                                                     │
└─────────────────────────────────────────────────────┘

B = Bell icon (24px, white, Lucide "bell" icon)
(7) = Unread badge
```

### 4.2 Bell Specifications

| Element | Specification |
|---|---|
| Bell icon | Lucide `bell`, 24px, white (`#FFFFFF`) |
| Bell hover | 36px circle background, zinc-700 (`#3F3F46`) |
| Bell active (drawer open) | 36px circle background, `--color-brand-red` (`#DC2626`) |
| Badge | 18px min-width circle, `--color-brand-red` background |
| Badge text | JetBrains Mono 10, white, bold, centered |
| Badge position | Top-right of bell, offset -4px up and -4px right |
| Badge animation | Scale-in 200ms ease-out on new notification |

### 4.3 Badge Count Display

| Count Range | Display | Notes |
|---|---|---|
| 0 | Hidden | No badge rendered |
| 1 -- 99 | Exact number | `"7"`, `"42"`, `"99"` |
| 100+ | `"99+"` | Overflow cap with indicator |

---

## 5. Push Notifications (NILWatch Mobile App)

### 5.1 Push Permission Prompt

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  ┌──────────────────────────────────────────────────┐│
│  │                                                  ││
│  │              [NIL Optic Logo]                    ││
│  │              120px, centered                     ││
│  │                                                  ││
│  │     Stay ahead of the NIL market                 ││
│  │     Inter Semi-Bold 20, white                    ││
│  │                                                  ││
│  │     Get real-time alerts for:                    ││
│  │     - Deal updates and deadlines                 ││
│  │     - Valuation spikes and drops                 ││
│  │     - Tournament news and bracket impact         ││
│  │     - Compliance flags                           ││
│  │     Inter Regular 14, zinc-400                   ││
│  │                                                  ││
│  │     ┌────────────┐   ┌────────────┐             ││
│  │     │  Not Now   │   │  Enable    │             ││
│  │     │  Ghost btn │   │  Red CTA   │             ││
│  │     └────────────┘   └────────────┘             ││
│  │                                                  ││
│  └──────────────────────────────────────────────────┘│
│                                                      │
└──────────────────────────────────────────────────────┘
```

**Prompt trigger:** Shown after user completes onboarding (never during onboarding wizard). For athletes, shown after they view their first valuation. For ADs, shown after first dashboard visit.

**"Not Now" behavior:** Dismiss prompt. Re-prompt after 7 days on next app open. Maximum 3 prompt attempts. After 3 declines, never prompt again (user must enable via Preferences).

### 5.2 Push Notification Categories

| Category | Badge | Sound | Priority | Allowed During Quiet Hours |
|---|---|---|---|---|
| Deals | Yes | Default | High | No |
| Valuations | Yes | Default | High | No |
| Messages | Yes | Chime | Medium | No |
| Compliance | Yes | Alert tone | Critical | Yes (Critical bypasses) |
| Tournaments | Yes | Default | Medium | No |
| Transfer Portal | Yes | Default | High | No |
| Predictions | No | Silent | Low | No |
| System | No | Silent | Low | No |

### 5.3 Push Notification Anatomy (Lock Screen)

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  ┌──────────────────────────────────────────────────┐│
│  │ [NIL Icon]  NIL Optic               now         ││
│  │  16x16      Inter Semi-Bold 13     JBMono 11    ││
│  │                                                  ││
│  │ Valuation Spike                                  ││
│  │ Inter Semi-Bold 15, white                        ││
│  │                                                  ││
│  │ K. Williams valuation up 12.4% -- Duke          ││
│  │ advances to Sweet 16                             ││
│  │ Inter Regular 13, zinc-300, 2-line clamp         ││
│  └──────────────────────────────────────────────────┘│
│                                                      │
└──────────────────────────────────────────────────────┘
```

### 5.4 Push Deep-Link Routing

| Notification Type | Deep-Link Target | Screen |
|---|---|---|
| Deal stage change | `niloptic://dashboard/pipelines?dealId={id}` | Deal detail in pipeline |
| Valuation spike/drop | `niloptic://athletes/{playerId}` | Athlete profile |
| New message | `niloptic://dashboard/messages/{threadId}` | Thread detail |
| Meet invite | `niloptic://dashboard/meet/{meetId}` | Meet room or join prompt |
| Huddle invite | `niloptic://dashboard/huddles/{huddleId}` | Huddle room |
| Compliance alert | `niloptic://dashboard/compliance/deal/{dealId}` | Compliance review |
| Tournament update | `niloptic://dashboard/tournaments` | Tournament dashboard |
| Transfer portal | `niloptic://dashboard/transfer-portal/{id}` | Portal athlete detail |
| Team invite | `niloptic://dashboard/notifications` | Notification inbox |
| Prediction ready | `niloptic://predictions` | Predictions dashboard |
| System announcement | N/A | Opens app to last screen |

### 5.5 Quiet Hours

| Setting | Default | Range |
|---|---|---|
| Enable quiet hours | Off | Toggle on/off |
| Start time | 10:00 PM | User local time, 15-min increments |
| End time | 7:00 AM | User local time, 15-min increments |
| During quiet hours | Push notifications silenced; in-app still collected | -- |
| Critical override | Compliance violations and P1 incidents bypass quiet hours | -- |
| Badge behavior | Badges still accumulate during quiet hours | -- |

---

## 6. Role-Based Notification Matrix

The following matrix defines which notification types are delivered to which roles. Scope qualifiers indicate the data boundary for each role.

| Notification Type | AD | Asst AD | GM | Agent | Athlete | Coach | Agency Admin | Affiliate Admin | Affiliate | Fan | Admin |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Valuation spike | Program athletes | Program athletes | Program athletes | Client athletes | Own only | Team athletes | Agency clients | -- | -- | Favorites | All |
| Valuation drop | Program athletes | Program athletes | Program athletes | Client athletes | Own only | Team athletes | Agency clients | -- | -- | Favorites | All |
| Deal stage change | All program deals | All program deals | All program deals | Client deals | Own deals | -- | Agency deals | -- | -- | -- | All |
| Deal signed | All program deals | All program deals | All program deals | Client deals | Own deals | Read-only | Agency deals | -- | -- | -- | All |
| Deal expired | All program deals | All program deals | All program deals | Client deals | Own deals | -- | Agency deals | -- | -- | -- | All |
| New message | All threads | All threads | All threads | All threads | Own threads | Program threads | Agency threads | Affiliate threads | Own threads | -- | All |
| Meet invite | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | -- | -- | Yes |
| Huddle invite | Yes | Yes | Yes | Yes | Join only | Yes | Yes | Yes | -- | -- | Yes |
| Pipeline prospect | Program pipeline | Program pipeline | Program pipeline | Client pipeline | -- | Team pipeline | Agency pipeline | -- | -- | -- | All |
| Compliance alert | All program | All program | All program | Client deals | Own deals | Team overview | Agency deals | -- | -- | -- | All |
| Compliance cleared | All program | All program | All program | Client deals | Own deals | -- | Agency deals | -- | -- | -- | All |
| Compliance deadline | All program | All program | All program | Client deals | Own deals | -- | Agency deals | -- | -- | -- | All |
| Prediction ready | Program athletes | Program athletes | Program athletes | Client athletes | Own only | Team athletes | -- | -- | -- | -- | All |
| Roster change | Program roster | Program roster | Program roster | -- | Own status | Team roster | -- | -- | -- | -- | All |
| Transfer portal entry | Conference-wide | Conference-wide | Conference-wide | Market-wide | Own status | Team impact | Market-wide | -- | -- | -- | All |
| Transfer portal commit | Conference-wide | Conference-wide | Conference-wide | Market-wide | -- | Team impact | Market-wide | -- | -- | -- | All |
| Tournament bracket | Conference teams | Conference teams | Conference teams | Client impact | Personal impact | Team impact | Client impact | -- | -- | All teams | All |
| Tournament elimination | Conference teams | Conference teams | Conference teams | Client impact | Personal impact | Team impact | Client impact | -- | -- | All teams | All |
| Team invite | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | -- | Yes |
| System announcement | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| System maintenance | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| Feature release | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| Budget threshold | Own program | Own program | Own program | -- | -- | -- | Agency budget | Affiliate budget | -- | -- | All |
| Conf tournament | Own conference | Own conference | Own conference | Clients in tourney | Personal | Team | Agency clients | -- | -- | Followed | All |

---

## 7. Notification Preferences UI

### 7.1 Preferences Screen Wireframe

```
┌──────────────────────────────────────────────────────────────────┐
│  NOTIFICATION PREFERENCES                         [Save Changes] │
│  ────────────────────────────────────────────────────────────── │
│                                                                  │
│  DELIVERY CHANNELS                                               │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │                     In-App     Push      Email               ││
│  │                                                              ││
│  │  Deals              [*]        [*]       [ ]                 ││
│  │  Valuations         [*]        [*]       [*]                 ││
│  │  Messages           [*]        [*]       [ ]                 ││
│  │  Compliance         [*]        [*]       [*]                 ││
│  │  Tournaments        [*]        [ ]       [ ]                 ││
│  │  Transfer Portal    [*]        [*]       [ ]                 ││
│  │  Predictions        [*]        [ ]       [ ]                 ││
│  │  System             [*]        [ ]       [ ]                 ││
│  │                                                              ││
│  │  [*] = Enabled    [ ] = Disabled                             ││
│  │                                                              ││
│  │  Note: In-app notifications cannot be fully disabled.        ││
│  │  Critical compliance alerts always delivered via all          ││
│  │  channels regardless of preferences.                         ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ────────────────────────────────────────────────────────────── │
│                                                                  │
│  QUIET HOURS                                                     │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │  Enable quiet hours:      [*━━━━━━━━━━━] On                 ││
│  │                                                              ││
│  │  Start time:   [10:00 PM  v]                                ││
│  │  End time:     [7:00 AM   v]                                ││
│  │                                                              ││
│  │  During quiet hours:                                         ││
│  │  - Push notifications silenced                               ││
│  │  - In-app notifications still collected                      ││
│  │  - Critical compliance alerts bypass quiet hours             ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ────────────────────────────────────────────────────────────── │
│                                                                  │
│  FREQUENCY                                                       │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │  Valuation alerts      [Every change v]                      ││
│  │                         Options: Every change | Daily digest ││
│  │                                   | Weekly digest             ││
│  │                                                              ││
│  │  Deal updates          [Every change v]                      ││
│  │                         Options: Every change | Daily digest ││
│  │                                                              ││
│  │  Tournament updates    [Real-time    v]                      ││
│  │                         Options: Real-time | After each round││
│  │                                   | Daily summary             ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ────────────────────────────────────────────────────────────── │
│                                                                  │
│  EMAIL PREFERENCES                                               │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │  Weekly digest           [*━━━━━━━━━━━] On                  ││
│  │  Monthly report          [*━━━━━━━━━━━] On                  ││
│  │  Onboarding emails       [*━━━━━━━━━━━] On                  ││
│  │  Re-engagement emails    [*━━━━━━━━━━━] On                  ││
│  │  Basketball alerts       [*━━━━━━━━━━━] On                  ││
│  │                                                              ││
│  │  [Unsubscribe from all marketing emails]                     ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  [Save Preferences]                                              │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### 7.2 Preferences Design Tokens

| Token | Value | Usage |
|---|---|---|
| `--notification-pref-row-height` | `48px` | Category row height |
| `--notification-pref-row-bg` | `#27272A` (zinc-800) | Row background |
| `--notification-pref-label` | Inter Medium 14, `#FFFFFF` | Category label |
| `--notification-pref-col-header` | Inter Semi-Bold 11, `#71717A`, uppercase | Column header |
| `--notification-pref-toggle-on` | `#DC2626` bg, white circle | Enabled toggle |
| `--notification-pref-toggle-off` | `#52525B` bg, `#A1A1AA` circle | Disabled toggle |
| `--notification-pref-toggle-size` | 36px wide, 20px tall | Toggle dimensions |
| `--notification-pref-time-dropdown` | `#3F3F46` bg, 8px radius, 40px height | Time selector |
| `--notification-pref-save-btn` | `#DC2626` bg, white text, 8px radius, 48px height | Save button |
| `--notification-pref-section-gap` | `32px` | Gap between preference sections |

### 7.3 Preference Persistence

| Property | Value |
|---|---|
| Storage | Server-side, per-user, per-organization |
| Default state | All in-app enabled; push enabled for High/Critical; email disabled except compliance/valuations |
| Sync | Immediate on save; optimistic UI with rollback on failure |
| Cross-device | Push preferences synced across all devices via user account |

---

## 8. Priority Levels

### 8.1 Priority Definitions

| Priority | Definition | Delivery Behavior | Sound | Badge | Examples |
|---|---|---|---|---|---|
| Critical | Immediate action required; regulatory, financial, or safety impact | All channels immediately, bypasses quiet hours, bypasses frequency caps | Alert tone | Yes, persistent | Compliance violation, P1 system incident, account suspension |
| High | Time-sensitive business event requiring attention within hours | All enabled channels, respects quiet hours, counted in frequency cap | Default | Yes | Deal deadline, valuation surge > 10%, transfer portal entry, payment failed |
| Medium | Relevant update that can wait for natural check-in | In-app + push (if enabled), batched if volume exceeds cap | Chime (push) or silent | Yes | New message, pipeline prospect update, tournament round result |
| Low | Informational, non-urgent, can be consumed at leisure | In-app only (unless user opted into push/email for category) | Silent | No | Weekly digest, prediction ready, feature release, system announcement |

### 8.2 Priority-Based Frequency Caps

| Priority | Max per Hour | Max per Day | Batching Rule |
|---|---|---|---|
| Critical | Unlimited | Unlimited | Never batched -- each delivered individually |
| High | 10 | 30 | Batch if > 5 same-category in 1 hour |
| Medium | 5 | 15 | Batch if > 3 same-category in 1 hour |
| Low | 2 | 5 | Always eligible for daily digest batching |

### 8.3 Batching Behavior

When multiple notifications of the same category exceed the per-hour cap, they are batched into a single summary notification:

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  ● [D]  5 deal updates                   Just now   │
│                                                      │
│     Multiple deal stage changes in the last hour.    │
│     Includes: M. Thompson, K. Williams, J. Proctor   │
│                                                      │
│     [View All Deals →]                               │
│                                                      │
└──────────────────────────────────────────────────────┘
```

---

## 9. Basketball-Specific Notifications

### 9.1 March Madness Round Updates

Triggered after each NCAA Tournament round is completed. Includes NIL valuation impact for the user's relevant athletes.

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  ● [B]  Sweet 16 Results: NIL Impact       1h ago   │
│                                                      │
│     3 athletes in your program advanced.             │
│     Combined valuation impact: +$142K (+8.4%)        │
│                                                      │
│     [View Tournament Dashboard →]                    │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### 9.2 Bracket Valuation Changes

Triggered when bracket outcomes cause significant valuation shifts for athletes the user follows or manages.

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  ● [V]  Bracket Impact: K. Williams      30m ago    │
│                                                      │
│     Valuation surged 18.2% after Duke's Elite 8     │
│     win. Tournament multiplier: 1.4x active.        │
│                                                      │
│     [View Athlete →]                                 │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### 9.3 Transfer Portal Alerts

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  ● [T]  Transfer Portal: J. Proctor      15m ago    │
│                                                      │
│     Entered from UConn. Position: PG.                │
│     NIL Valuation: $340K. Predicted destinations:    │
│     Kentucky (32%), Duke (24%), Kansas (18%)         │
│                                                      │
│     [View in Portal →]                               │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### 9.4 Conference Tournament Results

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  ● [B]  SEC Tournament: Kentucky wins     2h ago    │
│                                                      │
│     Kentucky defeated Tennessee 78-72 in the SEC     │
│     Championship. Program NIL impact: +6.1%.         │
│     Auto-bid to NCAA Tournament secured.             │
│                                                      │
│     [View Tournament →]                              │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### 9.5 Basketball Season Notification Cadence

| Period | Notification Volume | Special Triggers |
|---|---|---|
| Pre-season (Aug -- Oct) | Low | Roster finalization, preseason rankings impact |
| Regular season (Nov -- Feb) | Medium | Weekly valuation updates, rivalry game impacts |
| Conference tournaments (Mar) | High | Game-by-game results, auto-bid notifications |
| March Madness (Mar -- Apr) | Very high | Round-by-round results, bracket impact, surge alerts |
| Transfer portal windows | High | Portal entries, commitments, destination predictions |
| Signing periods (Nov, Apr) | Medium | Commitment announcements, class rankings |
| Off-season (May -- Jul) | Low | Portal late entries, off-season valuation shifts |

---

## 10. Full-Page Notifications Inbox

### 10.1 Inbox Wireframe

```
┌──────────────────────────────────────────────────────────────────┐
│  NOTIFICATIONS                                  [Mark All Read]  │
│  ────────────────────────────────────────────────────────────── │
│                                                                  │
│  [All]  [Deals]  [Valuations]  [Compliance]  [Messages]  [Sys]  │
│   ●                                                              │
│                                                                  │
│  ┌───────────────────────────────────────────────────┐           │
│  │  [Search notifications...]                        │           │
│  └───────────────────────────────────────────────────┘           │
│                                                                  │
│  TODAY                                                           │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │ ● [D]  Deal Stage Change                          2h ago    ││
│  │        M. Thompson deal moved to "Negotiation" stage        ││
│  │        [View Deal →]                                        ││
│  ├──────────────────────────────────────────────────────────────┤│
│  │ ● [V]  Valuation Spike                            5h ago    ││
│  │        K. Williams valuation up 12.4% in the last 24 hours  ││
│  │        [View Athlete →]                                     ││
│  ├──────────────────────────────────────────────────────────────┤│
│  │ ● [M]  New Message                                6h ago    ││
│  │        New message from Coach Williams in "Nike Deal"       ││
│  │        [Open Thread →]                                      ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  YESTERDAY                                                       │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │   [B]  Tournament Update                         18h ago    ││
│  │        Kentucky advances to Sweet 16 -- NIL impact: +8.2%  ││
│  │        [View Tournament →]                                  ││
│  ├──────────────────────────────────────────────────────────────┤│
│  │   [T]  Transfer Portal                            1d ago    ││
│  │        J. Proctor entered the transfer portal from UConn    ││
│  │        [View in Portal →]                                   ││
│  ├──────────────────────────────────────────────────────────────┤│
│  │   [C]  Compliance Alert                           1d ago    ││
│  │        Compliance review needed: Nike deal for M. Thompson  ││
│  │        [Review Compliance →]                                ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  THIS WEEK                                                       │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │   [S]  System Announcement                        3d ago    ││
│  │        New feature: Portfolio Comparison Tool now live       ││
│  │        [Try It →]                                           ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  [Load More]                                                     │
│                                                                  │
│  ────────────────────────────────────────────────────────────── │
│  [Notification Preferences]                                      │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### 10.2 Inbox Features

| Feature | Specification |
|---|---|
| Search | Full-text search across notification titles and body text |
| Pagination | 25 notifications per page, infinite scroll with "Load more" |
| Bulk actions | "Mark all read" (top-level), select multiple for bulk read/dismiss |
| Empty state | Bell icon (48px, zinc-600), "No notifications yet" message |
| Loading state | 3 skeleton rows with shimmer animation |
| Error state | Warning icon, "Unable to load notifications", retry button |

---

## 11. Notification Design Tokens (Complete)

### 11.1 Token Registry

| Token | Value | Usage |
|---|---|---|
| **Bell** | | |
| `--notification-bell-size` | `24px` | Bell icon size |
| `--notification-bell-hover-bg` | `#3F3F46` (zinc-700) | Bell hover circle |
| `--notification-bell-active-bg` | `#DC2626` | Bell active (drawer open) |
| `--notification-bell-circle-size` | `36px` | Hover/active circle diameter |
| `--notification-bell-badge-size` | `18px` min-width | Badge circle |
| `--notification-bell-badge-bg` | `#DC2626` | Badge background |
| `--notification-bell-badge-text` | JetBrains Mono 10, `#FFFFFF`, bold | Badge text |
| `--notification-bell-badge-offset` | `-4px` | Badge position offset |
| **Drawer** | | |
| `--notification-drawer-width` | `360px` (desktop), `100vw` (mobile) | Drawer panel width |
| `--notification-drawer-bg` | `#18181B` (zinc-900) | Drawer background |
| `--notification-drawer-overlay` | `rgba(0, 0, 0, 0.50)` | Overlay behind drawer |
| `--notification-drawer-z-index` | `--z-index-overlay` | Stacking order |
| `--notification-drawer-slide-in` | `200ms ease-out` | Open animation |
| `--notification-drawer-slide-out` | `150ms ease-in` | Close animation |
| **Card** | | |
| `--notification-card-unread-bg` | `#27272A` (zinc-800) | Unread card bg |
| `--notification-card-read-bg` | `#18181B` (zinc-900) | Read card bg |
| `--notification-card-hover-bg` | `#323238` (zinc-750) | Hover state bg |
| `--notification-card-pressed-bg` | `#3F3F46` (zinc-700) | Pressed state bg |
| `--notification-card-focus-ring` | `#DC2626`, 2px | Keyboard focus outline |
| `--notification-card-padding` | `10px 12px` | Card padding |
| `--notification-card-min-height` | `72px` | Minimum card height |
| `--notification-card-divider` | `#27272A`, 1px solid | Card separator |
| **Content** | | |
| `--notification-unread-dot-size` | `8px` | Unread indicator dot |
| `--notification-unread-dot-color` | `#DC2626` | Dot color |
| `--notification-icon-size` | `20px` | Category icon |
| `--notification-title-unread` | Inter Semi-Bold 14, `#FFFFFF` | Unread title |
| `--notification-title-read` | Inter Regular 14, `#A1A1AA` | Read title |
| `--notification-body-text` | Inter Regular 13, `#A1A1AA` | Body preview |
| `--notification-body-clamp` | `2` lines | Body line clamp |
| `--notification-timestamp` | JetBrains Mono 11, `#71717A` | Timestamp |
| `--notification-action-text` | Inter Medium 12, `#DC2626` | Action link |
| `--notification-role-badge` | Inter Medium 10, `#D4D4D8`, `#52525B` bg, 4px radius | Role badge pill |
| **Section** | | |
| `--notification-section-header` | Inter Semi-Bold 11, `#71717A`, uppercase | Time section header |
| `--notification-section-padding` | `8px 12px` | Section header padding |
| **Category Colors** | | |
| `--notification-cat-deals` | `#DC2626` | Deals category color |
| `--notification-cat-valuations-up` | `#16A34A` | Valuation increase |
| `--notification-cat-valuations-down` | `#DC2626` | Valuation decrease |
| `--notification-cat-messages` | `#3B82F6` | Messages category |
| `--notification-cat-compliance` | `#F59E0B` | Compliance category |
| `--notification-cat-tournaments` | `#8B5CF6` | Tournaments category |
| `--notification-cat-transfer` | `#06B6D4` | Transfer portal category |
| `--notification-cat-system` | `#A1A1AA` | System category |
| `--notification-cat-predictions` | `#EC4899` | Predictions category |
| **Preferences** | | |
| `--notification-pref-row-height` | `48px` | Preference row height |
| `--notification-pref-row-bg` | `#27272A` (zinc-800) | Row background |
| `--notification-pref-toggle-on-bg` | `#DC2626` | Enabled toggle track |
| `--notification-pref-toggle-off-bg` | `#52525B` | Disabled toggle track |
| `--notification-pref-toggle-thumb` | `#FFFFFF` (on), `#A1A1AA` (off) | Toggle thumb |
| `--notification-pref-toggle-width` | `36px` | Toggle width |
| `--notification-pref-toggle-height` | `20px` | Toggle height |

---

## 12. Accessibility

### 12.1 ARIA Attributes

| Element | ARIA Attribute | Value |
|---|---|---|
| Bell icon | `aria-label` | `"Notifications, {count} unread"` (dynamic) |
| Bell icon (0 unread) | `aria-label` | `"Notifications"` |
| Drawer panel | `role` | `"dialog"` |
| Drawer panel | `aria-label` | `"Notification drawer"` |
| Drawer panel | `aria-modal` | `"true"` |
| Filter tabs | `role` | `"tablist"` |
| Individual filter tab | `role` | `"tab"` |
| Individual filter tab | `aria-selected` | `"true"` / `"false"` |
| Tab content panel | `role` | `"tabpanel"` |
| Notification card | `role` | `"article"` |
| Notification card | `aria-label` | `"{Unread status}: {Title}, {Timestamp}"` |
| Unread dot | `aria-hidden` | `"true"` (visual-only, status in card aria-label) |
| Action button | `role` | `"link"` |
| Mark all read | `aria-live` | `"assertive"` (confirmation announcement) |
| Section header | `role` | `"heading"` with `aria-level="3"` |

### 12.2 Keyboard Navigation

| Key | Action |
|---|---|
| `Tab` | Move focus between bell, drawer elements, cards |
| `Enter` / `Space` | Open drawer (bell), navigate to notification target (card), toggle preference |
| `Escape` | Close drawer, return focus to bell |
| `Arrow Down` | Move to next notification card |
| `Arrow Up` | Move to previous notification card |
| `Home` | Move to first notification |
| `End` | Move to last loaded notification |
| `Tab` (within drawer) | Cycle through filter tabs, mark-all-read, notification cards, footer links |

### 12.3 Screen Reader Announcements

| Event | Announcement |
|---|---|
| New notification received | `"New notification: {Title}"` via `aria-live="polite"` |
| Critical notification received | `"Critical notification: {Title}"` via `aria-live="assertive"` |
| Drawer opened | `"Notification drawer opened. {Count} unread notifications."` |
| Drawer closed | `"Notification drawer closed."` |
| Mark all read | `"All notifications marked as read."` |
| Filter tab selected | `"Showing {Category} notifications. {Count} notifications."` |
| Notification read (clicked) | `"Notification marked as read. Navigating to {Target}."` |
| Preference toggle changed | `"{Category} {Channel} notifications {enabled/disabled}."` |
| Quiet hours toggled | `"Quiet hours {enabled/disabled}. {Start} to {End}."` |

### 12.4 Contrast and Color

| Surface | Text Color | Background | Contrast Ratio | WCAG Level |
|---|---|---|---|---|
| Unread card title | `#FFFFFF` | `#27272A` | 12.6:1 | AAA |
| Read card title | `#A1A1AA` | `#18181B` | 5.2:1 | AA |
| Body preview | `#A1A1AA` | `#27272A` | 4.5:1 | AA |
| Timestamp | `#71717A` | `#27272A` | 3.1:1 | AA (large text equiv) |
| Action button text | `#DC2626` | `#27272A` | 3.6:1 | AA (interactive) |
| Section header | `#71717A` | `#18181B` | 3.8:1 | AA |

### 12.5 Motion and Animation

| Animation | Duration | Reduced Motion Behavior |
|---|---|---|
| Drawer slide in | 200ms ease-out | Instant appear (no animation) |
| Drawer slide out | 150ms ease-in | Instant disappear |
| Badge count update | 200ms scale | Instant number change |
| Card hover highlight | 100ms | Instant color change |
| Notification arrival | Fade in 300ms | Instant appear |

---

## 13. States Reference

### 13.1 Empty State

```
┌──────────────────────────────────────────────────────┐
│  NOTIFICATIONS                                       │
│                                                      │
│              [Bell icon, 48px, zinc-600]             │
│                                                      │
│              No notifications yet                    │
│              Inter Semi-Bold 16, white               │
│                                                      │
│              You'll see updates here when deals      │
│              move, valuations change, or teammates   │
│              send messages.                          │
│              Inter Regular 14, zinc-400              │
│                                                      │
│              [Explore Dashboard]                     │
│              Primary button, --color-brand-red       │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### 13.2 Loading State

```
┌──────────────────────────────────────────────────────┐
│  NOTIFICATIONS                                       │
│                                                      │
│  ┌──────────────────────────────────────────────────┐│
│  │  [----] [================================]  [-] ││
│  │         [========================]              ││
│  ├──────────────────────────────────────────────────┤│
│  │  [----] [================================]  [-] ││
│  │         [========================]              ││
│  ├──────────────────────────────────────────────────┤│
│  │  [----] [================================]  [-] ││
│  │         [========================]              ││
│  └──────────────────────────────────────────────────┘│
│                                                      │
│  Skeleton rows with shimmer animation                │
│  3 rows, zinc-800 bg, 72px height each              │
│  Shimmer: linear gradient sweep, 1.5s loop           │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### 13.3 Error State

```
┌──────────────────────────────────────────────────────┐
│  NOTIFICATIONS                                       │
│                                                      │
│              [Warning icon, 48px, red]               │
│                                                      │
│              Unable to load notifications            │
│              Inter Semi-Bold 16, white               │
│                                                      │
│              Check your connection and try again.    │
│              Inter Regular 14, zinc-400              │
│                                                      │
│              [Retry]                                 │
│              Primary button, --color-brand-red       │
│                                                      │
└──────────────────────────────────────────────────────┘
```

---

## 14. Real-Time Delivery Architecture (Design Perspective)

This section describes the expected behavior from a design and UX standpoint. Implementation details are owned by the Codex engineering team.

| Behavior | Expectation |
|---|---|
| In-app delivery latency | Notification card appears within 3 seconds of trigger event |
| Push delivery latency | Push notification delivered within 10 seconds of trigger event |
| Bell badge update | Badge count updates in real time without page refresh |
| Drawer auto-refresh | New notifications appear at top of drawer while open |
| Read state sync | Marking as read in drawer immediately reflects in inbox and badge count |
| Cross-tab sync | Reading a notification in one tab updates badge and state in all open tabs |
| Offline behavior | Notifications queue server-side; delivered on next app open/reconnect |
| Push + in-app dedup | If user has app open and push arrives, push is suppressed; in-app card surfaces |

---

*NIL Optic -- See the Value. Own the Future.*
