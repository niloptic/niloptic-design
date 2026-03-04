# NIL Optic Organizational Structure

> TITAN VII: GARRISON -- Team Setup & Scaling
> Last updated: 2026-03-04

---

## Purpose

This document defines the organizational structure for NIL Optic, the AI-powered NIL intelligence platform for college athletics. The org chart, reporting lines, squad model, and communication cadences are designed around a **basketball-first** go-to-market strategy, with structure that scales cleanly into multi-sport and full-NCAA coverage.

NIL Optic serves 9+ user roles across athletic departments (`athletic_director`, `assistant_athletic_director`, `general_manager`, `coach`, `athlete`), agencies (`agency_admin`, `agent`), and affiliates (`affiliate_admin`, `affiliate`). The organizational structure must support all three customer categories while maintaining a tight, mission-driven team during early scaling.

---

## Executive Team

| Role | Responsibility | Reports To | Basketball Focus |
|---|---|---|---|
| **CEO** | Vision, fundraising, board, strategic partnerships, NCAA relationships | Board | Conference commissioner relationships, NCAA governance navigation |
| **CTO** | Technical architecture, engineering org, infrastructure, data pipeline | CEO | SportsRadar integration, real-time game data systems, ML model accuracy |
| **CPO** | Product strategy, design, research, roadmap prioritization | CEO | Basketball-specific feature prioritization (March Madness, transfer portal, valuation models) |
| **Head of Sales** | Revenue, pipeline, enterprise deals, conference partnerships | CEO | Power 4 AD relationships, agency partnerships, conference-level deals |
| **Head of Customer Success** | Onboarding, retention, expansion, support operations | CEO | Program onboarding playbooks, basketball season cadence alignment |
| **Head of Marketing** | Brand, demand generation, content, events | CEO | Basketball media presence, March Madness campaigns, NIL thought leadership |

### Executive Decision Authority

| Decision Type | Primary Owner | Approval Required |
|---|---|---|
| Product roadmap prioritization | CPO | CEO sign-off on quarterly OKRs |
| Pricing and packaging changes | CEO | Board notification for >20% changes |
| Enterprise deal terms (>$50K ACV) | Head of Sales | CEO approval |
| Technical architecture decisions | CTO | CPO alignment on user impact |
| Headcount additions | Hiring manager | CEO approval for all roles |
| Conference-level partnerships | Head of Sales | CEO co-sign |
| Compliance and NCAA policy responses | CEO | Legal counsel review |

---

## Engineering Organization

### Structure

```
CTO
 |-- VP Engineering (Phase 3+)
 |    |-- Engineering Manager, Frontend
 |    |-- Engineering Manager, Backend
 |    |-- Engineering Manager, Data/ML
 |
 |-- Frontend Team
 |    |-- Senior Frontend Engineer (Tech Lead)
 |    |-- Frontend Engineer x2-4
 |    |-- Mobile Engineer (React Native/Expo) x1-2
 |
 |-- Backend Team
 |    |-- Senior Backend Engineer (Tech Lead)
 |    |-- Backend Engineer x2-4
 |    |-- API/Integration Engineer x1
 |
 |-- Data & ML Team
 |    |-- ML Engineer (Tech Lead)
 |    |-- ML Engineer x1-2
 |    |-- Data Engineer x1-2
 |    |-- Data Analyst x1
 |
 |-- Infrastructure Team
 |    |-- DevOps/Infra Engineer (Lead)
 |    |-- SRE x1 (Phase 2+)
```

### Technology Stack Ownership

| Team | Owns | Key Technologies |
|---|---|---|
| Frontend | `next-app/`, design system, component library, role-specific shells | Next.js, React, TypeScript, Tailwind |
| Backend | API routes, Supabase schema, sync server, auth flows | Supabase, PostgreSQL, Edge Functions, SendGrid |
| Data/ML | Valuation models, prediction engine, data pipelines, analytics | Python, TensorFlow/PyTorch, SportsRadar API, statistical models |
| Infrastructure | CI/CD, monitoring, performance, security, deployment | Vercel, Supabase infra, sync-server orchestration |
| Mobile | React Native/Expo app, mobile-specific UX | React Native, Expo, mobile auth flows |

### Basketball-Specific Engineering Focus

