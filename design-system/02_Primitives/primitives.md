# Primitives Library

Last updated: 2026-03-01

---

## Overview

Primitives are the atomic building blocks — buttons, inputs, controls, indicators, and icons. They carry no domain knowledge and are brand-agnostic in behavior but NIL Optic-branded in appearance.

---

## Buttons

### Variants

| Variant | Background | Text | Border | Usage |
|---------|-----------|------|--------|-------|
| **Primary** | `--brand-red` | White | none | Main CTAs, submit actions |
| **Secondary** | Transparent | White | `zinc-700` | Supporting actions |
| **Ghost** | Transparent | `zinc-300` | none | Tertiary actions, navigation |
| **Destructive** | `red-500/10` | `red-400` | `red-500/30` | Delete, remove actions |
| **Success** | `green-500/10` | `green-400` | `green-500/30` | Confirm, verify actions |

### States

| State | Visual Change |
|-------|--------------|
| Default | Base variant style |
| Hover | Lighten 10%, glow shadow for Primary |
| Active/Pressed | Scale 0.98, darken 5% |
| Focus | Red focus ring (`--elevation-focus`) |
| Disabled | 50% opacity, no pointer events |
| Loading | Spinner replaces label, maintains width |

### Sizes

| Size | Height | Padding X | Font Size | Icon Size |
|------|--------|-----------|-----------|-----------|
| SM | 32px | 12px | 13px | 16px |
| MD | 40px | 16px | 14px | 18px |
| LG | 48px | 24px | 16px | 20px |
| XL | 56px | 32px | 18px | 24px |

### Button Anatomy

```
┌──────────────────────────────────┐
│  [Icon]  Label Text  [Chevron]   │
│   18px    14px Med     16px      │
│          ←── 16px ──→            │  ← padding-x
└──────────────────────────────────┘
   ↑ 40px height (MD)
```

---

## Inputs

### Text Input

```
┌──────────────────────────────────┐
│  Label Text                      │  ← 12px Medium, zinc-400
│  ┌────────────────────────────┐  │
│  │  Placeholder text...       │  │  ← 14px Regular, zinc-500
│  └────────────────────────────┘  │     bg: zinc-800/60, border: zinc-600
│  Helper or error text            │  ← 12px Regular, zinc-500 or red-400
└──────────────────────────────────┘
```

### Input States

| State | Border | Background | Label |
|-------|--------|-----------|-------|
| Default | `zinc-600` | `zinc-800/60` | `zinc-400` |
| Focus | `red-500` + focus ring | `zinc-800/60` | `zinc-300` |
| Error | `red-500` | `red-500/10` | `red-400` |
| Disabled | `zinc-700` | `zinc-800/30` | `zinc-500` |
| Success | `green-500` | `zinc-800/60` | `green-400` |

---

## Select / Dropdown

```
┌────────────────────────────────┐
│  Selected value          ▼     │
└────────────────────────────────┘
     │
     ▼
┌────────────────────────────────┐
│  Option 1                      │  ← hover: zinc-800
│  Option 2              ✓       │  ← selected: red accent
│  Option 3                      │
│  Option 4                      │
└────────────────────────────────┘
```

---

## Toggle / Switch

```
OFF:  ┌──[●]────┐   bg: zinc-700, knob: zinc-400
ON:   ┌────[●]──┐   bg: red-600, knob: white
```

Size: 44px × 24px track, 20px knob

---

## Checkbox

```
OFF:  ☐  ← 18px, border: zinc-600, bg: transparent
ON:   ☑  ← 18px, bg: red-600, check: white
```

---

## Badges / Tags

| Variant | Background | Text | Usage |
|---------|-----------|------|-------|
| Default | `zinc-800` | `zinc-300` | Neutral metadata |
| Red | `red-500/15` | `red-400` | Priority, value |
| Green | `green-500/15` | `green-400` | Verified, active |
| Amber | `amber-500/15` | `amber-400` | Warning, pending |
| Blue | `blue-500/15` | `blue-400` | Informational |
| Sport | Sport color/15 | Sport color | Sport context |

### Badge Anatomy

```
┌────────────────┐
│  ● Label Text  │  ← 11px Medium, padding: 2px 8px
└────────────────┘
   radius: pill
   height: 22px
```

---

## Indicators

### Status Dot
- 8px circle with color fill
- Green: active/online, Red: critical, Amber: warning, Blue: info, Gray: inactive

### Progress Bar
```
┌────────────────────────────────┐
│ ██████████████░░░░░░░░░░░░░░░ │  ← 4px height, radius-pill
└────────────────────────────────┘
   Fill: red-600    Track: zinc-800
```

### Confidence Score Ring
```
     ╭───╮
    │ 87% │   ← Circular progress, stroke: 3px
     ╰───╯      Fill: gradient red → red-light
                 Track: zinc-800
                 Center: Data font, white
```

---

## Icons

### System
- Source: Lucide icon set
- Default size: 20px
- Stroke: 1.5px
- Color: inherits from parent text color
- Sizes: 16px (SM), 20px (MD), 24px (LG)

### Sport Icons
Custom silhouettes for sport context headers:
- Football, Basketball, Baseball, Soccer, Track, Swimming, Volleyball, etc.
- Style: simplified silhouette, single-color, 24px default

---

## Dividers

| Type | Style | Usage |
|------|-------|-------|
| Horizontal | 1px solid `zinc-800` | Section separation |
| Vertical | 1px solid `zinc-800` | Inline group separation |
| Spaced | 1px + 32px margin | Major section breaks |
