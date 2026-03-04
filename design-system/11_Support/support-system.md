# Support System Design Spec

Last updated: 2026-03-04

---

## Overview

The NIL Optic support system is a persistent, contextual help layer embedded across all authenticated surfaces. It enables self-service resolution for common NIL workflows, surfaces role-specific guidance, and provides escalation paths when human intervention is required. Basketball-first examples and terminology are used throughout. The system adapts by role (Athletic Director, Agent, Athlete, Coach, Fan) and by platform context (current page, current sport, current workflow step).

---

## Design Tokens — Support System

### Color Tokens

| Token                            | Dark Mode Value                        | Light Mode Value                     | Usage                          |
|----------------------------------|----------------------------------------|--------------------------------------|--------------------------------|
| `--support-surface`              | `#18181b` (zinc-900)                   | `#ffffff`                            | Help panel / drawer bg         |
| `--support-surface-elevated`     | `#27272a` (zinc-800)                   | `#f8fafc`                            | Article cards, FAQ items       |
| `--support-surface-hover`        | `#3f3f46` (zinc-700)                   | `#f1f5f9`                            | Interactive row hover          |
| `--support-border`               | `#27272a` (zinc-800)                   | `#d4d4d8`                            | Panel dividers, card borders   |
| `--support-border-focus`         | `rgba(220, 38, 38, 0.5)` (red-600/50) | `rgba(185, 28, 28, 0.3)`            | Focus ring on interactive els  |
| `--support-text-primary`         | `#f4f4f5` (zinc-100)                   | `#111827`                            | Article titles, headings       |
| `--support-text-secondary`       | `#a1a1aa` (zinc-400)                   | `#5f6f82`                            | Body text, descriptions        |
| `--support-text-muted`           | `#71717a` (zinc-500)                   | `#94a3b8`                            | Timestamps, meta labels        |
| `--support-accent`               | `#dc2626` (red-600)                    | `#dc2626`                            | CTAs, active states, links     |
| `--support-accent-hover`         | `#b91c1c` (red-700)                    | `#b91c1c`                            | CTA hover states               |
| `--support-launcher-bg`          | `#dc2626` (red-600)                    | `#dc2626`                            | Floating launcher button       |
| `--support-launcher-shadow`      | `0 4px 16px rgba(220,38,38,0.4)`      | `0 4px 16px rgba(220,38,38,0.25)`   | Launcher elevation             |
| `--support-search-bg`            | `#09090b` (zinc-950)                   | `#f8fafc`                            | Search input background        |
| `--support-tag-bg`               | `rgba(220, 38, 38, 0.15)`             | `rgba(220, 38, 38, 0.1)`            | Role/category tag bg           |
| `--support-tag-text`             | `#fca5a5` (red-300)                    | `#b91c1c`                            | Role/category tag text         |
| `--support-success-bg`           | `rgba(5, 46, 22, 0.2)`                | `rgba(220, 252, 231, 0.9)`          | Ticket resolved states         |
| `--support-warning-bg`           | `rgba(120, 53, 15, 0.2)`              | `rgba(254, 243, 199, 0.9)`          | Pending / awaiting states      |

### Typography Tokens

| Token                            | Value                                  | Usage                          |
|----------------------------------|----------------------------------------|--------------------------------|
| `--support-font-heading`         | Inter Semi-Bold 16/24                  | Panel title, section heads     |
| `--support-font-subheading`      | Inter Semi-Bold 14/20                  | Article card titles            |
| `--support-font-body`            | Inter Regular 14/20                    | Article body, descriptions     |
| `--support-font-body-sm`         | Inter Regular 13/18                    | Helper text, summaries         |
| `--support-font-label`           | Inter Medium 11/16, uppercase          | Section labels, tags           |
| `--support-font-mono`            | JetBrains Mono Regular 12/16          | Ticket IDs, timestamps         |
| `--support-font-search`          | Inter Regular 15/20                    | Search input text              |

### Spacing Tokens

| Token                            | Value      | Usage                          |
|----------------------------------|------------|--------------------------------|
| `--support-space-xs`             | 4px        | Inline icon gaps               |
| `--support-space-sm`             | 8px        | Tag padding, tight gaps        |
| `--support-space-md`             | 12px       | Card internal padding          |
| `--support-space-lg`             | 16px       | Section gaps                   |
| `--support-space-xl`             | 24px       | Panel padding                  |
| `--support-space-2xl`            | 32px       | Major section dividers         |
| `--support-drawer-width`         | 420px      | Desktop drawer width           |
| `--support-launcher-size`        | 56px       | Floating button diameter       |
| `--support-launcher-offset`      | 24px       | Distance from viewport edge    |

### Radius Tokens

| Token                            | Value      | Usage                          |
|----------------------------------|------------|--------------------------------|
| `--support-radius-sm`            | 6px        | Tags, badges                   |
| `--support-radius-md`            | 8px        | Cards, inputs, FAQ items       |
| `--support-radius-lg`            | 12px       | Drawer panel, modals           |
| `--support-radius-pill`          | 999px      | Launcher button, search field  |
| `--support-radius-xl`            | 16px       | Mobile full-screen sheet       |

### Elevation Tokens

| Token                            | Value                                              | Usage               |
|----------------------------------|----------------------------------------------------|---------------------|
| `--support-elevation-drawer`     | `-4px 0 24px rgba(0,0,0,0.4)`                     | Help drawer shadow  |
| `--support-elevation-launcher`   | `0 4px 16px rgba(220,38,38,0.4)`                  | Floating button     |
| `--support-elevation-card`       | `0 1px 3px rgba(0,0,0,0.12)`                      | Article cards       |
| `--support-elevation-tooltip`    | `0 2px 8px rgba(0,0,0,0.3)`                       | Contextual tooltips |

### Motion Tokens

| Token                            | Value             | Usage                          |
|----------------------------------|-------------------|--------------------------------|
| `--support-motion-drawer`        | 300ms ease-out    | Drawer slide-in/out            |
| `--support-motion-fade`          | 150ms ease        | Tooltip appear/dismiss         |
| `--support-motion-accordion`     | 200ms ease-out    | FAQ expand/collapse            |
| `--support-motion-spotlight`     | 400ms ease-out    | Tour spotlight transition      |

