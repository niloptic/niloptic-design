# Admin Dashboard Template

Last updated: 2026-03-04

---

## Purpose

Platform-wide visibility for internal operations. The Admin Dashboard provides NIL Optic internal team members with centralized control over user management, onboarding pipelines, data sync orchestration, prediction governance, transfer portal overrides, capability matrix governance, and NCAA program coverage tracking (battle board). This is the operational backbone that ensures every external persona has a reliable, accurate, and performant experience.

**Role key:** `admin`
**Shell route:** `/admin`
**Renders through:** Shared `DashboardShell` with admin role context and `AdminDashboardView` content.

---

## Shell Composition

The Admin shell follows the standard dashboard shell pattern with admin-specific navigation context:

```
┌──────────────────────────────────────────────────────────────────────┐
│  [Logo]   NIL OPTIC ADMIN       [Huddles] [Messages] [Role ▼] [Av] │
├────────────┬─────────────────────────────────────────────────────────┤
│            │                                                         │
│  ADMIN     │   PAGE CONTENT                                          │
│            │                                                         │
│  ■ Home    │   ┌─────────────────────────────────────────────────┐  │
│  □ Onboard │   │   Page Header + Breadcrumbs                     │  │
│  □ Users   │   ├─────────────────────────────────────────────────┤  │
│  □ Admins  │   │                                                 │  │
│  □ Cap Mat │   │   Content Area (admin-specific)                 │  │
│  □ Predict │   │                                                 │  │
│  □ Tourney │   │   Cards / Tables / Sync Status / Metrics        │  │
│  □ Portal  │   │                                                 │  │
│  □ Present │   │                                                 │  │
│  □ Emails  │   │                                                 │  │
│  □ Sync    │   └─────────────────────────────────────────────────┘  │
│            │                                                         │
│  ─ GLOBAL  │                                                         │
│  □ Agent D │                                                         │
│  □ Affil D │                                                         │
│  □ Favs    │                                                         │
│  □ Pipes   │                                                         │
│  □ Roster  │                                                         │
│  □ Tourney │                                                         │
│            │                                                         │
│  ─ TOOLS   │                                                         │
│  □ Designer│  ← conditional: user has designer scope                 │
│            │                                                         │
│  [Profile] │                                                         │
└────────────┴─────────────────────────────────────────────────────────┘
```

### Top Navigation

| Element          | Behavior                                                                 |
|------------------|--------------------------------------------------------------------------|
| Logo             | Routes to `/admin`                                                       |
| Context Title    | Resolves from active organization/program context; skeleton during load   |
| Huddles          | Icon + label on desktop; icon-only on mobile                             |
| Messages         | Icon + label on desktop; icon-only on mobile                             |
| Role Switcher    | Lists all possessed roles + Fan preview routing to `/fan`                |
| Avatar Dropdown  | Profile, Settings, Keyboard Shortcuts panel, Sign Out                    |

### Keyboard Shortcuts

| Key     | Action                                |
|---------|---------------------------------------|
| `L`     | Switch to light mode                  |
| `D`     | Switch to dark mode                   |
| `H`     | Open Huddles                          |
| `M`     | Open Messages                         |
| `1`-`9` | Navigate in-order sidebar pages       |
| `0`     | Navigate to tenth sidebar page        |

---

## Admin Left Navigation

Full item list sourced from `admin-nav.ts`:

| #  | Icon         | Label              | Route                           | Nav ID                       |
|----|--------------|--------------------|----------------------------------|------------------------------|
| 1  | Shield       | Admin Home         | `/admin`                         | `admin-home`                 |
| 2  | UserPlus     | Onboarding         | `/admin/onboarding`              | `admin-onboarding`           |
| 3  | Users        | Users              | `/admin/users`                   | `admin-users`                |
| 4  | ShieldCheck  | Admins             | `/admin/admins`                  | `admin-admins`               |
| 5  | Table2       | Capability Matrix  | `/admin/capability-matrix`       | `admin-capability-matrix`    |
| 6  | BarChart3    | Predictions        | `/admin/predictions`             | `admin-predictions`          |
| 7  | Trophy       | Tournaments        | `/admin/tournaments`             | `admin-tournaments`          |
| 8  | BarChart3    | Transfer Portal    | `/admin/transfer-portal`         | `admin-transfer-portal`      |
| 9  | FileText     | Presentation Tools | `/admin/presentations`           | `admin-presentations`        |
| 10 | Mail         | Emails             | `/admin/invite-email-preview`    | `admin-invite-email-preview` |
| 11 | RefreshCw    | Sync               | `/admin/sync`                    | `admin-sync`                 |

**Global nav items** (all authenticated users, below separator):

| Icon     | Label               | Route                       |
|----------|---------------------|-----------------------------|
| Building | Agent Directory      | `/agent-directory`          |
| Handshake| Affiliate Directory  | `/affiliate-directory`      |
| Star     | Favorites            | `/dashboard/favorites`      |
| Kanban   | Pipelines            | `/dashboard/pipelines`      |
| Clipboard| Roster Builder       | `/dashboard/roster-builder` |
| Trophy   | Tournaments          | `/dashboard/tournaments`    |

**Conditional tools** (below separator):

| Condition              | Label    | Route       |
|------------------------|----------|-------------|
| User has designer scope| Designer | `/designer` |

---

## Admin Dashboard Home (`/admin`)

