# NIL Optic Scaling Playbook

> TITAN VII: GARRISON -- Team Setup & Scaling
> Last updated: 2026-03-04

---

## Purpose

This playbook defines the phase-by-phase scaling strategy for NIL Optic, from basketball beachhead through full NCAA coverage and into professional sports adjacency. Each phase specifies team composition, infrastructure investments, revenue milestones, go/no-go criteria, risk factors, and partnership strategy.

The scaling model is built on a **basketball-first** thesis: win basketball, prove the model, then expand sport by sport with validated playbooks.

---

## Scaling Overview

| Phase | Name | Timeline | Team Size | ARR Target | Programs | Sports |
|---|---|---|---|---|---|---|
| **Phase 1** | Basketball Beachhead | Current -- Month 12 | 5-8 | $500K | 50 basketball | Basketball only |
| **Phase 2** | Basketball Dominance | Month 12 -- Month 24 | 15-25 | $2M | 200 basketball | Basketball only |
| **Phase 3** | Multi-Sport Expansion | Month 24 -- Month 42 | 40-60 | $10M | 400+ multi-sport | Basketball, Football, Baseball, Softball, Soccer, Track |
| **Phase 4** | Full NCAA + Professional | Month 42 -- Month 60+ | 80-120 | $25M+ | 1,000+ all divisions | All NCAA + professional NIL adjacency |

---

## Phase 1 -- Basketball Beachhead

> **Mission**: Prove product-market fit with Power 4 basketball programs. Build the foundational valuation engine, land 50 programs, and reach $500K ARR.

### Team Composition (5-8 people)

| Role | Count | Focus |
|---|---|---|
| CEO / Founder | 1 | Vision, fundraising, Power 4 AD relationships, NCAA navigation |
| CTO / Co-Founder | 1 | Architecture, full-stack development, SportsRadar integration |
| Full-Stack Engineer | 1 | Next.js/Supabase, role dashboards, core platform features |
| ML Engineer | 1 | Valuation model v1, basketball prediction engine |
| Product Designer | 1 | Design system, AD/Coach/Agent dashboard UX, dark-mode-first UI |
| Account Executive | 1 | Power 4 basketball program sales, conference relationships |
| Customer Success Manager | 1 | Onboarding, retention, basketball-season-aligned support |
| Head of Partnerships | 1 | SportsRadar relationship, data partnerships, brand network seeding |

### Key Milestones

| Milestone | Target | Measurement |
|---|---|---|
| Power 4 programs onboarded | 30 | Signed contracts with active usage |
| High Major programs onboarded | 20 | Signed contracts with active usage |
| Total basketball programs | 50 | Active paying accounts |
| ARR | $500K | Contracted annual revenue |
| Valuation model accuracy | <20% median error | Against known basketball NIL transactions |
| AD dashboard NPS | >50 | Quarterly NPS survey |
| Product-market fit signal | 40%+ "very disappointed" | Sean Ellis test with active AD users |
| Agent/Affiliate adoption | 10 agencies, 5 affiliates | Pilot accounts with active usage |

### Infrastructure Investments

| Investment | Cost Estimate | Purpose |
|---|---|---|
| SportsRadar API contract (D1 basketball) | $50-100K/yr | Real-time game data, stats, rankings for Division I basketball |
| Supabase Pro + compute scaling | $5-15K/yr | Database, auth, real-time subscriptions, edge functions |
| Vercel Pro | $2-5K/yr | Next.js hosting, serverless functions, preview deployments |
| ML compute (cloud GPU) | $10-20K/yr | Model training, retraining, inference for valuation and prediction |
| Monitoring & observability | $3-8K/yr | Error tracking, performance monitoring, uptime alerting |
| SendGrid | $1-3K/yr | Transactional email, onboarding sequences, notifications |

### Revenue Model (Phase 1)

| Segment | Pricing | Target Count | Revenue |
|---|---|---|---|
| Power 4 Basketball Programs | $12,000/yr per program | 30 | $360,000 |
| High Major Basketball Programs | $6,000/yr per program | 20 | $120,000 |
| Agent Seats | $200/mo per agent | 10 | $24,000 |
| Affiliate Subscriptions | Free tier (Phase 1 pilot) | 5 | $0 |
| **Total Phase 1 ARR** | | | **$504,000** |