### Z-Index Tokens

| Token                            | Value   | Usage                          |
|----------------------------------|---------|--------------------------------|
| `--support-z-launcher`           | 900     | Floating launcher button       |
| `--support-z-drawer`             | 950     | Help drawer panel              |
| `--support-z-overlay`            | 940     | Backdrop overlay               |
| `--support-z-tooltip`            | 960     | Contextual help tooltips       |
| `--support-z-spotlight`          | 970     | Guided tour spotlight overlay  |

---

## Support Widget / Launcher

The launcher is a persistent floating action button anchored to the bottom-right corner of the viewport. It serves as the primary entry point to the help system.

### Launcher Wireframe

```
Desktop — Bottom-right floating launcher:

┌────────────────────────────────────────────────────────┐
│                                                        │
│  [Main Application Content]                            │
│                                                        │
│                                                        │
│                                                        │
│                                                        │
│                                                        │
│                                                        │
│                                                        │
│                                              ┌──────┐  │
│                                              │  ?   │  │  ← 56px circle
│                                              │      │  │    brand red bg
│                                              └──────┘  │    white icon
│                                              ← 24px →  │    24px from edge
└────────────────────────────────────────────────────────┘

Launcher with unread badge (new articles / open ticket update):

                                              ┌──────┐
                                              │  ?   │
                                              │   (2)│  ← 18px badge, top-right
                                              └──────┘
```

### Launcher Anatomy

| Element            | Token / Style                                             |
|--------------------|-----------------------------------------------------------|
| Container          | 56px circle, `--support-launcher-bg`, fixed position      |
| Icon               | 24px question mark, white, centered                       |
| Shadow             | `--support-elevation-launcher`                            |
| Badge              | 18px min-width, red-700 bg, white text, JetBrains Mono 10|
| Badge position     | Top-right of circle, -4px offset                          |
| Position           | `bottom: 24px; right: 24px;` fixed                       |
| Hover              | Scale 1.08, shadow intensifies                            |
| Active (pressed)   | Scale 0.96                                                |
| Z-index            | `--support-z-launcher` (900)                              |

### Launcher States

| State     | Visual                                                    |
|-----------|-----------------------------------------------------------|
| Default   | Red circle, white ? icon, subtle shadow                   |
| Hover     | Scale 1.08, intensified shadow                            |
| Active    | Scale 0.96, depressed                                     |
| Unread    | Red badge with count appears top-right                    |
| Drawer open| Icon morphs from ? to X (close), 200ms transition       |
| Hidden    | During guided tours, launcher hides to avoid overlap      |

### Launcher Accessibility

- `role="button"`
- `aria-label="Open help center"` (default) / `aria-label="Close help center"` (when open)
- `aria-expanded="true/false"` reflects drawer state
- `aria-haspopup="dialog"`
- Focus ring: 2px `--support-border-focus` offset
- Keyboard: `Enter` / `Space` to toggle drawer
- Tab order: placed after main content, before footer

---

## Help Panel / Drawer

The help drawer slides in from the right edge and provides the primary support interface. On desktop it overlays content with a backdrop. On mobile it becomes full-screen.

### Help Drawer — Desktop

```
┌──────────────────────────────────────────────────────────────────────┐
│                                                                      │
│  [Main Application Content]           ┌──────────────────────────┐  │
│  (dimmed, backdrop: black/50)         │  HELP CENTER          ╳  │  │
│                                        │                          │  │
│                                        │  ┌──────────────────────┐│  │
│                                        │  │ 🔍 Search help...   ││  │  ← Typeahead
│                                        │  └──────────────────────┘│  │
│                                        │                          │  │
│                                        │  QUICK LINKS             │  │  ← Section label
│                                        │  ┌──────────────────────┐│  │
│                                        │  │ Getting Started      ││  │
│                                        │  │ Basketball Rosters   ││  │
│                                        │  │ NIL Valuations       ││  │
│                                        │  │ Managing Deals       ││  │
│                                        │  └──────────────────────┘│  │
│                                        │                          │  │
│                                        │  POPULAR ARTICLES        │  │
│                                        │  ┌──────────────────────┐│  │
│                                        │  │ How do I check my    ││  │
│                                        │  │ basketball roster's  ││  │
│                                        │  │ NIL value?           ││  │
│                                        │  │ 5 min read  ● BB     ││  │
│                                        │  ├──────────────────────┤│  │
│                                        │  │ Understanding the    ││  │
│                                        │  │ NIL Predictor for    ││  │
│                                        │  │ March Madness        ││  │
│                                        │  │ 8 min read  ● BB     ││  │
│                                        │  └──────────────────────┘│  │
│                                        │                          │  │
│                                        │  ───────────────────     │  │
│                                        │                          │  │
│                                        │  [Browse All Articles]   │  │
│                                        │  [Contact Support]       │  │
│                                        │  [My Tickets (2)]        │  │
│                                        │                          │  │
│                                        └──────────────────────────┘  │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

### Help Drawer — Mobile (Full-Screen)

```
┌──────────────────────────────┐
│  ←  Help Center              │  ← Back arrow returns to app
│  ────────────────────────────│
│                              │
│  ┌──────────────────────────┐│
│  │ 🔍 Search help...       ││
│  └──────────────────────────┘│
│                              │
│  QUICK LINKS                 │
│  ┌──────────────────────────┐│
│  │ Getting Started        → ││
│  │ Basketball Rosters     → ││
│  │ NIL Valuations         → ││
│  │ Managing Deals         → ││
│  └──────────────────────────┘│
│                              │
│  POPULAR ARTICLES            │
│  ┌──────────────────────────┐│
│  │ How do I check my       ││
│  │ basketball roster's     ││
│  │ NIL value?              ││
│  │ 5 min read  ● BB        ││
│  ├──────────────────────────┤│
│  │ Understanding the NIL   ││
│  │ Predictor for March     ││
│  │ Madness                 ││
│  │ 8 min read  ● BB        ││
│  └──────────────────────────┘│
│                              │
│  [Browse All Articles]       │
│  [Contact Support]           │
│  [My Tickets (2)]            │
│                              │
└──────────────────────────────┘
```

### Drawer Anatomy

| Element                  | Token / Style                                            |
|--------------------------|----------------------------------------------------------|
| Drawer panel             | `--support-surface` bg, `--support-drawer-width` width   |
| Drawer shadow            | `--support-elevation-drawer`                             |
| Backdrop overlay         | `black/50`, `--support-z-overlay`                        |
| Close button             | 32px touch target, `--support-text-secondary` icon       |
| Panel header             | `--support-font-heading`, `--support-text-primary`       |
| Panel padding            | `--support-space-xl` (24px)                              |
| Section label            | `--support-font-label`, `--support-text-muted`           |
| Z-index                  | `--support-z-drawer` (950)                               |
| Enter animation          | Slide from right, `--support-motion-drawer` (300ms)      |
| Exit animation           | Slide to right, 200ms ease-in                            |
| Mobile behavior          | Full viewport, no backdrop needed                        |
| Scroll                   | Panel body scrolls independently, header is sticky       |

### Drawer Accessibility

- `role="dialog"`
- `aria-modal="true"`
- `aria-label="Help center"`
- Focus trap: Tab cycles within drawer while open
- `Escape` key closes drawer and returns focus to launcher
- First focusable element: search input
- Scroll lock on body when drawer is open (desktop)

---

## Help Search — Typeahead

The search bar is the primary interaction within the help drawer. It provides real-time typeahead results as the user types.

### Search Wireframe — Empty

```
┌──────────────────────────────────────┐
│  🔍  Search help articles...         │  ← Placeholder text
└──────────────────────────────────────┘