Primary view: Control center overview with system health, user metrics, sync status, recent activity, and conference coverage preview.

```
┌──────────────────────────────────────────────────────────────────────┐
│  [Logo]   NIL OPTIC ADMIN       [Huddles] [Messages] [Role ▼] [Av] │
├────────────┬─────────────────────────────────────────────────────────┤
│            │                                                         │
│  ADMIN     │   ADMIN CONTROL CENTER                                  │
│            │                                                         │
│  ■ Home    │   ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌─────┐│
│  □ Onboard │   │ ACTIVE     │ │ PROGRAMS   │ │ SYSTEM     │ │OPEN ││
│  □ Users   │   │ USERS      │ │ ONBOARDED  │ │ UPTIME     │ │TCKTS││
│  □ Admins  │   │            │ │            │ │            │ │     ││
│  □ Cap Mat │   │ 2,847      │ │ 412        │ │ 99.97%     │ │ 14  ││
│  □ Predict │   │ ▲ +142     │ │ ▲ +28      │ │ ▲ Stable   │ │ ▼ -3││
│  □ Tourney │   │ (30d)      │ │ (30d)      │ │ (30d)      │ │(24h)││
│  □ Portal  │   └────────────┘ └────────────┘ └────────────┘ └─────┘│
│  □ Present │                                                         │
│  □ Emails  │   ┌────────────────────────────┐ ┌────────────────────┐│
│  □ Sync    │   │ RECENT ACTIVITY            │ │ SYNC STATUS        ││
│            │   │                            │ │                    ││
│  ─ GLOBAL  │   │ [ts] New org: SEC Univ     │ │ Games:    ✓  2h   ││
│  □ Agent D │   │ [ts] User invite sent      │ │ Rankings: ✓  4h   ││
│  □ Affil D │   │ [ts] Prediction run OK     │ │ Leaders:  ✓  4h   ││
│  □ Favs    │   │ [ts] Portal entry: J.Davis │ │ Standings:✓  6h   ││
│  □ Pipes   │   │ [ts] Sync completed        │ │ Portal:   ✓  8h   ││
│  □ Roster  │   │ [ts] Admin added: mk@      │ │ Full Sync:✓ 12h   ││
│  □ Tourney │   │                            │ │ Predict:  ⚠ 14h   ││
│            │   │ [View All Activity]        │ │                    ││
│  ─ TOOLS   │   └────────────────────────────┘ └────────────────────┘│
│  □ Designer│                                                         │
│            │   ┌────────────────────────────────────────────────────┐│
│            │   │ CONFERENCE COVERAGE (Battle Board Preview)         ││
│            │   │                                                    ││
│            │   │ SEC:      ████████████░░░░ 75%   12/16 programs   ││
│            │   │ Big Ten:  █████████░░░░░░░ 61%   11/18 programs   ││
│            │   │ ACC:      ██████░░░░░░░░░░ 41%    7/17 programs   ││
│            │   │ Big 12:   █████░░░░░░░░░░░ 31%    5/16 programs   ││
│            │   │                                                    ││
│            │   │ Total Power 4: 35/67 (52%)   All D1: 142/362 (39%)││
│            │   │                                                    ││
│            │   │ [Open Battle Board]                                ││
│            │   └────────────────────────────────────────────────────┘│
│            │                                                         │
│            │   ┌────────────┐ ┌────────────┐ ┌────────────────────┐│
│            │   │ PREDICTION │ │ ONBOARDING │ │ FEATURE ADOPTION   ││
│            │   │ ACCURACY   │ │ PIPELINE   │ │                    ││
│            │   │            │ │            │ │ Pipelines:  72%    ││
│            │   │ 87.4%      │ │ Pending: 8 │ │ Roster Bldr: 64%  ││
│            │   │ Target:85% │ │ Active: 12 │ │ Predictions: 81%  ││
│            │   │ ▲ +1.2%    │ │ Done:  389 │ │ Messages:    58%  ││
│            │   │ (7d trend) │ │ Rate:  82% │ │ Tournaments: 45%  ││
│            │   └────────────┘ └────────────┘ └────────────────────┘│
│            │                                                         │
│  [Profile] │                                                         │
└────────────┴─────────────────────────────────────────────────────────┘
```

### Home Card Specifications

| Card                   | Data Source              | Font           | Format       |
|------------------------|--------------------------|----------------|--------------|
| Active Users           | Platform analytics       | JetBrains Mono | `#,###`      |
| Programs Onboarded     | `/admin/onboarding`      | JetBrains Mono | `###`        |
| System Uptime          | Infrastructure monitoring| JetBrains Mono | `XX.XX%`     |
| Open Tickets           | Support queue            | JetBrains Mono | `##`         |
| Prediction Accuracy    | `/admin/predictions`     | JetBrains Mono | `XX.X%`      |
| Onboarding Pipeline    | `/admin/onboarding`      | JetBrains Mono | `##` per stage|
| Feature Adoption       | Platform analytics       | JetBrains Mono | `XX%`        |
| Conference Coverage    | Battle board data        | JetBrains Mono | `##/##` + bar|

### Sync Status Badge Rules

| Status      | Badge Color                       | Icon |
|-------------|-----------------------------------|------|
| Completed   | `--color-positive` (green)        | `✓`  |
| Running     | `--color-info` (blue)             | `◉`  |
| Failed      | `--color-critical` (red)          | `✗`  |
| Stale (>12h)| `--color-risk` (amber)            | `⚠`  |

