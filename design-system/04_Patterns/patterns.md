# Patterns Library

Last updated: 2026-03-01

---

## Overview

Patterns are reusable behavioral solutions — how the product handles loading, errors, empty states, and user feedback. They enforce consistency across every surface.

---

## Loading Patterns

### Skeleton Loading (Preferred)

```
Card Skeleton:
┌─────────────────────────────────────┐
│  ████████  ──────                   │  ← Header skeleton
│                                     │
│  ████████████████████████           │  ← Metric skeleton (wider)
│                                     │
│  ████████████  ─────────            │  ← Body skeleton
│  ██████████████████████             │
│  ███████████                        │
└─────────────────────────────────────┘

Table Skeleton:
┌─────────────────────────────────────────────────────┐
│  ████  ████████  ████  ██████████  ████  ████      │
├─────────────────────────────────────────────────────┤
│  ████  ████████  ████  ██████████  ████  ████      │
│  ████  ████████  ████  ██████████  ████  ████      │
│  ████  ████████  ████  ██████████  ████  ████      │
└─────────────────────────────────────────────────────┘

Shimmer: gradient sweep left → right, 1500ms, loop
Colors: zinc-800 → zinc-700 → zinc-800
```

### Page-Level Loading
- Show skeleton for the full page structure
- Sidebar/navigation remain interactive
- Header loads first, then content sections top-to-bottom

### Inline Loading
- Button loading: spinner replaces label, button width stays fixed
- Input validation: spinner in suffix position
- Data refresh: subtle pulse on the updating value

---

## Error Patterns

### Page Error

```
┌─────────────────────────────────────┐
│                                     │
│         [Error Icon - Red]          │
│                                     │
│      Something went wrong           │  ← H2, white
│                                     │
│    We couldn't load this page.      │  ← Body, zinc-400
│    Please try again or contact      │
│    support if the issue persists.   │
│                                     │
│         [Try Again]                 │  ← Primary button
│                                     │
└─────────────────────────────────────┘
```

### Card Error

```
┌─────────────────────────────────────┐
│  Card Title                         │
│                                     │
│  ⚠ Unable to load data             │  ← Body SM, red-400
│  [Retry]                            │  ← Ghost button, small
│                                     │
└─────────────────────────────────────┘
```

### Inline Error
- Form field: red border + red helper text below
- Toast: red-tinted toast with error icon
- Table cell: "—" with tooltip on hover

---

## Empty States

### No Data

```
┌─────────────────────────────────────┐
│                                     │
│        [Illustration/Icon]          │  ← Subtle, zinc-600
│                                     │
│       No athletes found             │  ← H3, zinc-300
│                                     │
│    Try adjusting your filters       │  ← Body SM, zinc-500
│    or search criteria.              │
│                                     │
│    [Clear Filters]  [Browse All]    │  ← Actions
│                                     │
└─────────────────────────────────────┘
```

### First-Time / Onboarding

```
┌─────────────────────────────────────┐
│                                     │
│      Welcome to NIL Optic           │  ← H2, white
│                                     │
│  Get started by adding athletes     │  ← Body, zinc-400
│  to your pipeline.                  │
│                                     │
│  [+ Add First Athlete]             │  ← Primary CTA
│                                     │
│  1. Search the directory            │  ← Steps, numbered, Body SM
│  2. Add to your pipeline            │
│  3. Start tracking valuations       │
│                                     │
└─────────────────────────────────────┘
```

---

## Feedback Patterns

### Success Feedback
- Toast notification (top-right)
- Inline checkmark animation
- Green flash on updated value

### Error Feedback
- Toast notification (top-right, red tint)
- Inline field error with shake animation (single, 150ms)
- Form-level error banner above submit button

### Confirmation Dialog

```
┌────────────────────────────────────────┐
│                                        │
│  Are you sure?                         │  ← H3, white
│                                        │
│  This will remove J. Smith from your   │  ← Body, zinc-400
│  pipeline. This action cannot be       │
│  undone.                               │
│                                        │
│           [Cancel]  [Remove]           │  ← Secondary + Destructive
│                                        │
└────────────────────────────────────────┘
```

---

## Overlay Patterns

### Slide Panel (Right)

```
                    ┌──────────────────────────┐
                    │  Panel Title         ╳   │
                    │                          │
                    │  Panel content scrolls   │
                    │  independently while     │
                    │  main content is dimmed.  │
                    │                          │
                    │                          │
                    │         [Actions]         │
                    └──────────────────────────┘

Width: 480px (desktop), full-width (mobile)
Enter: slide from right, 300ms, ease-out
Backdrop: black/60
```

### Command Palette

```
┌────────────────────────────────────────┐
│  🔍  Search commands, athletes...     │
├────────────────────────────────────────┤
│  Recent                                │
│  → View J. Smith profile               │
│  → Open predictions dashboard          │
│                                        │
│  Actions                               │
│  → Add athlete to pipeline             │
│  → Create new deal                     │
│  → Export report                       │
└────────────────────────────────────────┘

Trigger: Cmd+K
Position: centered, top-third of viewport
Max-width: 640px
```

---

## Responsive Patterns

### Mobile Adaptations
| Desktop Pattern | Mobile Pattern |
|-----------------|----------------|
| Sidebar navigation | Bottom tab bar |
| Multi-column cards | Single-column stack |
| Data table | Scrollable with sticky first column |
| Slide panel | Full-screen sheet |
| Hover tooltips | Tap-and-hold or info icon |
| Command palette | Full-screen search |

### Sticky Elements
- Navigation header: always sticky
- Table headers: sticky on scroll
- Action bars: sticky to bottom on mobile
- Quick-nav pills: sticky horizontal scroll
