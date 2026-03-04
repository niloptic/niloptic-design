# NIL Optic — Product Education Guide

> For internal teams, partners, and collaborators working with Claude.

Last updated: 2026-03-01

---

## What Is NIL Optic?

NIL Optic is an AI-powered intelligence platform for the college athlete Name, Image, and Likeness (NIL) marketplace. It provides real-time valuations, predictive analytics, deal management, and compliance tools for three core personas: athletes, agents, and athletic departments.

---

## The NIL Market Context

### What is NIL?
NIL stands for **Name, Image, and Likeness** — the right of college athletes to profit from their personal brand. Following the 2021 NCAA ruling, college athletes can now earn money through endorsements, sponsorships, social media, appearances, and merchandise.

### The Problem We Solve
- **No standardized valuations**: Athletes don't know their market worth
- **No transparency**: Deals happen in the dark, leading to unfair compensation
- **No tools**: Athletic departments manage compliance on spreadsheets
- **No intelligence**: Agents negotiate without data
- **Fragmented ecosystem**: Point solutions for individual problems, no unified platform

---

## Core Product Modules

### 1. AI Valuation Engine
- Analyzes 50+ data points per athlete
- Social media followers, engagement rates, audience demographics
- Athletic performance stats, awards, conference standing
- Market demand signals from brand spending patterns
- Comparable deal analysis from transaction history
- Outputs: dollar valuation, confidence score (0-100%), factor breakdown

### 2. Predictor
- Machine learning model forecasting valuation trajectories
- 30, 60, and 90-day outlook windows
- Key driver identification (what will move the needle)
- Confidence bands showing prediction ranges
- 92% accuracy rate against actual outcomes

### 3. Roster Builder
- Construct hypothetical team rosters
- Real-time total NIL valuation as athletes are added
- Position-by-position value analysis
- Cross-program comparison capabilities
- Budget planning and forecasting tools

### 4. Recruiting CRM
- Kanban-style pipeline: Prospect → Outreach → Negotiate → Signed
- Per-athlete valuation cards with real-time updates
- Communication tracking and history
- Deal stage analytics and conversion metrics
- Integration with messaging/huddle features

### 5. Deal Management
- End-to-end deal lifecycle tracking
- Milestone management and deadline alerts
- Contract value and deliverable monitoring
- Compliance status per deal
- Brand partnership matching

### 6. Directory
- Searchable athlete database (4.2M+ athletes)
- Filter by sport, conference, position, valuation range
- Grid, list, and table view modes
- Athlete detail profiles with full valuation breakdown
- Team and program-level aggregations

---

## User Personas

### Athletic Director (AD)
**Goal**: Visibility and compliance across the program
**Key screens**: Program overview, compliance tracker, budget forecasting, sport-by-sport breakdown
**Value prop**: Replace spreadsheets with real-time intelligence

### Agent
**Goal**: Manage clients, find deals, close faster
**Key screens**: Client portfolio, deal pipeline, market opportunities, revenue tracking
**Value prop**: Data-driven negotiations and brand matching

### Athlete
**Goal**: Know my worth, track my deals, grow my brand
**Key screens**: Personal valuation, trend chart, active deals, social impact
**Value prop**: Transparency and empowerment

### Coach
**Goal**: Understand team NIL landscape, support athletes
**Key screens**: Team roster valuations, compliance alerts, recruiting pipeline
**Value prop**: Informed recruiting and retention

### Agency Admin
**Goal**: Manage the agency's entire operation
**Key screens**: Multi-agent overview, agency-wide revenue, client distribution
**Value prop**: Scale agency operations with data

---

## Technical Architecture (Design-Relevant)

### Platform Surfaces
| Surface | Framework | Notes |
|---------|-----------|-------|
| Web App | Next.js | Primary experience, all personas |
| Mobile App | Expo + React Native (NILWatch) | Athlete-first mobile experience |
| Marketing Site | Next.js | Public-facing, lead gen |
| API | REST + Supabase | Enterprise data access |

### Design System Stack
- **Tokens**: JSON source → CSS variables → Tailwind mapping
- **Token Studio**: `/designer/token-studio` for live editing
- **Component Library**: `/designer/component-library` for implementation inventory
- **Foundations**: Inter + JetBrains Mono, 4px base unit, 12-column grid
- **Mode**: Dark mode default, light mode available

### Role-Based Access
The entire UI adapts based on the authenticated user's role. Navigation items, dashboard content, available features, and data scope all change per role. This is governed by the capabilities matrix in `/docs/roles/capabilities-matrix.md`.

---

## Key Differentiators

| Differentiator | What It Means |
|----------------|---------------|
| **AI-First Valuations** | Not crowd-sourced or manual — ML model with 50+ inputs |
| **Predictive Intelligence** | Only platform with forward-looking valuation forecasting |
| **Multi-Persona** | One platform serving athletes, agents, and ADs differently |
| **Data Depth** | 4.2M athletes, $2.1B in transaction data analyzed |
| **Compliance Built-In** | Not an add-on — compliance tracking in every workflow |
| **Mobile-Native** | NILWatch app for athletes on the go |

---

## Design Principles (For All Collaborators)

1. **Performance-first**: Speed is a feature. Data loads fast or shows skeleton.
2. **Data-legible**: Numbers are the product. Typography, spacing, and contrast all serve readability.
3. **Executive-grade**: The interface should feel like Bloomberg, not a consumer app.
4. **Sports authority**: The visual language speaks the language of athletics — confident, competitive, precise.
5. **Financial clarity**: NIL valuations are financial products. Treat them with the same rigor as fintech.
6. **AI precision**: Predictions and confidence scores must be presented with appropriate uncertainty framing.

---

## Glossary

| Term | Definition |
|------|-----------|
| **NIL** | Name, Image, and Likeness — athlete's personal brand rights |
| **Valuation** | AI-calculated market value of an athlete's NIL |
| **Confidence Score** | 0-100% measure of valuation prediction reliability |
| **Comparable** | Historical deal used as reference for valuation |
| **Pipeline** | Stages of athlete/deal progression in CRM |
| **Collective** | Third-party entity pooling funds for athlete NIL deals |
| **Transfer Portal** | NCAA system for athletes transferring between schools |
| **Power 5** | Top 5 NCAA athletic conferences (SEC, Big Ten, ACC, Big 12, Pac-12) |
| **Roster Builder** | Tool for constructing hypothetical team rosters with valuations |
| **Deal Stage** | Progression phase: prospect, outreach, negotiate, signed |
