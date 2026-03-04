# Onboarding Design System

Last updated: 2026-03-04

---

## Design Philosophy

Onboarding is the first impression of NIL Optic. Every decision is measured against one question: how fast can we get a user to their first moment of value? The system is built on four pillars:

### Time-to-First-Value
- Get every user to their "aha moment" in under 5 minutes (athlete) to 15 minutes (AD)
- Minimize form fields; prefill everything derivable from invite metadata
- Basketball-first examples and sample data throughout every flow

### Progressive Disclosure
- Show only what is needed at each step
- Never overwhelm with features before the user has context
- Defer advanced configuration to post-onboarding settings surfaces

### Role-Derived Context
- Role comes from invite metadata or org signup intent, NEVER from manual self-selection
- `/dashboard/onboarding` must NOT include role-selection prompts
- Role context is derived from authenticated role/profile state
- Onboarding content adapts based on detected role without user intervention

### Basketball-First Content
- Basketball is always the first sport in selection lists
- Sample data uses basketball players, teams, and conferences
- Wireframe examples reference basketball positions, stats, and terminology

---

## Entry Points

NIL Optic has three distinct entry paths into the platform. Each maps to a different onboarding depth and feature scope.

### Public Signup  ->  Fan Preview

```
Route: /signup (no invite, no operator intent)

┌──────────────────────────────────────────────────┐
│                                                  │
│  [NIL Optic Logo]                                │
│                                                  │
│  Create Your Free Account                        │
│                                                  │
│  Email     [_________________________]           │
│  Password  [_________________________]           │
│                                                  │
│  [Create Free Account]              ← Red CTA    │
│                                                  │
│  Already have an account? Sign In                │
│                                                  │
│  ────────────────────────────────────────────── │
│  Free includes: Roster Builder, Favorites,       │
│  Tournament Intelligence (preview depth)         │
│                                                  │
└──────────────────────────────────────────────────┘
```

| Property              | Value                                            |
|-----------------------|--------------------------------------------------|
| Route                 | `/signup`                                        |
| Default destination   | `/fan`                                           |
| Org/program context   | None -- preview-only NIL access                  |
| Feature access        | Roster Builder, Favorites, Tournaments           |
| Valuation depth       | Fan-lite top-3 valuation window                  |
| Messaging/Huddles     | Hidden from navigation                           |
| Keyboard shortcuts    | Disabled                                         |
| Upgrade CTA           | Embedded throughout fan surfaces                 |

**Post-signup flow:**
1. Account created with `fan` role
2. Redirect to `/fan` shell
3. Lightweight 3-step interest selection (see flows-by-persona.md)
4. No org/program association required

### Invite Acceptance  ->  Role-Scoped Onboarding

```
Route: /invite/accept?token=<invite_token>

┌──────────────────────────────────────────────────┐
│                                                  │
│  [NIL Optic Logo]                                │
│                                                  │
│  You've Been Invited                             │
│                                                  │
│  University of Kentucky                          │
│  Men's Basketball Program                        │
│  Role: Head Coach                                │
│                                                  │
│  ────────────────────────────────────────────── │
│                                                  │
│  [Accept Invitation]                ← Red CTA    │
│                                                  │
│  Invited by: John Calipari, Athletic Director    │
│  Expires: March 11, 2026                         │
│                                                  │
└──────────────────────────────────────────────────┘
```

| Property              | Value                                            |
|-----------------------|--------------------------------------------------|
| Route                 | `/invite/accept`                                 |
| Invite carries        | `org_id`, `program_id`, `role`, `inviter_id`     |
| Token validation      | `pending` + unexpired + email-match              |
| Post-acceptance       | `/dashboard/onboarding` (if steps remain)        |
| Final destination     | Role-specific shell (`/athletic-director`, `/agent`, `/athlete`, `/coach`, etc.) |

**Post-acceptance flow:**
1. Token validated (status, expiry, email match)
2. Scoped memberships and roles created
3. If onboarding required -> redirect to `/dashboard/onboarding`
4. Wizard renders role-appropriate steps (from invite metadata)
5. On completion -> redirect to role shell

### Operator Signup  ->  Paid Plan Onboarding

```
Route: /signup (with operator intent parameter)

┌──────────────────────────────────────────────────┐
│                                                  │
│  [NIL Optic Logo]                                │
│                                                  │
│  Start Your Organization                         │
│                                                  │
│  Organization Name  [_________________________]  │
│  Category           [Athletic        ▼]          │
│                     (Athletic / Agency / Affiliate)│
│                                                  │
│  Your Name    [_________________________]        │
│  Email        [_________________________]        │
│  Password     [_________________________]        │
│                                                  │
│  Plan         [Professional ▼]                   │
│               (Starter / Professional / Enterprise)│
│                                                  │
│  [Create Organization]              ← Red CTA    │
│                                                  │
│  Already have an account? Sign In                │
│                                                  │
└──────────────────────────────────────────────────┘
```

