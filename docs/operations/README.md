# NIL Optic Operations Hub

> Last updated: 2026-03-04

---

## Purpose

The Operations Hub is the operational backbone for scaling NIL intelligence across all NCAA programs. It houses role-specific playbooks, team workflows, communication standards, support runbooks, and battle-board strategies that govern how every persona -- from Athletic Directors to Fans -- engages with the NIL Optic platform on a daily, weekly, monthly, and quarterly cadence.

These documents are designed to be living references. They define the operational rhythm for each role, prescribe KPI ownership, establish escalation paths, and ensure every user type has a clear playbook for extracting maximum value from the platform.

---

## Directory Structure

```
docs/operations/
  README.md .......................... This file -- Operations Hub index
  playbook-athletic-director.md ..... Athletic Director operations playbook
  playbook-agent.md ................. NIL Agent operations playbook
  playbook-athlete.md ............... Athlete operations playbook
  playbook-coach.md ................. Coach operations playbook
  playbook-agency-admin.md .......... Agency Admin operations playbook
  playbook-affiliate.md ............. Affiliate (tax/wealth) operations playbook
  playbook-admin.md ................. Platform Admin operations playbook
  playbook-fan.md ................... Fan persona operations playbook
  battle-board/ ..................... Battle board strategies and coverage tracking
  team/ ............................. Internal team workflows and sprint cadences
  communications/ ................... Communication templates and standards
  support/ .......................... Support runbooks and escalation procedures
```

---

## Role Playbooks

Each playbook follows a consistent structure: role overview, daily/weekly/monthly/quarterly cadences, key screens, KPIs, escalation paths, and basketball-first operational focus.

| Playbook | Role | Organization Category |
|---|---|---|
| [playbook-athletic-director.md](./playbook-athletic-director.md) | Athletic Director | `athletic` |
| [playbook-agent.md](./playbook-agent.md) | NIL Agent | `agency` |
| [playbook-athlete.md](./playbook-athlete.md) | College Athlete | `athletic` (program-scoped) |
| [playbook-coach.md](./playbook-coach.md) | Head / Assistant Coach | `athletic` (program-scoped) |
| [playbook-agency-admin.md](./playbook-agency-admin.md) | Agency Admin | `agency` |
| [playbook-affiliate.md](./playbook-affiliate.md) | Affiliate (Tax / Wealth) | `affiliate` |
| [playbook-admin.md](./playbook-admin.md) | Platform Admin | NIL Optic internal |
| [playbook-fan.md](./playbook-fan.md) | Fan | Public / limited-access persona |

---

## Subdirectories

### `battle-board/`

Strategic playbooks for NCAA program acquisition, conference penetration tracking, competitive displacement strategies, and market coverage dashboards. The battle board drives the go-to-market motion for expanding NIL Optic across Division I, II, and III programs.

| File | Description |
|------|-------------|
| `README.md` | Battle board overview, purpose, and strategy index |
| `ncaa-basketball-registry.md` | Complete NCAA basketball program registry with basketball-first targeting data |
| `conference-tracker.md` | Conference penetration tracking design spec with coverage dashboards |
| `onboarding-pipeline.md` | Program onboarding pipeline stages, conversion tracking, and success metrics |

### `team/`

Internal NIL Optic team workflows including sprint cadences, feature rollout checklists, cross-functional handoff procedures, and on-call rotation schedules for the engineering, design, data, and customer success teams.

| File | Description |
|------|-------------|
| `org-structure.md` | Organizational structure, reporting lines, squad model, and communication cadences |
| `hiring-plan.md` | Phase-by-phase hiring plan with role definitions, compensation estimates, and basketball expertise requirements |
| `scaling-playbook.md` | Scaling strategy from basketball beachhead through full NCAA coverage and professional sports adjacency |

### `communications/`

Templates and standards for all outbound communications: onboarding email sequences, in-app notification copy, compliance alert formatting, sales outreach templates, and investor update frameworks. Includes SendGrid template references and messaging tone guidelines aligned with the NIL Optic brand voice.

| File | Description |
|------|-------------|
| `email-lifecycle-matrix.md` | Complete email lifecycle organized by trigger: transactional, onboarding, engagement, re-engagement, seasonal |
| `communication-cadence.md` | Per-persona communication rhythm with channel mix, frequency caps, A/B testing, and basketball season integration |
| `notification-design-spec.md` | In-app and push notification design spec extending the feature-level notifications system |

### `support/`

Support runbooks covering tier-1 through tier-3 escalation procedures, common troubleshooting guides for sync failures, prediction accuracy issues, onboarding blockers, and role-context resolution problems. Includes SLA definitions and resolution time targets.

