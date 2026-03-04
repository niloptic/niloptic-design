# Onboarding Wizard Template

Last updated: 2026-03-04

---

## Overview

The onboarding wizard is a reusable, role-agnostic container that renders step-based flows. It receives role-specific content as children and manages progress state, navigation, and transitions. The wizard itself has no knowledge of what questions are asked -- it only knows steps, validation gates, and completion state.

---

## Anatomy

### Full Desktop Layout

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│  [NIL Optic Logo]                              Step 2 of 5      │
│                                                                  │
│  ────────────────────────────────────────────────────────────── │
│                                                                  │
│  ○─────●─────○─────○─────○                                      │
│  Profile  Setup  Tour  Config  Done                              │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │                                                              ││
│  │                                                              ││
│  │                                                              ││
│  │              Step Content Area                               ││
│  │              (role-specific content renders here)            ││
│  │                                                              ││
│  │              Max-width: 640px                                ││
│  │              Min-height: 320px                               ││
│  │                                                              ││
│  │                                                              ││
│  │                                                              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  [<- Back]                          [Skip]    [Next Step ->]     │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Anatomy Breakdown

| Region              | Element                          | Behavior                                       |
|---------------------|----------------------------------|-------------------------------------------------|
| Header-left         | NIL Optic Logo                   | Static, links to marketing home                |
| Header-right        | Step counter                     | "Step X of Y" -- updates on navigation         |
| Divider             | Full-width hairline              | `--onb-wizard-border` token                    |
| Progress stepper    | Horizontal pill rail             | Shows all steps with state indicators          |
| Step labels         | Text beneath each step dot       | Visible on desktop, hidden on mobile           |
| Content area        | Scrollable region                | Role-specific content injected per step        |
| Footer-left         | Back button                      | Returns to previous step                       |
| Footer-center       | Skip button                      | Advances without saving (optional steps only)  |
| Footer-right        | Next / Complete button           | Validates and advances, or completes wizard    |

---

## Step Types

### Step Type: Profile Capture

Purpose: Collect or confirm identity information.

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  Complete Your Profile                           │
│  Let's make sure we have your details right.     │
│                                                  │
│  ┌──────────┐                                    │
│  │          │  [Upload Photo]                    │
│  │  Avatar  │  Drag or click to upload           │
│  │  120px   │  JPG, PNG up to 5MB                │
│  └──────────┘                                    │
│                                                  │
│  First Name    [Marcus_____________]  <- prefill │
│  Last Name     [Johnson_____________] <- prefill │
│  Title / Role  [Head Coach__________] <- prefill │
│  Bio           [________________________]        │
│                [________________________]        │
│                                                  │
│  Pre-filled from your invitation data.           │
│  Edit anything that needs correction.            │
│                                                  │
└──────────────────────────────────────────────────┘
```

| Property         | Value                                             |
|------------------|---------------------------------------------------|
| Required fields  | First name, last name                             |
| Optional fields  | Avatar, bio, title                                |
| Prefill source   | Invite metadata, auth profile                     |
| Validation       | Non-empty required fields, image size/type check  |

### Step Type: Organization Association

Purpose: Confirm or create organizational membership.

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  Confirm Your Organization                       │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  University of Kentucky              [x]     ││
│  │  Athletic Organization                       ││
│  │  Men's Basketball Program                    ││
│  │  Invited by: Mitch Barnhart, AD              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  Is this correct?                                │
│                                                  │
│  (o) Yes, this is my organization                │
│  ( ) No, I need to contact my admin              │
│                                                  │
└──────────────────────────────────────────────────┘
```

