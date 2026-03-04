# TITAN X: CHRONICLE — The Coordinate

## The 10 Titans Full Blitz Index

> Master cross-reference for the NIL Optic design system and operations infrastructure.
> Last updated: 2026-03-04

---

## Executive Summary

The 10 Titans blitz is a coordinated expansion of the NIL Optic platform's design system and operations infrastructure. Named after Attack on Titan's nine Titans (plus the Coordinate that connects them all), each workstream delivered a specific category of design specs, operational playbooks, or system documentation.

**Total deliverables:** 38 files across 10 workstreams
**Estimated total lines:** ~18,500+
**Directories touched:** 9 (4 new, 5 extended)
**Roles covered:** 9+ personas with dedicated playbooks, templates, onboarding flows, and support paths
**Sport focus:** Basketball-first across every deliverable

The blitz transforms NIL Optic from a product with core feature specs into a fully-documented platform with operational playbooks for every role, onboarding flows for every persona, a battle board for NCAA program acquisition, a communications lifecycle engine, a tiered support system, and a complete admin operations surface.

---

## The 10 Titans Registry

| # | AoT Name | Code Name | Mission | Files | Primary Directory |
|---|----------|-----------|---------|-------|-------------------|
| I | Colossal Titan | **ATLAS** | Operations Playbooks | 9 | `docs/operations/` |
| II | Armored Titan | **FORGE** | Onboarding Design Specs | 3 | `design-system/10_Onboarding/` |
| III | Attack Titan | **WARBOARD** | NCAA Battle Board | 4 | `docs/operations/battle-board/` |
| IV | Female Titan | **SENTINEL** | Support & Help System | 3 | `design-system/11_Support/` + `docs/operations/support/` |
| V | War Hammer Titan | **COMMAND** | Admin & Internal Ops Templates | 2 | `design-system/06_Templates/` |
| VI | Beast Titan | **NEXUS** | Missing Feature Specs | 6 | `design-system/05_Features/` |
| VII | Cart Titan | **GARRISON** | Team Setup & Scaling | 3 | `docs/operations/team/` |
| VIII | Jaw Titan | **PRISM** | Missing Role Templates | 2 | `design-system/06_Templates/` |
| IX | Founding Titan | **HERALD** | Communications Lifecycle | 3 | `docs/operations/communications/` |
| X | Coordinate | **CHRONICLE** | Master Index | 3 | `docs/` + READMEs |

**Total new files: 38** (35 new + 3 updated/created by CHRONICLE)

---

## Complete File Inventory

### Titan I: ATLAS — Operations Playbooks (`docs/operations/`)

| File | Lines | Description |
|------|-------|-------------|
| `README.md` | ~110 | Operations Hub index, directory structure, role playbook table, conventions |
| `playbook-athletic-director.md` | ~500 | Athletic Director daily/weekly/monthly/quarterly cadences, KPIs, key screens |
| `playbook-agent.md` | ~500 | NIL Agent operations: deal pipeline management, valuation monitoring, client coordination |
| `playbook-athlete.md` | ~450 | Athlete self-service: profile management, deal review, valuation tracking |
| `playbook-coach.md` | ~450 | Coach operations: roster NIL overview, compliance awareness, recruiting integration |
| `playbook-agency-admin.md` | ~450 | Agency Admin: multi-agent oversight, portfolio analytics, billing management |
| `playbook-affiliate.md` | ~400 | Affiliate (tax/wealth) advisor: financial reporting, deal structuring, compliance |
| `playbook-admin.md` | ~500 | Platform Admin: system monitoring, user management, data pipeline governance |
| `playbook-fan.md` | ~350 | Fan persona: public athlete profiles, leaderboards, tournament engagement |

### Titan II: FORGE — Onboarding Design Specs (`design-system/10_Onboarding/`)

| File | Lines | Description |
|------|-------|-------------|
| `onboarding-system.md` | 460 | Design philosophy, shared patterns, token usage, system architecture |
| `onboarding-wizard-template.md` | 651 | Reusable role-agnostic wizard container, step management, progress state |
| `flows-by-persona.md` | 1,411 | Per-persona step sequences, wireframes, timing, first-value moments for all roles |

### Titan III: WARBOARD — NCAA Battle Board (`docs/operations/battle-board/`)