---

## User Management (`/admin/users`)

Org-level and program-level user management with invite email tooling.

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > USERS                                                       │
│                                                                     │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │ [Search users _______________]  [Org ▼] [Role ▼] [Status ▼] │  │
│  └───────────────────────────────────────────────────────────────┘  │
│                                                                     │
│  ┌──────┬───────────────┬──────────────┬──────────┬────────┬─────┐ │
│  │      │ NAME          │ EMAIL        │ ORG      │ ROLE   │ ... │ │
│  ├──────┼───────────────┼──────────────┼──────────┼────────┼─────┤ │
│  │ [Av] │ Marcus Chen   │ mc@sec-u.edu │ SEC Univ │ AD     │ Act │ │
│  │ [Av] │ Aisha Taylor  │ at@big10.edu │ Big Ten U│ Coach  │ Act │ │
│  │ [Av] │ James Ortiz   │ jo@acc.edu   │ ACC Coll │ GM     │ Pnd │ │
│  │ [Av] │ Kira Patel    │ kp@agent.com │ Octagon  │ Agent  │ Act │ │
│  │ [Av] │ Devon Brooks  │ db@aff.com   │ Kravitz  │ Affil  │ Inv │ │
│  └──────┴───────────────┴──────────────┴──────────┴────────┴─────┘ │
│                                                                     │
│  Expanded columns: Status, Last Login, Created, Actions             │
│  Actions: [Edit Role] [Resend Invite] [Deactivate] [View Org]      │
│                                                                     │
│  ─────────────────────────────────────────────────────────────────  │
│                                                                     │
│  INVITE EMAIL MANAGEMENT                                            │
│                                                                     │
│  ┌────────────────────────────────────┐ ┌──────────────────────┐   │
│  │ EMAIL PREVIEW                      │ │ TEST SEND            │   │
│  │                                    │ │                      │   │
│  │ [Scope: ▼ Org | Program | Athlete]│ │ Recipient:           │   │
│  │                                    │ │ [____________@___]   │   │
│  │ ┌──────────────────────────────┐  │ │                      │   │
│  │ │  NIL OPTIC                   │  │ │ Scope: [Org ▼]       │   │
│  │ │                              │  │ │                      │   │
│  │ │  You've been invited to      │  │ │ [Send Test Email]    │   │
│  │ │  join {org_name} on          │  │ │                      │   │
│  │ │  NIL Optic as {role}.        │  │ │ Last test:           │   │
│  │ │                              │  │ │ ✓ 2h ago to test@    │   │
│  │ │  [Accept Invitation]         │  │ │                      │   │
│  │ └──────────────────────────────┘  │ │ Delivery metrics:    │   │
│  │                                    │ │ Sent: 847            │   │
│  │ [Refresh Preview]                  │ │ Delivered: 839       │   │
│  └────────────────────────────────────┘ └──────────────────────┘   │
│                                                                     │
│  PENDING INVITES                                                    │
│                                                                     │
│  ┌────────┬──────────────┬──────────┬────────┬──────┬───────────┐  │
│  │ STATUS │ EMAIL        │ SCOPE    │ ROLE   │ SENT │ ACTIONS   │  │
│  ├────────┼──────────────┼──────────┼────────┼──────┼───────────┤  │
│  │ ● Pend │ jo@acc.edu   │ Org      │ GM     │ 2d   │ [Re] [Cx] │  │
│  │ ● Pend │ lm@mwc.edu  │ Program  │ Coach  │ 5d   │ [Re] [Cx] │  │
│  │ ● Exp  │ rk@big12.edu│ Athlete  │ Athlete│ 14d  │ [Re] [Cx] │  │
│  └────────┴──────────────┴──────────┴────────┴──────┴───────────┘  │
│                                                                     │
│  Status chips: Pending (amber), Expired (red), Accepted (green)     │
│  Actions: [Re] = Resend, [Cx] = Cancel/Revoke                      │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### User Table Columns

| Column     | Width   | Type           | Sort | Filter |
|------------|---------|----------------|------|--------|
| Avatar     | 40px    | Image          | No   | No     |
| Name       | fluid   | Text           | Yes  | Search |
| Email      | fluid   | Text           | Yes  | Search |
| Org        | 160px   | Text + badge   | Yes  | Dropdown |
| Role       | 100px   | Badge          | Yes  | Dropdown |
| Status     | 80px    | Status badge   | Yes  | Dropdown |
| Last Login | 120px   | Relative time  | Yes  | No     |
| Created    | 120px   | Date           | Yes  | No     |
| Actions    | 120px   | Button group   | No   | No     |

### Invite Lifecycle Status

| Status         | Outcome Code          | Badge Color     |
|----------------|-----------------------|-----------------|
| Invite Created | `invite_created`      | Blue            |
| Invite Resent  | `invite_resent`       | Blue            |
| Duplicate Pend | `duplicate_pending`   | Amber           |
| Send Failed    | `invite_send_failed`  | Red             |
| Revoked        | `invite_revoked`      | Zinc            |
| Role Updated   | `role_updated`        | Green           |
| Member Removed | `member_removed`      | Red             |

---

## Admin Accounts (`/admin/admins`)