**Operator variant (no invite):**

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  Create Your Organization                        │
│                                                  │
│  Organization Name  [________________________]   │
│                                                  │
│  Category                                        │
│  ┌──────────────┐ ┌──────────────┐ ┌───────────┐│
│  │  Athletic    │ │  Agency      │ │ Affiliate ││
│  │  [selected]  │ │              │ │           ││
│  └──────────────┘ └──────────────┘ └───────────┘│
│                                                  │
│  Primary Sport  [Basketball       ▼]             │
│  Conference     [SEC              ▼]             │
│                                                  │
└──────────────────────────────────────────────────┘
```

| Property          | Invite flow                        | Operator flow                      |
|-------------------|------------------------------------|------------------------------------|
| Org data          | Pre-filled from invite             | User enters manually               |
| Program data      | Pre-filled from invite             | Created in next step               |
| Validation        | Confirmation radio selection       | Non-empty org name + category      |
| Error state       | "Contact your admin" escape hatch  | Duplicate org name check           |

### Step Type: Feature Tour

Purpose: Guided walkthrough of key screens for the user's role.

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ││
│  │ ░░░░░░░░░░  SPOTLIGHT OVERLAY  ░░░░░░░░░░░░ ││
│  │ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ││
│  │ ░░░░░░┌─────────────────────┐░░░░░░░░░░░░░░ ││
│  │ ░░░░░░│                     │░░░░░░░░░░░░░░ ││
│  │ ░░░░░░│  Highlighted Area   │░░░░░░░░░░░░░░ ││
│  │ ░░░░░░│  (pulsing red ring) │░░░░░░░░░░░░░░ ││
│  │ ░░░░░░│                     │░░░░░░░░░░░░░░ ││
│  │ ░░░░░░└─────────────────────┘░░░░░░░░░░░░░░ ││
│  │ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  KPI Cards                         1 of 4   ││
│  │  These cards show your program's key         ││
│  │  metrics at a glance: total NIL value,       ││
│  │  active deals, roster size, and compliance.  ││
│  │                                              ││
│  │  [Try It]                    [Next ->]       ││
│  └──────────────────────────────────────────────┘│
│                                                  │
└──────────────────────────────────────────────────┘
```

| Property             | Value                                             |
|----------------------|---------------------------------------------------|
| Overlay              | `--onb-spotlight-overlay` with cutout              |
| Target ring          | `--onb-spotlight-ring`, 2px pulsing border         |
| Tooltip position     | Below target (preferred), above if overflow        |
| "Try It" action      | Removes overlay, enables interaction with target   |
| Tour step count      | 3-5 highlights per role                            |
| Skip entire tour     | Allowed via wizard Skip button                     |

### Step Type: Data Configuration

Purpose: Role-specific setup that configures the user's workspace.

```
AD/Coach Budget Configuration:
┌──────────────────────────────────────────────────┐
│                                                  │
│  Set Your NIL Budget                             │
│  Configure allocation for Men's Basketball.      │
│                                                  │
│  Total Program Budget                            │
│  $ [2,500,000_________]                          │
│                                                  │
│  Est. Team Valuation: $3,200,000                 │
│  Budget vs. Estimate: -$700,000                  │
│                                                  │
│  ────────────────────────────────────────────── │
│                                                  │
│  Per-Player Allocation (optional now)            │
│                                                  │
│  #   Player          Est. Value   Allocated      │
│  1   D. Wagner       $420,000     [__________]   │
│  3   R. Harper       $380,000     [__________]   │
│  5   T. Mitchell     $310,000     [__________]   │
│  11  A. Reeves       $290,000     [__________]   │
│                                                  │
│  You can adjust allocations later in Settings.   │
│                                                  │
└──────────────────────────────────────────────────┘

Agent Pipeline Configuration:
┌──────────────────────────────────────────────────┐
│                                                  │
│  Set Up Your Pipeline                            │
│  Customize your deal workflow stages.            │
│                                                  │
│  Default Stages:                                 │
│  [1] Prospect     [drag handle]                  │
│  [2] Outreach     [drag handle]                  │
│  [3] Negotiate    [drag handle]                  │
│  [4] Signed       [drag handle]                  │
│                                                  │
│  [+ Add Stage]                                   │
│                                                  │
│  ────────────────────────────────────────────── │
│                                                  │
│  Add Your First Prospect                         │
│  Search [________________________] [Search]      │
│                                                  │
│  Suggested (Basketball):                         │
│  D. Wagner, Kentucky, PG, Est. $420K             │
│  R. Harper, Rutgers, SF, Est. $380K              │
│                                                  │
└──────────────────────────────────────────────────┘

Athlete Social Media Linking:
┌──────────────────────────────────────────────────┐
│                                                  │
│  Connect Your Social Media                       │
│  This directly impacts your NIL valuation.       │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  Instagram      [Connect]     <- OAuth       ││
│  │  Twitter / X    [Connect]     <- OAuth       ││
│  │  TikTok         [Connect]     <- OAuth       ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  Connected accounts:                             │
│  ┌──────────────────────────────────────────────┐│
│  │  [IG icon] @dub_wagner  142K followers  [x]  ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  Estimated Social Reach: 142,000                 │
│  Valuation Impact: +$18,000 est.                 │
│                                                  │
│  You can connect more accounts later in Profile. │
│                                                  │
└──────────────────────────────────────────────────┘
```

