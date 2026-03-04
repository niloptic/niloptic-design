# TITAN IX: HERALD -- Communication Cadence

Last updated: 2026-03-04

---

## Overview

This document defines the communication rhythm for every NIL Optic persona: when, how, and through which channel each user is contacted. It covers per-persona communication calendars, channel mix strategy, frequency caps, A/B testing frameworks, segmentation strategy, basketball season calendar integration, content personalization rules, opt-out compliance, performance metrics, and escalation triggers.

**Basketball is the #1 priority sport.** All cadence examples, seasonal triggers, and content personalization default to basketball programs, athletes, and conferences.

---

## 1. Per-Persona Communication Calendar

### 1.1 Athletic Director -- Weekly Touchpoints

| Day | Channel | Communication | Content |
|---|---|---|---|
| Monday | Email | Weekly NIL digest | Program valuation summary, compliance status, top movers |
| Monday | In-app | Dashboard insight card refresh | KPI refresh, week-over-week deltas |
| Tuesday | In-app | Compliance digest notification | Pending reviews, upcoming deadlines |
| Wednesday | In-app | Prediction accuracy update | AI prediction performance for program athletes |
| Thursday | In-app | Pipeline activity summary | New deals, stage changes, expired contracts |
| Friday | Push | Week-end summary | "This week: {X} deals moved, {Y}% avg valuation change" |
| 1st of month | Email | Monthly NIL intelligence report | Full month-over-month analysis, QBR prep data |
| Quarterly | Email | QBR prep package | Board-ready slides data, compliance audit summary |

### 1.2 Agent -- Weekly Touchpoints

| Day | Channel | Communication | Content |
|---|---|---|---|
| Monday | Email | Weekly portfolio digest | Client valuation changes, deal pipeline updates |
| Monday | In-app | Portfolio performance card | Week-over-week client performance |
| Tuesday | In-app | Brand matching opportunities | New brand matches for client roster |
| Wednesday | Email | Prediction accuracy update | Prediction model performance for client athletes |
| Thursday | In-app | Deal deadline reminders | Contracts expiring within 14 days |
| Friday | In-app | New prospect alerts | Unsigned athletes matching client profile |
| 1st of month | Email | Monthly portfolio report | Complete client performance analysis |

### 1.3 Athlete -- Weekly Touchpoints

| Day | Channel | Communication | Content |
|---|---|---|---|
| Monday | Push | Weekly valuation update | "Your NIL value this week: ${Value} ({Direction} {X}%)" |
| Wednesday | In-app | Social media impact score | How social engagement affected valuation |
| Friday | In-app | Deal opportunity digest | New matching opportunities, pending deals |
| As needed | Push | Deal status change | Immediate notification on deal stage changes |
| As needed | Push | Valuation spike/drop | Alert when valuation changes > 10% in 24h |
| Monthly | Email | Monthly value report | Valuation trend, social growth, deal summary |

### 1.4 Coach -- Weekly Touchpoints

| Day | Channel | Communication | Content |
|---|---|---|---|
| Monday | Email | Weekly team NIL digest | Team valuation leaderboard, roster changes |
| Tuesday | In-app | Recruiting pipeline update | New prospects, commitment predictions |
| Thursday | In-app | Team compliance summary | Program compliance rate, pending reviews |
| As needed | In-app | Roster change notifications | Athletes added/removed, portal entries |
| 1st of month | Email | Monthly team report | Team valuation trends, recruiting impact |

### 1.5 Fan -- Weekly Touchpoints

| Day | Channel | Communication | Content |
|---|---|---|---|
| Monday | Email | Weekly NIL rankings | Top 10 athletes by valuation, biggest movers |
| Wednesday | In-app | Roster Builder suggestion | "Athletes you might want to follow" |
| Saturday | Push | Game day valuation preview | Pre-game NIL implications for followed teams |
| As needed | Push | Tournament updates | March Madness results, bracket impact |
| Monthly | Email | Monthly NIL market recap | Market trends, top stories, new features |

### 1.6 Affiliate -- Weekly Touchpoints

| Day | Channel | Communication | Content |
|---|---|---|---|
| Monday | Email | Weekly activity digest | Client matches, directory visibility stats |
| Wednesday | In-app | New client match notification | Athletes/programs seeking affiliate services |
| Friday | In-app | Service catalog performance | View counts, inquiry stats for listed services |
| Monthly | Email | Monthly affiliate report | Client pipeline, revenue impact, marketplace trends |

### 1.7 Agency Admin -- Weekly Touchpoints

| Day | Channel | Communication | Content |
|---|---|---|---|
| Monday | Email | Weekly agency digest | Firm-wide deal pipeline, agent performance, compliance |
| Tuesday | In-app | Agent activity summary | Per-agent deal counts, client engagement |
| Thursday | In-app | Compliance overview | Firm-wide compliance rate, flagged deals |
| 1st of month | Email | Monthly agency report | Revenue summary, client growth, prediction accuracy |
| Quarterly | Email | QBR package | Firm performance, competitive positioning |