| File | Lines | Description |
|------|-------|-------------|
| `README.md` | ~180 | Battle board overview, strategy index, basketball-first acquisition framework |
| `ncaa-basketball-registry.md` | ~550 | Complete NCAA basketball program registry with targeting and priority data |
| `conference-tracker.md` | ~550 | Conference penetration tracking, coverage dashboards, competitive displacement |
| `onboarding-pipeline.md` | ~560 | Program onboarding pipeline stages, conversion tracking, success metrics |

### Titan IV: SENTINEL — Support & Help System

Split across two directories:

**`design-system/11_Support/`**

| File | Lines | Description |
|------|-------|-------------|
| `support-system.md` | 1,228 | Persistent contextual help layer, role-specific guidance, escalation paths, knowledge base architecture |

**`docs/operations/support/`**

| File | Lines | Description |
|------|-------|-------------|
| `help-center-architecture.md` | ~600 | Knowledge base content structure, categories, role/sport tagging, contextual surfacing |
| `support-workflows.md` | ~900 | Ticket routing, SLA definitions, four-tier escalation, basketball-season priority boosting |

### Titan V: COMMAND — Admin & Internal Ops Templates (`design-system/06_Templates/`)

| File | Lines | Description |
|------|-------|-------------|
| `admin-template.md` | 870 | Platform Admin dashboard: user management, data sync, prediction governance, battle board |
| `internal-ops-templates.md` | 793 | Internal admin views: data pipelines, program coverage, email ops, presentation tools |

### Titan VI: NEXUS — Missing Feature Specs (`design-system/05_Features/`)

| File | Lines | Description |
|------|-------|-------------|
| `compliance.md` | 358 | NIL compliance tracking, NCAA/state regulation monitoring, audit trails, deal approval gates |
| `messaging-huddles.md` | 439 | Real-time messaging threads and synchronous video/audio huddle rooms |
| `notifications.md` | 471 | In-app and push notification system, role-based filtering, actionable alerts |
| `sports-directory.md` | 521 | Searchable directory of athletes, teams, conferences, and divisions |
| `tournaments.md` | 408 | NCAA tournament intelligence with NIL valuation overlays (March Madness focus) |
| `transfer-portal.md` | 397 | Transfer portal tracking workspace with valuation recalculation triggers |

### Titan VII: GARRISON — Team Setup & Scaling (`docs/operations/team/`)

| File | Lines | Description |
|------|-------|-------------|
| `org-structure.md` | ~400 | Organizational structure, reporting lines, squad model, communication cadences |
| `hiring-plan.md` | ~600 | Phase-by-phase hiring plan, role definitions, compensation, basketball expertise requirements |
| `scaling-playbook.md` | ~530 | Scaling strategy: basketball beachhead through full NCAA and professional sports adjacency |

### Titan VIII: PRISM — Missing Role Templates (`design-system/06_Templates/`)

| File | Lines | Description |
|------|-------|-------------|
| `role-templates-extended.md` | 1,068 | Seven role-specific dashboard templates: Coach, Agency Admin, Affiliate, Fan, Designer, Compliance Officer, Scout |
| `onboarding-wizard-template.md` | 586 | Template-level visual spec for onboarding wizard shell, breakpoints, stepper variants |

### Titan IX: HERALD — Communications Lifecycle (`docs/operations/communications/`)

| File | Lines | Description |
|------|-------|-------------|
| `email-lifecycle-matrix.md` | ~650 | Complete email lifecycle by trigger: transactional, onboarding, engagement, seasonal |
| `communication-cadence.md` | ~750 | Per-persona communication rhythm, channel mix, frequency caps, A/B testing, basketball calendar |
| `notification-design-spec.md` | ~1,050 | Extended notification design spec, role-based matrix, priority levels, preference UI, accessibility |

### Titan X: CHRONICLE — Master Index (`docs/` + READMEs)

| File | Lines | Description |
|------|-------|-------------|
| `docs/full-blitz-index.md` | ~600 | This file — master cross-reference for the entire blitz |
| `design-system/README.md` | ~100 | Updated design system index with new directories and Titans registry |
| `docs/operations/README.md` | ~160 | Updated operations hub with file listings, Titans section, cross-references |

---

## Cross-Reference Matrix

### Roles x Documents Matrix