### Step Type: First Action Prompt

Purpose: Drive the user to complete their single most important action.

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  You're All Set!                                 │
│                                                  │
│  One last thing -- complete your first action    │
│  to unlock the full power of NIL Optic.          │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  [Icon: Checkmark Shield]                    ││
│  │                                              ││
│  │  Run Your First Compliance Check             ││  <- AD
│  │  See how your program stacks up against      ││
│  │  NCAA NIL guidelines in real time.           ││
│  │                                              ││
│  │  [Run Compliance Check ->]     <- Red CTA    ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  Or skip and explore your dashboard              │
│                                                  │
└──────────────────────────────────────────────────┘
```

**First action by role:**

| Role                | First Action Prompt                        | CTA Label                       |
|---------------------|--------------------------------------------|---------------------------------|
| Athletic Director   | Run compliance check                       | "Run Compliance Check"          |
| Agent               | Add first client to pipeline               | "Add Your First Client"         |
| Athlete             | View personal NIL valuation                | "See My Valuation"              |
| Coach               | Review team roster with valuations         | "View My Roster"                |
| Fan                 | Build a roster in Roster Builder           | "Start Building"                |
| Affiliate           | Preview directory listing                  | "Preview My Listing"            |

---

## Progress Stepper

### Stepper Anatomy

```
Desktop / Tablet:
○─────────●─────────●─────────○─────────○
Profile    Setup     Tour      Config    Done
                     ^
                     Active (pulsing)

Mobile (compact dots):
○  ●  ●  ○  ○           Step 3 of 5
```

### Stepper States

| State      | Visual                                    | Token                     |
|------------|-------------------------------------------|---------------------------|
| Completed  | Filled red circle with check              | `--onb-step-complete`     |
| Active     | Filled white circle, pulsing ring         | `--onb-step-active`       |
| Upcoming   | Outlined circle                           | `--onb-step-upcoming`     |
| Skipped    | Dashed outline circle                     | `--onb-step-skipped`      |

### Stepper Specifications

| Property               | Value                                          |
|------------------------|------------------------------------------------|
| Circle diameter        | 32px (desktop), 12px (mobile compact)          |
| Track height           | 2px                                            |
| Track color            | `--onb-progress-track`                         |
| Fill color             | `--onb-progress-fill`                          |
| Active pulse           | `--onb-step-active` with 1.5s ease-in-out loop |
| Label font             | Inter 12px/600, `--ui-text-muted`              |
| Step counter font      | JetBrains Mono 14px/500, `--ui-text-secondary` |
| Transition             | Fill animation 300ms ease-out on completion    |

---

## Navigation Controls

### Button Specifications

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  [<- Back]              [Skip]    [Next Step ->] │
│                                                  │
└──────────────────────────────────────────────────┘
```