| Area | Engineering Priority | Why Basketball First |
|---|---|---|
| Valuation Models | ML team top priority | Basketball has the most mature NIL market data; models can be validated against known transaction data |
| Real-Time Game Sync | Backend + Infra priority | SportsRadar Division I game sync powers live stats, shot charts, and play-by-play for basketball |
| Transfer Portal Integration | Full-stack priority | Basketball transfer portal is the most active across all sports; AD/coach workflows depend on it |
| March Madness Features | Seasonal full-team sprint | Tournament intelligence is the #1 engagement driver and sales catalyst |
| Role-Specific Dashboards | Frontend priority | Athletic Director, Coach, Agent, and Athlete shells must deliver basketball-contextual intelligence |

---

## Product Organization

### Structure

```
CPO
 |-- Product Manager (Basketball/Core)
 |-- Product Manager (Platform/Growth) -- Phase 2+
 |-- Product Manager (Sport-Specific) -- Phase 3+ (per sport)
 |-- Head of Design
 |    |-- Product Designer (Design System + Core UX)
 |    |-- Product Designer (Role-Specific Experiences) -- Phase 2+
 |    |-- UX Researcher -- Phase 2+
```

### Product Ownership Areas

| Product Area | Owner | Basketball Scope |
|---|---|---|
| Valuation Engine | PM (Basketball/Core) | Basketball player valuation, conference rankings, program valuations |
| Predictor & Intelligence | PM (Basketball/Core) | NIL prediction models, competitive intelligence, tournament analytics |
| Role Dashboards | PM (Basketball/Core) + Design | AD, Coach, Agent, Athlete, Fan shells and workflows |
| Transfer Portal | PM (Basketball/Core) | Basketball transfer portal tracking, pipeline management |
| Battle Board / GTM Tools | PM (Platform/Growth) | Program coverage tracking, sales intelligence dashboards |
| Messaging & Huddles | PM (Platform/Growth) | Cross-role communication (threads, meets, huddle rooms) |
| Directory & Marketplace | PM (Platform/Growth) | Agent directory, affiliate directory, roster builder |
| Design System | Head of Design | Token Studio, component contracts, accessibility, theming |

---

## Go-to-Market Organization

### Structure

```
CEO
 |-- Head of Sales
 |    |-- Account Executive, Power 4 x1-2
 |    |-- Account Executive, High Major x1 (Phase 2+)
 |    |-- SDR x2 (Phase 2+)
 |    |-- Enterprise AE (Phase 2+)
 |    |-- Regional AEs x3-5 (Phase 3+)
 |
 |-- Head of Marketing
 |    |-- Content/Marketing Lead
 |    |-- Growth Marketer (Phase 2+)
 |    |-- Event Marketing (Phase 3+)
 |
 |-- Head of Customer Success
 |    |-- CSM, Athletic Programs x1-2
 |    |-- CSM, Agencies x1 (Phase 2+)
 |    |-- CSM, Affiliates x1 (Phase 2+)
 |    |-- Support Lead (Phase 2+)
 |    |-- Support Specialist x2 (Phase 3+)
 |
 |-- Head of Partnerships (Phase 1 hire)
 |    |-- Partnership Manager, Data (SportsRadar, social platforms)
 |    |-- Partnership Manager, Brands/Collectives (Phase 2+)
```

### Sales Territory Model (Basketball First)

| Territory | Coverage | AE Assignment | Target Programs |
|---|---|---|---|
| SEC + ACC | Power 4 South/East | AE 1 | ~30 basketball programs |
| Big Ten + Big 12 | Power 4 North/West | AE 2 | ~37 basketball programs |
| American + Mountain West + WCC | High Major Tier B | AE 3 (Phase 2) | ~35 basketball programs |
| A-10 + MVC + remaining High Major | High Major Tier B | AE 3 (Phase 2) | ~25 basketball programs |
| Mid-Major D1 | Tier C | Regional AEs (Phase 3) | ~230 basketball programs |
| D2/D3/NAIA | Tier D expansion | Inside sales (Phase 4) | 1,000+ programs |

### Customer Success Model