### 1.8 Affiliate Admin -- Weekly Touchpoints

| Day | Channel | Communication | Content |
|---|---|---|---|
| Monday | Email | Weekly network digest | Affiliate activity, client matches, revenue |
| Wednesday | In-app | Network performance | Top-performing affiliates, new inquiries |
| 1st of month | Email | Monthly network report | Revenue rollup, affiliate growth, market trends |

---

## 2. Channel Mix Strategy

### 2.1 Channel Selection Matrix

| Signal Type | Email | In-App | Push | SMS (Future) |
|---|---|---|---|---|
| Transactional (account/billing) | Primary | Secondary | -- | -- |
| Onboarding drip | Primary | -- | -- | -- |
| Deal stage change | Secondary | Primary | High-priority only | -- |
| Valuation change (> 10%) | If opted in | Primary | High-priority only | -- |
| New message | -- | Primary | If enabled | -- |
| Compliance alert | If opted in | Primary | Always (Critical) | Future: Critical only |
| Tournament update | If opted in | Primary | If enabled | -- |
| Transfer portal | If opted in | Primary | If enabled | -- |
| Weekly digest | Primary | Secondary (card) | -- | -- |
| Monthly report | Primary | -- | -- | -- |
| Re-engagement | Primary | -- | -- | Future: 30d+ |
| System announcement | -- | Primary | -- | -- |

### 2.2 Channel Priority Rules

1. **Email** -- Best for: digest content, reports, long-form updates, re-engagement, onboarding sequences. Not for: real-time alerts, chat-like updates.
2. **In-app** -- Best for: real-time events, actionable alerts, contextual updates users see during active sessions. Always-on for logged-in users.
3. **Push** -- Best for: time-sensitive events when user is not in-app. Requires explicit opt-in. Reserved for High and Critical priority.
4. **SMS** (future roadmap) -- Reserved for: Critical compliance violations, payment failures, account security. Requires separate consent under TCPA.

### 2.3 Channel Escalation

When a notification is not acted upon within a time window, escalate to the next channel:

| Initial Channel | Escalation Channel | Escalation Window | Conditions |
|---|---|---|---|
| In-app | Push | 2 hours | User not active in-app; notification is High priority |
| In-app | Email | 24 hours | User not active in-app; notification is High priority; push not enabled |
| Push | Email | 4 hours | Push delivered but not tapped; notification is Critical |
| Email (drip) | In-app banner | Next login | User did not open email; show contextual banner on next visit |

---

## 3. Frequency Caps

### 3.1 Global Frequency Caps

| Channel | Cap | Scope | Exceptions |
|---|---|---|---|
| Email (marketing) | Max 1 per day | Per user | Transactional emails (welcome, verify, reset, billing) are exempt |
| Email (total) | Max 3 per day | Per user | Includes transactional; hard cap to prevent inbox flooding |
| Push | Max 5 per day | Per user | Critical compliance alerts exempt |
| In-app | No daily cap | Per user | Batching rules apply (see 3.3) |
| SMS (future) | Max 2 per week | Per user | Critical only |

### 3.2 Per-Category Frequency Caps

| Category | Email Max | Push Max | In-App Max | Notes |
|---|---|---|---|---|
| Deals | 5/day | 5/day | No cap | Batch if > 5 same-hour |
| Valuations | 3/day | 3/day | No cap | Batch multiple athletes into single alert |
| Messages | 0 (no email for messages) | 10/day | No cap | Push only if not active in-app |
| Compliance | No cap (critical exempt) | No cap | No cap | Never suppressed, never batched |
| Tournaments | 2/round | 3/day | No cap | Batch multiple games per round |
| Transfer Portal | 2/day | 3/day | No cap | Batch multiple entries |
| Predictions | 1/week | 0 | 1/day | Low priority, easily suppressed |
| System | 1/day | 1/day | No cap | Maintenance and releases only |

### 3.3 Batching Rules

| Condition | Batching Behavior |
|---|---|
| > 3 same-category notifications in 1 hour | Batch into summary notification |
| > 5 valuation alerts in 1 day | Combine into "Daily valuation summary" email |
| > 3 deal stage changes in 1 hour | Single "Pipeline activity" notification |
| > 5 tournament results pending | Batch into "Round summary" notification |
| User is inactive (not in-app for 4+ hours) | Queue and deliver as batch on next session |

### 3.4 Conflict Resolution

When multiple communications compete for the same send slot:

| Priority | Communication Type | Rule |
|---|---|---|
| 1 (highest) | Transactional email | Always sends immediately, no deferral |
| 2 | Critical notification | Always sends, bypasses all caps |
| 3 | High-priority notification | Sends if within daily cap |
| 4 | Engagement email (digest, report) | Deferred if user already received marketing email today |
| 5 | Onboarding drip | Deferred by 24h if higher-priority email sent today |
| 6 (lowest) | Re-engagement email | Deferred if any other email sent in last 48h |

---

## 4. A/B Testing Framework

### 4.1 Subject Line Testing

| Parameter | Standard |
|---|---|
| Minimum sample size | 1,000 recipients per variant |
| Maximum variants | 3 (A, B, C) |
| Holdout group | 10% of audience receives control (no email) for baseline measurement |
| Test duration | 4 hours from first send before declaring winner |
| Winner criteria | Primary: open rate. Secondary: click-through rate. |
| Statistical significance | 95% confidence interval required |
| Rollout | Winner automatically sent to remaining audience after test window |

### 4.2 Send Time Optimization

| Parameter | Standard |
|---|---|
| Initial send window | 8:00 AM ET (default for all new users) |
| Optimization period | After 4 weeks of engagement data, per-user send time optimization activates |
| Optimization algorithm | Best open-rate hour from user's last 10 opened emails |
| Fallback | If insufficient data, use role-default time (AD: 8 AM, Athlete: 12 PM, Fan: 6 PM) |
| Time zone handling | All send times converted to user's local time zone |

**Role-default send times:**

| Role | Default Send Time (Local) | Rationale |
|---|---|---|
| Athletic Director | 8:00 AM | Start of business day, before meetings |
| Agent | 8:30 AM | Morning pipeline review time |
| Athlete | 12:00 PM | Between classes/practice |
| Coach | 7:30 AM | Pre-practice morning review |
| Fan | 6:00 PM | After work/school, leisure browsing |
| Affiliate | 9:00 AM | Standard business hours |

### 4.3 Content Variant Testing

| Parameter | Standard |
|---|---|
| Test scope | CTA text, hero image, content block order, personalization depth |
| Minimum sample | 500 recipients per variant |
| Test duration | 24 hours for click-through tests; 7 days for conversion tests |
| Winner criteria | Click-through rate (CTA tests); conversion to target action (content tests) |
| Max concurrent content tests | 1 per email template to avoid interaction effects |

### 4.4 Testing Calendar

| Month | Test Focus | Email Type | Metric |
|---|---|---|---|
| January | Send time optimization | Weekly digest | Open rate by hour |
| February | Subject line personalization | Re-engagement (7d) | Open rate |
| March | Tournament content framing | March Madness bracket preview | Click-through |
| April | CTA copy testing | Onboarding drip (all personas) | Conversion to target action |
| May | Content block ordering | Monthly report | Time on page |
| June | Personalization depth | Weekly digest | Click-through |
| July | Re-engagement sequence length | Win-back (30d) | Return rate |
| August | Pre-season subject lines | Pre-season preview | Open rate |
| September | Onboarding drip timing | Drip sequence (all personas) | Step completion |
| October | Deal alert formatting | Deal milestone | Click-through |
| November | Signing day content | Signing day reminder | Click-through |
| December | Portal window urgency framing | Transfer portal alerts | Click-through |

---

## 5. Segmentation Strategy

### 5.1 Primary Segmentation Axes

| Axis | Segments | Source |
|---|---|---|
| Role | AD, Agent, Athlete, Coach, Fan, Affiliate, Agency Admin, Affiliate Admin, Asst AD, GM, Admin, Designer | User profile |
| Sport | Basketball (primary), Football, Baseball, Soccer, Track, Swimming, Other | Program association |
| Engagement level | Power User, Active, Casual, At-Risk, Churned | Activity scoring model |
| Program tier | Power 4 (ACC, Big Ten, Big 12, SEC), Group of 5, Mid-Major, D-II, D-III | Organization metadata |
| Plan tier | Enterprise, Professional, Starter, Free/Fan | Billing record |
| Onboarding status | Complete, In-Progress, Not Started | Onboarding progress |
| Basketball season phase | Pre-season, Regular, Conference Tourney, March Madness, Off-season | Calendar |

### 5.2 Engagement Level Definitions

| Level | Definition | Scoring Criteria | Communication Treatment |
|---|---|---|---|
| Power User | Highly active, daily usage, multi-feature adoption | 5+ logins/week, 3+ features used, 10+ actions/week | Reduced email (they already know); push for real-time only; early access offers |
| Active | Regular usage, consistent engagement | 2-4 logins/week, 2+ features used | Standard cadence; full digest content; feature tips in digest |
| Casual | Sporadic usage, limited feature adoption | 1-3 logins/month, 1 feature primarily | Highlight underused features; nudge toward activation; simplified digest |
| At-Risk | Declining activity, may churn | Declining login frequency over 3 weeks; no login in 7+ days | Re-engagement sequence triggered; CS team alerted; personalized outreach |
| Churned | No activity for 30+ days | No login in 30+ days; no email engagement in 14+ days | Win-back sequence; 60-day final attempt; then suppress |

