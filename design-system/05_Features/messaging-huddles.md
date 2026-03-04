# Messaging & Huddles Feature Spec

Last updated: 2026-03-04

---

## Overview

Real-time communication layer for NIL negotiations, team coordination, and athlete-agent communication. Messaging provides asynchronous threaded conversations while Huddles deliver synchronous video/audio rooms. Both surfaces integrate with the deal pipeline, roster builder, and compliance system to keep context attached to every conversation.

Basketball-first: default thread filters prioritize basketball program threads and agent deal threads during peak NIL windows (tournament season, transfer portal).

---

## Thread List View

```
┌──────────────────────────────────────────────────┐
│  MESSAGES                        [+ New Thread]  │
│  ──────────────────────────────────────────────  │
│                                                  │
│  [Search threads...]              [Filter ▼]     │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │ ● [AV] Coach Williams              2:34 PM  ││
│  │   "Let's finalize the Nike terms before..."  ││
│  │   ┌─────────┐                                ││
│  │   │ Deal    │  ← Context pill, red bg        ││
│  │   └─────────┘                        (3) ●   ││  ← Unread badge
│  ├──────────────────────────────────────────────┤│
│  │   [AV] Marcus Thompson             1:12 PM  ││
│  │   "My Instagram numbers are up this week"    ││
│  │   ┌───────────┐                              ││
│  │   │ Recruiting│  ← Context pill, blue bg     ││
│  │   └───────────┘                              ││
│  ├──────────────────────────────────────────────┤│
│  │   [AV] Agent Rivera                11:45 AM  ││
│  │   "New offer from Gatorade — $25K/yr"        ││
│  │   ┌─────────┐                                ││
│  │   │ Deal    │                        (1) ●   ││
│  │   └─────────┘                                ││
│  ├──────────────────────────────────────────────┤│
│  │   [AV][AV][+3] Team Huddle         Yesterday││
│  │   "Practice film review at 4pm tomorrow"     ││
│  │   ┌─────────┐                                ││
│  │   │ Team    │                                ││
│  │   └─────────┘                                ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  [Compose message...]          [📎] [Send]   ││  ← Sticky composer (mobile)
│  └──────────────────────────────────────────────┘│
└──────────────────────────────────────────────────┘
```

### Thread List Anatomy

| Element               | Token / Style                        |
|-----------------------|--------------------------------------|
| Thread row            | `--surface-default`, 72px min-height |
| Avatar                | 40px circle, `--radius-pill`         |
| Participant name      | Inter Semi-Bold 14, white            |
| Message preview       | Inter Regular 13, zinc-400           |
| Timestamp             | JetBrains Mono 11, zinc-500          |
| Unread badge          | 20px circle, `--color-brand-red`     |
| Context pill          | 6px radius, category color bg        |
| Sticky composer       | `--surface-elevated`, 56px height    |

### Context Pill Types

| Type        | Background        | Text Color |
|-------------|-------------------|------------|
| Deal        | `#DC2626` (red)   | white      |
| Recruiting  | `#2563EB` (blue)  | white      |
| Team        | `#16A34A` (green) | white      |
| General     | zinc-700          | zinc-300   |

---

## Thread Detail View

```
┌──────────────────────────────────────────────────┐
│  ← Back   Coach Williams    [●] Online           │
│           University of Kentucky · Basketball     │
│           [Start Meet]                            │  ← Primary action
│  ──────────────────────────────────────────────  │
│                                                  │
│  ┌──────────────────────────────────────────┐    │
│  │  Coach Williams          2:30 PM  [Coach]│    │  ← Role badge
│  │  "Marcus had a great game last night.    │    │
│  │   Nike wants to move forward with the    │    │
│  │   campus ambassador deal."               │    │
│  └──────────────────────────────────────────┘    │
│                                                  │
│                  ┌──────────────────────────────┐ │
│                  │  You               2:32 PM   │ │  ← Outbound bubble
│                  │  "Perfect. What's the offer  │ │
│                  │   structure? Per-appearance   │ │
│                  │   or flat monthly?"           │ │
│                  └──────────────────────────────┘ │
│                                                  │
│  ┌──────────────────────────────────────────┐    │
│  │  Coach Williams          2:34 PM  [Coach]│    │
│  │  "Let's finalize the Nike terms before   │    │
│  │   the SEC tournament."                   │    │
│  │                                          │    │
│  │  ┌────────────────────────────┐          │    │
│  │  │ 📄 Nike_Terms_Draft.pdf   │          │    │  ← Attachment
│  │  │    245 KB  ·  [Download]   │          │    │
│  │  └────────────────────────────┘          │    │
│  │                                          │    │
│  │  👍 ✅ 🔥                               │    │  ← Reactions
│  └──────────────────────────────────────────┘    │
│                                                  │
│  ──────────────────────────────────────────────  │
│  [📎] [GIF] [Type a message...]        [Send]   │
└──────────────────────────────────────────────────┘
```

