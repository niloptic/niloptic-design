# Typography System

Last updated: 2026-03-01

---

## Overview

NIL Optic typography serves two masters: **editorial authority** for marketing and investor surfaces, and **data legibility** for product dashboards. The system uses Inter as the workhorse family and JetBrains Mono for numeric/data contexts.

---

## Font Families

### Inter — Primary Family
- Source: Google Fonts / Variable font
- Usage: All UI text, headings, body, labels
- Why: Excellent x-height, optimized for screens, variable weight support, comprehensive character set

### JetBrains Mono — Data Family
- Source: JetBrains / Google Fonts
- Usage: Financial figures, stats, IDs, code references, comparables
- Why: Tabular numerals, excellent at small sizes, clear distinction between similar characters (0/O, 1/l)

---

## Type Scale

### Display — Hero Metrics & Valuations

```
Display XL    48px / 3rem      Inter ExtraBold (800)    -0.02em    LH 1.1
Display LG    36px / 2.25rem   Inter ExtraBold (800)    -0.015em   LH 1.15
Display MD    30px / 1.875rem  Inter Bold (700)         -0.01em    LH 1.2
```

Use for: Valuation numbers ($2.4M), hero stats, pitch deck headlines, landing page metrics.

### Heading — Section Structure

```
H1            30px / 1.875rem  Inter Bold (700)         -0.01em    LH 1.2
H2            24px / 1.5rem    Inter Bold (700)         -0.005em   LH 1.25
H3            20px / 1.25rem   Inter SemiBold (600)     0          LH 1.3
H4            18px / 1.125rem  Inter SemiBold (600)     0          LH 1.35
```

Use for: Page titles, card headers, section labels, navigation groups.

### Body — Operational Content

```
Body LG       18px / 1.125rem  Inter Regular (400)      0          LH 1.5
Body          16px / 1rem      Inter Regular (400)      0          LH 1.5
Body SM       14px / 0.875rem  Inter Regular (400)      0          LH 1.4
```

Use for: Descriptions, explanations, form help text, long-form content.

### Data — Numeric & Statistical

```
Data LG       20px / 1.25rem   JetBrains Mono Med (500) 0.02em    LH 1.3
Data          14px / 0.875rem  JetBrains Mono Med (500) 0.02em    LH 1.4
Data SM       12px / 0.75rem   JetBrains Mono Med (500) 0.02em    LH 1.3
```

Use for: Dollar amounts in tables, stat lines, player IDs, confidence scores, comparisons.

### Label — Metadata & Controls

```
Label LG      14px / 0.875rem  Inter Medium (500)       0.01em    LH 1.3
Label         12px / 0.75rem   Inter Medium (500)       0.01em    LH 1.3
Label SM      11px / 0.6875rem Inter Medium (500)       0.02em    LH 1.2
```

Use for: Form labels, badge text, timestamps, table headers, filter chips.

---

## Hierarchy Rules

### Dashboard Context
1. **Metric first** — The largest number on any card should be Display or Data LG
2. **Label second** — Context around the metric uses Label weight
3. **Body last** — Explanatory text is smallest and lightest

### Marketing/Pitch Context
1. **Headline first** — Display XL for the hook
2. **Supporting metric** — Display LG for proof points
3. **Body** — Body LG for narrative

### Card Typography Stack

```
┌─────────────────────────────┐
│  Label SM  "NIL VALUATION"  │  ← Category label, uppercase, zinc-400
│                             │
│  Display LG  "$2.4M"       │  ← Hero metric, white or red
│                             │
│  Data  "+12.3% ▲"          │  ← Delta, mono, green/red
│                             │
│  Body SM  "Based on 847..." │  ← Context, zinc-400
└─────────────────────────────┘
```

---

## Color Pairing

| Text Role | Dark Mode | Light Mode |
|-----------|-----------|------------|
| Primary | `#FFFFFF` | `#000000` |
| Secondary | `#D4D4D8` (zinc-300) | `#27272A` (zinc-800) |
| Tertiary | `#A1A1AA` (zinc-400) | `#71717A` (zinc-500) |
| Accent | `#DC2626` (red-600) | `#DC2626` (red-600) |
| Positive | `#22C55E` (green-500) | `#16A34A` (green-600) |
| Negative | `#EF4444` (red-500) | `#DC2626` (red-600) |

---

## Responsive Behavior

| Breakpoint | Display XL | H1 | Body | Data |
|------------|------------|-----|------|------|
| Desktop (1280+) | 48px | 30px | 16px | 14px |
| Tablet (768-1279) | 36px | 24px | 16px | 14px |
| Mobile (<768) | 30px | 20px | 14px | 12px |

---

## Do / Don't

### Do
- Use mono font for all financial/statistical numbers
- Maintain consistent hierarchy within card components
- Let metrics breathe with generous line height
- Use letter-spacing for uppercase labels

### Don't
- Mix Inter and JetBrains Mono in the same text block
- Use Display sizes for non-metric content
- Underline text for emphasis (reserve for links)
- Use more than 3 type levels per card
- Set body text below 14px on mobile