### 5.3 Program Tier Segmentation

| Tier | Programs | Communication Differences |
|---|---|---|
| Power 4 | SEC, Big Ten, Big 12, ACC | Full feature content; enterprise-level reporting; conference-specific tournament content; highest-value deal examples |
| Group of 5 | AAC, Mountain West, Sun Belt, MAC, C-USA | Growth-focused content; "competing with Power 4" framing; budget optimization tips |
| Mid-Major | All other D-I conferences | Value proposition content; cost-efficiency framing; "hidden gem" athlete stories |
| D-II | Division II programs | Simplified feature set content; eligibility-aware messaging; smaller deal examples |
| D-III | Division III programs | Non-scholarship context; passion-sport framing; community-brand partnerships |

### 5.4 Sport-Specific Segmentation

| Segment | Content Priority | Seasonal Triggers | Example Personalization |
|---|---|---|---|
| Basketball (primary) | NCAA tournament, conference tournaments, transfer portal, signing days | Nov--Apr peak, year-round portal | "Your basketball program's NIL value is up 12% since Selection Sunday" |
| Football | CFP, bowl season, spring practice, recruiting | Aug--Jan peak | "Football NIL valuations surge after CFP semifinal" |
| Baseball | College World Series, draft window | Feb--Jun peak | "CWS projections: your athletes' draft stock and NIL impact" |
| Multi-sport | Cross-sport comparisons, program-wide metrics | Year-round | "Across all sports, your program's total NIL value is ${Total}" |

---

## 6. Basketball Season Calendar Integration

### 6.1 Season Phase Communication Map

| Phase | Dates | Communication Intensity | Key Triggers | Channel Mix |
|---|---|---|---|---|
| Pre-season | Aug 1 -- Oct 31 | Low | Roster finalization, preseason rankings, media day | Email: 1/week. Push: rankings only. In-app: standard. |
| Early season | Nov 1 -- Dec 31 | Medium | Season openers, early tournament results, Maui/Battle 4 Atlantis, winter portal window (Dec 4--28) | Email: 1/week + portal alerts. Push: game results + portal. In-app: elevated. |
| Conference play | Jan 1 -- Feb 28 | Medium-High | Rivalry games, mid-season valuations, conference standings impact | Email: 1/week + valuation alerts. Push: rivalry results. In-app: elevated. |
| Conference tournaments | Mar 1 -- Mar 15 | High | Game-by-game results, auto-bid implications, bubble watch | Email: daily during conference tourney week. Push: every game result. In-app: maximum. |
| Selection Sunday | Mar 15 (approx) | Very High | Bracket reveal, seed reactions, first four matchups | Email: bracket preview within 2h. Push: bracket notification. In-app: bracket dashboard live. |
| March Madness | Mar 16 -- Apr 7 | Maximum | Round-by-round results, Cinderella stories, valuation surges, upset alerts | Email: post-round summaries. Push: every game result for followed teams. In-app: real-time. |
| Spring portal window | Apr 15 -- Apr 30 | High | Portal entries, commitments, destination predictions | Email: daily portal digest. Push: entries for followed programs. In-app: portal dashboard. |
| Late signing period | Apr 15 -- May 15 | Medium | Commitment announcements, class rankings | Email: signing alerts. Push: commitments. In-app: recruiting updates. |
| Off-season | May 1 -- Jul 31 | Low | Summer workout valuations, early portal entries, schedule releases | Email: 2/month. Push: major moves only. In-app: standard. |

### 6.2 March Madness Communication Escalation

During the NCAA Tournament (approximately Mar 16 -- Apr 7), communication frequency increases significantly:

| Round | Email Cadence | Push Cadence | In-App Cadence | Special Content |
|---|---|---|---|---|
| First Four | 1 email post-results | Per-game for followed teams | Real-time | "First Four results: NIL implications" |
| Round of 64 | 1 email post-day (2 days) | Per-game for followed teams | Real-time | "Day 1/Day 2 results: biggest NIL movers" |
| Round of 32 | 1 email post-day (2 days) | Per-game for followed teams | Real-time | "Second round: who's surging, who's fading" |
| Sweet 16 | 1 email post-round | Per-game + surge alerts | Real-time | "Sweet 16 valuations: the $1M+ athletes" |
| Elite 8 | 1 email post-round | Per-game + surge alerts | Real-time | "Elite 8: Final Four contenders and NIL impact" |
| Final Four | 1 email post-semifinal | All games | Real-time | "Final Four: peak NIL valuation window" |
| Championship | 1 email post-championship | Championship game | Real-time | "National champion crowned: NIL market impact" |

