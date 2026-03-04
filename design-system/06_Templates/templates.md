# Templates Library

Last updated: 2026-03-01

---

## Overview

Templates are role-specific page layouts and dashboard scaffolds. They combine components and patterns into complete views scoped by user role.

---

## Dashboard Shell

Every authenticated user sees a consistent shell with role-specific content:

```
┌──────────────────────────────────────────────────────────────┐
│  [Logo]   Search _______________   [Notif] [Messages] [Avatar] │
├────────────┬─────────────────────────────────────────────────┤
│            │                                                 │
│  NAV       │   PAGE CONTENT                                  │
│            │                                                 │
│  ■ Dash    │   ┌─────────────────────────────────────────┐  │
│  □ Dir     │   │   Page Header + Breadcrumbs             │  │
│  □ Pred    │   ├─────────────────────────────────────────┤  │
│  □ Report  │   │                                         │  │
│  □ Roster  │   │   Content Area (role-specific)          │  │
│            │   │                                         │  │
│  ─ MANAGE  │   │   Grid / Table / Cards                  │  │
│  □ Deals   │   │                                         │  │
│  □ Msgs    │   │                                         │  │
│  □ Config  │   │                                         │  │
│            │   └─────────────────────────────────────────┘  │
│            │                                                 │
│  [Profile] │                                                 │
└────────────┴─────────────────────────────────────────────────┘
```

---

## Athletic Director Dashboard

Primary user: Athletic Directors, Assistant ADs, Coaches

```
┌─────────────────────────────────────────────────────────────┐
│  ATHLETIC DEPARTMENT OVERVIEW                                │
│                                                             │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌──────────┐│
│  │ Total NIL  │ │ Active     │ │ Athletes   │ │ Avg      ││
│  │ $42.8M     │ │ Deals: 87  │ │ 284        │ │ $150K    ││
│  │ ▲ +8.2%    │ │ ▲ +12      │ │ ▲ +15      │ │ ▲ +5.4%  ││
│  └────────────┘ └────────────┘ └────────────┘ └──────────┘│
│                                                             │
│  ┌────────────────────────────┐ ┌──────────────────────────┐│
│  │ VALUATION BY SPORT         │ │ TOP ATHLETES             ││
│  │                            │ │                          ││
│  │ [Donut Chart]              │ │ 1. J. Smith    $3.1M    ││
│  │                            │ │ 2. A. Jones    $2.4M    ││
│  │ FB: 52%  BK: 28%          │ │ 3. M. Davis    $1.8M    ││
│  │ BB: 12%  Other: 8%        │ │ 4. T. Brown    $1.5M    ││
│  │                            │ │ 5. K. Lee      $1.2M    ││
│  └────────────────────────────┘ └──────────────────────────┘│
│                                                             │
│  ┌──────────────────────────────────────────────────────────┐│
│  │ COMPLIANCE TRACKER                                       ││
│  │                                                          ││
│  │ ✓ 247 compliant  |  ⚠ 28 review needed  |  ✗ 9 expired  ││
│  │                                                          ││
│  │ [View All]                                               ││
│  └──────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────┘
```

---

## Agent Dashboard

Primary user: NIL Agents, Agency Admins