Surface: --support-search-bg
Border: 1px --support-border
Radius: --support-radius-pill
Height: 44px
Icon: 20px, --support-text-muted
Text: --support-font-search
```

### Search Wireframe — Typing with Results

```
┌──────────────────────────────────────┐
│  🔍  basketball roster              │  ← User input
└──────────────────────────────────────┘
┌──────────────────────────────────────┐
│                                      │
│  ARTICLES                            │  ← Section label
│  ┌──────────────────────────────────┐│
│  │ How do I check my basketball    ││  ← Bold match: "basketball"
│  │ roster's NIL value?             ││
│  │ Getting Started  ● 5 min read   ││  ← Category + read time
│  ├──────────────────────────────────┤│
│  │ Adding players to your          ││
│  │ basketball roster               ││
│  │ Roster Builder  ● 3 min read    ││
│  ├──────────────────────────────────┤│
│  │ Basketball roster import from   ││
│  │ transfer portal                 ││
│  │ Transfer Portal  ● 4 min read   ││
│  └──────────────────────────────────┘│
│                                      │
│  ACTIONS                             │  ← Quick actions section
│  ┌──────────────────────────────────┐│
│  │ → Go to Roster Builder          ││
│  │ → View basketball directory     ││
│  └──────────────────────────────────┘│
│                                      │
│  Can't find what you need?           │
│  [Contact Support]                   │
│                                      │
└──────────────────────────────────────┘
```

### Search Wireframe — No Results

```
┌──────────────────────────────────────┐
│  🔍  xyzabc123                       │
└──────────────────────────────────────┘
┌──────────────────────────────────────┐
│                                      │
│       No results found               │  ← --support-text-primary
│                                      │
│  Try different keywords or browse    │  ← --support-text-secondary
│  our help categories below.          │
│                                      │
│  [Browse Categories]                 │  ← Ghost button
│  [Contact Support]                   │  ← Primary link
│                                      │
└──────────────────────────────────────┘
```

### Search Wireframe — Loading

```
┌──────────────────────────────────────┐
│  🔍  basketball roster   [Spinner]   │  ← 16px spinner, right-aligned
└──────────────────────────────────────┘
┌──────────────────────────────────────┐
│                                      │
│  ████████████████████████████████    │  ← Skeleton line 1
│  ████████████████████                │  ← Skeleton line 2
│  ──────────────────────────────────  │
│  ████████████████████████████████    │  ← Skeleton line 3
│  ████████████████                    │  ← Skeleton line 4
│  ──────────────────────────────────  │
│  ████████████████████████████        │  ← Skeleton line 5
│  ████████████████████████            │
│                                      │
└──────────────────────────────────────┘
```

### Search Behavior

| Behavior              | Specification                                          |
|-----------------------|--------------------------------------------------------|
| Debounce              | 250ms after last keystroke                             |
| Minimum characters    | 2 characters before querying                           |
| Max results shown     | 5 articles + 3 quick actions                           |
| Match highlighting    | Bold matching substring in title                       |
| Keyboard navigation   | Arrow keys to move through results, Enter to select    |
| Escape                | Clears search input, collapses dropdown                |
| Index source          | Article title, summary, body, category, role tags      |
| Result ranking        | Relevance score, boosted by role match and sport match  |
| Analytics             | Log every query; track zero-result queries             |

### Search Accessibility

- `role="combobox"` on the search input
- `aria-expanded="true/false"` reflects dropdown visibility
- `aria-activedescendant` tracks highlighted result
- `role="listbox"` on the results dropdown
- `role="option"` on each result item
- Live region announces result count: "5 results found"

---

## Knowledge Base Article Card

Article cards are the primary content unit in the help system. They appear in search results, category listings, and the "Popular Articles" section.

### Article Card Wireframe

```
┌──────────────────────────────────────┐
│                                      │
│  How do I check my basketball        │  ← --support-font-subheading
│  roster's NIL value?                 │     --support-text-primary
│                                      │
│  Learn how to view aggregate and     │  ← --support-font-body-sm
│  per-player NIL valuations for your  │     --support-text-secondary
│  basketball roster in the Roster...  │     2-line clamp
│                                      │
│  Getting Started   5 min   ● BB      │  ← Category + read time + sport tag
│                                      │
└──────────────────────────────────────┘

Surface: --support-surface-elevated
Border: 1px --support-border
Radius: --support-radius-md
Padding: --support-space-md (12px)
Hover: --support-surface-hover bg, border shifts to --support-accent
```

### Article Card — Compact Variant (Search Results)

```
┌──────────────────────────────────────┐
│  How do I check my basketball        │  ← Title, bold match
│  roster's NIL value?                 │
│  Getting Started  ● 5 min read       │  ← Category + time, single line
└──────────────────────────────────────┘