Which documents are most relevant to each role. Relevance: **P** = Primary (daily reference), **S** = Secondary (periodic reference), **R** = Read-only awareness.

| Document | AD | Agent | Athlete | Coach | Agency Admin | Affiliate | Platform Admin | Fan |
|----------|:--:|:-----:|:-------:|:-----:|:------------:|:---------:|:--------------:|:---:|
| **Playbook (own role)** | P | P | P | P | P | P | P | P |
| `compliance.md` | P | P | S | S | P | P | P | — |
| `messaging-huddles.md` | S | P | P | S | S | S | R | — |
| `notifications.md` | P | P | P | P | P | P | P | S |
| `sports-directory.md` | P | P | S | P | S | S | R | P |
| `tournaments.md` | P | P | S | P | S | S | R | P |
| `transfer-portal.md` | P | P | S | P | S | R | R | S |
| `onboarding-system.md` | R | R | R | R | R | R | P | R |
| `flows-by-persona.md` | S | S | S | S | S | S | P | S |
| `support-system.md` | S | S | S | S | S | S | P | S |
| `admin-template.md` | — | — | — | — | — | — | P | — |
| `internal-ops-templates.md` | — | — | — | — | — | — | P | — |
| `role-templates-extended.md` | R | R | R | R | R | R | P | R |
| `battle-board/*` | — | — | — | — | — | — | P | — |
| `team/*` | — | — | — | — | — | — | P | — |
| `communications/*` | R | R | R | R | R | R | P | R |
| `support/help-center-architecture.md` | S | S | S | S | S | S | P | S |
| `support/support-workflows.md` | — | — | — | — | — | — | P | — |

### Features x Specs Matrix

How feature specs map to product modules and surfaces.

| Feature Spec | Product Module | Key Surfaces | Roles Served |
|-------------|----------------|--------------|-------------|
| `features.md` (core) | Valuation Engine | Athlete Profile, Dashboard, Deal Cards | All |
| `features.md` (core) | Predictor | Prediction Panel, Confidence Meters | AD, Agent, Coach |
| `features.md` (core) | Roster Builder | Roster Grid, Player Cards | AD, Coach, Agent |
| `features.md` (core) | Recruiting CRM | Pipeline Board, Contact Cards | Agent, Agency Admin |
| `features.md` (core) | Deals Pipeline | Deal Cards, Status Tracker | Agent, Athlete, AD |
| `compliance.md` | Compliance Tracker | Compliance Dashboard, Deal Review | AD, Agent, Agency Admin, Affiliate |
| `messaging-huddles.md` | Messaging / Huddles | Thread View, Huddle Room, Deal Sidebar | Agent, Athlete, Coach |
| `notifications.md` | Notification System | Bell Tray, Toast Stack, Push | All |
| `sports-directory.md` | Sports Directory | Search, Browse, Entity Profiles | All |
| `tournaments.md` | Tournament Intelligence | Bracket View, Valuation Overlay | AD, Agent, Coach, Fan |
| `transfer-portal.md` | Transfer Portal | Portal Grid, Timeline, Valuation Deltas | AD, Agent, Coach |

### Personas x Playbooks x Onboarding x Templates Matrix

End-to-end coverage for each persona across operations, onboarding, and design.

| Persona | Operations Playbook | Onboarding Flow | Dashboard Template | Support Tier |
|---------|--------------------|-----------------|--------------------|-------------|
| Athletic Director | `playbook-athletic-director.md` | `flows-by-persona.md` (AD section) | `templates.md` (AD Dashboard) | Tier 2+ |
| NIL Agent | `playbook-agent.md` | `flows-by-persona.md` (Agent section) | `templates.md` (Agent Dashboard) | Tier 2+ |
| Athlete | `playbook-athlete.md` | `flows-by-persona.md` (Athlete section) | `templates.md` (Athlete Dashboard) | Tier 1 |
| Coach | `playbook-coach.md` | `flows-by-persona.md` (Coach section) | `role-templates-extended.md` (Coach) | Tier 1 |
| Agency Admin | `playbook-agency-admin.md` | `flows-by-persona.md` (Agency Admin section) | `role-templates-extended.md` (Agency Admin) | Tier 2 |
| Affiliate | `playbook-affiliate.md` | `flows-by-persona.md` (Affiliate section) | `role-templates-extended.md` (Affiliate) | Tier 1 |
| Platform Admin | `playbook-admin.md` | `flows-by-persona.md` (Admin section) | `admin-template.md` | Internal |
| Fan | `playbook-fan.md` | `flows-by-persona.md` (Fan section) | `role-templates-extended.md` (Fan) | Tier 0 (self-serve) |
| Designer | — | — | `role-templates-extended.md` (Designer) | Internal |
| Compliance Officer | — | — | `role-templates-extended.md` (Compliance) | Internal |
| Scout | — | — | `role-templates-extended.md` (Scout) | Internal |