Manage platform admin user accounts.

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > ADMINS                                                      │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │ [Search admins ___________]             [+ Add Admin]       │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                     │
│  ┌──────┬───────────────┬──────────────────┬────────┬──────────┐   │
│  │      │ NAME          │ EMAIL            │ SCOPES │ ACTIONS  │   │
│  ├──────┼───────────────┼──────────────────┼────────┼──────────┤   │
│  │ [Av] │ Alex Bridewell│ ab@niloptic.com  │ A + D  │ [Edit]   │   │
│  │ [Av] │ Morgan Kim    │ mk@niloptic.com  │ A      │ [Edit]   │   │
│  │ [Av] │ Jordan Lee    │ jl@niloptic.com  │ A + D  │ [Edit]   │   │
│  └──────┴───────────────┴──────────────────┴────────┴──────────┘   │
│                                                                     │
│  Scopes: A = admin, D = designer                                    │
│  Actions: Edit scopes, Deactivate account                           │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Onboarding Management (`/admin/onboarding`)

Admin-internal onboarding question/flow management. Non-admin users must not see this in dashboard navigation.

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > ONBOARDING                                                  │
│                                                                     │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐      │
│  │ PENDING    │ │ IN PROG    │ │ COMPLETED  │ │ COMPLETION │      │
│  │ INVITES    │ │ ONBOARDING │ │ THIS MONTH │ │ RATE       │      │
│  │            │ │            │ │            │ │            │      │
│  │ 24         │ │ 12         │ │ 38         │ │ 82%        │      │
│  │ ▲ +6 (7d)  │ │ Avg: 4.2d  │ │ ▲ +14 MoM  │ │ ▲ +3% MoM  │      │
│  └────────────┘ └────────────┘ └────────────┘ └────────────┘      │
│                                                                     │
│  ONBOARDING QUESTION BUILDER                                        │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Flow: [Role Scope ▼]  Status: [● Active]                   │   │
│  │                                                             │   │
│  │ Q1: Organization name          [Text]     [Required ✓]     │   │
│  │ Q2: Primary sport              [Select]   [Required ✓]     │   │
│  │ Q3: Conference                 [Select]   [Required ✓]     │   │
│  │ Q4: Estimated roster size      [Number]   [Optional]       │   │
│  │ Q5: Current NIL budget range   [Range]    [Optional]       │   │
│  │                                                             │   │
│  │ [+ Add Question]          [Save Flow]  [Preview]           │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  ACTIVE ONBOARDING SESSIONS                                         │
│                                                                     │
│  ┌──────────────┬─────────┬──────────┬───────┬─────┬───────────┐  │
│  │ USER         │ ORG     │ ROLE     │ STEP  │ AGE │ ACTIONS   │  │
│  ├──────────────┼─────────┼──────────┼───────┼─────┼───────────┤  │
│  │ T. Williams  │ SEC U   │ AD       │ 3/5   │ 1d  │ [Nudge]   │  │
│  │ R. Jackson   │ Big12 C │ Coach    │ 2/5   │ 3d  │ [Nudge]   │  │
│  │ K. Nakamura  │ MWC Uni │ GM       │ 1/5   │ 5d  │ [Reset]   │  │
│  └──────────────┴─────────┴──────────┴───────┴─────┴───────────┘  │
│                                                                     │
│  PIPELINE FUNNEL                                                    │
│                                                                     │
│  Invite Sent    ██████████████████████████████████████  847         │
│  Accepted       █████████████████████████████░░░░░░░░░  612  (72%) │
│  Started        ████████████████████████░░░░░░░░░░░░░░  524  (86%) │
│  Completed      ██████████████████░░░░░░░░░░░░░░░░░░░░  412  (79%) │
│  Active (7d)    ████████████████░░░░░░░░░░░░░░░░░░░░░░  389  (94%) │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Onboarding Governance Rules

- Onboarding question/flow management is admin-internal only
- Non-admin users must not receive onboarding management UI in dashboard navigation
- User onboarding does not include role-selection prompts
- Role context is derived from authenticated role/profile state, not manual selection
- If no org/program context exists, onboarding does not auto-launch

---

## Sync Dashboard (`/admin/sync`)