### Partnership Strategy

| Partner Type | Phase 1 Action | Target Partners |
|---|---|---|
| Data Provider | Signed contract, full D1 basketball integration | SportsRadar |
| Social Platforms | API access for social media valuation signals | Instagram, TikTok, X (via third-party aggregators) |
| Brand Networks | Introductory partnerships for deal flow data | 2-3 regional NIL collectives |
| NCAA Relationships | Advisory board participation, compliance alignment | NCAA NIL working groups, conference compliance officers |

### Risk Factors

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Valuation model accuracy insufficient | Medium | High | Validate against 200+ known transactions before launch; continuous retraining loop |
| Power 4 AD sales cycle >6 months | High | Medium | Start with athletic department champions (assistant ADs, GMs); offer 90-day pilot |
| SportsRadar cost escalation | Low | Medium | Negotiate multi-year contract; build caching layer to reduce API calls |
| NCAA policy changes affecting NIL marketplace | Medium | High | Maintain compliance advisory board; build platform flexibility for policy shifts |
| Competitor launches similar product | Medium | Medium | Speed to market; basketball depth as moat; relationship-driven sales |
| Key engineer departure | Medium | High | Competitive comp; equity vesting; document architecture decisions |

### Go/No-Go Criteria for Phase 2

| Criteria | Threshold | Status |
|---|---|---|
| Active paying programs | >= 40 basketball programs | Required |
| ARR | >= $350K | Required |
| Product-market fit (Sean Ellis) | >= 40% "very disappointed" | Required |
| Valuation model accuracy | <20% median error on basketball | Required |
| Net revenue retention | >= 100% | Required |
| AD satisfaction (NPS) | >= 40 | Recommended |
| Agent ecosystem pilot validated | >= 5 active agencies | Recommended |
| Seed/Series A funding secured | >= $2M runway | Required |

---

## Phase 2 -- Basketball Dominance

> **Mission**: Own the basketball NIL intelligence market. Expand to all D1 basketball, build the agent/affiliate ecosystem, deliver March Madness features, and reach $2M ARR.

### Team Composition (15-25 people)

| Team | Roles | Count |
|---|---|---|
| **Executive** | CEO, CTO, CPO (new hire) | 3 |
| **Engineering** | Senior FE (Tech Lead), FE x2, Senior BE (Tech Lead), BE x1, ML Engineer x2, Data Engineer x1, Mobile Engineer x1, DevOps/Infra x1 | 10 |
| **Product & Design** | Product Manager x1, Product Designer x2, UX Researcher x1 | 4 |
| **Sales** | Head of Sales, AE x2, SDR x2, Enterprise AE x1 | 6 |
| **Customer Success** | Head of CS, CSM x2, Support Lead x1 | 4 |
| **Marketing** | Head of Marketing, Content/Marketing Lead, Growth Marketer x1 | 3 |
| **Partnerships** | Head of Partnerships | 1 |
| **Total** | | **~25** (with overlapping exec roles from Phase 1) |

### Key Hires (Phase 1 to Phase 2 Transition)

| Priority | Role | Why Now |
|---|---|---|
| P1 | CPO | Formalize product strategy; enable CEO to focus on fundraising and partnerships |
| P1 | Senior Frontend Engineer (Tech Lead) | Scale frontend architecture; establish engineering standards |
| P1 | Senior Backend Engineer (Tech Lead) | Scale backend architecture; lead Supabase schema evolution |
| P1 | Head of Sales | Scale sales org beyond founder-led selling; build pipeline process |
| P1 | Head of Customer Success | Formalize onboarding playbooks; build retention machine |
| P1 | Mobile Engineer (React Native/Expo) | Launch mobile app for coach/athlete daily usage |
| P2 | SDR x2 | Feed AE pipeline with outbound prospecting |
| P2 | Enterprise AE | Close conference-level and multi-program enterprise deals |
| P2 | Data Engineer | Scale data pipeline for all D1 basketball; prepare for multi-sport |
| P2 | Growth Marketer | Demand generation, content marketing, fan conversion funnel |

### Key Milestones