### 6.3 Key Basketball Calendar Dates (2026-27 Reference)

| Date | Event | Communication Trigger |
|---|---|---|
| Aug 1 | Pre-season practice begins | Pre-season preview email |
| Oct 15 | Media days begin | Preseason rankings notification |
| Nov 4 | Regular season tipoff | Season opener valuation snapshot |
| Nov 10 | Early signing period opens | Signing day -7d reminder |
| Nov 17 | Early signing period closes | Signing day wrap-up |
| Dec 4 | Winter transfer portal opens | Portal open alert |
| Dec 28 | Winter transfer portal closes | Portal close -48h alert |
| Mar 3 | Conference tournaments begin | Conference tourney kickoff emails (per conference) |
| Mar 15 | Selection Sunday | Bracket preview email |
| Mar 18 | First Four | Tournament results email |
| Mar 20-21 | Round of 64 | Daily results email |
| Mar 22-23 | Round of 32 | Daily results email |
| Mar 27-28 | Sweet 16 | Round results email |
| Mar 29-30 | Elite 8 | Round results email |
| Apr 5 | Final Four | Semifinal results email |
| Apr 7 | National Championship | Championship recap email |
| Apr 15 | Spring transfer portal opens | Portal open alert |
| Apr 30 | Spring transfer portal closes | Portal close -48h alert |
| Apr 15 | Late signing period opens | Signing day -7d reminder |
| May 15 | Late signing period closes | Signing day wrap-up |

---

## 7. Content Personalization Rules

### 7.1 Dynamic Content Block Rules

Every marketing email contains dynamic content blocks that render based on user attributes. The following rules govern what content appears for each user.

| Content Block | Personalization Source | Fallback (No Data) |
|---|---|---|
| Athlete valuation highlight | User's followed/managed athletes sorted by absolute valuation change | Top 3 athletes by valuation in user's conference |
| Deal pipeline summary | User's active deals (own or managed) sorted by stage recency | "No active deals -- explore the pipeline" CTA |
| Compliance status | User's program compliance rate and pending reviews | Hidden (only shown for AD, Agent, Coach, Agency Admin) |
| Tournament impact | Valuation changes for user's athletes/teams in active tournament | Conference tournament results if no direct athletes |
| Social media score | Athlete's social engagement metrics (Athlete role only) | "Connect your socials to track impact" CTA |
| Prediction highlight | Most interesting prediction for user's scope | Hidden if no predictions available |
| Upgrade prompt | Current plan limitations vs. next tier benefits (Fan, Starter only) | Hidden for Enterprise/Professional plans |

### 7.2 Subject Line Personalization

| Token | Source | Example Output |
|---|---|---|
| `{FirstName}` | User profile | `"Marcus"` |
| `{OrgName}` | Organization membership | `"University of Kentucky"` |
| `{ProgramName}` | Program association | `"UK Men's Basketball"` |
| `{AthleteName}` | Target athlete of notification | `"K. Williams"` |
| `{BrandName}` | Deal brand | `"Nike"` |
| `{ValuationDelta}` | Percentage change | `"+12.4%"` |
| `{DealAmount}` | Deal value | `"$25K"` |
| `{ConferenceName}` | Conference association | `"SEC"` |
| `{TeamName}` | Team/school name | `"Kentucky"` |
| `{AthleteCount}` | Number of athletes in scope | `"47"` |
| `{ClientCount}` | Number of clients (Agent) | `"12"` |
| `{Quarter}` | Current fiscal quarter | `"Q1"` |
| `{WeekDateRange}` | Monday-Sunday of digest week | `"Feb 24 -- Mar 2"` |
| `{MonthName}` | Full month name | `"March"` |

### 7.3 Preheader Personalization

Preheaders are dynamically generated to complement the subject line. Rules:

| Rule | Implementation |
|---|---|
| Max length | 90 characters |
| Must not repeat subject line | Content must differ from subject |
| Include one data point | At least one personalized metric or name |
| Basketball-first | Reference basketball context when applicable |
| Fallback | Generic brand-voice preheader if no personalization data available |

### 7.4 Content Block Ordering by Role

| Position | AD | Agent | Athlete | Coach | Fan |
|---|---|---|---|---|---|
| Block 1 (hero) | Program valuation summary | Portfolio performance | Personal valuation | Team valuation | Top athletes ranking |
| Block 2 | Compliance snapshot | Deal pipeline updates | Deal opportunities | Recruiting pipeline | Biggest movers |
| Block 3 | Top mover athletes | Brand matching | Social media impact | Compliance summary | Tournament impact |
| Block 4 | Prediction highlight | Prediction accuracy | Growth tips | Calendar events | Upgrade prompt |
| Block 5 | Calendar/deadlines | Portfolio report link | Connect socials CTA | Team messaging | Follow athletes CTA |