---

## Dependency Map

The 10 Titans were executed in four phases, with later phases building on earlier ones.

```
Phase 1 — Foundation
  ├── Titan I:   ATLAS     (Operations Playbooks)
  ├── Titan VI:  NEXUS     (Feature Specs)
  └── Titan VIII: PRISM    (Role Templates)

Phase 2 — Expansion
  ├── Titan II:  FORGE     (Onboarding) ← depends on ATLAS (role definitions) + PRISM (template layouts)
  ├── Titan V:   COMMAND   (Admin Templates) ← depends on NEXUS (feature surfaces to manage)
  └── Titan III: WARBOARD  (Battle Board) ← depends on ATLAS (operational cadences)

Phase 3 — Infrastructure
  ├── Titan IV:  SENTINEL  (Support) ← depends on FORGE (onboarding context) + NEXUS (feature surfaces)
  ├── Titan VII: GARRISON  (Team Scaling) ← depends on ATLAS (role scope) + WARBOARD (growth targets)
  └── Titan IX:  HERALD    (Communications) ← depends on FORGE (onboarding triggers) + ATLAS (persona definitions)

Phase 4 — Coordination
  └── Titan X:   CHRONICLE (Master Index) ← depends on ALL previous Titans
```

### Dependency Detail

| Titan | Depends On | Reason |
|-------|-----------|--------|
| ATLAS (I) | — | Foundation: defines all roles and operational cadences |
| NEXUS (VI) | — | Foundation: defines all feature surfaces |
| PRISM (VIII) | — | Foundation: defines all dashboard template layouts |
| FORGE (II) | ATLAS, PRISM | Onboarding flows reference role definitions and template shells |
| COMMAND (V) | NEXUS | Admin surfaces manage feature data and prediction models |
| WARBOARD (III) | ATLAS | Battle board inherits operational cadences and KPI formats |
| SENTINEL (IV) | FORGE, NEXUS | Support system covers onboarding blockers and feature-specific help |
| GARRISON (VII) | ATLAS, WARBOARD | Team scaling aligns to role scope and growth targets |
| HERALD (IX) | FORGE, ATLAS | Communications triggered by onboarding events and persona lifecycle |
| CHRONICLE (X) | ALL | Master index references every deliverable |

---

## Basketball-First Checklist

Every basketball-specific element across all 10 Titan deliverables.

### Data & Entities
- [ ] NCAA Division I, II, III basketball program registry (`ncaa-basketball-registry.md`)
- [ ] Basketball conference hierarchy (Power 5, Mid-Major, Low-Major) (`conference-tracker.md`)
- [ ] Basketball athlete profiles as default entity type (`sports-directory.md`)
- [ ] Basketball transfer portal as default portal view (`transfer-portal.md`)
- [ ] March Madness bracket intelligence as primary tournament surface (`tournaments.md`)
- [ ] Basketball season calendar integration across all cadences (`communication-cadence.md`)

### Valuation & Prediction
- [ ] Basketball-specific valuation factors: PPG, APG, RPG, tournament performance
- [ ] March Madness exposure multiplier in valuation engine
- [ ] Transfer portal entry/exit triggers valuation recalculation
- [ ] Conference tournament performance weighting
- [ ] Preseason ranking impact on projected NIL value

### Operations & Playbooks
- [ ] Basketball recruiting calendar in Agent playbook (`playbook-agent.md`)
- [ ] Basketball season KPI cadences in AD playbook (`playbook-athletic-director.md`)
- [ ] Basketball roster management in Coach playbook (`playbook-coach.md`)
- [ ] Basketball-first sample data in all onboarding flows (`flows-by-persona.md`)
- [ ] Basketball program acquisition pipeline (`onboarding-pipeline.md`)