| Milestone | Target | Measurement |
|---|---|---|
| All Power 4 basketball programs | 60+ of 67 | >90% Power 4 penetration |
| Total D1 basketball programs | 200 | Active paying accounts across Tiers A-C |
| ARR | $2M | Contracted annual revenue |
| Agent ecosystem | 50 agencies, 200+ agent seats | Active paying agent subscriptions |
| Affiliate ecosystem | 20 affiliate firms | Active subscriptions |
| Mobile app launched | iOS + Android | App Store/Play Store live |
| March Madness feature set | Complete tournament intelligence | Money Fight, Conference Value Clash, Seed vs Value, tier boards |
| Transfer portal feature set | Full basketball transfer portal intelligence | Prediction models, pipeline tools, AD/Coach workflows |
| Valuation model accuracy | <15% median error | Against known basketball NIL transactions |

### Infrastructure Investments

| Investment | Cost Estimate | Purpose |
|---|---|---|
| SportsRadar expanded contract | $100-200K/yr | Full D1 basketball + pre-positioning for football data |
| ML infrastructure scaling | $30-60K/yr | Dedicated GPU instances, model versioning, A/B testing framework |
| Mobile infrastructure (Expo EAS) | $5-10K/yr | Build service, OTA updates, app distribution |
| CDN and media storage | $10-20K/yr | Athlete media, team logos, marketing assets |
| Security audit + SOC 2 prep | $30-50K (one-time) | Enterprise sales requirement; compliance foundation |
| Customer success tooling | $10-20K/yr | Health scoring, onboarding automation, NPS tracking |
| CRM (HubSpot/Salesforce) | $15-30K/yr | Sales pipeline management, marketing automation |

### Revenue Model (Phase 2)

| Segment | Pricing | Target Count | Revenue |
|---|---|---|---|
| Power 4 Basketball Programs | $15,000/yr per program | 60 | $900,000 |
| High Major Basketball Programs | $8,000/yr per program | 60 | $480,000 |
| Mid-Major Basketball Programs | $4,000/yr per program | 80 | $320,000 |
| Agent Seats | $250/mo per agent | 200 | $600,000 |
| Affiliate Subscriptions | $150/mo per firm | 20 | $36,000 |
| Athlete Freemium (upsell to premium) | $10/mo premium tier | 500 | $60,000 |
| Enterprise/Conference Deals | $50-100K/yr per deal | 3 | $225,000 |
| **Total Phase 2 ARR** | | | **~$2.6M** |

### Customer Success Scaling

| Metric | Phase 1 | Phase 2 Target |
|---|---|---|
| CSM headcount | 1 | 3 (2 programs + 1 agencies) |
| CSM-to-account ratio (Power 4) | 1:30 | 1:10 |
| CSM-to-account ratio (High Major) | 1:30 | 1:20 |
| CSM-to-account ratio (Mid-Major) | N/A | 1:40 (tech-touch) |
| Onboarding time (Power 4) | Ad hoc | <14 days structured |
| Onboarding time (High/Mid-Major) | Ad hoc | <7 days self-serve + check-in |
| Net revenue retention | Baseline | >= 110% |
| Gross churn | Baseline | <10% annual |
| Support response SLA (Tier 1) | Best effort | <2 hours business hours |

### Technical Scaling

| Area | Phase 1 State | Phase 2 Investment |
|---|---|---|
| Database | Single Supabase project | Read replicas, connection pooling, query optimization |
| Data pipeline | Manual sync triggers | Automated sync server with schedule management, per-stage progress tracking |
| ML models | Single valuation model | Model versioning, A/B testing, automated retraining (weekly cadence) |
| Frontend | Monolithic Next.js app | Component library formalization, code splitting, performance optimization |
| Mobile | Responsive web only | Native React Native/Expo app with offline-first patterns |
| Monitoring | Basic error tracking | Full observability stack (APM, custom dashboards, alerting, on-call rotation) |
| Security | Basic auth + RLS | SOC 2 Type I preparation, security audit, penetration testing |

### Partnership Strategy

| Partner Type | Phase 2 Action | Target |
|---|---|---|
| Data Provider | Expand to include social media analytics partners | SportsRadar (expanded), social analytics vendors |
| Brand Networks | Formal data-sharing partnerships for deal flow validation | 10+ NIL collectives and brand partners |
| Conference Relationships | Conference-level pilot agreements | 2-3 Power 4 conferences |
| Technology Partners | Integration partnerships | CRM integrations, compliance platforms |
| Media | Content partnerships for thought leadership | Sports media outlets, NIL-focused publications |