Padding: --support-space-sm (8px) vertical, --support-space-md (12px) horizontal
No border, separator line between items
```

### Article Card Anatomy

| Element            | Token / Style                                           |
|--------------------|---------------------------------------------------------|
| Container          | `--support-surface-elevated` bg, `--support-border`     |
| Title              | `--support-font-subheading`, `--support-text-primary`   |
| Summary            | `--support-font-body-sm`, `--support-text-secondary`    |
| Category label     | `--support-font-label`, `--support-accent`              |
| Read time          | `--support-font-mono`, `--support-text-muted`           |
| Sport tag          | `--support-tag-bg`, `--support-tag-text`, 6px radius    |
| Hover state        | `--support-surface-hover`, left border accent            |
| Focus ring         | 2px `--support-border-focus`                            |

### Article Card States

| State     | Visual                                                    |
|-----------|-----------------------------------------------------------|
| Default   | Elevated surface, visible border                          |
| Hover     | Surface shifts to `--support-surface-hover`, red left bar |
| Focus     | 2px focus ring via `--support-border-focus`               |
| Loading   | Skeleton: title block + 2-line summary block + meta line  |
| Read      | Subtle "Read" checkmark badge top-right, muted surface    |

---

## Contact Support Form

A form within the help drawer that allows users to submit support tickets when self-service is insufficient.

### Contact Form Wireframe

```
┌──────────────────────────────────────┐
│  CONTACT SUPPORT                     │  ← Section heading
│                                      │
│  Category                            │
│  ┌──────────────────────────────────┐│
│  │ Select a category          ▼    ││  ← Dropdown
│  └──────────────────────────────────┘│
│                                      │
│  Subject                             │
│  ┌──────────────────────────────────┐│
│  │ Brief description of issue      ││  ← Text input
│  └──────────────────────────────────┘│
│                                      │
│  Description                         │
│  ┌──────────────────────────────────┐│
│  │ Provide details about what you  ││  ← Textarea, 4 rows min
│  │ need help with. Include any     ││
│  │ relevant player names, deal     ││
│  │ IDs, or error messages.         ││
│  └──────────────────────────────────┘│
│                                      │
│  Priority                            │
│  ○ Low — General question            │
│  ● Medium — Workflow blocked         │  ← Radio group
│  ○ High — Cannot use platform        │
│  ○ Critical — Data/compliance issue  │
│                                      │
│  Attachments                         │
│  ┌──────────────────────────────────┐│
│  │  [+ Drag or click to attach]    ││  ← File upload zone
│  │  Screenshots, exports, etc.     ││
│  └──────────────────────────────────┘│
│                                      │
│  ┌──────────────────────────────────┐│
│  │  Auto-captured context:         ││  ← Info box, muted
│  │  Page: /dashboard/roster-builder││
│  │  Role: Athletic Director        ││
│  │  Sport: Basketball              ││
│  │  Browser: Chrome 120            ││
│  └──────────────────────────────────┘│
│                                      │
│  [Cancel]          [Submit Ticket]   │  ← Secondary + Primary buttons
│                                      │
└──────────────────────────────────────┘
```

### Form Submission States

```
Submitting:
┌──────────────────────────────────────┐
│                                      │
│        [Spinner]                     │
│        Submitting your ticket...     │  ← --support-text-secondary
│                                      │
└──────────────────────────────────────┘

Success:
┌──────────────────────────────────────┐
│                                      │
│        [Checkmark Icon — Green]      │
│                                      │
│        Ticket submitted              │  ← --support-text-primary
│                                      │
│        Ticket #NIL-20260304-0847     │  ← JetBrains Mono, muted
│        We'll respond within 4 hours. │  ← Based on SLA for priority
│                                      │
│        [View My Tickets]             │  ← Primary link
│        [Back to Help Center]         │  ← Ghost link
│                                      │
└──────────────────────────────────────┘

