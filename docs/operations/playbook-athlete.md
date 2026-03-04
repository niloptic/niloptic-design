# Operations Playbook: Athlete

> Last updated: 2026-03-04

---

## Role Overview

**Who:** College athletes managing their personal NIL brand, evaluating deal offers, tracking their market valuation, and building long-term earning potential through the NIL Optic platform.

**Organization category:** `athletic` (program-scoped)
**Role key:** `athlete`
**Shell route:** `/athlete`

Athletes are the core value unit of the NIL ecosystem. Their on-court performance, social media presence, academic standing, and brand partnerships all contribute to their estimated NIL valuation. NIL Optic gives athletes a private dashboard to understand their worth, track their deals, and make informed decisions about their NIL future -- without relying solely on an agent's word.

### Core Responsibilities

- Monitor and understand personal NIL valuation and drivers
- Review and evaluate incoming deal offers
- Maintain and grow social media presence for brand value
- Track deal milestones and earnings
- Communicate with agent, coach, and Athletic Director
- Understand transfer portal implications on personal valuation
- Build a long-term NIL brand strategy

---

## Daily Operations

**Time allocation:** 15--20 minutes

### Morning Check-in (`9:00 AM`)

| Priority | Action | Screen | Duration |
|---|---|---|---|
| P0 | Check personal NIL valuation -- value and direction | `/athlete` | 3 min |
| P1 | Review any new deal offers or pipeline updates | `/athlete` | 5 min |
| P1 | Check messages from agent, coach, or AD | `/dashboard/messages` | 5 min |
| P2 | Review social media engagement metrics | `/athlete` insights tabs | 5 min |

### Daily KPI Glance

| Metric | Source | Format |
|---|---|---|
| Personal NIL Valuation | `/athlete` top cards | `$XXX.XK` |
| Valuation Change (24h) | `/athlete` trend indicator | `+/- $X.XK` |
| National Rank | `/athlete` rank display | `#XXX` |
| Active Deals | `/athlete` deal section | `#` |
| Unread Messages | `/dashboard/messages` badge | `#` |

### Social Media Content Cadence

```
DAILY CONTENT STRATEGY (Basketball Season):

  Game Day:
    - Pre-game: Warm-up / preparation content (1 post)
    - Post-game: Highlight or team celebration (1 post)
    - Story engagement: Poll, Q&A, or behind-the-scenes (2-3 stories)

  Non-Game Day:
    - Training / lifestyle content (1 post)
    - Brand partner content (if scheduled)
    - Story engagement: Daily life, campus, or interaction (1-2 stories)

  WEEKLY MINIMUM:
    - 4-5 feed posts
    - 10-15 stories
    - 1 brand partner deliverable (if active deal)
```

---

## Weekly Cadence

**Day:** Sunday (review) + Wednesday (planning)

### Sunday: Performance Review

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 10:00 AM | Valuation trend review -- 7-day direction and magnitude | `/athlete` | Athlete solo |
| 10:15 AM | Social media performance check -- follower growth, engagement rate | `/athlete` insights tabs | Athlete solo |
| 10:30 AM | Deal milestone tracking -- any pending actions or deadlines | `/athlete` | Athlete solo |
| 10:45 AM | Game performance reflection -- stat review and valuation correlation | `/athlete` stats table | Athlete solo |

### Wednesday: Forward Planning

| Time | Activity | Screen | Participants |
|---|---|---|---|
| 11:00 AM | Agent check-in -- discuss pipeline, upcoming opportunities | `/dashboard/messages` | Athlete + Agent |
| 11:15 AM | Content calendar review -- plan posts for remaining week | External tools | Athlete solo |
| 11:30 AM | Prediction review -- check valuation forecast direction | `/predictions` | Athlete solo |

### Weekly Report Awareness

Athletes should be aware of these metrics each week:

| Metric | What It Means | Where to Find It |
|---|---|---|
| Valuation 7-Day Trend | Is your NIL value going up or down this week? | `/athlete` valuation panel |
| Social Reach Change | Are you gaining or losing followers? | `/athlete` insights tabs |
| Deal Pipeline Status | Are deals moving forward or stalling? | `/athlete` deal section |
| Team as % of Conference | How does your team rank within the conference? | `/athlete` hierarchy cards |
| Conference as % of Division | How does your conference rank in the division? | `/athlete` hierarchy cards |

---

## Monthly Cadence

**Timing:** First weekend of each month

### Monthly Review

| Task | Description | Screen |
|---|---|---|
| Earnings Summary | Total NIL earnings for the month -- closed deals, payments received | `/athlete` |
| Brand Partnership Performance | Review deliverables completed vs. contracted; check partner satisfaction | `/athlete` |
| Agent Communication | Monthly strategy call with agent -- portfolio direction, new opportunities | `/dashboard/messages` |
| Valuation Trend Analysis | 30-day valuation chart review; identify drivers of movement | `/athlete` valuation/comparison panel |
| Competitive Positioning | Check national rank movement; compare to position peers | `/athlete` |

### Monthly Self-Assessment