### Risk Factors

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| March Madness feature delivery delay | Medium | High | Start development 4 months pre-tournament; phased rollout |
| Sales cycle for conference-level deals >9 months | High | Medium | Parallel bottom-up (program) and top-down (conference) sales motions |
| Mobile app quality issues at launch | Medium | Medium | Extended beta with 10 champion programs; phased rollout by tier |
| Agent churn due to limited athlete coverage | Medium | Medium | Prioritize agent-requested athletes for valuation coverage |
| SOC 2 preparation delays enterprise deals | Medium | High | Start process in Phase 2 Month 1; hire compliance consultant |
| Key leadership hire misalignment | Medium | High | Structured interview process; 90-day onboarding plans; advisory board referrals |

### Go/No-Go Criteria for Phase 3

| Criteria | Threshold | Status |
|---|---|---|
| D1 basketball programs | >= 150 | Required |
| ARR | >= $1.5M | Required |
| Basketball valuation model accuracy | <15% median error | Required |
| Net revenue retention | >= 110% | Required |
| Agent ecosystem revenue | >= $300K ARR | Required |
| Mobile app DAU | >= 500 | Recommended |
| March Madness feature set complete | Full tournament intelligence | Required |
| SOC 2 Type I achieved | Certified | Required |
| Series A funding secured | >= $5M | Required |
| Football data partnership signed | SportsRadar football contract | Required |
| Multi-sport valuation model prototype | Football model in validation | Recommended |

---

## Phase 3 -- Multi-Sport Expansion

> **Mission**: Expand from basketball dominance into football, baseball, softball, soccer, and track & field. Build sport-specific valuation models, reach 400+ multi-sport programs, and achieve $10M ARR.

### Team Composition (40-60 people)

| Team | Roles | Count |
|---|---|---|
| **Executive** | CEO, CTO, CPO, CFO (fractional), CHRO (fractional) | 3 + 2 fractional |
| **Engineering Leadership** | VP Engineering, Eng Manager (FE), Eng Manager (BE), Eng Manager (Data/ML) | 4 |
| **Frontend** | Tech Lead, Senior FE x2, FE x4, Mobile x2 | 9 |
| **Backend** | Tech Lead, Senior BE x2, BE x3, API/Integration x1 | 7 |
| **Data & ML** | ML Lead, ML Engineer x3, Data Engineer x3, Data Analyst x2 | 9 |
| **Infrastructure** | DevOps Lead, SRE x2 | 3 |
| **Product & Design** | PM (Basketball), PM (Football), PM (Multi-Sport), Head of Design, Designer x3, UX Researcher x1 | 8 |
| **Sales** | VP Sales, AE (Power 4) x2, AE (High Major) x2, Regional AE x3, Enterprise AE x2, SDR x3 | 13 |
| **Customer Success** | VP CS (Head of CS promoted), CSM x5, Support Lead, Support Specialist x3 | 10 |
| **Marketing** | VP Marketing, Content Lead, Growth Marketer x2, Event Marketing x1 | 5 |
| **Partnerships** | Head of Partnerships, Partnership Manager x2 | 3 |
| **Operations** | Compliance Specialist, Business Ops Analyst, HR Generalist | 3 |
| **Total** | | **~55** |

### Sport Expansion Sequence

| Priority | Sport | Why This Order | Valuation Model Complexity | Conference Coverage Target |
|---|---|---|---|---|
| 1 (existing) | Basketball | Market leader; validated model | Baseline (complete) | All D1 (357 programs) |
| 2 | Football | Highest NIL $ volume; massive market; AD budget overlap | High (large rosters, position-dependent value, CFP) | Power 4 + Group of 5 (133 FBS programs) |
| 3 | Baseball | Strong NIL growth; MLB draft pipeline; regional markets | Medium (pitcher/hitter split, draft stock influence) | Power 4 + top 50 programs (SEC/ACC heavy) |
| 4 | Softball | Rapidly growing NIL market; social media-driven valuations | Medium (social media weight higher than other sports) | Power 4 + top 40 programs |
| 5 | Soccer | Growing NIL market; international appeal; Title IX parity | Medium (international transfer dynamics, gender parity) | Power 4 + top 50 programs |
| 6 | Track & Field | Olympic pipeline; NIL emerging; large roster count | Lower (event-specific, Olympic trial value spikes) | Power 4 + top 30 programs |