### Message Bubble Anatomy

| Element            | Token / Style                            |
|--------------------|------------------------------------------|
| Inbound bubble     | zinc-800 bg, 12px radius, left-aligned   |
| Outbound bubble    | `--color-brand-red` bg, right-aligned    |
| Sender name        | Inter Semi-Bold 13, white                |
| Role badge         | 4px radius, zinc-600 bg, zinc-300 text   |
| Timestamp          | JetBrains Mono 11, zinc-500              |
| Message body       | Inter Regular 14, white                  |
| Attachment card    | zinc-700 bg, 8px radius, 48px height     |
| Reaction row       | 20px emoji, 4px spacing                  |

---

## Meet Room

```
┌──────────────────────────────────────────────────┐
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │                                              ││
│  │           [Primary Participant Tile]         ││  ← Video feed / avatar
│  │           Coach Williams                     ││     480px min-height
│  │           University of Kentucky             ││
│  │                                              ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  00:14:32 elapsed        3:47 PM local       ││  ← Scoreboard strip
│  └──────────────────────────────────────────────┘│
│                                                  │
│  ┌────────────────────────────────────────┐      │
│  │  🔥 "Great point!" — Marcus T.        │      │  ← Reaction feed overlay
│  │  👍 — Agent Rivera                    │      │     Fades after 4s
│  └────────────────────────────────────────┘      │
│                                                  │
│  ──────────────────────────────────────────────  │
│                                                  │
│  [🎤 Mute]  [📷 Camera]  [🔴 End]  [⋯ More]   │  ← Bottom controls
│                                                  │
└──────────────────────────────────────────────────┘
```

### Settings Lightbox (via "More" menu)

```
┌──────────────────────────────────────────────────┐
│  MEET SETTINGS                           [✕]    │
│  ──────────────────────────────────────────────  │
│                                                  │
│  Camera Preview                                  │
│  ┌────────────────────────────┐                  │
│  │                            │                  │
│  │    [Live camera feed]      │                  │
│  │                            │                  │
│  └────────────────────────────┘                  │
│                                                  │
│  Camera         [Built-in HD Camera       ▼]    │
│  Microphone     [AirPods Pro              ▼]    │
│  Speaker        [MacBook Pro Speakers     ▼]    │
│                                                  │
│  ──────────────────────────────────────────────  │
│                                                  │
│  Noise Defuser          [●━━━━━━━━━━━━━] On     │  ← Toggle
│  Echo Cancellation      [━━━━━━━━━━━━━●] On     │
│                                                  │
│  [Apply]                                [Cancel] │
└──────────────────────────────────────────────────┘
```

### Meet Room Anatomy

| Element                | Token / Style                         |
|------------------------|---------------------------------------|
| Participant tile       | 16:9 ratio, `--radius-lg`, zinc-900   |
| Scoreboard strip       | zinc-800 bg, JetBrains Mono 14        |
| Elapsed timer          | `--color-brand-red`, monospace         |
| Local clock            | zinc-400, monospace                    |
| Reaction overlay       | `--surface-elevated`, 80% opacity      |
| Control bar            | zinc-900 bg, 64px height               |
| Control button         | 48px circle, zinc-700 bg, white icon   |
| End button             | 48px circle, `--color-brand-red` bg    |
| Settings lightbox      | `--elevation-modal`, 480px max-width   |

---

## Huddle Room

### Conference Format Selector