| Property              | Value                                            |
|-----------------------|--------------------------------------------------|
| Route                 | `/signup?intent=operator`                        |
| Maps to               | Paid-plan onboarding flow                        |
| Creates               | Organization entity + initial program             |
| Org categories        | `athletic`, `agency`, `affiliate`                |
| Post-creation         | `/dashboard/onboarding`                          |
| Final destination     | Org-admin role shell                             |

**Post-signup flow:**
1. Organization entity created with selected category
2. Creator assigned org-admin role (`athletic_director`, `agency_admin`, or `affiliate_admin`)
3. Redirect to `/dashboard/onboarding` with full org-setup wizard
4. Includes program creation, staff invites, budget setup

---

## Onboarding Governance

Onboarding is split into two strict boundary surfaces: admin management and user-facing capture.

### Admin-Managed: /admin/onboarding

```
┌──────────────────────────────────────────────────┐
│  ADMIN > Onboarding Management                   │
│  ────────────────────────────────────────────── │
│                                                  │
│  [+ Add Question]   [Reorder]   [Preview]        │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │ #  Question              Type    Role    Req ││
│  ├──────────────────────────────────────────────┤│
│  │ 1  Organization confirm  select  ALL     Yes ││
│  │ 2  Sport selection       multi   AD      Yes ││
│  │ 3  Budget setup          input   AD      Yes ││
│  │ 4  Social media link     oauth   ATH     No  ││
│  │ 5  Agent association     search  ATH     No  ││
│  │ 6  Service categories    multi   AFF     Yes ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  Flow Rules:                                     │
│  • Questions filtered by user role at runtime    │
│  • Required questions block step advancement     │
│  • Optional questions show Skip control          │
│                                                  │
└──────────────────────────────────────────────────┘
```

| Constraint                                              | Enforcement                                  |
|---------------------------------------------------------|----------------------------------------------|
| Admin-internal only                                     | Route gated by `admin` auth scope            |
| Non-admin users must NOT see this in navigation         | Hidden from all non-admin left-nav configs   |
| Controls which questions appear in user-facing onboarding | Admin edits propagate to `/dashboard/onboarding` at runtime |

### User-Facing: /dashboard/onboarding

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 2 of 5   │
│  ──────────────────────────────────────────────  │
│  ○───●───○───○───○                               │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Role-specific onboarding content            ││
│  │  (rendered from admin-configured questions)  ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Skip]    [Next Step ->] │
│                                                  │
└──────────────────────────────────────────────────┘
```

| Constraint                                              | Enforcement                                  |
|---------------------------------------------------------|----------------------------------------------|
| NO role-selection prompts                               | Role derived from authenticated state        |
| Must not auto-launch without org/program context        | Guard checks for org/program membership      |
| Adapts content based on detected role                   | Question set filtered by role at render time  |
| Profile completion capture                              | Pre-fills known data from invite/signup       |

### Auto-Launch Guard Logic

Onboarding must NOT auto-launch if no org/program context exists. The system must check:

```
IF user.orgMemberships.length === 0 AND user.role === 'fan'
  -> Route to /fan (no onboarding)

IF user.orgMemberships.length === 0 AND user.role === 'member'
  -> Route to /dashboard (no onboarding, show empty state)

IF user.orgMemberships.length > 0 AND user.onboardingStatus !== 'complete'
  -> Route to /dashboard/onboarding (launch wizard)

IF user.orgMemberships.length > 0 AND user.onboardingStatus === 'complete'
  -> Route to role shell (skip onboarding)