Error:
┌──────────────────────────────────────┐
│                                      │
│  ┌──────────────────────────────────┐│
│  │ ⚠ Unable to submit ticket.      ││  ← Red error banner
│  │   Please try again or email     ││
│  │   support@niloptic.com          ││
│  └──────────────────────────────────┘│
│                                      │
│  [Try Again]                         │
│                                      │
└──────────────────────────────────────┘
```

### Contact Form Category Options

| Category              | Description                                         |
|-----------------------|-----------------------------------------------------|
| Billing & Account     | Subscription, payments, plan changes                |
| Technical Issue        | Bugs, errors, performance problems                  |
| Valuation Question     | NIL value methodology, data accuracy                |
| Compliance            | NCAA compliance, deal review, regulation questions  |
| Data Issue            | Missing or incorrect athlete/team data              |
| Feature Request       | New feature suggestions, workflow improvements      |
| Deal Management       | Deal workflow, contract, payment issues             |
| Transfer Portal       | Portal data, player tracking                        |
| Other                 | Anything not covered above                          |

### Form Field Tokens

| Element            | Token / Style                                           |
|--------------------|---------------------------------------------------------|
| Label              | `--support-font-body-sm`, `--support-text-primary`      |
| Input bg           | `--support-search-bg`                                   |
| Input border       | 1px `--support-border`                                  |
| Input focus        | 2px `--support-border-focus`                            |
| Input text         | `--support-font-body`, `--support-text-primary`         |
| Placeholder        | `--support-font-body`, `--support-text-muted`           |
| Error state        | Red border, red helper text below field                 |
| Required indicator | Red asterisk after label                                |
| Dropzone           | Dashed border, `--support-border`, 2px dash             |
| Context box        | `--support-surface-elevated` bg, muted text             |

---

## FAQ Accordion Component

FAQs use an accordion pattern for quick scanning. Each section groups related questions. Expandable items show answers inline without navigation.

### FAQ Accordion Wireframe — Collapsed

```
┌──────────────────────────────────────┐
│  FREQUENTLY ASKED QUESTIONS          │
│                                      │
│  Getting Started                     │  ← Category header
│  ┌──────────────────────────────────┐│
│  │  How do I view my basketball     ││
│  │  team's total NIL value?     [+] ││  ← Collapsed, chevron right
│  ├──────────────────────────────────┤│
│  │  What does the NIL Predictor     ││
│  │  score mean?                 [+] ││
│  ├──────────────────────────────────┤│
│  │  How is NIL valuation            ││
│  │  calculated for basketball   [+] ││
│  │  players?                        ││
│  └──────────────────────────────────┘│
│                                      │
│  Deals & Compliance                  │  ← Category header
│  ┌──────────────────────────────────┐│
│  │  How do I create a new NIL       ││
│  │  deal?                       [+] ││
│  ├──────────────────────────────────┤│
│  │  What compliance checks are      ││
│  │  required before signing?    [+] ││
│  └──────────────────────────────────┘│
│                                      │
└──────────────────────────────────────┘
```

### FAQ Accordion Wireframe — Expanded Item

```
┌──────────────────────────────────────┐
│  │  How do I view my basketball     ││
│  │  team's total NIL value?     [-] ││  ← Expanded, chevron down
│  │                                  ││
│  │  Navigate to the Roster Builder  ││  ← Answer body
│  │  from your dashboard sidebar.    ││     --support-font-body
│  │  Select your basketball program  ││     --support-text-secondary
│  │  and the aggregate NIL value     ││
│  │  appears at the top of the       ││
│  │  roster view. Individual player  ││
│  │  valuations are listed in the    ││
│  │  roster table below.             ││
│  │                                  ││
│  │  Related: "Understanding NIL     ││  ← Related article link
│  │  valuations" →                   ││     --support-accent
│  │                                  ││
│  ├──────────────────────────────────┤│
│  │  What does the NIL Predictor     ││
│  │  score mean?                 [+] ││  ← Still collapsed
│  └──────────────────────────────────┘│
```

### FAQ Accordion Anatomy

| Element            | Token / Style                                           |
|--------------------|---------------------------------------------------------|
| Category header    | `--support-font-heading`, `--support-text-primary`      |
| Question text      | `--support-font-subheading`, `--support-text-primary`   |
| Answer text        | `--support-font-body`, `--support-text-secondary`       |
| Expand icon        | 16px chevron, `--support-text-muted`, rotates 90deg     |
| Item container     | `--support-surface-elevated` bg                         |
| Item border        | 1px `--support-border` between items                    |
| Item padding       | `--support-space-md` (12px) vertical, `--support-space-lg` (16px) horizontal |
| Expand animation   | `--support-motion-accordion` (200ms ease-out)           |
| Answer max-height  | Animated from 0 to auto                                 |
| Related link       | `--support-font-body-sm`, `--support-accent`            |
| Hover state        | `--support-surface-hover` bg on question row            |

### FAQ Accordion Accessibility

- Each FAQ item is a `<details>` / `<summary>` pair or equivalent ARIA pattern
- `role="region"` on the answer container with `aria-labelledby` pointing to the question
- `aria-expanded="true/false"` on the toggle button
- Keyboard: `Enter` / `Space` toggles expansion
- Only one item expanded at a time per category (optional, configurable)
- Focus visible ring on interactive summary rows

---

## Contextual Help Tooltips

Contextual help tooltips are small inline affordances (? icon buttons) that appear next to complex features to provide immediate, context-aware guidance.

### Contextual Tooltip Wireframe

```
Inline help icon next to a label:

  NIL Valuation  [?]                    ← 16px circle, --support-text-muted
                  │
                  ▼
         ┌─────────────────────────────┐
         │  NIL Valuation is the       │  ← --support-font-body-sm
         │  estimated market value of  │     --support-text-primary
         │  an athlete's Name, Image,  │     on tooltip surface
         │  and Likeness based on      │
         │  social following, on-court │
         │  performance, market size,  │
         │  and brand potential.       │
         │                             │
         │  [Learn more →]             │  ← Links to full article
         └─────────────────────────────┘
            △ (arrow pointing to icon)