```
ATHLETE NIL HEALTH CHECK:

  1. VALUATION: Is my valuation trending up, flat, or down?
     → If down: review game performance + social engagement
     → If flat: identify growth levers (content, visibility, deals)
     → If up: maintain momentum; explore premium deal opportunities

  2. DEALS: Am I maximizing my current deal pipeline?
     → Active deals on track?
     → Any expired/expiring deals to renew?
     → Enough inbound interest to support growth?

  3. BRAND: Is my personal brand strengthening?
     → Follower growth positive?
     → Engagement rate stable or growing?
     → Content quality consistent?

  4. SUPPORT: Am I leveraging my support network?
     → Regular agent communication?
     → Coach aware of NIL activity?
     → AD compliance cleared?
```

---

## Key Screens

| Screen | Route | Primary Use |
|---|---|---|
| Athlete Dashboard | `/athlete` | Personal NIL overview, valuation, hierarchy cards, stats, insights |
| Predictions | `/predictions` | Valuation forecasting and confidence intervals |
| Messages | `/dashboard/messages` | Agent, coach, and AD communication |
| Player Detail | `/athletes/[playerId]` | Full public profile (deep-linked from athlete dashboard when mapping exists) |
| Favorites | `/dashboard/favorites` | Track other athletes and teams of interest |

### Athlete Dashboard Composition

The `/athlete` screen renders in this order:

1. **Section navigation tabs** -- quick jump to dashboard sections
2. **Hierarchy cards** -- Player, Team, Conference, Division with relational scaling context
3. **Support cards** -- Agent assignment + payment schedule
4. **Stats table** -- Game performance data (SportsRadar-backed)
5. **Insights tabs** -- Social reach, engagement, brand performance
6. **Valuation / Comparison panel** -- Current value, trend, peer comparison
7. **Predictor** -- Forward-looking valuation forecast
8. **Opponent Snapshot** -- Upcoming opponent context

### Navigation Context

- Left nav includes: `Favorites`, `Agent Directory`, `Affiliate Directory`
- `Find an Agent` CTA opens `mailto:Support@niloptic.com` when no agent assignment exists
- Top nav shows program context with `Huddles` and `Messages` controls
- Section navigation tabs provide in-page deep-linking
- Direct deep-link to `/athletes/[playerId]` available when player mapping exists

---

## KPIs

### Primary KPIs

| KPI | Definition | Target | Font |
|---|---|---|---|
| Personal NIL Valuation | Estimated NIL value based on performance, social reach, and market factors | Growth trend | `JetBrains Mono` `$XXX.XK` |
| Social Reach | Total followers across all connected social platforms | Growth trend | `JetBrains Mono` `XX.XK` |
| Active Deals | Number of current NIL deals in active status | 2+ for basketball starters | `JetBrains Mono` `#` |
| Total Earnings | Cumulative NIL earnings from all closed deals | Growth YoY | `JetBrains Mono` `$XX.XK` |
| National Rank | Position in national NIL valuation rankings | Top 500 for D1 starters | `JetBrains Mono` `#XXX` |

### Secondary KPIs

| KPI | Definition | Target |
|---|---|---|
| Team Value Contribution | % of team total NIL value attributed to this athlete | Awareness metric |
| Engagement Rate | Social media engagement / impressions ratio | 3%+ |
| Deal Completion Rate | % of offered deals that close successfully | 70%+ |
| Agent Responsiveness | Average response time from agent on deal inquiries | < 24 hours |
| Payment Timeliness | % of deal payments received on schedule | 100% |

---

## Escalation Paths

| Trigger | Severity | Escalation Target | SLA |
|---|---|---|---|
| Valuation drops > 15% in 7 days | MEDIUM | Agent review + strategy adjustment | 48 hours |
| Deal payment overdue > 14 days | HIGH | Agent escalation to brand partner | 24 hours |
| Compliance concern on active deal | CRITICAL | AD + compliance office notification | 4 hours |
| Agent unresponsive > 48 hours | MEDIUM | AD or `Support@niloptic.com` | 48 hours |
| Unauthorized use of name/image/likeness | CRITICAL | Agent + legal counsel | Immediate |
| Platform data not reflecting actual stats | LOW | NIL Optic support | 1 week |

### Escalation Flow

```
LEVEL 1: Athlete Self-Service
  - Check dashboard for valuation context
  - Review deal pipeline status
  - Message agent directly

LEVEL 2: Athlete + Agent
  - Agent investigates deal or valuation issue
  - Agent communicates with brand partner
  - Agent coordinates with AD if needed

LEVEL 3: Athlete + AD / Support
  - AD engages for compliance issues
  - NIL Optic support for platform issues
  - Legal counsel for NIL rights violations
```

---

## Basketball Focus

Basketball athletes represent the highest-value individual NIL opportunities in college sports. The combination of national television exposure, social media virality, and March Madness tournament visibility creates unique valuation dynamics.

### Game Performance Impact on Valuation