Data sync job management via external `/sync-server`. Supports manual runs, live streaming progress, and schedule configuration.

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > SYNC                                                        │
│                                                                     │
│  Syncs run in /sync-server with live progress updates               │
│  and scheduled automation.                                          │
│                                                                     │
│  AUTOMATION SCHEDULE                                                 │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Enabled: [Yes ▼]    Run Time: [03:00] UTC                  │   │
│  │ Range Days: [1]     Run Predictions After: [Yes ▼]         │   │
│  │                                         [Save Schedule]     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  ┌─────────────────────────────┐ ┌─────────────────────────────┐   │
│  │ DIVISION I GAME SYNC        │ │ NET RANKINGS SYNC           │   │
│  │                             │ │                             │   │
│  │ Status: ✓ Completed         │ │ Status: ✓ Completed         │   │
│  │ Last run: 2h ago            │ │ Last run: 4h ago            │   │
│  │ Duration: 3m 42s            │ │ Duration: 1m 18s            │   │
│  │ Records: 48/48              │ │ Records: 362/362            │   │
│  │                             │ │                             │   │
│  │ Start: [____] End: [____]   │ │ Year: [2025] Type: [REG ▼] │   │
│  │ [Sync Division I Games]     │ │ [Sync NET Rankings]         │   │
│  └─────────────────────────────┘ └─────────────────────────────┘   │
│                                                                     │
│  ┌─────────────────────────────┐ ┌─────────────────────────────┐   │
│  │ CONFERENCE LEADERS SYNC     │ │ STANDINGS SYNC              │   │
│  │                             │ │                             │   │
│  │ Status: ✓ Completed         │ │ Status: ✓ Completed         │   │
│  │ Last run: 4h ago            │ │ Last run: 6h ago            │   │
│  │ Duration: 2m 05s            │ │ Duration: 1m 52s            │   │
│  │ Records: 156/156            │ │ Records: 362/362            │   │
│  │                             │ │                             │   │
│  │ Year: [2025] Type: [REG ▼] │ │ Year: [2025] Type: [REG ▼] │   │
│  │ [Sync Conference Leaders]   │ │ [Sync Standings]            │   │
│  └─────────────────────────────┘ └─────────────────────────────┘   │
│                                                                     │
│  ┌─────────────────────────────┐ ┌─────────────────────────────┐   │
│  │ TRANSFER PORTAL SYNC        │ │ VIEWS SYNC                  │   │
│  │                             │ │                             │   │
│  │ Status: ✓ Completed         │ │ Status: ✓ Completed         │   │
│  │ Last run: 8h ago            │ │ Last run: 2h ago            │   │
│  │ Duration: 4m 31s            │ │ Duration: 0m 48s            │   │
│  │ Records: 214/214            │ │ Refreshes dashboard         │   │
│  │                             │ │ materialized views.         │   │
│  │ Pulls latest transfer       │ │                             │   │
│  │ portal feed.                │ │                             │   │
│  │ [Sync Transfer Portal]      │ │ [Refresh Views]             │   │
│  └─────────────────────────────┘ └─────────────────────────────┘   │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ FULL SYNC + PREDICTIONS                                     │   │
│  │                                                             │   │
│  │ Status: ◉ Running                                           │   │
│  │ Progress: Syncing NET Rankings (142/362)                    │   │
│  │ ████████████████░░░░░░░░░░░░░░░░  39%                      │   │
│  │                                                             │   │
│  │ Stage Log:                                                  │   │
│  │ ┌─────────────────────────────────────────────────────┐    │   │
│  │ │ 142/362  Syncing NET Rankings...                    │    │   │
│  │ │ 48/48    Division I games synced                    │    │   │
│  │ │ -        Starting full sync pipeline...             │    │   │
│  │ └─────────────────────────────────────────────────────┘    │   │
│  │                                                             │   │
│  │ [Run Full Sync + Predictions]  (disabled while running)     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  RESULT OUTPUT (post-completion)                                    │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ {                                                           │   │
│  │   "games_synced": 48,                                       │   │
│  │   "rankings_updated": 362,                                  │   │
│  │   "predictions_generated": 4218,                            │   │
│  │   "duration_ms": 184200                                     │   │
│  │ }                                                           │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Sync Job Types

| Job Type                   | Key                          | Parameters                       |
|---------------------------|------------------------------|----------------------------------|
| Division I Game Sync      | `division_i_games`           | `startDate`, `endDate`           |
| NET Rankings              | `net_rankings`               | `seasonYear`, `seasonType`       |
| Conference Leaders        | `conference_leaders`         | `seasonYear`, `seasonType`       |
| Standings                 | `standings`                  | `seasonYear`, `seasonType`       |
| Transfer Portal           | `transfer_portal`            | (none)                           |
| Views Sync                | `views_sync`                 | (none)                           |
| Predictions               | `predictions`                | (varies)                         |
| Full Sync + Predictions   | `full_sync_and_predictions`  | `seasonYear`, `seasonType`, `divisionRangeDays`, `runPredictionsAfter` |

### Sync Status Values

| Status     | Code         | Visual                        |
|------------|--------------|-------------------------------|
| Queued     | `queued`     | Zinc badge, clock icon        |
| Running    | `running`    | Blue badge, spinner icon      |
| Completed  | `completed`  | Green badge, check icon       |
| Failed     | `failed`     | Red badge, x-circle icon      |

---

## Predictions Admin (`/admin/predictions`)