### Key Milestones

| Milestone | Target | Measurement |
|---|---|---|
| Basketball programs | 300+ | Maintained dominance across all D1 |
| Football programs onboarded | 80+ | Power 4 + Group of 5 |
| Multi-sport programs | 100+ (baseball, softball, soccer, track) | Active paying accounts |
| Total programs (all sports) | 400+ | Active paying accounts |
| ARR | $10M | Contracted annual revenue |
| Agent ecosystem | 150 agencies, 500+ agent seats | Active paying subscriptions |
| Affiliate ecosystem | 75 affiliate firms | Active paying subscriptions |
| Football valuation model accuracy | <20% median error | Against known football NIL transactions |
| Baseball/Softball valuation models | <25% median error | Initial accuracy targets |
| SOC 2 Type II achieved | Certified | Annual audit passed |
| Series B funding | $15-25M | Secured |

### Infrastructure Investments

| Investment | Cost Estimate | Purpose |
|---|---|---|
| SportsRadar multi-sport contract | $300-500K/yr | Football, baseball, softball, soccer, track data |
| ML infrastructure (dedicated cluster) | $100-200K/yr | Multi-model training, sport-specific pipelines, real-time inference |
| Data warehouse | $50-100K/yr | Cross-sport analytics, reporting, business intelligence |
| Security and compliance | $50-100K/yr | SOC 2 Type II maintenance, penetration testing, compliance tooling |
| Customer success platform | $30-50K/yr | Health scoring, automated playbooks, NPS, ticket management |
| Sales tooling (CRM, enrichment, outreach) | $50-80K/yr | Pipeline management, territory planning, engagement tracking |
| Office / co-working (if hybrid) | $50-100K/yr | Team collaboration space for 40-60 person team |

### Revenue Model (Phase 3)

| Segment | Pricing | Target Count | Revenue |
|---|---|---|---|
| Power 4 Multi-Sport Bundle | $30,000/yr per AD office (all sports) | 50 | $1,500,000 |
| Power 4 Single-Sport (Basketball) | $18,000/yr per program | 15 | $270,000 |
| Power 4 Single-Sport (Football) | $15,000/yr per program | 20 | $300,000 |
| High Major Basketball | $10,000/yr per program | 60 | $600,000 |
| High Major Multi-Sport | $18,000/yr per AD office | 30 | $540,000 |
| Mid-Major Programs | $5,000/yr per program | 120 | $600,000 |
| Football Programs (Group of 5) | $8,000/yr per program | 50 | $400,000 |
| Baseball/Softball Programs | $5,000/yr per program | 80 | $400,000 |
| Soccer/Track Programs | $4,000/yr per program | 50 | $200,000 |
| Agent Seats | $300/mo per agent | 500 | $1,800,000 |
| Affiliate Subscriptions | $200/mo per firm | 75 | $180,000 |
| Athlete Premium | $15/mo | 2,000 | $360,000 |
| Enterprise/Conference Deals | $75-200K/yr per deal | 10 | $1,250,000 |
| Data Licensing (emerging) | Variable | 5 partners | $500,000 |
| **Total Phase 3 ARR** | | | **~$9M-$11M** |

### Customer Success Scaling

| Metric | Phase 2 | Phase 3 Target |
|---|---|---|
| CSM headcount | 3 | 6 (3 basketball + 2 football + 1 multi-sport) |
| CSM-to-account ratio (Power 4) | 1:10 | 1:8 (sport-specific CSMs) |
| CSM-to-account ratio (High Major) | 1:20 | 1:15 |
| CSM-to-account ratio (Mid-Major) | 1:40 | 1:50 (improved tech-touch) |
| Support headcount | 1 | 4 (Lead + 3 specialists) |
| Support hours | Business hours | Extended hours (7am-10pm ET) |
| Onboarding time (new sport) | N/A | <21 days for football; <14 days for other sports |
| Net revenue retention | >= 110% | >= 120% (sport expansion upsells) |

### Technical Scaling

