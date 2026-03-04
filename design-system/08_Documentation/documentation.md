# Documentation Standards

Last updated: 2026-03-01

---

## Overview

Every component in the NIL Optic design system requires documentation. This ensures designers, developers, and AI agents can implement components consistently without ambiguity.

---

## Required Documentation Per Component

### 1. Component Anatomy

Visual breakdown of every part of the component:

```
Example: Metric Card Anatomy

┌─────────────────────────────────────┐
│ ① Category Label                    │  ← 01: Label SM, uppercase, zinc-400
│                                     │
│ ② Hero Metric                       │  ← 02: Display LG, red or white
│                                     │
│ ③ Delta Indicator   ④ Badge         │  ← 03: Data, green/red  |  04: Badge
│                                     │
│ ⑤ Context Text                      │  ← 05: Body SM, zinc-500
└─────────────────────────────────────┘
     ⑥ Container                         ← 06: zinc-900, radius-lg, p-6
```

### 2. Props / Variants

Document all configurable aspects:

| Prop | Type | Default | Options |
|------|------|---------|---------|
| `size` | enum | `md` | `sm`, `md`, `lg` |
| `variant` | enum | `default` | `default`, `highlighted`, `compact` |
| `showDelta` | boolean | `true` | — |
| `metric` | string | — | Dollar or numeric format |

### 3. Visual Variants

Show each variant with visual example:

```
Default:     Standard card with zinc-900 surface
Highlighted: Red left border accent, slight glow
Compact:     Reduced padding, no context text
```

### 4. Accessibility Notes

| Requirement | Implementation |
|-------------|---------------|
| Color contrast | All text meets WCAG AAA |
| Screen reader | Metric announced with label context |
| Keyboard | Focusable, Enter activates link |
| Reduced motion | No animation, static state |

### 5. Data Contracts

For components that display dynamic data:

| Field | Type | Format | Example |
|-------|------|--------|---------|
| `valuation` | number | USD currency | `$2,400,000` |
| `delta` | number | Percentage with sign | `+16.7%` |
| `confidence` | number | 0-100 integer | `87` |
| `updatedAt` | datetime | Relative | `2 hours ago` |

### 6. Do / Don't Rules

| Do | Don't |
|----|-------|
| Use for primary valuation display | Use for secondary/supporting metrics |
| Show exactly one hero metric | Stack multiple hero metrics in one card |
| Include delta when data supports it | Show delta without sufficient data points |
| Use red for valuation amounts | Use red for non-financial metrics |

---

## Documentation File Naming

```
design-system/08_Documentation/
├── anatomy/
│   ├── metric-card.md
│   ├── athlete-row.md
│   ├── deal-card.md
│   └── ...
├── contracts/
│   ├── valuation-contracts.md
│   ├── table-contracts.md
│   └── ...
├── accessibility/
│   ├── color-contrast-audit.md
│   ├── keyboard-navigation.md
│   └── screen-reader-guide.md
└── changelog.md
```

---

## Changelog Format

```markdown
## [2026-03-01] Design System v1.0

### Added
- Global Design System Library structure (00-08)
- Brand guidelines with full color, typography, and voice specs
- Complete foundations: color, typography, spacing, motion
- Primitives: buttons, inputs, controls, badges, indicators
- Components: cards, tables, navigation, charts, modals
- Patterns: loading, error, empty, feedback, overlays
- Feature components: valuation, predictor, roster, CRM, deals
- Templates: dashboard shells for AD, Agent, Athlete roles
- Marketing: hero, pricing, testimonials, CTAs, footer
- Documentation standards and contracts

### Design Decisions
- Dark mode as default experience
- Red (#DC2626) as sole brand accent — no secondary colors
- Inter + JetBrains Mono type pairing
- 4px base spacing unit
- WCAG AAA compliance target
- Skeleton loading over spinners
- Motion for state changes only, no decoration
```

---

## Governance

1. **Token changes** require updating `docs/design/design-tokens.md`
2. **New components** require full anatomy, variants, a11y, and contracts documentation
3. **Breaking changes** require changelog entry and version bump
4. **Component removal** requires deprecation notice for one version before deletion
5. **Route teams** consume via props/variants — never fork component styles locally