Prediction run management, accuracy monitoring, and model governance.

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > PREDICTIONS                                                 │
│                                                                     │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐      │
│  │ ACCURACY   │ │ DIRECTION  │ │ CONFIDENCE │ │ BIAS       │      │
│  │ (MAE)      │ │ ACCURACY   │ │ CALIBR.    │ │ CHECK      │      │
│  │            │ │            │ │            │ │            │      │
│  │ 12.4%      │ │ 83.2%      │ │ 87.1%      │ │ +1.8%      │      │
│  │ Target:<15%│ │ Target:80% │ │ Target:85% │ │ Target:<3% │      │
│  │ ✓ Pass     │ │ ✓ Pass     │ │ ✓ Pass     │ │ ✓ Pass     │      │
│  └────────────┘ └────────────┘ └────────────┘ └────────────┘      │
│                                                                     │
│  RUN CONTROLS                                                       │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Last Run: 2026-03-04 03:14 UTC    Duration: 12m 38s        │   │
│  │ Athletes Predicted: 4,218         Model Version: v2.4.1    │   │
│  │                                                             │   │
│  │ [Trigger Prediction Run]     [Configure Schedule]           │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  ┌────────────────────────────────┐ ┌──────────────────────────┐   │
│  │ CONFIDENCE DISTRIBUTION        │ │ ACCURACY TREND (30d)     │   │
│  │                                │ │                          │   │
│  │ 90-100%: ████████████████ 42% │ │   90% ─ ─ ─ ─ ─ ─ ─ ─  │   │
│  │ 80-89%:  ████████████░░░░ 31% │ │        /‾‾\    /‾\      │   │
│  │ 70-79%:  ████████░░░░░░░░ 18% │ │   85% ─ ── ── ─ ─ ─ ─  │   │
│  │ 60-69%:  ████░░░░░░░░░░░░  7% │ │   ──/       \/    \──   │   │
│  │ <60%:    █░░░░░░░░░░░░░░░  2% │ │   80%                   │   │
│  │                                │ │                          │   │
│  │ Median Confidence: 88.4%       │ │   W1  W2  W3  W4  Now   │   │
│  └────────────────────────────────┘ └──────────────────────────┘   │
│                                                                     │
│  MODEL DRIFT INDICATORS                                             │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Sport     │ 7d MAE  │ 30d MAE │ Drift   │ Status          │   │
│  ├───────────┼─────────┼─────────┼─────────┼─────────────────│   │
│  │ Basketball│ 11.8%   │ 12.4%   │ -0.6%   │ ✓ Stable        │   │
│  │ Football  │ 14.2%   │ 13.8%   │ +0.4%   │ ✓ Stable        │   │
│  │ Baseball  │ 16.1%   │ 14.9%   │ +1.2%   │ ⚠ Monitor       │   │
│  └───────────┴─────────┴─────────┴─────────┴─────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Prediction Accuracy Metrics

| Metric                  | Definition                                          | Target    |
|-------------------------|-----------------------------------------------------|-----------|
| Mean Absolute Error     | Avg absolute diff between predicted and actual       | < 15%     |
| Directional Accuracy    | % correctly predicting up/down/flat direction        | 80%+      |
| Confidence Calibration  | % of actuals within stated confidence interval       | 85%+ in 90% CI |
| Bias Check              | Average signed error (positive = overestimating)     | < 3%      |

---

## Transfer Portal Admin (`/admin/transfer-portal`)

Override controls for transfer portal entry/exit dates, manual status corrections, and data quality governance.

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > TRANSFER PORTAL                                             │
│                                                                     │
│  PORTAL WINDOW STATUS                                               │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Current Window: OPEN (Dec 9 - Apr 16)                       │   │
│  │ Override Status: [● Active Override]                         │   │
│  │ Days Remaining: 43                                          │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  OVERRIDE CONTROLS                                                  │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Window Start Override:  [2025-12-09]  [✓ Override Active]   │   │
│  │ Window End Override:    [2026-04-16]  [✓ Override Active]   │   │
│  │                                                             │   │
│  │ Force Portal:  [○ Open] [○ Closed] [● Use Dates]           │   │
│  │                                                             │   │
│  │ [Save Overrides]            [Reset to Default]              │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  DATA QUALITY FLAGS                                                 │
│  ┌──────────────────┬────────┬──────────┬────────┬─────────────┐  │
│  │ ATHLETE          │ SCHOOL │ STATUS   │ FLAG   │ ACTION      │  │
│  ├──────────────────┼────────┼──────────┼────────┼─────────────┤  │
│  │ J. Davis         │ UK     │ Entered  │ ⚠ Dup  │ [Resolve]   │  │
│  │ M. Thompson      │ Duke   │ Exited   │ ⚠ Date │ [Correct]   │  │
│  │ A. Rodriguez     │ UConn  │ Entered  │ ⚠ Miss │ [Add Data]  │  │
│  └──────────────────┴────────┴──────────┴────────┴─────────────┘  │
│                                                                     │
│  AUDIT LOG                                                          │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ [ts] admin@nil set window end override to 2026-04-16       │   │
│  │ [ts] admin@nil corrected entry date for J. Davis           │   │
│  │ [ts] system: portal sync completed (214 records)           │   │
│  │ [ts] admin@nil force-opened portal window                  │   │
│  │                                                             │   │
│  │ [Load More]                                                 │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Capability Matrix Viewer (`/admin/capability-matrix`)

Read-only visual representation of the role-capability matrix. Must avoid vendor-specific copy in capability labels.

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > CAPABILITY MATRIX                                           │
│                                                                     │
│  [Search capabilities ________]  [Category ▼]                       │
│                                                                     │
│  ┌────────────────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐     │
│  │ CAPABILITY     │ ADM │ DES │ AD  │ AAD │ GM  │ COA │ ATH │     │
│  ├────────────────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤     │
│  │ Dashboard Home │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │     │
│  │ Directory      │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │ ◐   │     │
│  │ Predictions    │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │ ◐   │     │
│  │ Messages       │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │     │
│  │ Huddles        │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │     │
│  │ Pipelines      │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │ ○   │     │
│  │ Roster Builder │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │ ○   │     │
│  │ Favorites      │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │     │
│  │ Transfer Portal│ ●   │ ○   │ ●   │ ●   │ ●   │ ●   │ ◐   │     │
│  │ Tournaments    │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │ ●   │     │
│  │ Admin Panel    │ ●   │ ●   │ ○   │ ○   │ ○   │ ○   │ ○   │     │
│  │ Token Studio   │ ○   │ ●   │ ○   │ ○   │ ○   │ ○   │ ○   │     │
│  │ NIL Payments   │ ○   │ ○   │ ○   │ ○   │ ○   │ ○   │ ○   │     │
│  │ Org Settings   │ ●   │ ○   │ ●   │ ○   │ ●   │ ●   │ ○   │     │
│  └────────────────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘     │
│                                                                     │
│  Legend: ● Full  ◐ Partial  ○ None                                  │
│                                                                     │
│  Continued roles: AGT, AA, AFA, AFN, FAN                           │
│                                                                     │
│  [Expand row] → Shows detail: feature description, partial access   │
│  conditions, and route mapping.                                     │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Permission Legend

