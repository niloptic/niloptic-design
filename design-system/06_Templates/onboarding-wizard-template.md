# Onboarding Wizard Template

Last updated: 2026-03-04

---

## Overview

This document defines the template-level visual spec for the onboarding wizard layout. It covers the full wizard shell composition at each breakpoint, progress stepper variants, step content area, navigation controls, and the completion screen.

The component-level spec (individual step content, question types, validation rules) lives in `10_Onboarding/`. This template defines the structural scaffold that wraps any onboarding step content.

Key constraints from capabilities-matrix.md:
- Onboarding question/flow management is admin-internal only (`/admin/onboarding`)
- User onboarding must not include role-selection prompts
- Role context is derived from authenticated role/profile state
- Fan signup defaults to non-team preview-only NIL access
- Operator signup maps to paid-plan onboarding

---

## Wizard Shell Layout

### Desktop (>= 1024px)

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│  [NIL Optic Logo]                              Step 2 of 5       │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                    PROGRESS STEPPER                          ││
│  │                                                              ││
│  │   ●────────●────────○────────○────────○                     ││
│  │  Profile   Org     Program  Budget   Review                  ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │                    STEP CONTENT AREA                          ││
│  │                                                              ││
│  │  ┌────────────────────────────────────────────────────────┐  ││
│  │  │                                                        │  ││
│  │  │   Step Title                                           │  ││
│  │  │   Step description text explaining what this           │  ││
│  │  │   step collects and why.                               │  ││
│  │  │                                                        │  ││
│  │  │   ┌──────────────────────────────────────────────┐     │  ││
│  │  │   │                                              │     │  ││
│  │  │   │   [Form fields / selections / content]       │     │  ││
│  │  │   │                                              │     │  ││
│  │  │   │   Field Label                                │     │  ││
│  │  │   │   ┌────────────────────────────────────┐     │     │  ││
│  │  │   │   │  Input value                       │     │     │  ││
│  │  │   │   └────────────────────────────────────┘     │     │  ││
│  │  │   │                                              │     │  ││
│  │  │   │   Field Label                                │     │  ││
│  │  │   │   ┌────────────────────────────────────┐     │     │  ││
│  │  │   │   │  Input value                       │     │     │  ││
│  │  │   │   └────────────────────────────────────┘     │     │  ││
│  │  │   │                                              │     │  ││
│  │  │   └──────────────────────────────────────────────┘     │  ││
│  │  │                                                        │  ││
│  │  └────────────────────────────────────────────────────────┘  ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                    NAVIGATION CONTROLS                       ││
│  │                                                              ││
│  │   [<- Back]                               [Continue ->]      ││
│  │                                                              ││
│  │                    Skip this step                            ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │   Need help? Contact support@niloptic.com                    ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Tablet (768px - 1023px)

```
┌────────────────────────────────────────────┐
│                                            │
│  [NIL Optic Logo]           Step 2 of 5    │
│                                            │
│  ┌────────────────────────────────────────┐│
│  │         PROGRESS STEPPER               ││
│  │                                        ││
│  │  ●────────●────────○────────○────────○ ││
│  │ Profile   Org    Program  Budget  Rev  ││
│  │                                        ││
│  └────────────────────────────────────────┘│
│                                            │
│  ┌────────────────────────────────────────┐│
│  │                                        ││
│  │  Step Title                            ││
│  │  Step description.                     ││
│  │                                        ││
│  │  ┌──────────────────────────────────┐  ││
│  │  │  [Form fields / content]         │  ││
│  │  │                                  │  ││
│  │  │  Field Label                     │  ││
│  │  │  ┌────────────────────────────┐  │  ││
│  │  │  │  Input value               │  │  ││
│  │  │  └────────────────────────────┘  │  ││
│  │  │                                  │  ││
│  │  └──────────────────────────────────┘  ││
│  │                                        ││
│  └────────────────────────────────────────┘│
│                                            │
│  ┌────────────────────────────────────────┐│
│  │  [<- Back]            [Continue ->]    ││
│  │              Skip this step            ││
│  └────────────────────────────────────────┘│
│                                            │
└────────────────────────────────────────────┘
```