Tooltip surface: zinc-800 (dark), white (light)
Border: 1px --support-border
Radius: --support-radius-md
Max-width: 280px
Shadow: --support-elevation-tooltip
```

### Tooltip Placement Rules

| Screen Area          | Tooltip Position | Arrow Direction |
|----------------------|------------------|-----------------|
| Left half of screen  | Right of icon    | Points left     |
| Right half of screen | Left of icon     | Points right    |
| Near bottom edge     | Above icon       | Points down     |
| Default              | Below icon       | Points up       |

### Contextual Tooltip — Page-Specific Examples

| Page                 | Tooltip Location              | Content                                          |
|----------------------|-------------------------------|--------------------------------------------------|
| Roster Builder       | Next to "Aggregate NIL"       | Explanation of how roster-level NIL is calculated |
| Athlete Profile      | Next to "Predictor Score"     | What the AI predictor model considers             |
| Deal Dashboard       | Next to "Compliance Status"   | What each compliance status means                 |
| Transfer Portal      | Next to "Transfer Impact"     | How NIL value changes during transfer window      |
| Tournament View      | Next to "Bracket Boost"       | How March Madness tournament runs affect NIL      |

### Contextual Tooltip Anatomy

| Element            | Token / Style                                           |
|--------------------|---------------------------------------------------------|
| Trigger icon       | 16px circle, `?` character, `--support-text-muted`      |
| Trigger hover      | `--support-accent` text color                           |
| Tooltip surface    | zinc-800 (dark) / white (light), `--support-border`     |
| Tooltip text       | `--support-font-body-sm`, `--support-text-primary`      |
| Arrow              | 8px CSS triangle, matches tooltip surface color         |
| Max-width          | 280px                                                   |
| Padding            | `--support-space-md` (12px)                             |
| Shadow             | `--support-elevation-tooltip`                           |
| Appear             | `--support-motion-fade` (150ms)                         |
| Dismiss            | Click outside, `Escape`, or focus leaves                |
| "Learn more" link  | `--support-font-body-sm`, `--support-accent`            |

### Contextual Tooltip Accessibility

- Trigger: `role="button"`, `aria-label="More info about [feature name]"`
- Trigger: `aria-describedby` pointing to tooltip content ID
- Tooltip: `role="tooltip"` for hover variant, `role="dialog"` for click variant
- Click variant has focus trap for keyboard users
- Dismiss: `Escape` closes tooltip
- Hover variant: 300ms delay before showing, persists while hovering tooltip itself
- Mobile: always click-to-show (no hover variant)

---

## Role-Based Help Content

The support system tailors content based on the authenticated user's role. Each role has different feature access, different common questions, and different onboarding needs.

### Role Content Matrix

| Content Area            | AD  | Agent | Athlete | Coach | Fan |
|-------------------------|-----|-------|---------|-------|-----|
| Getting Started         | AD  | AGT   | ATH     | COA   | FAN |
| NIL Valuations          | Yes | Yes   | Own     | Team  | View|
| Roster Builder          | Yes | No    | No      | Yes   | No  |
| Deal Management         | Yes | Yes   | Own     | View  | No  |
| Transfer Portal         | Yes | Yes   | Own     | Yes   | View|
| Compliance              | Yes | Yes   | Basic   | Basic | No  |
| Predictions/Predictor   | Yes | Yes   | Own     | Team  | View|
| Directory               | Full| Full  | Limited | Full  | Full|
| Messaging               | Yes | Yes   | Yes     | Yes   | No  |
| Billing & Account       | Yes | Yes   | Yes     | No    | Yes |
| Tournament Intelligence | Yes | Yes   | Own     | Team  | View|
| CRM / Pipeline          | No  | Yes   | No      | No    | No  |

### Role-Specific Help Home Views

**Athletic Director:**
```
┌──────────────────────────────────────┐
│  Welcome back, Coach Smith           │
│  Athletic Director • Kentucky        │
│                                      │
│  FOR YOU                             │
│  ┌──────────────────────────────────┐│
│  │ Managing your basketball         ││
│  │ program's NIL budget            ││
│  ├──────────────────────────────────┤│
│  │ Conference NIL comparison        ││
│  │ reports explained               ││
│  ├──────────────────────────────────┤│
│  │ March Madness NIL prep guide    ││
│  └──────────────────────────────────┘│
│                                      │
│  QUICK ACTIONS                       │
│  → Export NIL report                 │
│  → View compliance dashboard         │
│  → Roster Builder walkthrough        │
└──────────────────────────────────────┘
```

**Agent:**
```
┌──────────────────────────────────────┐
│  Welcome back, Jordan                │
│  Agent • Creative Artists Agency     │
│                                      │
│  FOR YOU                             │
│  ┌──────────────────────────────────┐│
│  │ Building your athlete pipeline   ││
│  │ for basketball season           ││
│  ├──────────────────────────────────┤│
│  │ Using the NIL Predictor to find ││
│  │ undervalued basketball talent   ││
│  ├──────────────────────────────────┤│
│  │ Deal workflow: from pitch to    ││
│  │ signed contract                 ││
│  └──────────────────────────────────┘│
│                                      │
│  QUICK ACTIONS                       │
│  → Search athlete directory          │
│  → Create new deal                   │
│  → CRM pipeline overview             │
└──────────────────────────────────────┘
```

**Athlete:**
```
┌──────────────────────────────────────┐
│  Welcome, Marcus                     │
│  Athlete • Duke • Basketball         │
│                                      │
│  FOR YOU                             │
│  ┌──────────────────────────────────┐│
│  │ Understanding your NIL           ││
│  │ valuation                       ││
│  ├──────────────────────────────────┤│
│  │ How to review and accept        ││
│  │ deal offers                     ││
│  ├──────────────────────────────────┤│
│  │ Your transfer portal options    ││
│  │ and NIL impact                  ││
│  └──────────────────────────────────┘│
│                                      │
│  QUICK ACTIONS                       │
│  → View my valuation                 │
│  → Check pending deals               │
│  → Update my profile                 │
└──────────────────────────────────────┘
```

### Role Tag Component

```
Role tags appear on article cards to indicate audience:

  [AD]  [AGENT]  [ATHLETE]  [COACH]  [FAN]

Active tag (this role matches user):
  Surface: --support-accent (red-600)
  Text: white
  Radius: --support-radius-sm

Inactive tag (other roles):
  Surface: --support-tag-bg
  Text: --support-tag-text
  Radius: --support-radius-sm

Size: --support-font-label height, 4px horizontal padding
```

---

## In-App Guided Tours / Spotlight Overlays

Guided tours walk first-time users through key workflows using spotlight overlays that highlight specific UI elements with step-by-step instructions.

### Spotlight Overlay Wireframe

```
┌──────────────────────────────────────────────────────────┐
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│  ← Dimmed overlay
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│    black/70
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒┌─────────────────────┐▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒│                     │▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│  ← Spotlight cutout
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒│  [Highlighted UI    │▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│    around target
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒│   Element]          │▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│    element
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒│                     │▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒└─────────────────────┘▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒          │            ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒          ▼            ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒┌───────────────────────────┐▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│                           │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│  Step 2 of 5              │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│  ← Tooltip card
│  ▒▒▒▒▒▒▒▒▒▒│                           │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│  Your Basketball Roster   │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│                           │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│  This shows every player  │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│  on your basketball team  │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│  with their current NIL   │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│  valuation and predictor   │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│  score.                   │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│                           │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│  [Back]  ●●○○○  [Next]   │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│           [Skip Tour]     │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒│                           │▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒└───────────────────────────┘▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
│  ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│
└──────────────────────────────────────────────────────────┘
```

### Tour Step Tooltip Anatomy

```
┌───────────────────────────────┐
│  Step 2 of 5                  │  ← --support-font-label, --support-text-muted
│                               │
│  Your Basketball Roster       │  ← --support-font-heading, --support-text-primary
│                               │
│  This shows every player on   │  ← --support-font-body, --support-text-secondary
│  your basketball team with    │
│  their current NIL valuation  │
│  and predictor score.         │
│                               │
│  [Back]  ●●○○○  [Next]       │  ← Navigation + progress dots
│           [Skip Tour]         │  ← Ghost link, --support-text-muted
│                               │
└───────────────────────────────┘

