# NIL Optic Global Design System Library

> Design-only reference library. No code. For product education, keynotes, and design collaboration with Claude.

Last updated: 2026-03-04

## Purpose

NIL Optic's design system is the single source of truth for visual language, component anatomy, interaction patterns, and brand governance across all surfaces — web, mobile, marketing, and investor-facing materials.

This library exists to:
- Maintain brand consistency across NIL Optic products
- Educate collaborators and stakeholders on design decisions
- Provide design keynotes for pitches, demos, and investor decks
- Serve as a reference for the Codex engineering team

## Library Structure

```
design-system/
├── 00_Brand/           → Logo, identity, voice, brand guidelines
├── 01_Foundations/      → Color, typography, spacing, elevation, motion
├── 02_Primitives/       → Buttons, inputs, controls, indicators, icons
├── 03_Components/       → Cards, tables, navigation, charts, stat blocks
├── 04_Patterns/         → Loading, error, empty states, overlays, feedback
├── 05_Features/         → Valuation, recruiting CRM, roster builder, deals, compliance, messaging, tournaments, transfer portal, notifications, sports directory
├── 06_Templates/        → Role-page layouts, dashboard scaffolds, admin templates, internal ops templates, onboarding wizard
├── 07_Marketing/        → Pricing, CTA, testimonials, trust modules
├── 08_Documentation/    → Contracts, anatomy, do/don't, changelog
├── 09_Intelligence/     → UX direction and AI intelligence specs
├── 10_Onboarding/       → Onboarding system design, wizard template, per-persona flows
├── 11_Support/          → Support system design, contextual help, knowledge base
```

### 05_Features/ — Complete File Listing

| File | Description |
|------|-------------|
| `features.md` | Core feature specs: valuation engine, predictor, roster builder, recruiting CRM, deals pipeline |
| `compliance.md` | NIL compliance tracking, NCAA/state regulation monitoring, audit trails |
| `messaging-huddles.md` | Real-time messaging threads and synchronous video/audio huddle rooms |
| `notifications.md` | In-app and push notification system, role-based filtering, actionable alerts |
| `sports-directory.md` | Searchable directory of athletes, teams, conferences, and divisions |
| `tournaments.md` | NCAA tournament intelligence with NIL valuation overlays (March Madness focus) |
| `transfer-portal.md` | Transfer portal tracking workspace with valuation recalculation triggers |

### 06_Templates/ — Complete File Listing

| File | Description |
|------|-------------|
| `templates.md` | Core role-page layouts and dashboard scaffolds (AD, Agent, Athlete) |
| `admin-template.md` | Platform Admin dashboard template for internal operations |
| `role-templates-extended.md` | Seven additional role-specific dashboard templates (Coach, Agency Admin, Affiliate, Fan, Designer, Compliance Officer, Scout) |
| `onboarding-wizard-template.md` | Template-level visual spec for onboarding wizard shell and layout |
| `internal-ops-templates.md` | Internal admin views for data pipelines, program coverage, prediction governance |

### 10_Onboarding/ — Complete File Listing

| File | Description |
|------|-------------|
| `onboarding-system.md` | Onboarding design philosophy, shared patterns, token usage, and system architecture |
| `onboarding-wizard-template.md` | Reusable role-agnostic wizard container with step management and progress state |
| `flows-by-persona.md` | Per-persona onboarding step sequences, wireframes, timing, and first-value moments |

### 11_Support/ — Complete File Listing

| File | Description |
|------|-------------|
| `support-system.md` | Persistent contextual help layer, role-specific guidance, escalation paths, knowledge base architecture |

## Brand DNA

| Attribute | Value |
|-----------|-------|
| **Colors** | Red `#DC2626`, Black `#000000`, White `#FFFFFF` |
| **Voice** | Authoritative, precise, data-driven |
| **Visual Direction** | Sports authority, financial clarity, AI precision |
| **Design Principle** | Performance-first, data-legible, executive-grade |

## Governance

- Token keys are immutable after v1 freeze
- Components consumed via props/variants only — no local style forks
- All components require accessibility notes and contract documentation
- Figma-to-code parity maps tokens to Tailwind/runtime CSS variables

## Recent Additions — The 10 Titans Blitz (2026-03-04)

The following deliverables were created as part of the 10 Titans blitz, a comprehensive expansion of the NIL Optic design system and operations infrastructure.

| Titan | Code Name | Deliverables Added |
|-------|-----------|-------------------|
| I: Colossal Titan | ATLAS | 8 role playbooks + operations README (`docs/operations/`) |
| II: Armored Titan | FORGE | 3 onboarding design specs (`design-system/10_Onboarding/`) |
| III: Attack Titan | WARBOARD | 4 NCAA battle board files (`docs/operations/battle-board/`) |
| IV: Female Titan | SENTINEL | 3 support system files (`design-system/11_Support/` + `docs/operations/support/`) |
| V: War Hammer Titan | COMMAND | 2 admin/internal ops templates (`design-system/06_Templates/`) |
| VI: Beast Titan | NEXUS | 6 feature specs (`design-system/05_Features/`) |
| VII: Cart Titan | GARRISON | 3 team scaling files (`docs/operations/team/`) |
| VIII: Jaw Titan | PRISM | 2 role templates (`design-system/06_Templates/`) |
| IX: Founding Titan | HERALD | 3 communication lifecycle files (`docs/operations/communications/`) |
| X: Coordinate | CHRONICLE | 3 master index files (this README + `docs/operations/README.md` + `docs/full-blitz-index.md`) |

## Cross-References

- **Operations Hub**: `docs/operations/README.md` — role playbooks, battle board, team scaling, communications, support runbooks
- **Full Blitz Index**: `docs/full-blitz-index.md` — master cross-reference connecting all 10 Titan deliverables
- **Capabilities Matrix**: `docs/roles/capabilities-matrix.md`
- **Route Inventory**: `docs/route-inventory.md`

## Related Resources

- **Code repo**: Managed by Codex team (separate workflow)
- **Design Tokens Source**: `docs/design/design-tokens.md`
- **Component Contracts**: `docs/design/contracts/component-contracts.md`
- **System Overview**: `docs/design/system/design-system-overview.md`