### Mobile (< 768px)

```
┌──────────────────────────┐
│                          │
│  [Logo]     Step 2 of 5  │
│                          │
│  ┌──────────────────────┐│
│  │  COMPACT DOT STEPPER ││
│  │                      ││
│  │   ●  ●  ○  ○  ○     ││
│  │                      ││
│  └──────────────────────┘│
│                          │
│  ┌──────────────────────┐│
│  │                      ││
│  │  Step Title          ││
│  │  Step description.   ││
│  │                      ││
│  │  Field Label         ││
│  │  ┌────────────────┐  ││
│  │  │  Input value   │  ││
│  │  └────────────────┘  ││
│  │                      ││
│  │  Field Label         ││
│  │  ┌────────────────┐  ││
│  │  │  Input value   │  ││
│  │  └────────────────┘  ││
│  │                      ││
│  └──────────────────────┘│
│                          │
│  ┌──────────────────────┐│
│  │                      ││
│  │  [Continue ->]       ││
│  │                      ││
│  │  [<- Back]           ││
│  │                      ││
│  │  Skip this step      ││
│  │                      ││
│  └──────────────────────┘│
│                          │
└──────────────────────────┘
```

---

## Progress Stepper Variants

### Horizontal Stepper (Desktop + Tablet)

Used when viewport width >= 768px. Shows labeled steps with connecting lines.

```
  ●─────────●─────────○─────────○─────────○
 Profile    Org     Program   Budget    Review
 (done)   (active) (pending) (pending) (pending)
```

States:
- **Completed**: Filled circle `●`, label in `--ui-text-primary`
- **Active**: Filled circle `●` with pulsing ring, label in `--auth-accent-primary` (`#DC2626`)
- **Pending**: Hollow circle `○`, label in `--ui-text-muted`
- **Connecting line (done)**: Solid, `--ui-text-primary`
- **Connecting line (pending)**: Dashed or dimmed, `--ui-border-default`

Token mapping:
| Element | Token |
| --- | --- |
| Completed dot fill | `--ui-text-primary` |
| Active dot fill | `--auth-accent-primary` |
| Active pulse ring | `--auth-accent-focus-ring` |
| Pending dot stroke | `--ui-border-strong` |
| Completed line | `--ui-text-secondary` |
| Pending line | `--ui-border-default` |
| Step label (done) | `--ui-text-secondary` |
| Step label (active) | `--auth-accent-primary` |
| Step label (pending) | `--ui-text-muted` |

### Compact Dot Stepper (Mobile)

Used when viewport width < 768px. Omits labels, shows only dots.

```
   ●  ●  ○  ○  ○
```

States follow the same token mapping as the horizontal stepper, minus labels. Dot size increases from 8px to 10px for the active step. Dots are spaced at `--space-unit` x 3 (12px) apart.

---

## Step Content Area Composition

The step content area is the central panel that holds the current step's form fields, selections, or informational content.

### Structure

```
┌────────────────────────────────────────────────────┐
│                                                    │
│   Step Title                  [font: heading-lg]   │
│   Step description text       [font: body]         │
│                                                    │
│   ┌────────────────────────────────────────────┐   │
│   │                                            │   │
│   │   STEP-SPECIFIC CONTENT                    │   │
│   │                                            │   │
│   │   (form fields, card selectors,            │   │
│   │    file uploads, confirmation lists,       │   │
│   │    review summaries)                       │   │
│   │                                            │   │
│   └────────────────────────────────────────────┘   │
│                                                    │
│   [Inline validation message]                      │
│                                                    │
└────────────────────────────────────────────────────┘
```

### Token References

