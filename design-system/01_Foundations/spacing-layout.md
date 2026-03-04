# Spacing & Layout System

Last updated: 2026-03-01

---

## Base Unit

All spacing derives from a **4px base unit** (`--space-unit: 4px`).

| Token | Value | Px | Common Use |
|-------|-------|-----|------------|
| `--space-1` | 0.25rem | 4px | Tight gaps, icon padding |
| `--space-2` | 0.5rem | 8px | Inline spacing, badge padding |
| `--space-3` | 0.75rem | 12px | Input padding, compact cards |
| `--space-4` | 1rem | 16px | Standard padding, card gaps |
| `--space-5` | 1.25rem | 20px | Section padding |
| `--space-6` | 1.5rem | 24px | Card padding, group spacing |
| `--space-8` | 2rem | 32px | Section margins |
| `--space-10` | 2.5rem | 40px | Large section gaps |
| `--space-12` | 3rem | 48px | Page section dividers |
| `--space-16` | 4rem | 64px | Hero section padding |
| `--space-20` | 5rem | 80px | Major layout gaps |

---

## Grid System

### 12-Column Grid
- Columns: 12
- Gutter: 24px (space-6)
- Max width: `max-w-7xl` (80rem / 1280px)
- Extended: `max-w-[90rem]` (1440px) for 2xl screens
- Margin: auto-centered with `px-4` (mobile) to `px-8` (desktop)

### Common Grid Patterns

```
Dashboard:     [Sidebar 280px] [Main 12-col fluid]
Directory:     [Filters 280px] [Content 12-col fluid]
Card Grid:     3-col (desktop) → 2-col (tablet) → 1-col (mobile)
Data Table:    Full-width fluid with horizontal scroll
Profile:       [Left 4-col] [Right 8-col] at desktop
```

---

## Density Principle

> Favor clarity over density in vertical rhythm.

NIL Optic handles complex financial and athletic data. Rather than cramming information, we use generous spacing to let data breathe:

- Cards use `padding: space-6` (24px) minimum
- Table rows use `padding-y: space-3` (12px) minimum
- Section gaps use `space-8` (32px) minimum
- Metric numbers get 1.5x the spacing of body text around them

---

## Border Radius

| Token | Value | Usage |
|-------|-------|-------|
| `--radius-xs` | 4px | Badges, small chips |
| `--radius-sm` | 6px | Buttons, inputs |
| `--radius-md` | 8px | Small cards, dropdowns |
| `--radius-lg` | 12px | Standard cards |
| `--radius-xl` | 16px | Feature cards, modals |
| `--radius-2xl` | 24px | Auth shells, hero cards |
| `--radius-pill` | 9999px | Pills, status badges |

---

## Elevation

NIL Optic uses minimal elevation. Dark mode relies on surface color layering rather than shadows.

| Token | Value | Usage |
|-------|-------|-------|
| `--elevation-flat` | none | Default state |
| `--elevation-focus` | `0 0 0 2px rgba(220,38,38,0.25)` | Focus rings |
| `--elevation-card` | `0 1px 3px rgba(0,0,0,0.1)` | Light mode cards |
| `--elevation-compare` | `0 4px 12px rgba(0,0,0,0.15)` | Comparison emphasis |
| `--elevation-modal` | `0 20px 60px rgba(0,0,0,0.5)` | Modal dialogs |

---

## Z-Index Scale

| Token | Value | Usage |
|-------|-------|-------|
| `--z-base` | 0 | Page content |
| `--z-header` | 100 | Sticky headers, navigation |
| `--z-dropdown` | 200 | Dropdowns, popovers |
| `--z-overlay` | 300 | Overlay backdrops |
| `--z-modal` | 400 | Modal dialogs |
| `--z-toast` | 500 | Toast notifications |

---

## Responsive Breakpoints

| Name | Min Width | Typical Device |
|------|-----------|----------------|
| `sm` | 640px | Large phone landscape |
| `md` | 768px | Tablet portrait |
| `lg` | 1024px | Tablet landscape / small desktop |
| `xl` | 1280px | Desktop |
| `2xl` | 1536px | Large desktop |