| Symbol | Meaning  | Color Token                  |
|--------|----------|------------------------------|
| `●`    | Full     | `--color-positive` (green)   |
| `◐`    | Partial  | `--color-risk` (amber)       |
| `○`    | None     | `--text-tertiary` (zinc-500) |

---

## Presentation Tools (`/admin/presentations`)

Admin presentation workspace for creating and managing internal/external presentations.

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > PRESENTATION TOOLS                                          │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ [Search presentations _______]          [+ New Presentation]│   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐              │
│  │ ┌──────┐ │ │ ┌──────┐ │ │ ┌──────┐ │ │ ┌──────┐ │              │
│  │ │ [  ] │ │ │ │ [  ] │ │ │ │ [  ] │ │ │ │ [  ] │ │              │
│  │ │ Prev │ │ │ │ Prev │ │ │ │ Prev │ │ │ │ Prev │ │              │
│  │ └──────┘ │ │ └──────┘ │ │ └──────┘ │ │ └──────┘ │              │
│  │ Q1 Pitch │ │ SEC Demo │ │ Board    │ │ Investor │              │
│  │ 12 slides│ │ 8 slides │ │ Update   │ │ Deck     │              │
│  │ Mar 1    │ │ Feb 28   │ │ 6 slides │ │ 18 slides│              │
│  │ [Edit]   │ │ [Edit]   │ │ Feb 15   │ │ Jan 30   │              │
│  └──────────┘ └──────────┘ │ [Edit]   │ │ [Edit]   │              │
│                             └──────────┘ └──────────┘              │
│                                                                     │
│  PRESENTATION EDITOR (when editing)                                 │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ ┌─────────┐  Slide 3 of 12                                 │   │
│  │ │ [Slide] │  ┌───────────────────────────────────────────┐  │   │
│  │ │ 1       │  │                                           │  │   │
│  │ │ [Slide] │  │         SLIDE CANVAS                      │  │   │
│  │ │ 2       │  │         16:9 aspect ratio                 │  │   │
│  │ │ [Slide]*│  │         Dark theme default                │  │   │
│  │ │ 3       │  │                                           │  │   │
│  │ │ [Slide] │  │                                           │  │   │
│  │ │ 4       │  └───────────────────────────────────────────┘  │   │
│  │ │ ...     │  [+ Add Slide] [Duplicate] [Delete] [Export]    │   │
│  │ └─────────┘                                                 │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Emails Admin (`/admin/invite-email-preview`)

Branded invite email template preview and SendGrid test-send controls.

```
┌─────────────────────────────────────────────────────────────────────┐
│  ADMIN > EMAILS                                                      │
│                                                                     │
│  TEMPLATE PREVIEW                                                   │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Scope: [● Org] [○ Program] [○ Athlete]                     │   │
│  │                                                             │   │
│  │ ┌─────────────────────────────────────────────────────┐    │   │
│  │ │           ┌─────────────────────┐                   │    │   │
│  │ │           │   NIL OPTIC LOGO    │                   │    │   │
│  │ │           └─────────────────────┘                   │    │   │
│  │ │                                                     │    │   │
│  │ │   You've been invited to join                       │    │   │
│  │ │   {organization_name} on NIL Optic                  │    │   │
│  │ │   as {role_label}.                                  │    │   │
│  │ │                                                     │    │   │
│  │ │   ┌─────────────────────────┐                       │    │   │
│  │ │   │  ACCEPT INVITATION      │  ← brand-red button  │    │   │
│  │ │   └─────────────────────────┘                       │    │   │
│  │ │                                                     │    │   │
│  │ │   This invite expires in 7 days.                    │    │   │
│  │ │                                                     │    │   │
│  │ │   ---                                               │    │   │
│  │ │   NIL Optic | Support@niloptic.com                  │    │   │
│  │ └─────────────────────────────────────────────────────┘    │   │
│  │                                                             │   │
│  │ [Refresh Preview]                                           │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  TEST SEND CONTROLS                                                 │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Recipient: [_________________________@________________]     │   │
│  │ Scope:     [Org ▼]                                          │   │
│  │                                                             │   │
│  │ [Send Test Email]                                           │   │
│  │                                                             │   │
│  │ Recent test sends:                                          │   │
│  │ ✓ test@niloptic.com  (Org scope)     2h ago   Delivered    │   │
│  │ ✓ dev@niloptic.com   (Program scope) 1d ago   Delivered    │   │
│  │ ✗ qa@niloptic.com    (Athlete scope) 2d ago   Bounced      │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Access Control

| Condition                              | Behavior                                        |
|----------------------------------------|------------------------------------------------|
| User has `admin` scope                 | Full access to all `/admin` routes              |
| User has `designer` scope              | Full access to all `/admin` routes              |
| User has `admin` + `designer` scope    | Full access + cross-shell link to `/designer`   |
| Non-admin/non-designer authenticated   | Redirect to `/dashboard`                        |
| Unauthenticated user                   | Redirect to `/login`                            |

### Cross-Shell Navigation

| Current Shell    | Condition              | Link Displayed            |
|------------------|------------------------|---------------------------|
| `/admin`         | User has designer scope| Show link to `/designer`  |
| `/designer`      | User has admin scope   | Show link to `/admin`     |

---

## Design Tokens

### Admin-Specific Layout Tokens

| Token                          | Value    | Usage                                |
|--------------------------------|----------|--------------------------------------|
| `--admin-nav-width`            | 280px    | Left sidebar collapsed width         |
| `--admin-nav-width-collapsed`  | 64px     | Left sidebar collapsed state         |
| `--admin-content-max-width`    | 1440px   | Main content area max width          |
| `--admin-content-padding`      | 32px     | Content area padding (space-8)       |
| `--admin-card-gap`             | 24px     | Gap between dashboard cards (space-6)|
| `--admin-table-row-height`     | 48px     | Standard table row height            |

### Status Color Tokens

| Token                    | Value     | Usage                        |
|--------------------------|-----------|------------------------------|
| `--status-success`       | `#22C55E` | Completed, active, healthy   |
| `--status-warning`       | `#F59E0B` | Stale, pending, review       |
| `--status-error`         | `#EF4444` | Failed, expired, critical    |
| `--status-info`          | `#3B82F6` | Running, in-progress, queued |
| `--status-neutral`       | `#71717A` | Inactive, disabled           |