Tooltip surface: --support-surface (zinc-900 / white)
Border: 1px --support-border
Radius: --support-radius-lg (12px)
Max-width: 340px
Padding: --support-space-xl (24px)
Shadow: --support-elevation-drawer
```

### Guided Tour Inventory — Basketball-First

| Tour ID              | Role(s)     | Steps | Description                                              |
|----------------------|-------------|-------|----------------------------------------------------------|
| `tour-ad-welcome`    | AD          | 6     | Dashboard overview, roster, valuations, compliance, reports |
| `tour-agent-welcome` | Agent       | 5     | Directory, pipeline, deal creation, predictor, messaging  |
| `tour-athlete-welcome`| Athlete    | 4     | Profile, valuation, deals inbox, transfer portal          |
| `tour-coach-welcome` | Coach       | 5     | Roster view, player valuations, compliance, tournaments   |
| `tour-fan-welcome`   | Fan         | 3     | Directory browsing, player profiles, tournament tracker   |
| `tour-roster-builder`| AD, Coach   | 5     | Add players, view NIL breakdown, compare, export          |
| `tour-deal-flow`     | AD, Agent   | 6     | Create deal, assign athlete, compliance check, sign, track|
| `tour-march-madness` | All         | 4     | Tournament bracket, NIL impact tracking, predictions      |
| `tour-transfer-portal`| AD, Agent, Athlete | 5 | Browse portal, filter by sport, track NIL impact, watchlist |

### Spotlight Overlay Tokens

| Element            | Token / Style                                           |
|--------------------|---------------------------------------------------------|
| Overlay bg         | `black/70`, `--support-z-spotlight`                     |
| Spotlight cutout   | 8px padding around target, 8px border-radius            |
| Spotlight ring     | 2px pulsing `--support-accent` glow around cutout       |
| Tooltip surface    | `--support-surface`, `--support-border`                 |
| Tooltip arrow      | 12px CSS triangle pointing toward cutout                |
| Step counter       | `--support-font-label`, `--support-text-muted`          |
| Title              | `--support-font-heading`, `--support-text-primary`      |
| Body               | `--support-font-body`, `--support-text-secondary`       |
| Progress dots      | 8px circles, active: `--support-accent`, inactive: zinc-600 |
| Nav buttons        | Ghost variant, `--support-text-primary`                 |
| Skip link          | `--support-font-body-sm`, `--support-text-muted`        |
| Transition         | `--support-motion-spotlight` (400ms ease-out)           |

### Tour Behavior

| Behavior                  | Specification                                          |
|---------------------------|--------------------------------------------------------|
| Trigger                   | First login per role, or manual from Help Center       |
| Persistence               | Tour completion stored per user in localStorage/DB     |
| Restart                   | Available from Help Center > "Restart guided tour"     |
| Skip                      | "Skip Tour" link at every step                         |
| Step navigation           | Back/Next buttons, keyboard arrows                     |
| Scroll handling           | Auto-scrolls target element into view                  |
| Resize handling           | Recalculates cutout position on viewport change        |
| Interaction               | Target element is interactive during spotlight         |
| Completion                | Final step shows completion message with suggested next actions |

### Tour Accessibility

- Overlay: `role="dialog"`, `aria-modal="true"`, `aria-label="Guided tour"`
- Focus trap within tooltip
- `Escape` skips the entire tour
- Arrow keys navigate between steps
- Screen reader announces: step number, title, body text
- Progress dots: `role="progressbar"`, `aria-valuenow`, `aria-valuemax`

---

## Support Ticket Status Tracker

Users can track their submitted support tickets from within the help panel.

### Ticket List Wireframe

```
┌──────────────────────────────────────┐
│  MY TICKETS                          │
│                                      │
│  ┌──────────────────────────────────┐│
│  │ ● OPEN                          ││
│  │   #NIL-20260303-1247            ││  ← JetBrains Mono
│  │   Basketball roster not loading  ││  ← --support-font-subheading
│  │   for 2026 season               ││
│  │   Submitted 1d ago  ● P2 High   ││  ← Timestamp + priority badge
│  │   Status: In Progress           ││  ← Status badge
│  ├──────────────────────────────────┤│
│  │ ● OPEN                          ││
│  │   #NIL-20260301-0891            ││
│  │   Valuation discrepancy for     ││
│  │   Marcus Thompson               ││
│  │   Submitted 3d ago  ● P3 Medium ││
│  │   Status: Awaiting Response     ││
│  ├──────────────────────────────────┤│
│  │   RESOLVED                      ││  ← Muted styling
│  │   #NIL-20260228-0432            ││
│  │   Cannot export NIL report      ││
│  │   Resolved 5d ago  ● P3 Medium  ││
│  │   Status: Resolved              ││
│  └──────────────────────────────────┘│
│                                      │
│  Showing 3 tickets                   │
│  [View All in Full Page]             │
│                                      │
└──────────────────────────────────────┘
```

### Single Ticket Detail Wireframe

```
┌──────────────────────────────────────┐
│  ← Back to tickets                   │
│                                      │
│  #NIL-20260303-1247                  │  ← JetBrains Mono
│  Basketball roster not loading       │  ← --support-font-heading
│  for 2026 season                     │
│                                      │
│  ┌──────────────────────────────────┐│
│  │  Status    │ In Progress         ││
│  │  Priority  │ P2 — High           ││
│  │  Category  │ Technical Issue     ││
│  │  Created   │ 2026-03-03 12:47    ││
│  │  Updated   │ 2026-03-04 09:15    ││
│  │  Assigned  │ Support Team        ││
│  └──────────────────────────────────┘│
│                                      │
│  TIMELINE                            │
│  ┌──────────────────────────────────┐│
│  │  ● Mar 4, 9:15 AM               ││
│  │    Agent Response                ││
│  │    "We've identified the issue.  ││
│  │    The 2026 season roster data   ││
│  │    import is being processed.    ││
│  │    Expected resolution: today."  ││
│  │                                  ││
│  │  ○ Mar 3, 12:47 PM              ││
│  │    Ticket Created                ││
│  │    "Basketball roster shows      ││
│  │    empty for the new season.     ││
│  │    All other sports load fine."  ││
│  └──────────────────────────────────┘│
│                                      │
│  ADD REPLY                           │
│  ┌──────────────────────────────────┐│
│  │ Type your reply...               ││
│  └──────────────────────────────────┘│
│  [+ Attach]          [Send Reply]    │
│                                      │
└──────────────────────────────────────┘
```

### Ticket Status Badges

| Status              | Badge Color                    | Text                |
|---------------------|--------------------------------|---------------------|
| Open                | `--support-accent` bg, white   | Open                |
| In Progress         | Blue-600 bg, white             | In Progress         |
| Awaiting Response   | Amber-600 bg, white            | Awaiting Response   |
| Resolved            | Green-600 bg, white            | Resolved            |
| Closed              | Zinc-600 bg, white             | Closed              |

### Priority Badges

| Priority   | Badge Color                    | Label              |
|------------|--------------------------------|--------------------|
| P1 Critical| Red-700 bg, white              | P1 Critical        |
| P2 High    | Red-600 bg, white              | P2 High            |
| P3 Medium  | Amber-600 bg, white            | P3 Medium          |
| P4 Low     | Zinc-600 bg, white             | P4 Low             |

### Ticket Tracker Tokens

| Element            | Token / Style                                           |
|--------------------|---------------------------------------------------------|
| Ticket ID          | `--support-font-mono`, `--support-text-muted`           |
| Ticket title       | `--support-font-subheading`, `--support-text-primary`   |
| Timeline node (active)  | 10px circle, `--support-accent`                    |
| Timeline node (past)    | 10px circle, `--support-border`                    |
| Timeline line      | 2px, `--support-border`, vertical connector             |
| Timeline entry     | `--support-font-body-sm`, `--support-text-secondary`    |
| Reply input        | Same tokens as contact form fields                      |
| Status badge       | Inter Medium 11, white text, 4px radius, category color |
| Priority badge     | Inter Medium 11, white text, 4px radius, priority color |

---

## Responsive Behavior

| Breakpoint   | Layout                                                    |
|--------------|-----------------------------------------------------------|
| Desktop (>1024px) | 420px right drawer with backdrop overlay             |
| Tablet (768-1024px) | 360px right drawer with backdrop overlay           |
| Mobile (<768px) | Full-screen sheet, no backdrop, back arrow navigation  |

### Desktop vs Mobile Adaptations

| Component             | Desktop                       | Mobile                        |
|-----------------------|-------------------------------|-------------------------------|
| Help Drawer           | 420px right panel, overlay    | Full-screen sheet             |
| Search results        | Dropdown below input          | Full-screen results list      |
| Article view          | Inline within drawer          | Full-screen article           |
| FAQ accordion         | Standard accordion            | Full-width, larger touch targets |
| Contact form          | Inline within drawer          | Full-screen form              |
| Ticket list           | Inline within drawer          | Full-screen list              |
| Guided tour tooltip   | Positioned near target        | Bottom sheet with scroll-to   |
| Launcher button       | 56px, bottom-right            | 48px, bottom-right, 16px offset |
| Contextual tooltips   | Hover + click                 | Click only, larger hit area   |

### Mobile Full-Screen Sheet Pattern

```
┌──────────────────────────────┐
│  ←  [Title]                  │  ← Sticky header with back nav
│  ────────────────────────────│
│                              │
│  [Scrollable Content]        │  ← Full viewport height
│                              │
│                              │
│                              │
│                              │
│                              │
│                              │
│  ────────────────────────────│
│  [Primary Action]            │  ← Sticky bottom bar (if needed)
└──────────────────────────────┘

