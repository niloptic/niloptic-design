# NIL Optic — World-Class UX Direction

> The definitive UX strategy for building the most intelligent, beautiful, and performant interface in sports technology.

Last updated: 2026-03-01

---

## Executive Summary

NIL Optic's UX must accomplish something no sports technology platform has achieved: Bloomberg-level data density with Linear-level design craft. This is not about making a "nice-looking dashboard." It's about building an interface so good that using any competitor afterward feels like going back to spreadsheets. This document defines the UX philosophy, patterns, systems, and standards that will make that happen.

---

## Design Philosophy

### The Three Truths

**1. Data IS the interface.**
Every pixel exists to make a number more legible, a trend more obvious, or a decision more confident. If an element doesn't serve data comprehension, it doesn't belong.

**2. Speed IS a feature.**
If a valuation takes more than 200ms to appear, we've failed. If a page transition takes more than 100ms, it feels broken. Performance is not an optimization — it's a design principle.

**3. Intelligence IS visible.**
The AI doesn't work in the background — it's a first-class citizen of the UI. Predictions, confidence scores, and factor breakdowns are not tooltips and footnotes. They are the main event.

---

## Reference Class: Best-in-Class Interfaces

NIL Optic's UX draws from the best across finance, sports, developer tools, and AI:

| Reference | What We Take | What We Skip |
|-----------|-------------|--------------|
| **Bloomberg Terminal** | Data density, real-time updates, keyboard-first navigation | Visual complexity, learning curve, monochrome aesthetic |
| **Linear** | Keyboard shortcuts, buttery animations, minimal chrome | Over-simplification of data-heavy views |
| **Stripe Dashboard** | Information hierarchy, progressive disclosure, typographic clarity | Consumer-friendly tone (we're more professional) |
| **Attio CRM** | Relationship visualization, flexible views, modern dark mode | Consumer-social aesthetic |
| **Vercel Dashboard** | Real-time status, deployment confidence, clean data | Developer-specific patterns |
| **Perplexity AI** | AI response transparency, source citations, streaming results | Chat-centric interface (we're dashboard-centric) |
| **Catapult / Sportradar** | Sports data visualization, athlete profiles, performance metrics | Enterprise-legacy UI patterns |

---

## Core UX Patterns

### 1. Command Palette (Cmd+K)

The single most important UX feature. Everything in NIL Optic is accessible through a keyboard-driven command palette.

**Behavior**:
- `Cmd+K` opens global search overlay
- Type to search athletes, agents, schools, features, settings
- Recent searches and frequently accessed items appear first
- Contextual actions based on current screen (e.g., on athlete profile: "Compare to...", "Add to roster", "View predictions")
- Keyboard-navigable results with instant preview

**Design Specs**:
```
Container: 560px wide, centered, max-height 420px
Background: rgba(0, 0, 0, 0.85) backdrop + blur(20px)
Border: 1px solid rgba(255, 255, 255, 0.08)
Border-radius: 12px
Input: 48px height, Inter 16px, no visible border
Results: 40px row height, Inter 14px
Highlight: rgba(220, 38, 38, 0.12) background on active row
Shadow: 0 24px 48px rgba(0, 0, 0, 0.4)
Animation: Scale from 0.98, opacity 0→1, 150ms ease-out
```

**Keyboard Shortcuts System**:
| Shortcut | Action |
|----------|--------|
| `Cmd+K` | Open command palette |
| `Cmd+/` | Show all keyboard shortcuts |
| `Cmd+1–5` | Switch between main nav sections |
| `Cmd+Shift+V` | Quick valuation lookup |
| `Cmd+Shift+P` | Open predictor |
| `Cmd+Shift+R` | Open roster builder |
| `Cmd+Shift+N` | New deal / new entry |
| `Esc` | Close overlay / go back |
| `J/K` | Navigate lists (vim-style) |
| `Enter` | Open/select |
| `Cmd+Enter` | Primary action on current item |

---

### 2. Role-Based Dashboard Shells

Every user sees a completely different experience based on their role. Not just different data — different layout, different navigation, different information hierarchy.

**Athletic Director Shell**:
```
┌─────────────────────────────────────────────────┐
│ [Logo]  Program Overview  Compliance  Budget  ◆ │  ← Top nav: institutional focus
├──────────┬──────────────────────────────────────┤
│ Sidebar  │  Program NIL Health Score         ▲  │
│ ────────│  ┌─────────┬─────────┬──────────┐   │
│ Dashboard│  │Total NIL │Compliant│ Budget   │   │
│ Athletes │  │ $4.2M   │  94%    │ 67% used │   │
│ Sports   │  └─────────┴─────────┴──────────┘   │
│ Compliance│ ┌──────────────────────────────────┐│
│ Budget   │  │ Sport-by-Sport Breakdown   [Grid]││
│ Reports  │  │ Football: $2.1M  Basketball: $890K│
│ Settings │  │ Baseball: $340K  Track: $210K    ││
│          │  └──────────────────────────────────┘│
│          │  ┌──────────────────────────────────┐│
│          │  │ Compliance Alerts          [Live]││
│          │  │ ⚠ 3 pending disclosures          ││
│          │  │ ✓ Revenue sharing on track        ││
│          │  └──────────────────────────────────┘│
└──────────┴──────────────────────────────────────┘
```

**Agent Shell**:
```
┌─────────────────────────────────────────────────┐
│ [Logo]  Portfolio  Pipeline  Market  Revenue  ◆ │  ← Top nav: deal-centric
├──────────┬──────────────────────────────────────┤
│ Sidebar  │  Active Deals Pipeline            ▲  │
│ ────────│  ┌──────┬──────┬──────┬──────────┐  │
│ Dashboard│  │Prospe│Outre│Negot│ Signed    │  │
│ Clients  │  │  12  │  8  │  5  │   23      │  │
│ Deals    │  └──────┴──────┴──────┴──────────┘  │
│ Discover │  ┌──────────────────────────────────┐│
│ Analytics│  │ Client Portfolio Value    [Chart]││
│ Revenue  │  │ Total: $12.4M  ▲ 18% this month ││
│ Settings │  │ [sparkline chart of portfolio]   ││
│          │  └──────────────────────────────────┘│
│          │  ┌──────────────────────────────────┐│
│          │  │ Top Opportunities         [List]││
│          │  │ 1. Jordan Smith → Nike ($45K)    ││
│          │  │ 2. Maria Chen → Gatorade ($32K)  ││
│          │  └──────────────────────────────────┘│
└──────────┴──────────────────────────────────────┘
```

**Athlete Shell**:
```
┌─────────────────────────────────────────────────┐
│ [Logo]  My Value  Deals  Brand  Growth        ◆ │  ← Top nav: personal focus
├─────────────────────────────────────────────────┤
│  ┌───────────────────────────────────────────┐  │
│  │        YOUR NIL VALUATION                 │  │
│  │         $42,500                           │  │
│  │     ▲ 12% from last month                │  │
│  │     Confidence: 87%                       │  │
│  │  [=============================------]    │  │
│  └───────────────────────────────────────────┘  │
│  ┌─────────────┬─────────────────────────────┐  │
│  │ 90-Day      │  Active Deals               │  │
│  │ Prediction  │  ┌─────────────────────┐    │  │
│  │ $48,200     │  │ Nike Campus · $5,000│    │  │
│  │ ▲ 13.4%     │  │ Local Auto · $2,500 │    │  │
│  │ [chart]     │  │ + 2 more            │    │  │
│  └─────────────┴──┴─────────────────────┘────┘  │
│  ┌───────────────────────────────────────────┐  │
│  │ What's Moving Your Value           [Live] │  │
│  │ ◉ Instagram engagement ▲ 24%  (+$3,200)  │  │
│  │ ◉ Team ranked #8 nationally   (+$1,800)  │  │
│  │ ◉ Missed 2 posting deadlines  (-$900)    │  │
│  └───────────────────────────────────────────┘  │
└─────────────────────────────────────────────────┘
```

---

### 3. AI-Native Interface Patterns

NIL Optic doesn't bolt AI on — the AI is woven into every surface.

**Valuation Card (Core Component)**:
```
┌─────────────────────────────────────────────┐
│  Jordan Smith          QB · SEC · Alabama    │
│                                              │
│  $142,500              Confidence: 91%       │
│  ▲ 8.2% (30d)         ████████████████░░░   │
│                                              │
│  Factors ─────────────────────────────────   │
│  ◉ Social (42%)  ◉ Athletic (31%)           │
│  ◉ Market (18%)  ◉ Comparable (9%)          │
│                                              │
│  90-Day Forecast ─────────────────────────   │
│  $148,200 – $167,800                         │
│  [confidence band visualization]             │
│                                              │
│  [View Full Profile]  [Add to Roster]        │
└─────────────────────────────────────────────┘
```

**AI Transparency Pattern (Perplexity-Inspired)**:
- Every AI-generated insight shows its sources
- Confidence scores on all predictions with tooltip explanation
- Factor attribution bars show what's driving each number
- "Why this number?" expandable section on every valuation
- Methodology link always one click away

**Streaming Prediction Updates**:
- Valuations update in real-time via WebSocket
- Number changes animate smoothly (counter animation, 200ms)
- Subtle pulse indicator when new data arrives
- "Last updated: 2 minutes ago" timestamp on all AI outputs

---

### 4. Data Visualization System

**Color System for Data**:
```
Positive/Growth:  #22C55E (green-500)
Negative/Decline: #EF4444 (red-400) — NOT brand red
Neutral/Stable:   #A1A1AA (zinc-400)
Brand Accent:     #DC2626 (red-600) — for selections, CTAs only
Confidence High:  #22C55E
Confidence Med:   #F59E0B (amber-500)
Confidence Low:   #EF4444
```

**Chart Defaults**:
- All charts dark background (#0A0A0A or #111111)
- Grid lines: rgba(255, 255, 255, 0.04) — barely visible
- Axis labels: zinc-500 (#71717A), Inter 11px
- Data labels: white (#FFFFFF), Inter 12px semibold
- Animation: 300ms ease-out on initial render, none on updates
- Responsive: Charts reflow, never overflow

**Core Chart Types**:
| Chart | Use Case | NIL Optic Application |
|-------|----------|----------------------|
| **Line + Confidence Band** | Trend over time with uncertainty | Valuation trajectory with prediction range |
| **Horizontal Bar** | Comparison across categories | Factor attribution, sport-by-sport breakdown |
| **Donut** | Part-of-whole | Revenue distribution, deal type mix |
| **Sparkline** | Inline trend indication | Table rows, card headers, nav items |
| **Scatter** | Correlation between variables | Valuation vs. social following, deals vs. performance |
| **Heat Map** | Density across two dimensions | Conference map, position value matrix |

---

### 5. Multi-View Data Pattern (HubSpot-Inspired)

Every data collection in NIL Optic supports three view modes:

**Grid View** (Default for browsing):
```
┌──────────┬──────────┬──────────┬──────────┐
│ [Avatar] │ [Avatar] │ [Avatar] │ [Avatar] │
│ J. Smith │ M. Chen  │ T. Park  │ A. Davis │
│ $142,500 │ $98,200  │ $87,600  │ $76,300  │
│ ▲ 8.2%   │ ▲ 12.1%  │ ▼ 3.4%   │ ▲ 1.2%   │
│ QB · SEC  │ WBB · B10│ P · ACC  │ WR · B12 │
└──────────┴──────────┴──────────┴──────────┘
```

**List View** (For scanning):
```
┌─ J. Smith    QB · Alabama · SEC    $142,500  ▲ 8.2%  91% ─┐
├─ M. Chen     WBB · Iowa · B10     $98,200   ▲ 12.1% 88% ─┤
├─ T. Park     P · Vanderbilt · ACC  $87,600   ▼ 3.4%  82% ─┤
└─ A. Davis    WR · Oklahoma · B12   $76,300   ▲ 1.2%  79% ─┘
```

**Table View** (For analysis):
```
┌──────────┬──────┬────────┬─────────┬───────┬──────┬────────┐
│ Name     │ Pos  │ School │ Value   │ Δ 30d │ Conf │ Deals  │
├──────────┼──────┼────────┼─────────┼───────┼──────┼────────┤
│ J. Smith │ QB   │ Alabama│$142,500 │+8.2%  │ 91%  │ 4      │
│ M. Chen  │ WBB  │ Iowa   │$98,200  │+12.1% │ 88%  │ 7      │
│ T. Park  │ P    │ Vandy  │$87,600  │-3.4%  │ 82%  │ 2      │
│ A. Davis │ WR   │ Oklaho │$76,300  │+1.2%  │ 79%  │ 3      │
└──────────┴──────┴────────┴─────────┴───────┴──────┴────────┘
```

**View Switcher**: Compact 3-icon toggle in top-right of data sections. Current view highlighted with brand red underline.

---

### 6. Real-Time Data Architecture

**WebSocket-Driven Updates**:
- Valuation changes stream in real-time
- Deal stage transitions update across all connected clients
- Compliance alerts push immediately to AD dashboards
- Transfer portal movements trigger instant notification + valuation recalculation

**Micro-Animation System for Data Changes**:
| Change Type | Animation |
|-------------|-----------|
| Value increase | Number counts up, brief green flash on container |
| Value decrease | Number counts down, brief red flash on container |
| New item | Slides in from top, 200ms ease-out |
| Removed item | Fades to 0 opacity, collapses height, 200ms |
| Status change | Pill color morphs with 150ms crossfade |
| Confidence update | Progress bar animates width, 300ms ease-out |

---

### 7. Dark Mode Excellence

NIL Optic's dark mode is not "inverted light mode." It's a carefully crafted luminance system.

**Surface Hierarchy**:
```
Level 0 (Page bg):     #0A0A0A  — near-black, not true black
Level 1 (Card bg):     #111111  — primary content surface
Level 2 (Elevated):    #1A1A1A  — modals, dropdowns, command palette
Level 3 (Hover):       #222222  — interactive hover states
Level 4 (Active):      #2A2A2A  — pressed/selected states
```

**Why not true #000000?**
- True black creates harsh contrast with white text, causing eye strain
- #0A0A0A provides depth perception (elements can go darker on hover/press)
- Matches OLED optimization without the flatness of #000
- Bloomberg, Linear, and Vercel all use off-black for this reason

**Text Hierarchy on Dark**:
```
Primary text:     #FFFFFF (100% white — headings, values, key data)
Secondary text:   #A1A1AA (zinc-400 — labels, descriptions)
Tertiary text:    #71717A (zinc-500 — timestamps, metadata)
Disabled text:    #52525B (zinc-600 — inactive states)
```

**Border System**:
```
Subtle:           rgba(255, 255, 255, 0.06)  — card edges, dividers
Medium:           rgba(255, 255, 255, 0.10)  — input borders, table rules
Strong:           rgba(255, 255, 255, 0.15)  — focused inputs, active elements
Brand:            rgba(220, 38, 38, 0.40)    — brand-accented borders
```

---

### 8. Loading & Skeleton System

**Skeleton Screens** (not spinners):
- Every component has a skeleton variant
- Skeletons match the exact layout of the loaded content
- Skeleton animation: subtle pulse (opacity 0.06 → 0.10), 1.5s cycle
- Content fades in over 200ms when loaded, replacing skeleton

**Progressive Loading Priority**:
1. Navigation and layout shell (instant)
2. Primary metric / headline number (< 200ms)
3. Supporting data and charts (< 500ms)
4. Secondary panels and lists (< 1000ms)
5. Images and avatars (lazy load on scroll)

**Empty States**:
- Every list, table, and grid has a designed empty state
- Empty states include: icon, headline, description, primary CTA
- Never show a blank area — always explain what goes here and how to fill it

---

### 9. Mobile-First Patterns (NILWatch)

The NILWatch mobile app is not a shrunken web app. It's a purpose-built athlete experience.

**Core Mobile Principles**:
- One primary action per screen
- Thumb-zone optimized (key actions in bottom 40% of screen)
- Swipe gestures for deal stage transitions
- Pull-to-refresh for valuation updates
- Haptic feedback on key interactions (value changes, deal milestones)

**Mobile Navigation**:
```
┌─────────────────────────┐
│                         │
│    [Athlete Content]    │
│                         │
│                         │
│                         │
├─────────────────────────┤
│ ◉Value  Deals  Brand  ⚙│  ← Bottom tab bar, 4 items max
└─────────────────────────┘
```

---

### 10. Accessibility as Design Quality

Accessibility is not a compliance checkbox — it's a design quality signal.

**Standards**:
- WCAG 2.2 AA minimum, AAA for core data elements
- All data visualizations include text alternatives
- Color is never the sole indicator (always paired with shape, label, or pattern)
- Full keyboard navigation for every feature
- Screen reader optimized with ARIA landmarks and live regions
- Focus indicators visible and styled (2px brand red outline, 2px offset)
- Reduced motion respected (prefers-reduced-motion: reduce)

**Contrast Requirements**:
| Element | Minimum Ratio |
|---------|--------------|
| Primary text on dark bg | 15.3:1 (AAA) |
| Secondary text on dark bg | 7.2:1 (AA) |
| Brand red on dark bg | 5.8:1 (AA) |
| Data values | 15.3:1 (AAA) — numbers must be maximally legible |
| Chart labels | 4.5:1 (AA minimum) |

---

## Interaction Design Standards

### Timing
| Interaction | Duration | Easing |
|------------|----------|--------|
| Hover state | 100ms | ease-out |
| Button press | 80ms | ease-in-out |
| Modal open | 200ms | ease-out (scale 0.95→1, opacity 0→1) |
| Modal close | 150ms | ease-in |
| Page transition | 0ms | Instant (no page transitions — SPA) |
| Tooltip appear | 200ms delay, 100ms fade |
| Toast notification | Slide in 250ms, auto-dismiss 4000ms |
| Data counter | 200ms per significant digit change |
| Skeleton pulse | 1500ms cycle, ease-in-out |

### Click Targets
- Minimum 44×44px for all interactive elements (mobile)
- Minimum 32×32px for desktop interactive elements
- 8px minimum spacing between adjacent click targets
- Ghost click area extends 4px beyond visible boundaries

### Form Design
- Labels always above inputs (never floating or inline)
- Error states: red-400 border + error message below input
- Success states: green-500 border + checkmark icon
- Autofocus on first field when entering a form context
- Tab order follows visual reading order (top-to-bottom, left-to-right)

---

## Responsive Breakpoints

| Breakpoint | Width | Layout |
|-----------|-------|--------|
| **Mobile** | < 640px | Single column, bottom nav, stacked cards |
| **Tablet** | 640–1024px | Two columns, collapsible sidebar, condensed data |
| **Desktop** | 1024–1440px | Full layout, sidebar + main + optional panel |
| **Wide** | > 1440px | Extended data views, multi-panel layouts |

**Responsive Rules**:
- Never horizontally scroll on any breakpoint
- Tables convert to card lists on mobile
- Charts resize and simplify (remove legend, reduce data points) on mobile
- Navigation converts from sidebar to bottom tabs on mobile
- Command palette is full-screen on mobile

---

## NIL-Specific Visualizations

### Valuation Confidence Band
```
     $160K ─ ─ ─ ─ ─ ─ ─ ─ ─╱╲─ ─ ─ ─ ─ ─ ─
           ╱░░░░░░░░░░░░░░░╱░░╲░░░░░░░░░░░░░
     $140K ╱░░░░░░░░░░░░░░╱░░░░╲░░░░░░░░░░░░
          ╱▓▓▓▓▓▓▓▓▓▓▓▓▓╱▓▓▓▓▓▓╲▓▓▓▓▓▓▓▓▓▓▓
     $120K─▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
           ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
     $100K ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─
           Jan    Feb    Mar    Apr    May   Jun
           ─── Actual   ▓▓▓ 68% CI   ░░░ 95% CI
```

### Factor Attribution Bar
```
  Social Media  ████████████████████░░░░░░░  42%
  Athletic Perf ████████████████░░░░░░░░░░░  31%
  Market Demand ████████░░░░░░░░░░░░░░░░░░░  18%
  Comparables   ████░░░░░░░░░░░░░░░░░░░░░░░   9%
```

### Deal Pipeline (Kanban)
```
  Prospect (12)    Outreach (8)     Negotiate (5)    Signed (23)
  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
  │ Nike     │    │ Adidas   │    │ Gatorade │    │ Local Co │
  │ $45,000  │    │ $32,000  │    │ $28,000  │    │ $15,000  │
  │ ◉ 72%    │    │ ◉ 65%    │    │ ◉ 88%    │    │ ✓ Done   │
  ├──────────┤    ├──────────┤    ├──────────┤    ├──────────┤
  │ Under A  │    │ Boost    │    │ ESPN     │    │ Fanatics │
  │ $22,000  │    │ $18,500  │    │ $55,000  │    │ $42,000  │
  │ ◉ 58%    │    │ ◉ 71%    │    │ ◉ 91%    │    │ ✓ Done   │
  └──────────┘    └──────────┘    └──────────┘    └──────────┘
```

---

## Design Quality Checklist

Before any screen ships, verify:

- [ ] All numbers use JetBrains Mono
- [ ] All text uses Inter
- [ ] Dark mode surfaces follow the 5-level hierarchy
- [ ] Data has proper positive/negative color coding
- [ ] Confidence scores are visible on all AI outputs
- [ ] Skeleton states exist for all async content
- [ ] Empty states are designed, not blank
- [ ] Keyboard navigation works for all interactions
- [ ] Command palette can reach this screen's key actions
- [ ] Mobile layout is purposeful, not just responsive reflow
- [ ] Loading time for primary data < 200ms (perceived)
- [ ] Animations respect prefers-reduced-motion
- [ ] Color contrast meets AA minimum (AAA for data)
- [ ] Click targets meet 44px minimum (mobile) / 32px (desktop)
- [ ] Real-time data changes animate smoothly

---

## Implementation Priority

### Phase 1: Foundation (Weeks 1–4)
- Design token system (CSS variables + Tailwind mapping)
- Dark mode surface hierarchy
- Typography scale implementation
- Core layout shells (AD, Agent, Athlete)
- Command palette (Cmd+K)
- Base component library (buttons, inputs, cards, badges)

### Phase 2: Intelligence Layer (Weeks 5–8)
- Valuation card component
- Confidence score visualization
- Factor attribution bars
- Prediction trend charts with confidence bands
- Streaming data animation system
- AI transparency patterns (source citations, methodology links)

### Phase 3: Data Surfaces (Weeks 9–12)
- Multi-view data pattern (grid/list/table)
- Data table component with sorting, filtering, column customization
- Deal pipeline (Kanban board)
- Roster builder interface
- Directory search and filter system
- Chart component library

### Phase 4: Mobile & Polish (Weeks 13–16)
- NILWatch mobile app design system
- Mobile-specific navigation and interaction patterns
- Micro-interaction polish across all surfaces
- Accessibility audit and remediation
- Performance optimization (skeleton states, progressive loading)
- Final design QA across all breakpoints