| Customer Tier | CSM Ratio | Touch Model | Basketball Cadence |
|---|---|---|---|
| Power 4 Programs | 1:10 | High-touch, weekly check-ins | Season-aligned: preseason setup, in-season weekly, March Madness daily, offseason monthly |
| High Major Programs | 1:20 | Mid-touch, biweekly check-ins | Season-aligned with lighter offseason cadence |
| Mid-Major Programs | 1:40 | Tech-touch + quarterly reviews | Automated onboarding, self-serve, escalation-based support |
| Agencies | 1:15 | High-touch, deal-cycle aligned | Transfer portal windows, signing periods, March Madness pipeline |
| Affiliates | 1:30 | Mid-touch, service-cycle aligned | Tax season peaks, NIL payment schedule alignment |

---

## Operations Organization

### Structure

```
CEO
 |-- Head of Operations (Phase 3+)
 |    |-- Support Lead
 |    |    |-- Support Specialist x2-4
 |    |
 |    |-- Compliance Specialist (Phase 3+)
 |    |-- Business Operations Analyst (Phase 2+)
 |
 |-- Legal Counsel (external, then Phase 4 hire)
 |-- Finance (fractional CFO, then Phase 4 hire)
 |-- HR (fractional, then Phase 3 hire)
```

### Support Tiers

| Tier | Scope | Response SLA | Staffing |
|---|---|---|---|
| Tier 1 | Account access, basic navigation, FAQ | <2 hours (business) | Support Specialist |
| Tier 2 | Data discrepancies, sync failures, role-context issues | <8 hours (business) | Support Lead + Engineering on-call |
| Tier 3 | Prediction accuracy disputes, compliance escalations, security incidents | <24 hours | CTO/CPO + dedicated engineering |
| Critical | Platform outage, data breach, NCAA compliance violation | <1 hour | All-hands war room protocol |

---

## RACI Matrix

> R = Responsible, A = Accountable, C = Consulted, I = Informed

### Feature Launches

| Activity | CEO | CTO | CPO | Head of Sales | Head of CS | Head of Marketing |
|---|---|---|---|---|---|---|
| Feature scoping & requirements | I | C | **A/R** | C | C | I |
| Technical design & architecture | I | **A/R** | C | I | I | I |
| UX design & prototyping | I | C | **A/R** | C | C | I |
| Engineering implementation | I | **A/R** | C | I | I | I |
| QA & acceptance testing | I | **R** | **A** | I | C | I |
| Go-to-market messaging | C | I | C | C | C | **A/R** |
| Customer communication & training | I | I | C | C | **A/R** | C |
| Launch go/no-go decision | **A** | C | **R** | C | C | C |
| Post-launch monitoring | I | **A/R** | C | I | **R** | I |

### Pricing Changes

| Activity | CEO | CTO | CPO | Head of Sales | Head of CS | Head of Marketing |
|---|---|---|---|---|---|---|
| Pricing strategy & modeling | **A** | I | **R** | **R** | C | C |
| Technical implementation | I | **A/R** | C | I | I | I |
| Customer migration plan | C | I | C | **R** | **A/R** | C |
| Market communication | **A** | I | C | C | C | **R** |
| Contract amendment processing | C | I | I | **A/R** | C | I |

### Enterprise Deals (>$50K ACV)

| Activity | CEO | CTO | CPO | Head of Sales | Head of CS | Head of Partnerships |
|---|---|---|---|---|---|---|
| Deal qualification | C | I | I | **A/R** | I | C |
| Technical requirements review | I | **A/R** | C | C | I | I |
| Custom feature negotiation | **A** | C | **R** | C | I | I |
| Contract & legal review | **A** | I | I | **R** | I | C |
| Onboarding handoff | I | I | C | **R** | **A/R** | I |
| Ongoing relationship management | C | I | I | C | **A/R** | C |

### Platform Outages

| Activity | CEO | CTO | CPO | Head of Sales | Head of CS | Head of Marketing |
|---|---|---|---|---|---|---|
| Incident detection & triage | I | **A/R** | I | I | I | I |
| Technical resolution | I | **A/R** | I | I | I | I |
| Customer communication | C | I | I | C | **A/R** | **R** |
| Internal status updates | **A** | **R** | I | I | I | I |
| Post-mortem & remediation | C | **A/R** | C | I | C | I |
| External communication (if public) | **A** | C | I | I | C | **R** |