---

## 8. Opt-Out and Compliance

### 8.1 CAN-SPAM Compliance

| Requirement | NIL Optic Implementation |
|---|---|
| Sender identification | Every email includes "NIL Optic" in From name; physical address in footer |
| Subject line accuracy | No deceptive subject lines; subject must reflect content |
| Opt-out mechanism | One-click unsubscribe via `List-Unsubscribe` header + footer link |
| Opt-out processing | Processed within 10 minutes (target: immediate via SendGrid suppression) |
| Transactional exemption | Welcome, verification, password reset, billing are transactional; exempt from unsubscribe |
| Honoring opt-out | Once unsubscribed, user receives zero marketing emails until they re-subscribe |

### 8.2 Unsubscribe Management

| Unsubscribe Level | Scope | Processing |
|---|---|---|
| Per-category | Unsubscribes from one email category (e.g., "Weekly Digest") | Category suppressed; all other categories continue |
| All marketing | Unsubscribes from all marketing/engagement emails | All non-transactional emails suppressed |
| Global | Requests complete email cessation | All emails suppressed including engagement; transactional still sent for legal/account reasons |

### 8.3 Preference Center Design

```
┌──────────────────────────────────────────────────────────────────┐
│  EMAIL PREFERENCES                                               │
│  ────────────────────────────────────────────────────────────── │
│                                                                  │
│  Manage what emails you receive from NIL Optic.                  │
│                                                                  │
│  REPORTS & DIGESTS                                               │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │  Weekly NIL Digest          [*━━━━━━━━━━━] On               ││
│  │  Monthly Intelligence Report [*━━━━━━━━━━━] On              ││
│  │  Prediction Accuracy Update  [━━━━━━━━━━━*] Off             ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ALERTS                                                          │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │  Valuation Change Alerts    [*━━━━━━━━━━━] On               ││
│  │  Deal Milestone Emails      [*━━━━━━━━━━━] On               ││
│  │  Compliance Alerts (email)  [*━━━━━━━━━━━] On               ││
│  │  Transfer Portal Alerts     [━━━━━━━━━━━*] Off              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  BASKETBALL                                                      │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │  March Madness Alerts       [*━━━━━━━━━━━] On               ││
│  │  Conference Tournament      [*━━━━━━━━━━━] On               ││
│  │  Transfer Portal Windows    [*━━━━━━━━━━━] On               ││
│  │  Signing Day Reminders      [━━━━━━━━━━━*] Off              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ONBOARDING & TIPS                                               │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │  Onboarding Sequence        [*━━━━━━━━━━━] On               ││
│  │  Re-engagement Emails       [*━━━━━━━━━━━] On               ││
│  │  Feature Announcements      [━━━━━━━━━━━*] Off              ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                  │
│  ────────────────────────────────────────────────────────────── │
│                                                                  │
│  [Unsubscribe from all marketing emails]                         │
│  This will not affect account-related emails                     │
│  (billing, security, verification).                              │
│                                                                  │
│  [Save Preferences]                                              │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### 8.4 GDPR Considerations

| Requirement | Implementation |
|---|---|
| Consent basis (marketing) | Explicit opt-in during account creation; granular consent per category |
| Consent basis (transactional) | Legitimate interest (contractual obligation) |
| Right to access | User can view all email preferences and send history in Preference Center |
| Right to erasure | Account deletion removes all email preferences, suppression lists, and send logs |
| Data portability | Email preferences included in data export (see `admin-data-export-001`) |
| Processing records | All sends logged: timestamp, template ID, consent basis, suppression status |
| Cross-border data transfer | SendGrid data processing agreement covers EU-US data transfers |

---

## 9. Metrics and KPIs

### 9.1 Email Performance Targets

| Email Type | Open Rate Target | Click-Through Target | Unsubscribe Cap | Spam Complaint Cap |
|---|---|---|---|---|
| Transactional (welcome, verify) | > 80% | > 60% | N/A (no unsub) | < 0.01% |
| Onboarding drip | > 50% | > 25% | < 1% per send | < 0.05% |
| Weekly digest | > 35% | > 12% | < 0.3% per send | < 0.05% |
| Monthly report | > 45% | > 25% | < 0.2% per send | < 0.03% |
| Valuation alert | > 50% | > 30% | < 0.2% per send | < 0.03% |
| Deal milestone | > 55% | > 40% | < 0.1% per send | < 0.02% |
| Re-engagement (7d) | > 25% | > 10% | < 2% per send | < 0.1% |
| Re-engagement (14d) | > 20% | > 8% | < 2% per send | < 0.1% |
| Re-engagement (30d) | > 15% | > 5% | < 3% per send | < 0.15% |
| Re-engagement (60d) | > 10% | > 3% | < 5% per send | < 0.2% |
| Basketball-specific | > 50% | > 30% | < 0.2% per send | < 0.03% |

### 9.2 Notification Engagement Targets

| Metric | Target | Measurement |
|---|---|---|
| In-app notification click rate | > 35% | Notifications clicked / notifications delivered |
| In-app notification read rate | > 70% | Notifications read (viewed) / delivered |
| Push notification tap rate | > 12% | Push tapped / push delivered |
| Push opt-in rate | > 65% | Users who enable push / users prompted |
| Notification drawer open rate | > 3x per active session | Drawer opens / active sessions |
| Time to first notification action | < 2 minutes | Time from notification delivery to click |
| Notification preference change rate | < 5% per month | Users modifying preferences / total users |
| Quiet hours adoption | > 25% | Users who enable quiet hours / push-enabled users |

### 9.3 Composite Health Metrics

| Metric | Formula | Healthy Range | Alert Threshold |
|---|---|---|---|
| Email deliverability rate | Delivered / Sent | > 98% | < 95% triggers investigation |
| Email engagement score | (Open rate x 0.5) + (Click rate x 0.3) + (1 - Unsub rate x 0.2) | > 0.30 | < 0.20 triggers review |
| Notification fatigue index | Dismiss rate + Mute rate over trailing 7 days | < 15% | > 25% triggers frequency reduction |
| Channel coverage | Users reachable via 2+ channels / Total users | > 80% | < 60% triggers push opt-in campaign |
| Communication ROI | Feature activation from email/notification / Total sends | > 5% | < 2% triggers content audit |

### 9.4 Reporting Cadence

| Report | Frequency | Audience | Content |
|---|---|---|---|
| Daily email dashboard | Daily | Marketing + CS | Deliverability, open rates, complaints, bounces |
| Weekly engagement report | Weekly (Monday) | Product + Marketing | Per-email performance, A/B test results, notification engagement |
| Monthly communication review | Monthly (1st) | Leadership + Product + Marketing | Trends, segmentation performance, churn correlation |
| Quarterly optimization review | Quarterly | All stakeholders | Full audit, cadence adjustments, content strategy shifts |

---

## 10. Escalation Triggers

### 10.1 At-Risk User Identification

| Signal | Definition | Trigger | Action |
|---|---|---|---|
| Declining login frequency | Logins decreased 50%+ week-over-week for 2 consecutive weeks | Automatic | Move user to "At-Risk" segment; trigger re-engagement sequence |
| Email non-engagement | User has not opened any email in 14+ days | Automatic | Flag for CS review; adjust send frequency down |
| Notification ignore | User has 20+ unread notifications with 0 actions in 7 days | Automatic | Trigger in-app "catch up" prompt; reduce push frequency |
| Feature abandonment | User stopped using a feature they previously used 3+ times/week | Automatic | Trigger feature-specific re-engagement email |
| Deal pipeline stagnation | No deal stage changes for user's scope in 21+ days | Automatic | Send "pipeline checkup" email; flag for CS if paid user |

### 10.2 CS Team Handoff Triggers

| Trigger | User Segment | Handoff Method | SLA |
|---|---|---|---|
| At-Risk user + paid plan | Enterprise, Professional | Automated Slack notification to CS team + CRM task | CS contact within 24 hours |
| 30-day inactive + paid plan | Professional, Starter | CRM task for CS rep; include usage summary | CS outreach within 48 hours |
| 60-day inactive + paid plan | All paid | CRM task flagged "churn risk"; include full history | CS outreach within 24 hours; manager escalation if no response in 72h |
| Repeated payment failure (3+ attempts) | All paid | Automated CS alert + billing team cc | CS call/email same business day |
| Compliance alert unresolved 7+ days | AD, Agent | CS notification + compliance team cc | CS contact within 12 hours |
| User downgrade request | All paid | CS retention workflow triggered | CS contact before downgrade processes |
| Negative feedback survey (score < 3/10) | All | CRM task flagged "urgent feedback" | CS contact within 4 hours |

### 10.3 Escalation Workflow

```
┌──────────────────────────────────────────────────────┐
│                                                      │
│  USER ACTIVITY SIGNAL                                │
│       │                                              │
│       ▼                                              │
│  ┌────────────┐                                      │
│  │ Engagement │                                      │
│  │ Scoring    │ ← Daily recalculation                │
│  │ Engine     │                                      │
│  └─────┬──────┘                                      │
│        │                                              │
│        ├── Score > 70 ──→ Active (standard cadence)  │
│        │                                              │
│        ├── Score 40-70 ──→ Casual (reduced cadence,  │
│        │                    feature nudges)           │
│        │                                              │
│        ├── Score 20-40 ──→ At-Risk (re-engagement    │
│        │                    triggered, CS alerted     │
│        │                    for paid users)           │
│        │                                              │
│        └── Score < 20 ──→ Churned (win-back sequence,│
│                            CS priority outreach for  │
│                            paid users, suppress low-  │
│                            priority communications)  │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### 10.4 Engagement Scoring Model