### Communications
- [ ] Basketball season email triggers: preseason, conference play, March Madness, draft (`email-lifecycle-matrix.md`)
- [ ] Game-day notification patterns (`notification-design-spec.md`)
- [ ] Transfer window communication surges (`communication-cadence.md`)
- [ ] Tournament bracket update push notifications (`notifications.md`)

### Support & Onboarding
- [ ] Basketball-specific help content categories (`help-center-architecture.md`)
- [ ] Basketball season awareness in support priority boosting (`support-workflows.md`)
- [ ] Basketball sample data in onboarding wizard (`onboarding-wizard-template.md`)
- [ ] Basketball-first first-value moments per persona (`flows-by-persona.md`)

### Admin & Internal
- [ ] Basketball program coverage tracking in Admin dashboard (`admin-template.md`)
- [ ] Basketball data pipeline monitoring (`internal-ops-templates.md`)
- [ ] Basketball-focused hiring requirements (`hiring-plan.md`)
- [ ] Basketball beachhead as Phase 1 scaling strategy (`scaling-playbook.md`)

---

## Design System Integration

How the new Titan deliverables connect to the existing design system layers (00-09).

```
┌─────────────────────────────────────────────────────────────┐
│ 00_Brand        │ Voice, color, and identity rules applied  │
│                 │ across ALL Titan deliverables              │
├─────────────────┼───────────────────────────────────────────┤
│ 01_Foundations   │ Tokens (color, type, spacing, elevation,  │
│                 │ motion) consumed by all new specs          │
├─────────────────┼───────────────────────────────────────────┤
│ 02_Primitives    │ Buttons, inputs, badges, indicators used  │
│                 │ in templates, onboarding, support widgets  │
├─────────────────┼───────────────────────────────────────────┤
│ 03_Components    │ Cards, tables, charts, stat blocks        │
│                 │ composed into feature specs and templates  │
├─────────────────┼───────────────────────────────────────────┤
│ 04_Patterns      │ Loading, error, empty, feedback states    │
│                 │ referenced in onboarding + support specs   │
├─────────────────┼───────────────────────────────────────────┤
│ 05_Features      │ EXTENDED by NEXUS (6 new specs):          │
│                 │ compliance, messaging, notifications,      │
│                 │ sports directory, tournaments, transfer    │
├─────────────────┼───────────────────────────────────────────┤
│ 06_Templates     │ EXTENDED by COMMAND (2) + PRISM (2):      │
│                 │ admin, internal ops, role extensions,      │
│                 │ onboarding wizard layout                   │
├─────────────────┼───────────────────────────────────────────┤
│ 07_Marketing     │ Referenced by HERALD for email design      │
│                 │ patterns and brand-consistent CTAs         │
├─────────────────┼───────────────────────────────────────────┤
│ 08_Documentation │ Contracts and anatomy referenced by all    │
│                 │ new feature specs and templates            │
├─────────────────┼───────────────────────────────────────────┤
│ 09_Intelligence  │ UX direction informs AI-powered surfaces  │
│                 │ in tournaments, predictions, valuations    │
├─────────────────┼───────────────────────────────────────────┤
│ 10_Onboarding    │ NEW layer by FORGE: system design, wizard │
│   [NEW]         │ template, per-persona flow definitions     │
├─────────────────┼───────────────────────────────────────────┤
│ 11_Support       │ NEW layer by SENTINEL: contextual help,   │
│   [NEW]         │ role-specific guidance, escalation paths   │
└─────────────────┴───────────────────────────────────────────┘
```

### Token Consumption

All new deliverables consume tokens from `docs/design/design-tokens.md`:

| Token Category | Consumed By |
|----------------|-------------|
| `color.surface.*` | All templates, onboarding wizard, support widget |
| `color.brand.red` (`#DC2626`) | KPI highlights, alerts, action buttons across all specs |
| `typography.family.inter` | All UI text in templates, onboarding, support |
| `typography.family.jetbrains-mono` | Data values, KPIs, code references in playbooks |
| `spacing.*` | Layout grids in all templates and feature specs |
| `elevation.*` | Modals, dropdowns, support overlay, notification toasts |
| `motion.*` | Onboarding wizard transitions, notification animations |

---

## Key Reference Files

These pre-existing documents are referenced across multiple Titan deliverables.