| File | Description |
|------|-------------|
| `help-center-architecture.md` | Knowledge base content structure, categories, role/sport tagging, and contextual surfacing |
| `support-workflows.md` | Ticket routing, SLA definitions, four-tier escalation, basketball-season priority boosting |

---

## The 10 Titans — Attack on Titan Blitz (2026-03-04)

This Operations Hub was built as part of the 10 Titans blitz — a coordinated expansion of the NIL Optic design system and operations infrastructure. Each Titan represents a workstream named after Attack on Titan characters.

| # | AoT Name | Code Name | Mission | Files | Primary Directory |
|---|----------|-----------|---------|-------|-------------------|
| I | Colossal Titan | ATLAS | Operations Playbooks | 9 | `docs/operations/` |
| II | Armored Titan | FORGE | Onboarding Design Specs | 3 | `design-system/10_Onboarding/` |
| III | Attack Titan | WARBOARD | NCAA Battle Board | 4 | `docs/operations/battle-board/` |
| IV | Female Titan | SENTINEL | Support & Help System | 3 | `design-system/11_Support/` + `docs/operations/support/` |
| V | War Hammer Titan | COMMAND | Admin & Internal Ops Templates | 2 | `design-system/06_Templates/` |
| VI | Beast Titan | NEXUS | Missing Feature Specs | 6 | `design-system/05_Features/` |
| VII | Cart Titan | GARRISON | Team Setup & Scaling | 3 | `docs/operations/team/` |
| VIII | Jaw Titan | PRISM | Missing Role Templates | 2 | `design-system/06_Templates/` |
| IX | Founding Titan | HERALD | Communications Lifecycle | 3 | `docs/operations/communications/` |
| X | Coordinate | CHRONICLE | Master Index | 3 | `docs/full-blitz-index.md` + READMEs |

Operations-specific Titans: ATLAS (I), WARBOARD (III), GARRISON (VII), HERALD (IX), and portions of SENTINEL (IV).

---

## Cross-References to Design System

The Operations Hub works in tandem with the design system. Key cross-references:

| Operations Document | Related Design System Spec |
|---------------------|---------------------------|
| Role playbooks (all 8) | `design-system/06_Templates/role-templates-extended.md` |
| Role playbooks (all 8) | `design-system/10_Onboarding/flows-by-persona.md` |
| `battle-board/conference-tracker.md` | `design-system/05_Features/sports-directory.md` |
| `communications/notification-design-spec.md` | `design-system/05_Features/notifications.md` |
| `communications/email-lifecycle-matrix.md` | `design-system/10_Onboarding/onboarding-system.md` |
| `support/help-center-architecture.md` | `design-system/11_Support/support-system.md` |
| `support/support-workflows.md` | `design-system/11_Support/support-system.md` |
| Platform Admin playbook | `design-system/06_Templates/admin-template.md` |
| Platform Admin playbook | `design-system/06_Templates/internal-ops-templates.md` |

Full cross-reference: [`docs/full-blitz-index.md`](../full-blitz-index.md)

---

## Conventions

- **Dark theme default** -- all operational dashboards and data surfaces render in dark mode with `#DC2626` red accents
- **Typography** -- `Inter` for UI text, `JetBrains Mono` for data values, KPI figures, and code references
- **Basketball-first** -- all examples, sample data, and scenario walkthroughs default to men's basketball unless otherwise specified
- **Cadence labels** -- Daily, Weekly, Monthly, Quarterly (QBR) are the four operational rhythms
- **KPI format** -- all KPIs use `JetBrains Mono` rendering with clear unit labels (%, $, #, rank)

---

## Related Documentation

| Document | Location |
|---|---|
| Capabilities Matrix | `docs/roles/capabilities-matrix.md` |
| Organization Role Taxonomy | `docs/roles/organization-role-taxonomy.md` |
| Program Association Rules | `docs/roles/program-association-rules.md` |
| Route Inventory | `docs/route-inventory.md` |
| Design System Overview | `docs/design/system/design-system-overview.md` |
| Component Contracts | `docs/design/contracts/component-contracts.md` |
| Design Tokens | `docs/design/design-tokens.md` |

---

## Ownership

| Area | Owner |
|---|---|
| Playbook content | Product + Operations |
| Battle board strategy | Growth + Sales |
| Team workflows | Engineering + Design |
| Communications templates | Marketing + Customer Success |
| Support runbooks | Customer Success + Engineering |

---

*NIL Optic -- Performance-first NIL intelligence for every program.*