```
┌──────────────────────────────────────────────────┐
│  START A HUDDLE                                  │
│  ──────────────────────────────────────────────  │
│                                                  │
│  Step 1: Choose Format                           │
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐      │
│  │          │  │          │  │          │      │
│  │   1:1    │  │  1→Many  │  │  Team /  │      │
│  │          │  │          │  │ Division │      │
│  │ ● Active │  │          │  │          │      │
│  └──────────┘  └──────────┘  └──────────┘      │
│                                                  │
│  ┌──────────┐                                    │
│  │ Affiliate│                                    │
│  │ Workshop │                                    │
│  └──────────┘                                    │
│                                                  │
│  Step 2: Audience & Agenda                       │
│                                                  │
│  Invite       [Search participants...]           │
│  Agenda       [Optional: describe topic...]      │
│                                                  │
│  Step 3: Start                                   │
│                                                  │
│  [Start Huddle]                                  │
│                                                  │
└──────────────────────────────────────────────────┘
```

### Huddle Room (Active)

```
┌──────────────────────────────────────────────────┐
│  ┌──────────────────────────────────────────────┐│
│  │  🏀 NIL OPTIC HUDDLE          00:32:15      ││  ← Branded scoreboard
│  │  "SEC Tournament Prep — NIL Strategy"        ││     Room header
│  │  4 participants    [Invite +]                ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐        │
│  │          │ │          │ │          │        │
│  │ Coach W. │ │ Agent R. │ │ Marcus T.│        │  ← Participant tiles
│  │ [Host]   │ │          │ │          │        │
│  └──────────┘ └──────────┘ └──────────┘        │
│                                                  │
│  ┌──────────┐                                    │
│  │          │                                    │
│  │ AD Smith │                                    │
│  │          │                                    │
│  └──────────┘                                    │
│                                                  │
│  Audience Mode: [Interactive ▼]                  │  ← Mode selector
│  Options: Interactive | Listen Only | Host Q&A   │
│                                                  │
│  ──────────────────────────────────────────────  │
│  [🎤 Mute]  [📷 Camera]  [🔴 Leave]  [⋯ More] │
└──────────────────────────────────────────────────┘
```

### Invite Modal

```
┌──────────────────────────────────────────────────┐
│  INVITE TO HUDDLE                        [✕]    │
│  ──────────────────────────────────────────────  │
│                                                  │
│  [Search by name, role, or program...]           │
│                                                  │
│  SUGGESTED                                       │
│  ┌──────────────────────────────────────────────┐│
│  │ [AV] Marcus Thompson   Athlete  Basketball   ││
│  │                                    [Invite]  ││
│  ├──────────────────────────────────────────────┤│
│  │ [AV] Agent Rivera      Agent    Basketball   ││
│  │                                    [Invite]  ││
│  ├──────────────────────────────────────────────┤│
│  │ [AV] Coach Williams    Coach    Kentucky     ││
│  │                                    [Invited] ││  ← Already invited
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [Copy Invite Link]                              │
└──────────────────────────────────────────────────┘
```

### Huddle Anatomy

| Element                | Token / Style                         |
|------------------------|---------------------------------------|
| Format card            | zinc-800 bg, 120px, `--radius-md`     |
| Format card (active)   | `--color-brand-red` border, 2px       |
| Room header            | zinc-900 bg, 64px height              |
| Scoreboard             | JetBrains Mono 16, red elapsed timer  |
| Participant tile       | 160px square, `--radius-lg`           |
| Host badge             | `--color-brand-red` bg, white text    |
| Mode selector          | Dropdown, zinc-700 bg                 |
| Invite modal           | `--elevation-modal`, 400px width      |

---

## Role-Based Behavior

| Capability                    | AD / GM       | Agent         | Coach              | Affiliate          | Athlete            |
|-------------------------------|---------------|---------------|--------------------|--------------------|------------------  |
| Start thread                  | Any user      | Any user      | Program-scoped     | Inbound-first only | Program-scoped     |
| Send messages                 | Unrestricted  | Unrestricted  | Program + agents   | Reply only         | Program + agents   |
| Start Meet (1:1)              | Yes           | Yes           | Yes                | No                 | Yes                |
| Start Huddle                  | All formats   | All formats   | Team/Division only | Workshop only      | No (join only)     |
| Invite participants           | Unrestricted  | Unrestricted  | Program-scoped     | No                 | No                 |
| View deal-tagged threads      | Yes           | Client only   | Read-only          | No                 | Own deals only     |
| Attach files                  | Yes           | Yes           | Yes                | No                 | Yes                |
| Set audience mode             | Yes           | Yes           | Yes                | No                 | No                 |