| Area | Phase 2 State | Phase 3 Investment |
|---|---|---|
| Database | Read replicas | Multi-region deployment, sharding strategy for scale |
| Data pipeline | Automated basketball sync | Multi-sport parallel sync pipelines; sport-specific data models |
| ML models | Basketball valuation + prediction | Sport-specific model architectures; transfer learning across sports |
| ML retraining | Weekly | Daily for in-season sports; weekly for offseason; automated quality gates |
| Frontend | Component library | Sport-specific dashboard variants; design system maturity level 3 |
| Mobile | V1 app | V2 with offline-first, push notifications, sport-specific views |
| API | REST + Supabase realtime | GraphQL evaluation for complex cross-sport queries |
| Security | SOC 2 Type I | SOC 2 Type II, annual pen testing, bug bounty program |

### Partnership Strategy

| Partner Type | Phase 3 Action | Target |
|---|---|---|
| Data Providers | Multi-sport data contracts; secondary data sources for validation | SportsRadar (expanded), PFF (football), StatCast-adjacent (baseball) |
| Brand Networks | Formal brand marketplace integration; deal flow data exchange | 50+ brand partners and collectives |
| Conference Relationships | Conference-level enterprise deals; league-wide analytics | 5+ conference partnerships |
| Compliance Platforms | Integration partnerships for compliance workflow | Teamworks, INFLCR, Opendorse |
| Social Analytics | Deep integration for social-media-driven valuations | Social analytics platforms |
| NIL Collectives | Data exchange partnerships; collective management tools | 20+ collectives |

### Risk Factors

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Football valuation model accuracy challenges | High | High | Dedicated football ML team; longer validation period; position-specific models |
| Multi-sport complexity overwhelms engineering | Medium | High | Sequential sport launches (not parallel); shared platform infrastructure |
| Power 4 expansion requires conference-level negotiation | High | Medium | Top-down (commissioner) and bottom-up (AD) dual sales strategy |
| Key talent retention during hypergrowth | Medium | High | Competitive equity refresh; leadership development; remote flexibility |
| NCAA regulatory changes | Medium | High | Compliance specialist hire; policy monitoring; platform adaptability |
| Competitor raises larger round | Medium | Medium | Basketball depth moat; customer loyalty; data advantage |

### Go/No-Go Criteria for Phase 4

| Criteria | Threshold | Status |
|---|---|---|
| Total programs (all sports) | >= 350 | Required |
| ARR | >= $7M | Required |
| Football model live and validated | <20% median error | Required |
| At least 3 sports with active programs | Basketball + Football + 1 other | Required |
| Net revenue retention | >= 115% | Required |
| SOC 2 Type II maintained | Annual renewal | Required |
| Series B secured | >= $15M | Required |
| Enterprise deals closed | >= 5 conference-level deals | Required |
| International market research complete | Market sizing for 2+ international markets | Recommended |
| Professional sports pilot conversations | 3+ professional league/agency conversations | Recommended |

---

## Phase 4 -- Full NCAA + Professional

> **Mission**: Cover all NCAA divisions. Expand into NIL-adjacent professional sports opportunities. Reach $25M+ ARR with a path to $50M+ within 18 months.

### Team Composition (80-120 people)

| Team | Roles | Count |
|---|---|---|
| **Executive / C-Suite** | CEO, CTO, CPO, CFO, CHRO, CLO (General Counsel) | 6 |
| **Engineering** | VP Eng, Directors x3, Eng Managers x5, Senior Engineers x15, Engineers x20, SRE x3 | 47 |
| **Product & Design** | VP Product, PMs x5 (sport-specific + platform), Head of Design, Designers x5, UX Researchers x2 | 13 |
| **Sales** | VP Sales, Directors x2, Enterprise AEs x5, Regional AEs x8, SDRs x5, Sales Ops x2 | 23 |
| **Customer Success** | VP CS, Directors x2, CSMs x10, Support Leads x2, Support Specialists x6 | 21 |
| **Marketing** | VP Marketing, Directors x2, Content x3, Growth x2, Events x2, Brand x1 | 11 |
| **Partnerships** | VP Partnerships, Partnership Managers x3 | 4 |
| **Operations** | Head of Ops, Compliance x2, Business Ops x2, Finance x2, HR x2, Legal x2 | 11 |
| **International** | International GM, Regional leads x2 (Phase 4 late) | 3 |
| **Total** | | **~100-120** |