Enter: slide up from bottom, 300ms
Exit: slide down, 200ms
Full viewport, safe area insets respected
```

---

## Accessibility Summary

### ARIA Roles and Landmarks

| Component             | ARIA Role           | Notes                              |
|-----------------------|---------------------|------------------------------------|
| Launcher button       | `button`            | `aria-expanded`, `aria-haspopup`   |
| Help drawer           | `dialog`            | `aria-modal="true"`                |
| Search input          | `combobox`          | `aria-expanded`, `aria-activedescendant` |
| Search results        | `listbox`           | Children have `role="option"`      |
| FAQ item toggle       | `button`            | `aria-expanded`                    |
| FAQ answer region     | `region`            | `aria-labelledby`                  |
| Contextual tooltip    | `tooltip` / `dialog`| Hover vs click variant             |
| Tour overlay          | `dialog`            | `aria-modal="true"`                |
| Tour progress         | `progressbar`       | `aria-valuenow`, `aria-valuemax`   |
| Ticket status badge   | `status`            | Live region for updates            |

### Keyboard Navigation

| Action                    | Key(s)                                |
|---------------------------|---------------------------------------|
| Open/close help drawer    | Launcher focus + `Enter` / `Space`    |
| Close any overlay         | `Escape`                              |
| Navigate search results   | `Arrow Up` / `Arrow Down`             |
| Select search result      | `Enter`                               |
| Clear search              | `Escape` (when input focused)         |
| Toggle FAQ item           | `Enter` / `Space`                     |
| Navigate tour steps       | `Arrow Left` / `Arrow Right`          |
| Skip tour                 | `Escape`                              |
| Tab through form fields   | `Tab` / `Shift+Tab`                   |

### Focus Management

- Drawer open: focus moves to search input
- Drawer close: focus returns to launcher button
- Tour start: focus moves to first step tooltip
- Tour end: focus returns to triggering element or launcher
- Tooltip open: focus moves into tooltip (click variant)
- Tooltip close: focus returns to trigger icon
- Form submit: focus moves to success/error feedback region

### Screen Reader Behavior

- Search: live region announces result count after debounce
- Tour: announces step number and content on each transition
- Ticket status: live region announces status changes
- FAQ: announces expanded/collapsed state
- Error states: assertive live region for form errors

---

## State Summary

| Component        | Empty              | Loading           | Error              | Results           | No Results        |
|------------------|--------------------|-------------------|--------------------|-------------------|-------------------|
| Search           | Placeholder shown  | Skeleton lines    | "Search unavailable"| Article list      | "No results" + CTA|
| Article list     | "No articles yet"  | Card skeletons    | "Unable to load"   | Card grid/list    | "No articles match"|
| FAQ              | "FAQ coming soon"  | Shimmer rows      | "Unable to load"   | Accordion groups  | N/A               |
| Ticket list      | "No tickets yet"   | Row skeletons     | "Unable to load"   | Ticket rows       | N/A               |
| Contact form     | Empty fields       | Spinner on submit | Error banner       | N/A               | N/A               |
| Guided tour      | N/A                | N/A               | Skip to next step  | Active spotlight   | N/A               |
| Contextual tip   | N/A                | N/A               | "Help unavailable" | Tooltip visible    | N/A               |
