# Color System

Last updated: 2026-03-01

---

## Overview

NIL Optic's color system is built on three pillars:
1. **Brand Core** — Red, Black, White identity
2. **Semantic Intent** — Colors communicate meaning, not decoration
3. **Accessibility** — WCAG AAA contrast compliance across dark and light modes

---

## Color Architecture

```
Brand Core
├── Red (#DC2626)        → Action, value, urgency
├── Black (#000000)      → Authority, foundation
└── White (#FFFFFF)      → Clarity, space

Semantic Layer
├── Priority/Delta       → Red family
├── Positive/Verified    → Green family
├── Risk/Uncertainty     → Amber family
├── Critical/Failure     → Red-bright family
└── Informational        → Blue family

Surface Layer (Dark Mode Default)
├── Background           → #000000, #09090B
├── Surface              → #18181B (zinc-900)
├── Elevated Surface     → #27272A (zinc-800)
├── Border               → #3F3F46 (zinc-700)
└── Text                 → #FFFFFF, #D4D4D8, #A1A1AA

Surface Layer (Light Mode)
├── Background           → #FAFAFA, #F4F4F5
├── Surface              → #FFFFFF
├── Elevated Surface     → #F4F4F5
├── Border               → #E4E4E7
└── Text                 → #000000, #27272A, #71717A
```

---

## Dark Mode Surfaces

Dark mode is the default experience. Surfaces use layered zinc to create depth without shadow dependency.

| Layer | Token | Value | Purpose |
|-------|-------|-------|---------|
| Canvas | `--surface-canvas` | `#000000` | Page-level background |
| Base | `--surface-base` | `#09090B` | Section backgrounds |
| Card | `--surface-card` | `#18181B` | Card containers |
| Elevated | `--surface-elevated` | `#27272A` | Floating elements, inputs |
| Overlay | `--surface-overlay` | `rgba(0,0,0,0.8)` | Modal backdrops |

---

## Light Mode Surfaces

| Layer | Token | Value | Purpose |
|-------|-------|-------|---------|
| Canvas | `--surface-canvas` | `#FAFAFA` | Page-level background |
| Base | `--surface-base` | `#F4F4F5` | Section backgrounds |
| Card | `--surface-card` | `#FFFFFF` | Card containers |
| Elevated | `--surface-elevated` | `#F4F4F5` | Floating elements |
| Overlay | `--surface-overlay` | `rgba(255,255,255,0.8)` | Modal backdrops |

---

## Contrast Requirements

All text/background combinations must meet **WCAG AAA** (7:1 for normal text, 4.5:1 for large text):

| Pair | Ratio | Pass |
|------|-------|------|
| White on Black | 21:1 | AAA |
| White on Zinc-900 | 15.4:1 | AAA |
| Zinc-300 on Zinc-900 | 9.7:1 | AAA |
| Red-600 on Black | 4.6:1 | AA Large |
| Red-600 on White | 4.5:1 | AA Large |
| White on Red-600 | 4.5:1 | AA Large |

**Rule**: Red is never used for small body text on dark backgrounds. Use red for display metrics, buttons, and badges where minimum size is 18px bold or 24px regular.

---

## Data Visualization Colors

Charts and graphs use the six-band palette. Each band is chosen for maximum distinguishability in both color vision and grayscale:

| Band | Hex | Name | Grayscale Equiv |
|------|-----|------|-----------------|
| A | `#DC2626` | Red | 30% |
| B | `#F97316` | Orange | 52% |
| C | `#FACC15` | Yellow | 78% |
| D | `#22C55E` | Green | 55% |
| E | `#3B82F6` | Blue | 42% |
| F | `#8B5CF6` | Purple | 38% |

---

## Sport Context Colors

When UI surfaces are scoped to a specific sport, these accent colors provide contextual identity without overriding brand hierarchy:

| Sport | Accent | Application |
|-------|--------|-------------|
| Football | `#8B5CF6` | Sport badge, chart accent, header highlight |
| Basketball | `#F97316` | Sport badge, chart accent, header highlight |
| Baseball | `#06B6D4` | Sport badge, chart accent, header highlight |
| Soccer | `#10B981` | Sport badge, chart accent, header highlight |

**Rule**: Sport colors are accent only — never replace brand red for primary actions.

---

## Red Usage Rules

Red is the power color of NIL Optic. Use it deliberately:

### Do
- Primary CTA buttons
- Value/valuation display numbers
- Active navigation indicators
- Notification badges
- Key metric highlights
- Hover glow effects on action elements

### Don't
- Body text on dark backgrounds (contrast issue)
- Large background fills (overwhelming)
- Warning states (use amber instead)
- Informational badges (use blue instead)
- Decoration without meaning