```
┌─────────────────────────────────────────────────────────────┐
│  AGENT PORTFOLIO                                             │
│                                                             │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌──────────┐│
│  │ Portfolio   │ │ Active     │ │ Pipeline   │ │ Revenue  ││
│  │ $18.4M     │ │ Clients:12 │ │ 8 deals    │ │ $420K    ││
│  │ ▲ +14%     │ │ ▲ +3       │ │ $2.1M val  │ │ YTD      ││
│  └────────────┘ └────────────┘ └────────────┘ └──────────┘│
│                                                             │
│  ┌──────────────────────────────────────────────────────────┐│
│  │ CLIENT ROSTER                                             ││
│  │                                                          ││
│  │ [Avatar] J.Smith  FB·WR  UGA   $3.1M  ▲+12%  3 deals   ││
│  │ [Avatar] A.Jones  FB·QB  LSU   $2.4M  ▲+8%   2 deals   ││
│  │ [Avatar] M.Davis  BK·PG  UCLA  $1.8M  ▼-2%   1 deal    ││
│  │                                                          ││
│  │ [View All Clients]                                       ││
│  └──────────────────────────────────────────────────────────┘│
│                                                             │
│  ┌──────────────────────┐ ┌────────────────────────────────┐│
│  │ DEAL PIPELINE        │ │ MARKET OPPORTUNITIES           ││
│  │                      │ │                                ││
│  │ Prospect:  8         │ │ 5 new brand matches            ││
│  │ Outreach:  5         │ │ based on client profiles       ││
│  │ Negotiate: 3         │ │                                ││
│  │ Signed:   12         │ │ [View Matches]                 ││
│  └──────────────────────┘ └────────────────────────────────┘│
└─────────────────────────────────────────────────────────────┘
```

---

## Athlete Dashboard

Primary user: Individual athletes

```
┌─────────────────────────────────────────────────────────────┐
│  MY NIL PROFILE                                              │
│                                                             │
│  ┌──────────────────────────────────────────────────────────┐│
│  │  [Photo]   Jordan Smith                                  ││
│  │            University of Georgia · Football · WR         ││
│  │            Junior · Atlanta, GA                          ││
│  │                                                          ││
│  │  NIL Valuation: $3.1M         Confidence: 92%           ││
│  │  ▲ +16.7% (30d)                                         ││
│  └──────────────────────────────────────────────────────────┘│
│                                                             │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌──────────┐│
│  │ Total      │ │ Active     │ │ Social     │ │ NIL Rank ││
│  │ Earnings   │ │ Deals      │ │ Reach      │ │          ││
│  │ $245K      │ │ 3          │ │ 6.4M       │ │ #47      ││
│  │ YTD        │ │            │ │ combined   │ │ National ││
│  └────────────┘ └────────────┘ └────────────┘ └──────────┘│
│                                                             │
│  ┌──────────────────────────────┐ ┌────────────────────────┐│
│  │ VALUATION TREND              │ │ MY DEALS               ││
│  │                              │ │                        ││
│  │ [Line Chart - 90d]           │ │ Nike - $50K - Active   ││
│  │                              │ │ Gatorade - $30K - Done ││
│  │                              │ │ Local Co - $15K - New  ││
│  └──────────────────────────────┘ └────────────────────────┘│
└─────────────────────────────────────────────────────────────┘
```

---

## Directory Template

Sports directory with search, filters, and browsable athlete/team listings:

```
┌─────────────────────────────────────────────────────────────┐
│  ATHLETE DIRECTORY                                           │
│                                                             │
│  [Search ___________]  [Sport ▼] [Conf ▼] [Position ▼]     │
│                                                             │
│  847 athletes found                    [Grid] [List] [Table]│
│                                                             │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐      │
│  │ [Photo]  │ │ [Photo]  │ │ [Photo]  │ │ [Photo]  │      │
│  │ J.Smith  │ │ A.Jones  │ │ M.Davis  │ │ T.Brown  │      │
│  │ FB · WR  │ │ FB · QB  │ │ BK · PG  │ │ BB · P   │      │
│  │ $3.1M    │ │ $2.4M    │ │ $1.8M    │ │ $1.5M    │      │
│  │ UGA      │ │ LSU      │ │ UCLA     │ │ Vandy    │      │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘      │
│                                                             │
│  [Load More]                                                │
└─────────────────────────────────────────────────────────────┘
```

---

## Mobile Templates

### Mobile Dashboard (Bottom Tab Bar)

```
┌──────────────────────┐
│  [Header + Avatar]   │
│                      │
│  Metric Cards        │
│  (horizontal scroll) │
│                      │
│  ──────────────────  │
│                      │
│  Quick Actions       │
│  [Card] [Card]       │
│                      │
│  Recent Activity     │
│  [List Items]        │
│                      │
├──────────────────────┤
│ 🏠  📊  🔍  💬  👤  │  ← Bottom tab bar
└──────────────────────┘
```