| Document | Path | Referenced By |
|----------|------|---------------|
| Capabilities Matrix | `docs/roles/capabilities-matrix.md` | ATLAS, FORGE, PRISM, COMMAND |
| Route Inventory | `docs/route-inventory.md` | NEXUS, COMMAND, PRISM |
| Design Tokens | `docs/design/design-tokens.md` | ALL design-system deliverables |
| Component Contracts | `docs/design/contracts/component-contracts.md` | NEXUS, COMMAND, PRISM, FORGE |
| Design System Overview | `docs/design/system/design-system-overview.md` | CHRONICLE |
| Organization Role Taxonomy | `docs/roles/organization-role-taxonomy.md` | ATLAS, FORGE, GARRISON |
| Program Association Rules | `docs/roles/program-association-rules.md` | ATLAS, WARBOARD |
| Core Features Spec | `design-system/05_Features/features.md` | NEXUS (extends), COMMAND, SENTINEL |
| Core Templates Spec | `design-system/06_Templates/templates.md` | PRISM (extends), COMMAND |
| UX Direction | `design-system/09_Intelligence/ux-direction.md` | NEXUS, FORGE |
| Pitch Deck | `pitch-deck/slides.md` | WARBOARD (market sizing), GARRISON (hiring justification) |

---

## What's Next

### Immediate Priorities

1. **GitHub Pages Setup** — Publish the design system as a browsable static site. The 12-layer directory structure (00-11) maps cleanly to a sidebar navigation. Each markdown file becomes a page. Priority: `05_Features/` and `06_Templates/` specs are the most frequently referenced by the Codex engineering team.

2. **Codex Handoff Packages** — Bundle feature specs with their corresponding component contracts and design tokens into handoff documents that the Codex team can consume directly. Priority order:
   - Transfer Portal (`transfer-portal.md` + `sports-directory.md`)
   - Tournament Intelligence (`tournaments.md`)
   - Compliance Tracker (`compliance.md`)
   - Messaging & Huddles (`messaging-huddles.md`)
   - Notification System (`notifications.md` + `notification-design-spec.md`)

3. **Onboarding Implementation** — The FORGE onboarding specs are the highest-impact deliverable for user activation. Recommended implementation order:
   - Onboarding Wizard shell component
   - Athletic Director flow (highest-value persona)
   - Agent flow (highest-volume persona)
   - Remaining flows by priority

4. **Battle Board Operationalization** — Connect the WARBOARD specs to a live tracking surface (Airtable, Notion, or custom admin dashboard). The `ncaa-basketball-registry.md` contains the seed data for program targeting.

5. **Support System Build** — SENTINEL specs are implementation-ready. The `support-system.md` design spec + `help-center-architecture.md` content structure + `support-workflows.md` ticket routing define a complete support stack.

### Future Titans (Potential)

| Candidate | Mission | Prerequisites |
|-----------|---------|---------------|
| Analytics & Reporting | Usage analytics, funnel metrics, executive reporting templates | ATLAS, NEXUS |
| API & Integration Specs | Third-party integration design patterns (ESPN, On3, Opendorse) | NEXUS |
| Mobile-Specific Templates | Native mobile layout specs for iOS/Android | PRISM, NEXUS |
| Investor Materials | Updated pitch deck with blitz deliverables, product demo scripts | CHRONICLE, all |
| Accessibility Audit | WCAG 2.1 AA compliance review across all specs | ALL |

---

## Appendix: Directory Tree (Complete)