| Element | Token | Value |
| --- | --- | --- |
| Content surface | `--auth-surface` | `rgba(24, 24, 27, 0.9)` |
| Content border | `--auth-surface-border` | `rgba(63, 63, 70, 0.6)` |
| Content radius | `--auth-radius-shell` | `1.5rem` |
| Content padding | `--auth-shell-padding` | `2rem` |
| Max width (desktop) | `--auth-shell-max-width` | `28rem` (expandable to `36rem` for wizard) |
| Title font | `--font-display-metric` | Inter Bold, 24px |
| Description font | `--font-body-operational` | Inter Regular, 16px |
| Title color | `--auth-text-primary` | `#ffffff` |
| Description color | `--auth-text-secondary` | `#d4d4d8` |
| Input bg | `--auth-input-bg` | `rgba(39, 39, 42, 0.6)` |
| Input border | `--auth-input-border` | `#52525b` |
| Input radius | `--auth-radius-field` | `0.75rem` |
| Input padding x | `--auth-field-padding-x` | `1rem` |
| Input padding y | `--auth-field-padding-y` | `0.75rem` |
| Error text | `--auth-feedback-error-text` | `#fecaca` |
| Error bg | `--auth-feedback-error-bg` | `rgba(69, 10, 10, 0.3)` |
| Error border | `--auth-feedback-error-border` | `rgba(239, 68, 68, 0.6)` |
| Success text | `--auth-feedback-success-text` | `#dcfce7` |
| Success bg | `--auth-feedback-success-bg` | `rgba(5, 46, 22, 0.2)` |

### Wizard Max Width Override

The default auth shell max width (`28rem`) is extended for the wizard context:
- Desktop: `max-width: 40rem` (640px) for content area
- Tablet: `max-width: 36rem` (576px)
- Mobile: full width with `1rem` horizontal padding

---

## Navigation Controls Layout

### Desktop/Tablet Controls

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  [<- Back]                          [Continue ->]    │
│                                                      │
│                   Skip this step                     │
│                                                      │
└──────────────────────────────────────────────────────┘
```

- **Back**: Secondary button, left-aligned. Hidden on first step.
- **Continue**: Primary button, right-aligned. Uses `--auth-accent-primary` bg.
- **Skip**: Text link, centered below buttons. Only shown on optional steps.
- On final step, Continue label changes to "Complete Setup".

### Mobile Controls

```
┌────────────────────────────┐
│                            │
│  [     Continue ->     ]   │   <- Full-width primary
│                            │
│  [     <- Back         ]   │   <- Full-width secondary
│                            │
│       Skip this step       │   <- Centered text link
│                            │
└────────────────────────────┘
```

On mobile, buttons stack vertically. Continue is always first (top) for thumb reach. Back is second. Skip is a text link below both.

### Button Token References

| Element | Token |
| --- | --- |
| Continue bg | `--auth-accent-primary` (`#DC2626`) |
| Continue hover | `--auth-accent-primary-strong` (`#b91c1c`) |
| Continue text | `#ffffff` |
| Continue glow | `--auth-accent-glow` |
| Continue padding | `--auth-action-padding-y` (1rem) |
| Continue radius | `--auth-radius-field` (0.75rem) |
| Back bg | transparent |
| Back border | `--auth-surface-border` |
| Back text | `--auth-text-secondary` |
| Back hover text | `--auth-text-primary` |
| Skip text | `--auth-text-tertiary` |
| Skip hover text | `--auth-text-secondary` |
| Min tap target | 44px (mobile) |

---

## Completion Screen Layout

Shown after the final step is submitted successfully.

### Desktop/Tablet

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│  [NIL Optic Logo]                                                │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │                    ●────●────●────●────●                     ││
│  │                    (all steps complete)                       ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │                     [Checkmark Icon]                          ││
│  │                                                              ││
│  │               You're all set.                                ││
│  │                                                              ││
│  │       Your account is configured and ready to go.            ││
│  │       We'll take you to your dashboard now.                  ││
│  │                                                              ││
│  │              [Go to Dashboard ->]                             ││
│  │                                                              ││
│  │       ──────────────────────────────                         ││
│  │                                                              ││
│  │       Quick Links:                                           ││
│  │       [ ] Roster Builder                                     ││
│  │       [ ] Agent Directory                                    ││
│  │       [ ] Favorites                                          ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Mobile