### Coverage Expansion

| Division | Programs | Pricing Tier | Approach |
|---|---|---|---|
| D1 Power 4 (all sports) | 67 AD offices (~400 sport programs) | Premium ($25-50K/yr per AD office) | High-touch enterprise sales |
| D1 Non-Power 4 (all sports) | ~290 AD offices | Standard ($8-18K/yr per AD office) | Mid-touch + inside sales |
| D2 | ~300 programs | Essentials ($3-5K/yr per program) | Self-serve + tech-touch CS |
| D3 | ~400 programs | Essentials ($2-4K/yr per program) | Self-serve + tech-touch CS |
| NAIA | ~250 programs | Essentials ($2-3K/yr per program) | Self-serve + marketplace |
| Professional NIL adjacency | Agencies, brands, leagues | Custom enterprise | Strategic partnerships |

### Revenue Model (Phase 4)

| Segment | Pricing | Target Count | Revenue |
|---|---|---|---|
| D1 Power 4 Multi-Sport Enterprise | $40,000/yr avg per AD office | 65 | $2,600,000 |
| D1 Non-Power 4 Programs | $10,000/yr avg per AD office | 200 | $2,000,000 |
| D2/D3/NAIA Programs | $3,000/yr avg per program | 400 | $1,200,000 |
| Agent Seats | $350/mo per agent | 1,500 | $6,300,000 |
| Affiliate Subscriptions | $250/mo per firm | 200 | $600,000 |
| Athlete Premium | $20/mo | 10,000 | $2,400,000 |
| Enterprise/Conference Deals | $100-300K/yr per deal | 25 | $5,000,000 |
| Data Licensing | Variable | 15 partners | $2,000,000 |
| Brand Marketplace Fees | Transaction-based | N/A | $1,500,000 |
| Professional Sports Pilots | Custom | 5 | $1,500,000 |
| **Total Phase 4 ARR** | | | **~$25M+** |

### International Expansion Signals

| Signal | Indicator | Action |
|---|---|---|
| International athlete NIL growth | >$100M international NIL transaction volume | Begin market research for UK, Canada, Australia |
| NCAA international recruitment | >20% of D1 basketball players international | Build international scouting integration |
| Brand demand for international | 5+ brands requesting international athlete data | Pilot international valuation models |
| Professional league interest | 3+ professional leagues exploring NIL-adjacent tools | Dedicated international GM hire |

### Infrastructure Investments (Phase 4)

| Investment | Cost Estimate | Purpose |
|---|---|---|
| Multi-region cloud infrastructure | $300-500K/yr | Low-latency serving, data residency compliance |
| Enterprise data platform | $200-400K/yr | Cross-sport analytics, data warehouse, BI tooling |
| ML platform (dedicated) | $200-400K/yr | Multi-sport model management, feature store, inference optimization |
| Security and compliance (enterprise) | $150-300K/yr | SOC 2 Type II, GDPR prep, enterprise security requirements |
| Enterprise sales tooling | $100-200K/yr | CRM, CPQ, contract management, sales intelligence |
| Customer success platform (enterprise) | $100-200K/yr | Account health, QBR automation, renewal management |
| Office infrastructure | $200-400K/yr | Multi-location or expanded headquarters |

### Customer Success Scaling (Phase 4)

| Metric | Phase 3 | Phase 4 Target |
|---|---|---|
| CSM headcount | 6 | 12 (sport-specific + tier-specific) |
| CSM-to-account ratio (Enterprise) | 1:8 | 1:5 (white-glove) |
| CSM-to-account ratio (Standard) | 1:15 | 1:20 (process-driven) |
| CSM-to-account ratio (Essentials/D2/D3) | N/A | 1:100 (fully automated, escalation-only) |
| Support headcount | 4 | 8+ |
| Support hours | Extended | 24/5 (Mon-Fri full coverage) |
| Net revenue retention | >= 120% | >= 130% |
| Gross churn | <8% | <5% |

### Technical Scaling (Phase 4)