```
niloptic/
├── design-system/
│   ├── README.md .......................... Design system index (updated by CHRONICLE)
│   ├── 00_Brand/ .......................... Logo, identity, voice, brand guidelines
│   ├── 01_Foundations/ .................... Color, typography, spacing, elevation, motion
│   ├── 02_Primitives/ ..................... Buttons, inputs, controls, indicators, icons
│   ├── 03_Components/ ..................... Cards, tables, navigation, charts, stat blocks
│   ├── 04_Patterns/ ....................... Loading, error, empty states, overlays, feedback
│   ├── 05_Features/
│   │   ├── features.md .................... Core features: valuation, predictor, roster, CRM, deals
│   │   ├── compliance.md .................. [NEXUS] NIL compliance tracking
│   │   ├── messaging-huddles.md ........... [NEXUS] Real-time messaging and huddle rooms
│   │   ├── notifications.md ............... [NEXUS] Notification system
│   │   ├── sports-directory.md ............ [NEXUS] Athlete/team/conference directory
│   │   ├── tournaments.md ................. [NEXUS] Tournament intelligence
│   │   └── transfer-portal.md ............. [NEXUS] Transfer portal tracking
│   ├── 06_Templates/
│   │   ├── templates.md ................... Core role-page layouts (AD, Agent, Athlete)
│   │   ├── admin-template.md .............. [COMMAND] Platform Admin dashboard
│   │   ├── internal-ops-templates.md ...... [COMMAND] Internal operations views
│   │   ├── role-templates-extended.md ..... [PRISM] 7 additional role dashboards
│   │   └── onboarding-wizard-template.md .. [PRISM] Onboarding wizard layout spec
│   ├── 07_Marketing/ ...................... Pricing, CTA, testimonials, trust modules
│   ├── 08_Documentation/ .................. Contracts, anatomy, do/don't, changelog
│   ├── 09_Intelligence/
│   │   └── ux-direction.md ................ UX direction and AI intelligence specs
│   ├── 10_Onboarding/
│   │   ├── onboarding-system.md ........... [FORGE] Onboarding design philosophy and architecture
│   │   ├── onboarding-wizard-template.md .. [FORGE] Reusable wizard container
│   │   └── flows-by-persona.md ............ [FORGE] Per-persona onboarding step sequences
│   └── 11_Support/
│       └── support-system.md .............. [SENTINEL] Support system design spec
├── docs/
│   ├── full-blitz-index.md ................ [CHRONICLE] This file — master cross-reference
│   ├── route-inventory.md ................. Route inventory
│   ├── design/
│   │   ├── design-tokens.md ............... Design token definitions
│   │   ├── contracts/
│   │   │   └── component-contracts.md ..... Component contract specifications
│   │   └── system/
│   │       └── design-system-overview.md .. Design system overview
│   ├── roles/
│   │   ├── capabilities-matrix.md ......... Role capabilities matrix
│   │   ├── organization-role-taxonomy.md .. Organization role taxonomy
│   │   └── program-association-rules.md ... Program association rules
│   └── operations/
│       ├── README.md ...................... [ATLAS/CHRONICLE] Operations Hub index
│       ├── playbook-athletic-director.md .. [ATLAS] AD playbook
│       ├── playbook-agent.md .............. [ATLAS] Agent playbook
│       ├── playbook-athlete.md ............ [ATLAS] Athlete playbook
│       ├── playbook-coach.md .............. [ATLAS] Coach playbook
│       ├── playbook-agency-admin.md ....... [ATLAS] Agency Admin playbook
│       ├── playbook-affiliate.md .......... [ATLAS] Affiliate playbook
│       ├── playbook-admin.md .............. [ATLAS] Platform Admin playbook
│       ├── playbook-fan.md ................ [ATLAS] Fan playbook
│       ├── battle-board/
│       │   ├── README.md .................. [WARBOARD] Battle board index
│       │   ├── ncaa-basketball-registry.md  [WARBOARD] NCAA basketball program registry
│       │   ├── conference-tracker.md ...... [WARBOARD] Conference penetration tracker
│       │   └── onboarding-pipeline.md ..... [WARBOARD] Program onboarding pipeline
│       ├── team/
│       │   ├── org-structure.md ........... [GARRISON] Org structure and squad model
│       │   ├── hiring-plan.md ............. [GARRISON] Phase-by-phase hiring plan
│       │   └── scaling-playbook.md ........ [GARRISON] Scaling strategy
│       ├── communications/
│       │   ├── email-lifecycle-matrix.md .. [HERALD] Email lifecycle by trigger
│       │   ├── communication-cadence.md ... [HERALD] Per-persona communication rhythm
│       │   └── notification-design-spec.md  [HERALD] Notification design spec
│       └── support/
│           ├── help-center-architecture.md  [SENTINEL] Knowledge base structure
│           └── support-workflows.md ....... [SENTINEL] Ticket routing and escalation
└── pitch-deck/
    ├── slides.md .......................... 18-slide keynote deck
    └── product-education.md ............... Internal product guide
```

---

*NIL Optic — Performance-first NIL intelligence for every program.*

*Titan X: CHRONICLE — The Coordinate that connects them all.*