```
┌──────────────────────────┐
│                          │
│  [Logo]                  │
│                          │
│    ●  ●  ●  ●  ●        │
│                          │
│  ┌──────────────────────┐│
│  │                      ││
│  │   [Checkmark Icon]   ││
│  │                      ││
│  │   You're all set.    ││
│  │                      ││
│  │   Your account is    ││
│  │   configured.        ││
│  │                      ││
│  │  [Go to Dashboard]   ││
│  │                      ││
│  │  Quick Links:        ││
│  │  [ ] Roster Builder  ││
│  │  [ ] Agent Directory ││
│  │  [ ] Favorites       ││
│  │                      ││
│  └──────────────────────┘│
│                          │
└──────────────────────────┘
```

### Completion Screen Tokens

| Element | Token |
| --- | --- |
| Checkmark icon color | `--color-positive-verified` |
| Checkmark icon size | 48px (desktop), 40px (mobile) |
| Heading | `--font-display-metric`, `--auth-text-primary` |
| Body text | `--font-body-operational`, `--auth-text-secondary` |
| Primary CTA | `--auth-accent-primary` bg, full-width on mobile |
| Quick links | `--ui-text-secondary`, hover `--auth-accent-primary` |
| Divider | `--auth-surface-border` |

---

## Animation Specs

### Step Transition

When navigating between steps, the content area animates:

**Forward (Next step):**
- Outgoing: slide left 24px + fade to 0 opacity over `--motion-duration-standard` (200ms)
- Incoming: slide in from right 24px + fade to 1 opacity over `--motion-duration-standard` (200ms)
- Easing: `ease-out` for outgoing, `ease-in-out` for incoming

**Backward (Previous step):**
- Outgoing: slide right 24px + fade to 0 opacity over `--motion-duration-standard` (200ms)
- Incoming: slide in from left 24px + fade to 1 opacity over `--motion-duration-standard` (200ms)
- Easing: `ease-out` for outgoing, `ease-in-out` for incoming

**Stepper update:**
- Dot fill transition: 300ms `ease-in-out`
- Line fill transition: 300ms `ease-in-out`, delayed 100ms after dot
- Active pulse ring: `ease-in-out` infinite pulse at 1.5s period

### Completion Entrance

- Checkmark icon: scale from 0 to 1 over 400ms with `ease-out` + bounce overshoot
- Heading: fade in + slide up 16px over 300ms, delayed 200ms
- Body text: fade in over 300ms, delayed 400ms
- CTA button: fade in + slide up 8px over 300ms, delayed 600ms
- Quick links: staggered fade in at 100ms intervals starting at 800ms

### Reduced Motion

All animations respect `prefers-reduced-motion: reduce`:
- Step transitions become instant opacity crossfade (0ms slide, 150ms fade)
- Completion entrance becomes instant (no stagger, no scale/slide)
- Active dot pulse is disabled
- Stepper line fill transition reduced to 150ms

---

## Responsive Breakpoints

| Breakpoint | Stepper Variant | Content Max Width | Nav Layout | Notes |
| --- | --- | --- | --- | --- |
| >= 1024px | Horizontal labeled | 40rem (640px) | Side-by-side Back/Continue | Full desktop wizard |
| 768px - 1023px | Horizontal labeled | 36rem (576px) | Side-by-side Back/Continue | Condensed labels |
| < 768px | Compact dots | 100% - 2rem padding | Stacked (Continue first) | Mobile-first stack |

### Breakpoint-Specific Adjustments

**Desktop (>= 1024px):**
- Wizard shell centered vertically and horizontally on viewport
- Background: `--auth-bg-base` with optional subtle grid pattern
- Backdrop blur on content card: `--auth-backdrop-blur`
- Shadow elevation: `--auth-shadow-elevation`

**Tablet (768px - 1023px):**
- Wizard shell centered horizontally, top-aligned with `3rem` top padding
- Step labels use abbreviated text when space is tight
- Form fields remain full width within content area