| Control       | Type           | Condition                           | Behavior                                |
|---------------|----------------|-------------------------------------|-----------------------------------------|
| Back          | Ghost button   | Disabled on step 1                  | Returns to previous step, no data loss  |
| Skip          | Text link      | Only visible for optional steps     | Marks step as skipped, advances         |
| Next Step     | Primary button | Validates current step first        | Saves data, advances to next step       |
| Complete      | Primary button | Replaces Next on final step         | Saves, marks complete, routes to shell  |

### Button Token Mapping

| Element             | Token                                     |
|---------------------|-------------------------------------------|
| Back text           | `--ui-text-secondary`                     |
| Back hover          | `--ui-text-primary`                       |
| Skip text           | `--ui-text-muted`                         |
| Skip hover          | `--ui-text-secondary`                     |
| Next/Complete bg    | `--onb-cta-bg` (`#dc2626`)               |
| Next/Complete hover | `--onb-cta-hover` (`#b91c1c`)            |
| Next/Complete text  | `#ffffff`                                 |
| Disabled state      | 50% opacity, cursor-not-allowed           |

---

## Responsive Behavior

### Desktop (>1024px)

```
┌──────────────────────────────────────────────────────────────────┐
│  [Logo]                                          Step 2 of 5    │
│  ────────────────────────────────────────────────────────────── │
│  ○─────●─────○─────○─────○                                      │
│  Profile  Setup  Tour  Config  Done                              │
│                                                                  │
│              ┌──────────────────────────────┐                    │
│              │                              │                    │
│              │     Step Content             │  <- max-w: 640px   │
│              │     Centered horizontally    │                    │
│              │                              │                    │
│              └──────────────────────────────┘                    │
│                                                                  │
│  [<- Back]                          [Skip]    [Next Step ->]     │
└──────────────────────────────────────────────────────────────────┘
```

| Property           | Value                               |
|--------------------|-------------------------------------|
| Wizard card        | Centered, max-width 640px           |
| Content padding    | 48px horizontal, 32px vertical      |
| Stepper            | Horizontal with labels              |
| Background         | Subtle dark overlay on dashboard    |

### Tablet (768-1024px)

```
┌──────────────────────────────────────────────┐
│  [Logo]                        Step 2 of 5   │
│  ──────────────────────────────────────────  │
│  ○─────●─────○─────○─────○                   │
│  Profile  Setup  Tour  Config  Done          │
│                                              │
│  ┌──────────────────────────────────────────┐│
│  │                                          ││
│  │  Step Content                            ││
│  │  Full-width with 24px padding            ││
│  │                                          ││
│  └──────────────────────────────────────────┘│
│                                              │
│  [<- Back]            [Skip]  [Next Step ->] │
└──────────────────────────────────────────────┘
```

| Property           | Value                               |
|--------------------|-------------------------------------|
| Wizard card        | Full-width with 24px padding        |
| Stepper            | Horizontal with labels              |
| Nav controls       | Tighter spacing                     |

### Mobile (<768px)

```
┌────────────────────────────┐
│  [Logo]       Step 2 of 5  │
│  ────────────────────────  │
│  ○  ●  ○  ○  ○             │
│                            │
│  ┌────────────────────────┐│
│  │                        ││
│  │  Step Content          ││
│  │  Full bleed            ││
│  │  Edge-to-edge          ││
│  │  16px padding          ││
│  │                        ││
│  │                        ││
│  │                        ││
│  │                        ││
│  │                        ││
│  └────────────────────────┘│
│                            │
│ ┌────────────────────────┐ │
│ │[<- Back] [Skip] [Next]│ │  <- Bottom-anchored
│ └────────────────────────┘ │
└────────────────────────────┘
```