| Area | Phase 3 State | Phase 4 Investment |
|---|---|---|
| Database | Multi-region | Global distribution, data partitioning, archive strategy |
| Data pipeline | Multi-sport parallel | Real-time streaming architecture for all sports, all divisions |
| ML models | Sport-specific models | Unified feature store; cross-sport transfer learning; automated model monitoring |
| ML retraining | Daily in-season | Continuous learning pipeline with automated quality gates and rollback |
| API | REST + evaluating GraphQL | API platform with versioning, rate limiting, developer portal for partners |
| Mobile | V2 app | V3 with sport-specific experiences, push intelligence, offline analytics |
| Security | SOC 2 Type II | ISO 27001 evaluation, GDPR compliance for international, enterprise SSO |
| Infrastructure | Multi-region | Global CDN, edge computing for real-time features, disaster recovery |

### Partnership Strategy (Phase 4)

| Partner Type | Phase 4 Action | Target |
|---|---|---|
| Data Providers | All-sport data coverage; international data sources | SportsRadar (all sports), international data providers |
| Professional Leagues | Pilot partnerships for NIL-adjacent analytics | NBA G League, MLS NEXT, MLB Draft League |
| Technology Platform | Deep integrations; potential platform partnerships | Teamworks, INFLCR, compliance platforms, university CRMs |
| Brand Marketplace | Transaction facilitation; marketplace economics | 200+ brands, top NIL collectives nationwide |
| Media | Exclusive data partnerships for editorial content | ESPN, Sports Illustrated, The Athletic, NIL-focused media |
| International | Market entry partnerships | International sports data providers, international agencies |
| Financial Services | NIL financial product partnerships | Banks, financial planners, insurance providers for athletes |

---

## Revenue Growth Trajectory

```
Phase 1 ($500K ARR)
  |
  |  [12 months] -- Prove PMF, basketball beachhead
  |
Phase 2 ($2M ARR)
  |
  |  [12 months] -- Basketball dominance, ecosystem growth
  |
Phase 3 ($10M ARR)
  |
  |  [18 months] -- Multi-sport expansion, enterprise sales
  |
Phase 4 ($25M+ ARR)
  |
  |  [18+ months] -- Full NCAA, professional adjacency
  |
$50M+ ARR runway
```

### Revenue Mix Evolution

| Revenue Source | Phase 1 | Phase 2 | Phase 3 | Phase 4 |
|---|---|---|---|---|
| Program Subscriptions | 95% | 60% | 45% | 25% |
| Agent/Affiliate Seats | 5% | 25% | 20% | 25% |
| Enterprise Deals | 0% | 10% | 15% | 20% |
| Athlete Premium | 0% | 3% | 5% | 10% |
| Data Licensing & Marketplace | 0% | 2% | 15% | 20% |

---

## Cross-Phase Operational Principles

### 1. Basketball Never Gets Deprioritized
As new sports are added, basketball maintains dedicated engineering, product, and CS resources. Basketball is the proof point and the retention anchor.

### 2. Sport Expansion Is Sequential, Not Parallel
Each new sport is launched as a dedicated initiative with its own PM, model validation period, and go/no-go gate. No more than 2 sports are in active launch at any given time.

### 3. Platform Before Features
Shared platform infrastructure (auth, messaging, directories, billing) is built once and reused across sports. Sport-specific features build on top of common primitives.

### 4. Data Accuracy Is Non-Negotiable
Valuation model accuracy for each sport must meet threshold targets before commercial launch. Inaccurate data destroys trust faster than missing data.

### 5. Customer Success Scales Ahead of Sales
CS capacity must be in place before new programs are onboarded. The CSM-to-account ratio is a leading indicator, not a lagging one.

### 6. Revenue Diversification Is a Phase 3+ Priority
Phase 1-2 revenue is subscription-driven. Phase 3+ introduces data licensing, marketplace economics, and professional adjacency. Diversification reduces churn risk and increases enterprise value.

---

## Related Documents

| Document | Location |
|---|---|
| Organizational Structure | `docs/operations/team/org-structure.md` |
| Hiring Plan | `docs/operations/team/hiring-plan.md` |
| Capabilities Matrix | `docs/roles/capabilities-matrix.md` |
| Battle Board Strategy | `docs/operations/battle-board/` |
| Operations Hub README | `docs/operations/README.md` |

---

*NIL Optic -- Performance-first NIL intelligence for every program.*