```

---

## Success Metrics

### Activation Rate Targets by Persona

| Persona            | First Value Moment                        | Time Target | Activation Rate Target |
|--------------------|-------------------------------------------|-------------|------------------------|
| Athletic Director  | First compliance check completed          | < 24 hours  | 70% within 48h        |
| Agent              | First client added to pipeline            | < 1 hour    | 80% within 24h        |
| Athlete            | View personal NIL valuation               | < 5 minutes | 90% within 1h         |
| Coach              | Review team roster with valuations        | < 30 minutes| 75% within 24h        |
| Fan                | Browse 3+ athletes in Roster Builder      | < 10 minutes| 85% within 1h         |
| Affiliate          | Appear in affiliate directory             | < 5 minutes | 80% within 24h        |

### Onboarding Funnel Metrics

| Metric                        | Target          | Measurement                            |
|-------------------------------|-----------------|----------------------------------------|
| Wizard start rate             | > 95%           | Users who begin step 1 / users routed  |
| Wizard completion rate        | > 80%           | Users who finish all steps / started    |
| Step abandonment rate         | < 5% per step   | Users who leave at each step           |
| Average completion time (AD)  | < 15 minutes    | Timer from step 1 to completion        |
| Average completion time (ATH) | < 5 minutes     | Timer from step 1 to completion        |
| Skip rate (optional steps)    | < 30%           | Skips / total optional step views      |
| Return-to-complete rate       | > 60%           | Users who return to finish / abandoned |

### Basketball-First Content Benchmarks

| Content Surface               | Basketball Priority                        |
|-------------------------------|--------------------------------------------|
| Sport selection lists         | Basketball appears first, pre-checked      |
| Sample data in tours          | Uses basketball players and stats          |
| Budget allocation examples    | Basketball gets primary allocation slot     |
| Pipeline demo content         | Basketball recruit prospects               |
| Valuation preview             | Basketball athlete valuation shown first    |

---

## Onboarding Completion States

| State           | Definition                                            | Visual Indicator          | Behavior                                  |
|-----------------|-------------------------------------------------------|---------------------------|-------------------------------------------|
| `complete`      | All required steps finished                           | Green check badge         | Route directly to role shell              |
| `in_progress`   | User started but has not finished all required steps  | Amber progress ring       | Resume from last incomplete step          |
| `skipped`       | User skipped one or more optional steps               | Dashed outline badge      | Route to role shell, show reminder banner |
| `not_started`   | Onboarding available but not yet begun                | Empty circle              | Route to `/dashboard/onboarding` step 1   |

### State Persistence

```
┌──────────────────────────────────────────────────┐
│  onboarding_progress                             │
│  ─────────────────────────────────────────────── │
│                                                  │
│  user_id:          uuid                          │
│  status:           complete | in_progress |      │
│                    skipped | not_started         │
│  current_step:     integer (1-based)             │
│  completed_steps:  integer[]                     │
│  skipped_steps:    integer[]                     │
│  started_at:       timestamp                     │
│  completed_at:     timestamp | null              │
│  role_context:     string (role key)             │
│  org_id:           uuid                          │
│  program_id:       uuid | null                   │
│                                                  │
└──────────────────────────────────────────────────┘
```

### Resume Behavior

When a user returns with `in_progress` status:

```
┌──────────────────────────────────────────────────┐
│                                                  │
│  [NIL Optic Logo]                                │
│                                                  │
│  Welcome Back, Coach Williams                    │
│                                                  │
│  You have 2 steps remaining to complete          │
│  your setup for UK Men's Basketball.             │
│                                                  │
│  ○───●───●───○───○                               │
│  Done Done  Here  Left  Left                     │
│                                                  │
│  [Continue Setup]                   ← Red CTA    │
│  [Skip for Now]                     ← Ghost link │
│                                                  │
└──────────────────────────────────────────────────┘
```

---

## Role-to-Shell Routing Matrix

After onboarding completion, users route to their designated shell:

| Role                         | Post-Onboarding Shell           | Navigation Emphasis                          |
|------------------------------|---------------------------------|----------------------------------------------|
| `athletic_director`          | `/athletic-director`            | NIL-value-first executive dashboard          |
| `assistant_athletic_director`| `/assistant-athletic-director`  | Operations/event nav                         |
| `general_manager`            | `/general-manager`              | Roster/valuation/contract nav                |
| `coach`                      | `/coach`                        | Team roster, athlete performance, messaging  |
| `athlete`                    | `/athlete`                      | Profile, valuation, communication            |
| `agent`                      | `/agent`                        | Client/valuation/deal pipeline               |
| `agency_admin`               | `/agency-admin`                 | Office/agent/compliance nav                  |
| `affiliate_admin`            | `/affiliate-admin`              | Office/account/service nav                   |
| `affiliate`                  | `/affiliate`                    | Account/advisory/activity nav                |
| `fan`                        | `/fan`                          | Roster Builder, Favorites, Tournaments       |

---

## Invite Metadata Schema

Every invite carries the context needed for role-scoped onboarding:

```
┌──────────────────────────────────────────────────┐
│  invite_payload                                  │
│  ─────────────────────────────────────────────── │
│                                                  │
│  token:            string (unique)               │
│  email:            string                        │
│  organization_id:  uuid                          │
│  program_id:       uuid | null                   │
│  role:             string (role key)             │
│  inviter_id:       uuid                          │
│  status:           pending | accepted | expired  │
│                    | revoked                     │
│  created_at:       timestamp                     │
│  expires_at:       timestamp                     │
│                                                  │
│  Prefill mapping:                                │
│  ─────────────────────────────────────────────── │
│  org_name       -> Welcome message, org confirm  │
│  program_name   -> Program selection pre-check   │
│  role           -> Step set filtering            │
│  inviter_name   -> "Invited by" attribution      │
│                                                  │
└──────────────────────────────────────────────────┘
```

---

## Design Token Dependencies

Onboarding surfaces consume these token families:

| Token Family   | Usage in Onboarding                                   |
|----------------|-------------------------------------------------------|
| `--auth-*`     | Signup and invite acceptance screens                  |
| `--ui-*`       | Wizard card surfaces, controls, form fields           |
| `--onb-*`      | Onboarding-specific tokens (stepper, progress, steps) |
| `--dash-nav-*` | Shell chrome visible behind wizard overlay            |

### Onboarding-Specific Tokens

| Token                          | Dark Mode Value                    | Light Mode Value                   | Usage                        |
|--------------------------------|------------------------------------|------------------------------------|------------------------------|
| `--onb-wizard-bg`              | `#09090b` (zinc-950)               | `#ffffff`                          | Wizard card background       |
| `--onb-wizard-border`          | `#27272a` (zinc-800)               | `#d4d4d8` (zinc-300)              | Wizard card border           |
| `--onb-step-complete`          | `#dc2626` (red-600)                | `#dc2626` (red-600)               | Completed step fill          |
| `--onb-step-active`            | `#ffffff`                          | `#111827`                          | Active step indicator        |
| `--onb-step-upcoming`          | `#3f3f46` (zinc-700)               | `#d4d4d8` (zinc-300)              | Upcoming step outline        |
| `--onb-step-skipped`           | `#52525b` (zinc-600)               | `#9ca3af` (gray-400)              | Skipped step dashed          |
| `--onb-progress-track`         | `#27272a` (zinc-800)               | `#e5e7eb` (gray-200)              | Stepper track rail           |
| `--onb-progress-fill`          | `#dc2626` (red-600)                | `#dc2626` (red-600)               | Stepper progress fill        |
| `--onb-content-bg`             | `#18181b` (zinc-900)               | `#f9fafb` (gray-50)               | Step content area background |
| `--onb-cta-bg`                 | `#dc2626` (red-600)                | `#dc2626` (red-600)               | Primary action button        |
| `--onb-cta-hover`              | `#b91c1c` (red-700)                | `#b91c1c` (red-700)               | Primary action hover         |
| `--onb-spotlight-overlay`      | `rgba(0, 0, 0, 0.75)`             | `rgba(0, 0, 0, 0.5)`              | Feature tour spotlight mask  |
| `--onb-spotlight-ring`         | `rgba(220, 38, 38, 0.6)`          | `rgba(220, 38, 38, 0.4)`          | Spotlight target ring        |