### Affiliate Inbound-First Rule

Affiliates (NIL collectives, brands) cannot initiate outbound messages to athletes or coaches. They may:
1. Respond to inbound threads where they are tagged
2. Post in General threads visible to their program scope
3. Request a connection through the CRM pipeline (agent or AD must approve)

---

## States

### Loading
```
┌──────────────────────────────────────────────────┐
│  MESSAGES                                        │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ││  ← Skeleton rows
│  │  ░░░░░░░░░░░░░░░░░░░░░░                     ││     3 shimmer rows
│  ├──────────────────────────────────────────────┤│
│  │  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ││
│  │  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░              ││
│  ├──────────────────────────────────────────────┤│
│  │  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ││
│  │  ░░░░░░░░░░░░░░░░                           ││
│  └──────────────────────────────────────────────┘│
└──────────────────────────────────────────────────┘
```

### Empty (No Threads)
```
┌──────────────────────────────────────────────────┐
│  MESSAGES                                        │
│                                                  │
│              [💬 Icon, 48px, zinc-600]           │
│                                                  │
│              No conversations yet                │  ← Inter Semi-Bold 16
│              Start a thread to connect with      │  ← Inter Regular 14
│              athletes, agents, and coaches.       │     zinc-400
│                                                  │
│              [+ Start a Thread]                  │  ← Primary button, red
│                                                  │
└──────────────────────────────────────────────────┘
```

### Error
```
┌──────────────────────────────────────────────────┐
│  MESSAGES                                        │
│                                                  │
│              [⚠ Icon, 48px, red]                │
│                                                  │
│              Unable to load messages              │  ← Inter Semi-Bold 16
│              Check your connection and try again. │  ← zinc-400
│                                                  │
│              [Retry]                             │
│                                                  │
└──────────────────────────────────────────────────┘
```

### First-Use Tutorial
```
┌──────────────────────────────────────────────────┐
│  WELCOME TO MESSAGING                            │
│                                                  │
│  Step 1 of 3                 [●  ○  ○]          │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  [Illustration: thread list preview]         ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  Threaded Conversations                          │
│  Every message lives in a thread tagged to its   │
│  context — deals, recruiting, or team ops.       │
│                                                  │
│  [Next →]                           [Skip]       │
└──────────────────────────────────────────────────┘
```

---

## Routes

| Route                            | Description                    |
|----------------------------------|--------------------------------|
| `/dashboard/messages`            | Thread list (role-filtered)    |
| `/dashboard/messages/[threadId]` | Thread detail                  |
| `/dashboard/meet/[meetId]`       | Meet room (1:1 or small group) |
| `/dashboard/huddles`             | Huddle lobby                   |
| `/dashboard/huddles/[huddleId]` | Active huddle room             |

---

## Design Tokens

| Token Family        | Example Tokens                                          |
|---------------------|---------------------------------------------------------|
| `--thread-*`        | `--thread-row-height`, `--thread-preview-lines`         |
| `--meet-*`          | `--meet-tile-radius`, `--meet-control-size`             |
| `--huddle-*`        | `--huddle-format-card-size`, `--huddle-header-height`   |
| `--msg-*`           | `--msg-bubble-radius`, `--msg-inbound-bg`               |
| `--msg-outbound-bg` | `--color-brand-red`                                     |
| `--msg-timestamp`   | JetBrains Mono 11, zinc-500                             |

---

## Accessibility

- All controls meet WCAG 2.1 AA contrast ratios on dark surfaces
- Meet/Huddle controls are keyboard-navigable (Tab + Enter)
- Screen reader announces participant join/leave, unread counts
- Reaction overlay has `aria-live="polite"` region
- Composer supports Enter-to-send with Shift+Enter for newline