### Compliance Issues (NCAA / NIL Policy)

| Activity | CEO | CTO | CPO | Head of Sales | Head of CS | Legal |
|---|---|---|---|---|---|---|
| Issue identification & assessment | **A** | C | C | I | C | **R** |
| Platform impact analysis | C | **A/R** | **R** | I | I | C |
| Customer notification | **A** | I | I | C | **R** | C |
| Technical remediation | I | **A/R** | C | I | I | C |
| Policy response & positioning | **A/R** | I | C | C | I | **R** |
| Regulatory filing (if required) | **A** | I | I | I | I | **R** |

---

## Cross-Functional Squad Model

Squads are persistent, cross-functional teams aligned to product domains. Each squad has a dedicated mission, owns its roadmap within the product strategy, and operates with autonomy on execution while aligning on quarterly OKRs.

### Active Squads

#### Valuation Squad

| Role | Person/Count | Responsibility |
|---|---|---|
| Product Manager | PM (Basketball/Core) | Valuation roadmap, model requirements, accuracy targets |
| ML Engineer | 1 (Lead) | Valuation model development, training, retraining cadence |
| ML Engineer | 1 | Feature engineering, data pipeline for model inputs |
| Backend Engineer | 1 | Valuation API, caching, performance optimization |
| Frontend Engineer | 1 | Valuation UI surfaces across AD, Coach, Agent, Athlete dashboards |
| Designer | 1 (shared with Intelligence Squad) | Valuation data visualization, confidence indicators, comparison UX |

**Mission**: Deliver the most accurate, transparent, and actionable NIL valuation intelligence in the market. Basketball valuation models are the foundation; accuracy against known transaction data is the north star metric.

**Key Metrics**: Valuation model accuracy (target: <15% median error vs. actual transactions), coverage (% of D1 basketball players with valuations), latency (valuation API p95 <200ms).

#### Intelligence Squad

| Role | Person/Count | Responsibility |
|---|---|---|
| Product Manager | PM (Basketball/Core) | Prediction engine, competitive intelligence, tournament analytics |
| ML Engineer | 1 (shared with Valuation) | Prediction model development |
| Data Engineer | 1 | Data pipeline, SportsRadar sync, stat aggregation |
| Backend Engineer | 1 | Prediction API, transfer portal data, battle board backend |
| Frontend Engineer | 1 | Predictor UI, tournament features, competitive intelligence dashboards |
| Designer | 1 (shared with Valuation Squad) | Data visualization, prediction confidence UX, March Madness features |

**Mission**: Power the predictive intelligence layer that differentiates NIL Optic. From transfer portal predictions to March Madness tournament intelligence, this squad owns the forward-looking analytics that drive user engagement and retention.

**Key Metrics**: Prediction accuracy, tournament feature engagement, transfer portal prediction adoption rate.

#### Platform Squad

| Role | Person/Count | Responsibility |
|---|---|---|
| Product Manager | PM (Platform/Growth) | Messaging, directories, settings, onboarding, admin tools |
| Backend Engineer | 1 | Auth, messaging infrastructure, Supabase schema, sync server |
| Frontend Engineer | 1 | Messaging UI, directory pages, settings surfaces, admin dashboard |
| Frontend Engineer | 1 | Role-specific shells, navigation, onboarding flows |
| DevOps/Infra | 1 | CI/CD, monitoring, deployment, performance |
| Designer | 1 (shared across squads) | Platform UX, design system maintenance, Token Studio |

**Mission**: Build and maintain the platform infrastructure that every role depends on. Messaging, authentication, role management, directory services, and the core shell architecture that supports 9+ user roles.

**Key Metrics**: Platform uptime (target: 99.9%), message delivery reliability, onboarding completion rate, role-context resolution accuracy.

#### Growth Squad (Phase 2+)

| Role | Person/Count | Responsibility |
|---|---|---|
| Product Manager | PM (Platform/Growth) | Activation, retention, expansion, self-serve conversion |
| Growth Marketer | 1 | Demand generation, conversion optimization, content |
| SDR | 2 | Outbound prospecting, lead qualification |
| Data Analyst | 1 | Funnel analytics, cohort analysis, churn prediction |
| Frontend Engineer | 1 (shared) | Marketing site, onboarding optimization, fan conversion funnel |