**Mobile (< 768px):**
- Wizard shell fills viewport width with `1rem` horizontal padding
- Content card loses border radius on sides (flush to edges)
- All form controls use minimum 44px tap targets
- Step counter text ("Step 2 of 5") replaces progress labels
- Navigation buttons are full-width stacked

---

## Accessibility Notes

### Keyboard Navigation

| Key | Action |
| --- | --- |
| `Tab` | Move focus to next interactive element within the step |
| `Shift + Tab` | Move focus to previous interactive element |
| `Enter` | Activate focused button or submit current step |
| `Escape` | No action (wizard has no modal to dismiss) |
| `Arrow Left/Right` | Navigate between stepper dots (informational, non-interactive) |

### Focus Management

- When a step transitions, focus moves to the step title (`h2`) of the new step
- After validation error, focus moves to the first invalid field
- On completion screen, focus moves to the heading
- Focus ring uses `--auth-accent-focus-ring` for all interactive elements
- Focus ring is visible only on keyboard navigation (`:focus-visible`)

### Screen Reader

- Progress stepper uses `role="progressbar"` with `aria-valuenow` (current step) and `aria-valuemax` (total steps)
- Each step has `aria-label` describing its name and position: "Step 2 of 5: Organization"
- Step content area uses `role="region"` with `aria-live="polite"` for content changes
- Validation errors use `role="alert"` for immediate announcement
- Navigation buttons use descriptive `aria-label`: "Go to previous step", "Continue to next step"
- Skip link uses `aria-label`: "Skip this optional step"
- Completion screen checkmark has `aria-hidden="true"` (decorative)
- Quick links section has `aria-label`: "Quick links to get started"

### Color Contrast

All text and interactive elements meet WCAG 2.1 AA minimum contrast ratios:
- Primary text on dark surface: `#ffffff` on `rgba(24, 24, 27, 0.9)` = 15.4:1
- Secondary text on dark surface: `#d4d4d8` on `rgba(24, 24, 27, 0.9)` = 10.2:1
- Muted text on dark surface: `#a1a1aa` on `rgba(24, 24, 27, 0.9)` = 5.8:1
- Red accent on dark surface: `#DC2626` on `rgba(24, 24, 27, 0.9)` = 4.6:1 (AA for large text)
- Error text: `#fecaca` on `rgba(69, 10, 10, 0.3)` = 7.1:1

### Touch Targets

- All buttons: minimum 44px height on all breakpoints
- Input fields: minimum 44px height (`--auth-field-padding-y` ensures this)
- Stepper dots on mobile: 44px tap target area (even though visual dot is 8-10px)
- Skip link: 44px tap target on mobile

---

## Token Summary

All tokens referenced in this template spec:

### Surface Tokens
- `--auth-bg-base`
- `--auth-surface`
- `--auth-surface-border`
- `--auth-input-bg`
- `--auth-input-border`

### Color Tokens
- `--auth-text-primary`
- `--auth-text-secondary`
- `--auth-text-tertiary`
- `--auth-accent-primary`
- `--auth-accent-primary-strong`
- `--auth-accent-focus-ring`
- `--auth-accent-glow`
- `--color-positive-verified`
- `--ui-text-primary`
- `--ui-text-secondary`
- `--ui-text-muted`
- `--ui-border-default`
- `--ui-border-strong`

### Spacing Tokens
- `--auth-shell-max-width`
- `--auth-shell-padding`
- `--auth-field-padding-x`
- `--auth-field-padding-y`
- `--auth-action-padding-y`
- `--space-unit`

### Radius Tokens
- `--auth-radius-shell`
- `--auth-radius-field`

### Motion Tokens
- `--motion-duration-standard`
- `--auth-transition-default`

### Effect Tokens
- `--auth-backdrop-blur`
- `--auth-shadow-elevation`
- `--auth-button-hover-glow`

### Feedback Tokens
- `--auth-feedback-error-bg`
- `--auth-feedback-error-border`
- `--auth-feedback-error-text`
- `--auth-feedback-success-bg`
- `--auth-feedback-success-border`
- `--auth-feedback-success-text`