### Surface Tokens (Dark Mode Default)

| Token                    | Value     | Usage                        |
|--------------------------|-----------|------------------------------|
| `--surface-canvas`       | `#000000` | Page background              |
| `--surface-base`         | `#09090B` | Section backgrounds          |
| `--surface-card`         | `#18181B` | Card containers              |
| `--surface-elevated`     | `#27272A` | Inputs, floating elements    |

---

## Responsive Behavior

### Breakpoint Adaptations

| Breakpoint | Sidebar           | Content Grid          | Cards              |
|------------|-------------------|-----------------------|--------------------|
| `2xl`      | 280px fixed       | 4-col metric cards    | 2-col job cards    |
| `xl`       | 280px fixed       | 4-col metric cards    | 2-col job cards    |
| `lg`       | 280px collapsible | 3-col metric cards    | 2-col job cards    |
| `md`       | Hidden + overlay  | 2-col metric cards    | 1-col job cards    |
| `sm`       | Hidden + overlay  | 1-col metric cards    | 1-col job cards    |

### Mobile Navigation

On viewports below `lg` (1024px):
- Left sidebar collapses to hamburger menu overlay
- Top nav condenses: Huddles and Messages become icon-only
- Role switcher moves into avatar dropdown
- Metric cards stack vertically with horizontal scroll option
- Tables switch to card-based list views

---

## Accessibility

### ARIA Requirements

| Element              | ARIA Role          | Additional Attributes                     |
|----------------------|--------------------|-------------------------------------------|
| Left navigation      | `navigation`       | `aria-label="Admin navigation"`           |
| Sync status badges   | `status`           | `aria-live="polite"`                      |
| Progress bars        | `progressbar`      | `aria-valuenow`, `aria-valuemax`          |
| Metric cards         | `region`           | `aria-label="{metric name}"`             |
| Data tables          | `table`            | Column headers with `scope="col"`         |
| Action buttons       | `button`           | Disabled state with `aria-disabled`       |
| Modal dialogs        | `dialog`           | `aria-modal="true"`, focus trap           |
| Alert notifications  | `alert`            | `aria-live="assertive"` for errors        |

### Color Contrast

All text/background combinations follow WCAG AAA compliance as defined in the color system:
- Primary text on card surfaces: 15.4:1 minimum
- Secondary text on card surfaces: 9.7:1 minimum
- Status badge text meets AA Large minimum (4.5:1)
- Red brand color used only for display metrics, buttons, and badges at 18px+ bold or 24px+ regular

### Keyboard Navigation

- All interactive elements are focusable via Tab
- Enter/Space activates buttons and links
- Escape closes modals and overlays
- Arrow keys navigate within tables and dropdown menus
- Sidebar shortcuts (1-9) provide fast page switching

---

## Data Fonts

All numeric data, metrics, timestamps, and monospaced content use `JetBrains Mono`. All UI labels, headings, and body text use `Inter`.

| Content Type       | Font            | Weight    | Example           |
|--------------------|-----------------|-----------|-------------------|
| Metric values      | JetBrains Mono  | 600       | `2,847`           |
| Percentages        | JetBrains Mono  | 600       | `99.97%`          |
| Timestamps         | JetBrains Mono  | 400       | `2h ago`          |
| Status codes       | JetBrains Mono  | 500       | `COMPLETED`       |
| Record counts      | JetBrains Mono  | 400       | `48/48`           |
| Page headings      | Inter           | 600       | Admin Control Center |
| Card labels        | Inter           | 500       | ACTIVE USERS      |
| Body text          | Inter           | 400       | Description text  |
| Nav items          | Inter           | 500       | Onboarding        |

---

*NIL Optic -- The engine behind the intelligence.*