| Factor | Weight | Data Source | Scoring |
|---|---|---|---|
| Login frequency (trailing 14 days) | 30% | Auth logs | Daily = 100, 4-5x/week = 80, 2-3x = 60, 1x = 30, 0 = 0 |
| Feature breadth (trailing 14 days) | 20% | Event tracking | 5+ features = 100, 3-4 = 70, 2 = 50, 1 = 25, 0 = 0 |
| Notification engagement (trailing 7 days) | 15% | Notification analytics | > 50% clicked = 100, 30-50% = 70, 10-30% = 40, < 10% = 10 |
| Email engagement (trailing 30 days) | 15% | SendGrid events | > 50% opened = 100, 30-50% = 70, 10-30% = 40, < 10% = 10 |
| Deal/pipeline activity (trailing 14 days) | 10% | Pipeline events | Active deals moving = 100, stagnant = 30, no deals = 0 |
| Messaging activity (trailing 7 days) | 10% | Message events | Sent 5+ messages = 100, 1-4 = 60, 0 = 0 |

---

## 11. Communication Suppression Rules

### 11.1 Automatic Suppression Events

| Event | Suppressed Communications | Duration |
|---|---|---|
| User marks email as spam | All marketing emails for that user | Permanent until user re-subscribes via Preference Center |
| Hard bounce | All emails to that address | Permanent (email address invalid) |
| 3 consecutive soft bounces | All emails to that address | 30-day pause; retry after |
| User unsubscribes from category | That email category only | Until user re-enables in Preference Center |
| User unsubscribes from all marketing | All non-transactional emails | Until user re-subscribes via Preference Center |
| Account suspended | All marketing emails; only billing/reactivation transactional sent | Until account reactivated |
| Account deleted | All emails permanently | Permanent |