| Property                | Value                               |
|-------------------------|-------------------------------------|
| Wizard                  | Full-screen, edge-to-edge           |
| Content padding         | 16px horizontal                     |
| Stepper                 | Compact dots only (no labels)       |
| Nav controls            | Bottom-anchored, sticky             |
| Min touch target        | 44px height for all controls        |

---

## Animation and Motion

### Step Transitions

| Transition         | Direction   | Animation                        | Duration  | Easing       |
|--------------------|-------------|----------------------------------|-----------|--------------|
| Forward (Next)     | Left        | Content slides left, new enters  | 300ms     | ease-out     |
| Backward (Back)    | Right       | Content slides right, new enters | 300ms     | ease-out     |
| Skip               | Left        | Same as forward                  | 300ms     | ease-out     |

### Progress Stepper Animation

| Event                  | Animation                                     | Duration  |
|------------------------|-----------------------------------------------|-----------|
| Step completed         | Circle fills red, check fades in              | 200ms     |
| Track fill             | Progress bar extends to next step             | 300ms     |
| Active pulse           | White circle with expanding/contracting ring  | 1500ms    |
| Step skipped           | Circle outline becomes dashed                 | 150ms     |

### Reduced Motion

When `prefers-reduced-motion: reduce` is active:
- Step transitions: instant swap (no slide)
- Progress stepper: instant state change (no fill animation)
- Active pulse: static indicator (no animation)
- Spotlight overlay: instant appear/disappear

---

## Design Tokens Reference

### Wizard Surface Tokens

| Token                      | Dark Value                      | Light Value                     |
|----------------------------|---------------------------------|---------------------------------|
| `--onb-wizard-bg`          | `#09090b`                       | `#ffffff`                       |
| `--onb-wizard-border`      | `#27272a`                       | `#d4d4d8`                       |
| `--onb-wizard-shadow`      | `0 25px 50px rgba(0,0,0,0.5)`  | `0 25px 50px rgba(0,0,0,0.1)`  |
| `--onb-wizard-radius`      | `1.5rem`                        | `1.5rem`                        |
| `--onb-wizard-max-width`   | `640px`                         | `640px`                         |

### Step Content Tokens

| Token                      | Dark Value                      | Light Value                     |
|----------------------------|---------------------------------|---------------------------------|
| `--onb-content-bg`         | `#18181b`                       | `#f9fafb`                       |
| `--onb-content-border`     | `#27272a`                       | `#e5e7eb`                       |
| `--onb-content-radius`     | `0.75rem`                       | `0.75rem`                       |
| `--onb-content-padding`    | `1.5rem`                        | `1.5rem`                        |

### Stepper Tokens

| Token                      | Dark Value                      | Light Value                     |
|----------------------------|---------------------------------|---------------------------------|
| `--onb-step-complete`      | `#dc2626`                       | `#dc2626`                       |
| `--onb-step-active`        | `#ffffff`                       | `#111827`                       |
| `--onb-step-upcoming`      | `#3f3f46`                       | `#d4d4d8`                       |
| `--onb-step-skipped`       | `#52525b`                       | `#9ca3af`                       |
| `--onb-progress-track`     | `#27272a`                       | `#e5e7eb`                       |
| `--onb-progress-fill`      | `#dc2626`                       | `#dc2626`                       |
| `--onb-step-size`          | `32px`                          | `32px`                          |
| `--onb-step-size-mobile`   | `12px`                          | `12px`                          |

### Interactive Tokens

| Token                      | Dark Value                      | Light Value                     |
|----------------------------|---------------------------------|---------------------------------|
| `--onb-cta-bg`             | `#dc2626`                       | `#dc2626`                       |
| `--onb-cta-hover`          | `#b91c1c`                       | `#b91c1c`                       |
| `--onb-cta-text`           | `#ffffff`                       | `#ffffff`                       |
| `--onb-cta-radius`         | `0.75rem`                       | `0.75rem`                       |
| `--onb-cta-height`         | `48px`                          | `48px`                          |
| `--onb-ghost-text`         | `--ui-text-secondary`           | `--ui-text-secondary`           |
| `--onb-ghost-hover`        | `--ui-text-primary`             | `--ui-text-primary`             |