**Mission**: Drive efficient customer acquisition and expansion revenue. Own the funnel from awareness through activation to expansion, with basketball programs as the primary acquisition target.

**Key Metrics**: MQL-to-SQL conversion rate, time-to-first-value, net revenue retention, fan-to-paid conversion rate.

### Squad Rituals

| Ritual | Cadence | Duration | Participants | Purpose |
|---|---|---|---|---|
| Squad Standup | Daily | 15 min | Squad members | Progress, blockers, coordination |
| Sprint Planning | Biweekly (Monday) | 60 min | Squad members | Sprint scope, story sizing, commitment |
| Sprint Review | Biweekly (Friday) | 45 min | Squad + stakeholders | Demo completed work, gather feedback |
| Squad Retro | Biweekly (Friday) | 30 min | Squad members | Process improvement, team health |
| Cross-Squad Sync | Weekly (Wednesday) | 30 min | Squad leads + CPO + CTO | Dependency management, shared roadmap alignment |

---

## Communication Channels

### Slack Structure

| Channel | Purpose | Members | Cadence |
|---|---|---|---|
| `#general` | Company-wide announcements, celebrations | All | As needed |
| `#engineering` | Engineering discussions, technical decisions, on-call handoffs | Engineering + CTO | Active daily |
| `#product` | Product discussions, roadmap updates, user research findings | Product + Design + Eng leads | Active daily |
| `#sales` | Deal updates, pipeline reviews, competitive intel | Sales + CS + CEO | Active daily |
| `#customer-success` | Account health, churn risk, onboarding status, support escalations | CS + Support + Product | Active daily |
| `#marketing` | Campaign updates, content calendar, event planning | Marketing + Sales + Product | Active daily |
| `#squad-valuation` | Valuation squad coordination | Valuation squad members | Active daily |
| `#squad-intelligence` | Intelligence squad coordination | Intelligence squad members | Active daily |
| `#squad-platform` | Platform squad coordination | Platform squad members | Active daily |
| `#squad-growth` | Growth squad coordination (Phase 2+) | Growth squad members | Active daily |
| `#incidents` | Production incidents, outage communication, post-mortems | Engineering + CTO + CPO | As needed (critical) |
| `#basketball-intel` | Basketball-specific market intelligence, NCAA news, NIL policy updates | All | Active daily (peak during season) |
| `#march-madness-war-room` | March Madness operational coordination (seasonal) | All hands | Intensive during tournament |
| `#deals` | Deal alerts, closed-won celebrations, contract milestones | Sales + CS + CEO | As deals progress |
| `#bugs-and-feedback` | Customer-reported issues, internal QA findings | Engineering + CS + Product | Active daily |
| `#random` | Non-work, team bonding, basketball game threads | All | As desired |

### Meeting Cadence

| Meeting | Cadence | Duration | Attendees | Agenda |
|---|---|---|---|---|
| **All Hands** | Biweekly (Friday) | 45 min | Entire company | Company metrics, wins, roadmap updates, Q&A |
| **Executive Sync** | Weekly (Monday) | 60 min | CEO, CTO, CPO, Heads of Sales/CS/Marketing | OKR progress, blockers, strategic decisions, pipeline review |
| **Product-Engineering Sync** | Weekly (Tuesday) | 45 min | CPO, CTO, PMs, Eng leads, Design | Roadmap priorities, technical feasibility, sprint alignment |
| **Sales Pipeline Review** | Weekly (Wednesday) | 30 min | Head of Sales, AEs, CEO | Pipeline health, deal progression, forecast updates |
| **Customer Health Review** | Weekly (Thursday) | 30 min | Head of CS, CSMs, Head of Sales | Account health, churn risks, expansion opportunities |
| **Cross-Squad Sync** | Weekly (Wednesday) | 30 min | Squad leads, CPO, CTO | Inter-squad dependencies, shared components, release coordination |
| **Board Update** | Monthly | 60 min | CEO, Board | Financials, growth metrics, strategic updates, fundraising |
| **QBR (Quarterly Business Review)** | Quarterly | Half-day | All leadership + extended team | OKR scoring, next-quarter planning, team retrospective |