### 11.2 Contextual Suppression

| Context | Suppressed | Reason |
|---|---|---|
| User is actively in-app | Push notifications for that session | Prevent duplicate: in-app notification already visible |
| User received transactional email today | Marketing email deferred to tomorrow | Global daily cap compliance |
| User received re-engagement email in last 48h | All non-critical emails | Re-engagement sequence takes priority |
| User is in onboarding wizard | All non-onboarding communications | Prevent distraction during critical activation flow |
| Tournament game in progress (for followed team) | Non-tournament notifications via push | Prevent alert overload during live games |

---

## 12. Communication Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│                   NIL OPTIC COMMUNICATION ENGINE                │
│                                                                 │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐      │
│  │   TRIGGERS   │    │ SEGMENTATION │    │  FREQUENCY   │      │
│  │              │    │              │    │  MANAGER     │      │
│  │  - Events    │───→│  - Role      │───→│              │      │
│  │  - Schedules │    │  - Sport     │    │  - Caps      │      │
│  │  - Thresholds│    │  - Engagement│    │  - Batching  │      │
│  │  - Calendar  │    │  - Tier      │    │  - Conflicts │      │
│  └──────────────┘    │  - Season    │    │  - Priority  │      │
│                      └──────────────┘    └──────┬───────┘      │
│                                                  │              │
│                                                  ▼              │
│                                          ┌──────────────┐      │
│                                          │PERSONALIZATION│     │
│                                          │              │      │
│                                          │  - Content   │      │
│                                          │  - Subject   │      │
│                                          │  - Timing    │      │
│                                          │  - Channel   │      │
│                                          └──────┬───────┘      │
│                                                  │              │
│                          ┌───────────┬───────────┼───────────┐  │
│                          │           │           │           │  │
│                          ▼           ▼           ▼           ▼  │
│                    ┌──────────┐┌──────────┐┌──────────┐┌──────┐│
│                    │  EMAIL   ││  IN-APP  ││  PUSH    ││ SMS  ││
│                    │          ││          ││          ││(TBD) ││
│                    │ SendGrid ││ WebSocket││ APNs/FCM ││      ││
│                    └──────────┘└──────────┘└──────────┘└──────┘│
│                          │           │           │           │  │
│                          ▼           ▼           ▼           ▼  │
│                    ┌──────────────────────────────────────────┐ │
│                    │          ANALYTICS + FEEDBACK            │ │
│                    │                                          │ │
│                    │  Opens, clicks, taps, dismisses,         │ │
│                    │  unsubscribes, bounces, complaints       │ │
│                    │                                          │ │
│                    │  → Engagement scoring → Segmentation     │ │
│                    │  → A/B test results → Optimization       │ │
│                    └──────────────────────────────────────────┘ │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

*NIL Optic -- See the Value. Own the Future.*
