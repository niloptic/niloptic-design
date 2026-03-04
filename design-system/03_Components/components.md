# Components Library

Last updated: 2026-03-01

---

## Overview

Components combine primitives into functional UI units. They carry domain awareness and serve specific product needs across NIL Optic's role-based dashboards.

---

## Cards

Cards are the **primary product unit** of NIL Optic. Every key data surface — valuations, athletes, deals, predictions — is expressed as a card.

### Card Base

```
┌─────────────────────────────────────┐
│                                     │
│  Card Header                        │  ← H3, padding: 24px 24px 0
│                                     │
│  Card Content                       │  ← Body, padding: 16px 24px
│                                     │
│  Card Footer                        │  ← Actions/meta, padding: 0 24px 24px
│                                     │
└─────────────────────────────────────┘

Surface: zinc-900 (dark), white (light)
Border: 1px zinc-800 (dark), zinc-200 (light)
Radius: radius-lg (12px)
```

### Metric Card

```
┌─────────────────────────────────────┐
│  LABEL SM  "NIL VALUATION"          │
│                                     │
│  Display LG  "$2.4M"               │  ← Red or white
│                                     │
│  Data  "+12.3% ▲"  Badge "Top 5%"  │  ← Green delta + badge
│                                     │
│  Body SM  "Updated 2h ago"          │  ← zinc-500
└─────────────────────────────────────┘
```

### Athlete Row Card

```
┌─────────────────────────────────────────────────────┐
│  [Avatar]  Name / School / Sport    $1.2M   +8.4%  │
│   48px     Body + Label SM          Data    Data SM │
│            zinc-300  zinc-500                green   │
└─────────────────────────────────────────────────────┘
```

### Deal Card

```
┌─────────────────────────────────────┐
│  [Brand Logo]  Deal Title           │
│                                     │
│  $50,000     ● Active               │  ← Data LG + Status badge
│                                     │
│  Athlete: J. Smith  |  Due: Mar 15  │  ← Label SM
│                                     │
│  [View Details]  [Edit]             │  ← Ghost + Secondary buttons
└─────────────────────────────────────┘
```

---

## Data Tables

### Table Structure

```
┌─────────────────────────────────────────────────────────┐
│  [Search]  [Filter ▼]  [Sort ▼]  [Export]              │  ← Toolbar
├─────────────────────────────────────────────────────────┤
│  Name ▲    School    Sport    Value    Δ     Conf     │  ← Header row
├─────────────────────────────────────────────────────────┤
│  J. Smith  UGA       FB       $2.4M   +12%  87%      │  ← Data row
│  A. Jones  LSU       BB       $1.8M   +5%   92%      │
│  M. Davis  UCLA      BK       $3.1M   -2%   78%      │
├─────────────────────────────────────────────────────────┤
│  Showing 1-25 of 847          [◀ 1 2 3 4 5 ▶]         │  ← Pagination
└─────────────────────────────────────────────────────────┘
```

### Table Features
- Sortable columns (click header to toggle asc/desc)
- Filterable with persistent filter chips
- Virtualized rows for 1000+ entries
- Horizontal scroll on mobile with sticky first column
- Row hover: zinc-800/50 highlight
- Row click: navigates to detail

---

## Navigation

### Sidebar Navigation

```
┌──────────────────────┐
│  [NIL OPTIC LOGO]    │  ← Logo, 40px height
│                      │
│  ■ Dashboard         │  ← Active: red left border, red icon
│  □ Directory         │  ← Default: zinc-400 icon, zinc-300 text
│  □ Predictions       │
│  □ NIL Report        │
│  □ Roster Builder    │
│                      │
│  ── MANAGE ──        │  ← Section label, zinc-500, uppercase
│                      │
│  □ Deals             │
│  □ Messages          │
│  □ Settings          │
│                      │
│  ┌────────────────┐  │
│  │ [Avatar] Name  │  │  ← User profile, bottom-pinned
│  │ Role / Org     │  │
│  └────────────────┘  │
└──────────────────────┘

Width: 280px (desktop), collapsible to 64px (icon only)
Surface: zinc-950
Border-right: 1px zinc-800
```

### Tab Navigation

```
┌──────┬──────┬──────┬──────┐
│ Tab1 │ Tab2 │ Tab3 │ Tab4 │
└──┬───┴──────┴──────┴──────┘
   ▬ ← Active: 2px red underline, white text
     ← Inactive: zinc-400 text, no underline
```

### Breadcrumbs

```
Home  /  Directory  /  Basketball  /  Player Name
zinc-400  /  zinc-400  /  zinc-400  /  white (current)
```

---

## Charts

### Chart Container

```
┌─────────────────────────────────────┐
│  Chart Title          [Legend]       │
│                                     │
│         ╭─────╮                     │
│    ╭────╯     ╰──╮                  │  ← Line/area chart
│  ──╯              ╰────            │
│                                     │
│  Jan  Feb  Mar  Apr  May  Jun       │  ← X-axis labels
└─────────────────────────────────────┘
```

### Chart Types Used
| Type | Use Case |
|------|----------|
| Line | Valuation over time |
| Bar | Comparison across athletes |
| Donut | Portfolio allocation |
| Radar | Multi-factor athlete profile |
| Heat Map | Conference/division strength |
| Sparkline | Inline trend in table cells |

### Chart Colors
- Use data viz palette bands A-F
- Always include legend
- Hover tooltip with exact values in mono font
- Grid lines: zinc-800, subtle

---

## Stat Blocks

### Single Stat

```
┌─────────────────┐
│  847             │  ← Display MD, white
│  Athletes        │  ← Label, zinc-400
│  Tracked         │
└─────────────────┘
```

### Comparative Stat

```
┌─────────────────────────────┐
│  $2.4M  →  $2.8M           │  ← Display, white → red
│  ▲ +16.7%                   │  ← Data, green
│  NIL Value (30d)            │  ← Label, zinc-400
└─────────────────────────────┘
```

---

## Modals

### Standard Modal

```
┌────────────────────────────────────────┐
│  ╳                                     │  ← Close button, top-right
│                                        │
│  Modal Title                           │  ← H2
│                                        │
│  Modal body content goes here with     │  ← Body
│  relevant information and context.     │
│                                        │
│           [Cancel]  [Confirm]          │  ← Secondary + Primary buttons
└────────────────────────────────────────┘

Surface: zinc-900
Border: 1px zinc-700
Radius: radius-xl (16px)
Max-width: 560px
Backdrop: black/80 + blur-xl
```

---

## Toasts / Notifications

```
┌──────────────────────────────────────┐
│  ✓  Action completed successfully    │  ← Success: green icon
│     Deal updated for J. Smith        │  ← Body SM, zinc-400
└──────────────────────────────────────┘

Position: top-right, stacked
Auto-dismiss: 5 seconds
Enter: slide from right, 300ms
Exit: fade out, 150ms
```