---

## Accessibility Requirements

| Requirement                    | Standard      | Implementation                              |
|--------------------------------|---------------|---------------------------------------------|
| Color contrast (text)          | WCAG 2.1 AA   | All text meets 4.5:1 on onboarding surfaces |
| Color contrast (controls)      | WCAG 2.1 AA   | All interactive elements meet 3:1           |
| Keyboard navigation            | Full support   | Tab through all wizard controls             |
| Screen reader                  | Full support   | ARIA roles on stepper, steps, and controls  |
| Focus management               | Auto-focus     | Focus moves to step content on transition   |
| Reduced motion                 | Respected      | Step transitions disabled when preferred    |
| Step announcements             | Live region    | "Step X of Y: [step name]" announced        |

---

## Error Handling

### Invite Errors

| Error Condition            | User Message                                         | Recovery Action              |
|----------------------------|------------------------------------------------------|------------------------------|
| Token expired              | "This invitation has expired. Contact your admin."   | Link to support email        |
| Token already used         | "This invitation has already been accepted."         | Link to sign-in              |
| Email mismatch             | "This invitation was sent to a different email."     | Show expected email hint     |
| Token revoked              | "This invitation has been cancelled."                | Link to support email        |
| Org not found              | "Organization no longer exists."                     | Link to support email        |

### Wizard Errors

| Error Condition            | User Message                                         | Recovery Action              |
|----------------------------|------------------------------------------------------|------------------------------|
| Save failed                | "Could not save your progress. Retrying..."          | Auto-retry with manual retry |
| Session expired            | "Your session has expired. Please sign in again."    | Redirect to sign-in          |
| Required field empty       | Inline validation beneath field                      | Focus on first invalid field |
| API timeout                | "Connection issue. Your progress is saved."          | Retry button                 |
| Step data conflict         | "This information was updated. Please review."       | Refresh step content         |