### Basketball Season Communication Adjustments

| Period | Communication Adjustment |
|---|---|
| **Preseason (Aug--Oct)** | Intensified onboarding support cadence; weekly new-program check-ins; sales push for Power 4 closes |
| **Regular Season (Nov--Feb)** | Weekly basketball intel briefings; game-day data sync monitoring; in-season feature requests fast-tracked |
| **Conference Tournaments (Mar)** | Daily cross-squad syncs; tournament feature war room; customer engagement monitoring |
| **March Madness (Mar--Apr)** | War room activated; all-hands on deck for tournament intelligence features; daily customer pulse checks |
| **Transfer Portal Window (Apr--May)** | Transfer portal squad focus; daily pipeline updates for ADs/coaches; agent engagement campaigns |
| **Offseason (Jun--Jul)** | Strategic planning; technical debt sprints; next-season feature development; conference-level sales pushes |

---

## Basketball-First Organizational Focus

### Why Basketball Is the First Dedicated Sport Vertical

| Factor | Basketball Advantage |
|---|---|
| **Market Maturity** | Basketball has the most developed NIL marketplace with the highest per-athlete transaction volumes and the most sophisticated buyer ecosystem (brands, collectives, agencies) |
| **Data Availability** | SportsRadar provides comprehensive Division I basketball data including play-by-play, box scores, NET rankings, and conference standings -- enabling accurate valuation models |
| **Athlete Concentration** | Basketball rosters are small (13-15 players) compared to football (85+), making per-athlete valuation more actionable and per-program pricing more attractive |
| **Seasonal Intensity** | March Madness creates a concentrated engagement peak that drives viral adoption, media coverage, and sales pipeline acceleration |
| **Transfer Portal Activity** | Basketball has the most active transfer portal relative to roster size, making prediction and intelligence tools immediately valuable to ADs and coaches |
| **Decision-Maker Access** | Basketball ADs and head coaches are more accessible than football counterparts and often have direct NIL budget authority |
| **Revenue Per Program** | Basketball generates the second-highest athletic department revenue, ensuring programs have budget for intelligence tools |
| **Conference Structure** | The Power 4 conference alignment (67 programs) creates a manageable, high-value beachhead for initial sales territory coverage |

### Basketball Team Dedication

Every functional area maintains basketball-specific focus:

- **Engineering**: SportsRadar basketball sync is the #1 data pipeline priority; valuation models are trained on basketball transaction data first; March Madness features get dedicated sprint allocation
- **Product**: Basketball use cases drive all feature prioritization; role dashboards are designed around basketball AD/Coach workflows; tournament intelligence is a product pillar
- **Sales**: Basketball programs are the primary acquisition target; territory model is built around basketball conferences; all sales materials lead with basketball examples
- **Customer Success**: Onboarding playbooks are basketball-season-aligned; CSM training emphasizes basketball program operations; success metrics track basketball-specific outcomes
- **Marketing**: Content strategy leads with basketball NIL stories; event presence targets basketball conferences; thought leadership focuses on basketball NIL trends

---

## Organizational Scaling Milestones

| Milestone | Team Size | Org Structure Change |
|---|---|---|
| **5-8 people** (Phase 1) | Founders + first hires | Flat structure, everyone reports to CEO, informal squads |
| **15-25 people** (Phase 2) | Dedicated functional leads | Formal squad model, Head of Sales/CS/Marketing hired, engineering team leads |
| **40-60 people** (Phase 3) | VP-level management layer | VP Engineering, VP Sales, VP Marketing; sport-specific PMs; regional sales teams |
| **80-120 people** (Phase 4) | Full C-suite + department structure | CFO, CHRO, CLO; international team; multiple sport verticals with dedicated leadership |

---

## Related Documents

| Document | Location |
|---|---|
| Scaling Playbook | `docs/operations/team/scaling-playbook.md` |
| Hiring Plan | `docs/operations/team/hiring-plan.md` |
| Capabilities Matrix | `docs/roles/capabilities-matrix.md` |
| Organization Role Taxonomy | `docs/roles/organization-role-taxonomy.md` |
| Operations Hub README | `docs/operations/README.md` |

---

*NIL Optic -- Performance-first NIL intelligence for every program.*