| Performance Event | Estimated Valuation Impact | Window |
|---|---|---|
| 20+ point game on national TV | +3--8% valuation lift | 48 hours |
| Game-winning shot / buzzer beater | +5--15% valuation lift | 72 hours |
| Conference Player of the Week | +2--5% valuation lift | 1 week |
| Double-double / triple-double | +3--7% valuation lift | 48 hours |
| Draft stock rising (mock draft inclusion) | +10--25% valuation lift | Sustained |
| Injury (game missed) | -2--5% valuation dip per game | Until return |
| Poor performance / controversy | -5--15% valuation dip | 1--2 weeks |

### Tournament Exposure Windows

```
MARCH MADNESS VALUATION MULTIPLIER:

  First Four:           1.0x baseline (minimal incremental exposure)
  Round of 64:          1.05-1.10x (national audience activated)
  Round of 32:          1.10-1.20x (repeat exposure compounds)
  Sweet 16:             1.20-1.35x (mainstream media coverage)
  Elite 8:              1.35-1.50x (casual fan awareness)
  Final Four:           1.50-2.00x (peak national attention)
  Championship Game:    2.00-3.00x for standout performers

  KEY INSIGHT: Each round compounds the previous lift.
  A player who advances to the Final Four and performs well
  can see 2-3x their pre-tournament valuation within 3 weeks.
```

### Transfer Portal Considerations

| Scenario | Valuation Impact | Action |
|---|---|---|
| Entering portal from mid-major to power conference | +20--40% projected lift | Discuss with agent before entering |
| Entering portal from power conference to power conference | Neutral to +10% | Evaluate program fit and exposure |
| Entering portal from power conference to mid-major | -10--30% projected decline | Carefully evaluate non-NIL factors |
| Receiving multiple offers in portal | +5--15% negotiation leverage | Agent coordinates competitive process |
| Remaining at current program (loyalty signal) | +2--5% stability premium | Communicate commitment publicly |

### Basketball Athlete Content Strategy

| Content Type | Frequency | NIL Impact |
|---|---|---|
| Game highlights | After every game | Direct valuation driver |
| Training footage | 2--3x per week | Engagement and reach builder |
| Campus / lifestyle | 2--3x per week | Brand partnership content foundation |
| Brand partner content | Per contract terms | Direct revenue driver |
| Community engagement | 1--2x per month | Reputation and brand equity builder |
| Behind-the-scenes | 3--5x per week (stories) | Follower growth and retention |

---

## Agent Relationship Management

### If You Have an Agent

| Activity | Frequency | Channel |
|---|---|---|
| Deal status update | Weekly | `/dashboard/messages` |
| Valuation discussion | Bi-weekly | Messages or huddle |
| Strategy session | Monthly | Huddle (video call) |
| Contract review | As needed | Messages + external review |

### If You Do Not Have an Agent

- `Find an Agent` CTA on `/athlete` dashboard routes to `mailto:Support@niloptic.com`
- Browse available agents via `/agent-directory`
- View agent profiles: name, agency, public contact info, represented athletes
- In-app `Message` action available for listed agents in the directory
- NIL Optic support can facilitate introductions to verified agents

---

## Financial Awareness

### Payment Schedule Tracking

The athlete dashboard includes a payment schedule support card showing:

- Upcoming payment dates and amounts
- Payment status: pending, received, overdue
- Total expected earnings for current term
- Historical payment record

### Tax and Wealth Advisory

- Browse affiliated tax and wealth advisors via `/affiliate-directory`
- Filter by category: `Wealth Management`, `Tax`, `Legal`
- Filter by state and city for local advisors
- Affiliate partners can provide NIL-specific tax guidance
- Affiliate communication follows inbound-first messaging policy

---

## Seasonal Calendar

| Month | Focus Area | Key Action |
|---|---|---|
| August | Preseason preparation | Set NIL goals with agent; baseline valuation snapshot |
| September | Early season brand activation | Begin scheduled brand content; social growth push |
| October | Conference play begins | Game performance focus; valuation monitoring |
| November | Non-conference tournaments | Exposure opportunity from MTE appearances |
| December | Finals period | Reduced content; maintain deal compliance |
| January | Conference play intensity | Peak regular-season exposure window |
| February | Tournament positioning | Bracket projection awareness; valuation optimization |
| March | March Madness | Maximum exposure window; active deal management |
| April | Post-season / off-season transition | Close tournament deals; evaluate portal options |
| May | Transfer portal window | Make portal decision if applicable |
| June | Summer training + content | Build brand through summer content; AAU/showcase |
| July | Pre-season preparation | Finalize fall brand partnerships; set goals |

---

## Access and Permissions

| Capability | Allowed |
|---|---|
| View personal NIL valuation and trends | Yes |
| View deal offers and pipeline status | Yes |
| Access stats table (SportsRadar-backed) | Yes |
| Send/receive messages (within program scope) | Yes |
| Access predictions for personal valuation | Yes |
| Browse agent directory | Yes |
| Browse affiliate directory | Yes |
| Manage team roster or budgets | No |
| Create NIL payments | No |
| Access other athletes' private dashboards | No |

---

*NIL Optic -- Know your worth. Own your brand.*