### Spotlight Tokens (Feature Tour)

| Token                      | Dark Value                      | Light Value                     |
|----------------------------|---------------------------------|---------------------------------|
| `--onb-spotlight-overlay`  | `rgba(0, 0, 0, 0.75)`          | `rgba(0, 0, 0, 0.5)`           |
| `--onb-spotlight-ring`     | `rgba(220, 38, 38, 0.6)`       | `rgba(220, 38, 38, 0.4)`       |
| `--onb-spotlight-tooltip`  | `#18181b`                       | `#ffffff`                       |
| `--onb-spotlight-tooltip-border` | `#3f3f46`                | `#d4d4d8`                       |
| `--onb-spotlight-tooltip-shadow` | `0 10px 25px rgba(0,0,0,0.4)` | `0 10px 25px rgba(0,0,0,0.1)` |

---

## Validation Behavior

### Field-Level Validation

```
Valid state:
┌──────────────────────────────┐
│  First Name                  │
│  [Marcus Johnson_________]   │  <- default border
└──────────────────────────────┘

Error state:
┌──────────────────────────────┐
│  First Name                  │
│  [____________________]      │  <- red border (#dc2626)
│  First name is required      │  <- red-200 text, 12px
└──────────────────────────────┘
```

| Validation Trigger     | Behavior                                    |
|------------------------|---------------------------------------------|
| On Next click          | Validate all required fields in current step |
| On field blur          | Validate individual field after first submit |
| Real-time (optional)   | Character count, format hints               |
| Skip available         | No validation on optional steps             |

### Step-Level Validation

| Condition              | Next Button State    | User Feedback                    |
|------------------------|----------------------|----------------------------------|
| All required valid     | Enabled (red)        | None                             |
| Any required invalid   | Enabled (red)        | Scroll to first error on click   |
| API save in progress   | Loading spinner      | "Saving..." indicator            |
| API save failed        | Enabled (red)        | Toast: "Could not save. Retry?"  |

---

## Keyboard Shortcuts

| Key              | Action                          | Condition                  |
|------------------|---------------------------------|----------------------------|
| `Enter`          | Submit current step (Next)      | Focus in form              |
| `Escape`         | No action (prevents accidental) | Always                     |
| `Tab`            | Move to next form field         | Standard browser behavior  |
| `Shift+Tab`      | Move to previous form field     | Standard browser behavior  |
| Arrow keys       | Navigate within selects/radios  | Focus on control group     |

---

## ARIA and Accessibility

```html
<!-- Wizard container -->
<div role="region" aria-label="Onboarding wizard">

  <!-- Progress stepper -->
  <nav role="navigation" aria-label="Onboarding progress">
    <ol role="list">
      <li aria-current="step" aria-label="Step 2 of 5: Setup">
      ...
    </ol>
  </nav>

  <!-- Step content -->
  <main role="main" aria-live="polite" aria-label="Step 2: Setup">
    <!-- Role-specific content -->
  </main>

  <!-- Navigation controls -->
  <footer role="navigation" aria-label="Step navigation">
    <button aria-label="Go back to previous step">Back</button>
    <button aria-label="Skip this step">Skip</button>
    <button aria-label="Continue to next step">Next Step</button>
  </footer>

</div>
```

| ARIA Pattern           | Implementation                                    |
|------------------------|---------------------------------------------------|
| Live region            | Step content area announces changes               |
| Current step           | `aria-current="step"` on active stepper item      |
| Step completion         | `aria-label` includes "completed" for done steps  |
| Error announcement     | Field errors announced via `aria-describedby`     |
| Focus management       | Focus moves to step heading on transition         |
