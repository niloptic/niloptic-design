# NIL Compliance Tracking Feature Spec

Last updated: 2026-03-04

---

## Overview

Compliance monitoring for athletic departments ensuring all NIL deals meet NCAA, conference, and state regulations. The compliance surface is the guardrail layer for every deal that flows through NIL Optic. It provides real-time status tracking, automated flagging for expired or non-conforming deals, audit trails for NCAA reporting, and state-specific regulation awareness. For ADs, compliance is a top-level dashboard concern — every deal must pass compliance review before it is considered active.

---

## Compliance Dashboard

```
┌──────────────────────────────────────────────────┐
│  NIL COMPLIANCE                   [Export Report]│
│  ──────────────────────────────────────────────  │
│                                                  │
│  STATUS SUMMARY                                  │
│  ┌──────────────┐ ┌──────────────┐ ┌────────────┐
│  │  ✓ 142       │ │  ⚠ 12       │ │  ✗ 3      │
│  │  Compliant   │ │  Review      │ │  Violation │
│  │              │ │  Needed      │ │  / Expired │
│  └──────────────┘ └──────────────┘ └────────────┘
│                                                  │
│  COMPLIANCE RATE                                 │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │       ╭─────────────╮                        ││
│  │      ╱  90.4%        ╲                       ││  ← Gauge ring
│  │     │   Compliant     │                       ││     Red = below 85%
│  │      ╲               ╱                        ││     Green = above 90%
│  │       ╰─────────────╯                        ││     Yellow = 85-90%
│  │                                              ││
│  │  Target: 95%        Last audit: Feb 28, 2026 ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  RECENT ALERTS                                   │
│  ┌──────────────────────────────────────────────┐│
│  │ ✗ Nike deal for M. Thompson — contract       ││
│  │   expired Feb 28. Renewal or removal needed. ││
│  │   [Review Deal]                    2 hrs ago ││
│  ├──────────────────────────────────────────────┤│
│  │ ⚠ Gatorade deal for K. Williams — missing    ││
│  │   state disclosure form (Kentucky).           ││
│  │   [Review Deal]                    5 hrs ago ││
│  ├──────────────────────────────────────────────┤│
│  │ ⚠ Under Armour deal for J. Proctor — pending ││
│  │   compliance review for 14+ days.             ││
│  │   [Review Deal]                   1 day ago  ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  UPCOMING DEADLINES                              │
│  ┌──────────────────────────────────────────────┐│
│  │ Mar 10  M. Thompson — Nike renewal deadline  ││
│  │ Mar 15  K. Williams — KY disclosure due      ││
│  │ Mar 22  Annual NCAA NIL report submission    ││
│  │ Apr 01  Q1 compliance audit closes           ││
│  └──────────────────────────────────────────────┘│
│                                                  │
└──────────────────────────────────────────────────┘
```

### Dashboard Anatomy

| Element               | Token / Style                          |
|-----------------------|----------------------------------------|
| Status card (green)   | `#16A34A` bg at 15%, green border      |
| Status card (yellow)  | `#F59E0B` bg at 15%, amber border      |
| Status card (red)     | `#DC2626` bg at 15%, red border        |
| Status count          | JetBrains Mono 32, white               |
| Status label          | Inter Regular 12, zinc-400             |
| Gauge ring            | 160px diameter, 12px stroke            |
| Gauge fill color      | Green >90%, yellow 85-90%, red <85%    |
| Gauge percentage      | JetBrains Mono 28, white               |
| Alert row             | zinc-800 bg, 12px padding, left border |
| Alert icon (error)    | `--color-brand-red`                    |
| Alert icon (warning)  | `#F59E0B`                              |
| Deadline row          | zinc-800 bg, 8px padding               |
| Deadline date         | JetBrains Mono 13, zinc-300            |
| Deadline text         | Inter Regular 13, zinc-400             |

---

## Deal Compliance Card

```
┌──────────────────────────────────────────────────┐
│  ┌────────────────────────────────────────────┐  │
│  │  Nike Campus Ambassador Deal               │  │
│  │  ──────────────────────────────────────── │  │
│  │                                            │  │
│  │  Athlete:    Marcus Thompson               │  │
│  │  Brand:      Nike, Inc.                    │  │
│  │  Value:      $50,000 / 12 months           │  │
│  │                                            │  │
│  │  STATUS                                    │  │
│  │  ┌──────────────────────────────────────┐  │  │
│  │  │  ⚠ PENDING REVIEW                    │  │  │  ← Status badge
│  │  │    Awaiting compliance officer sign-off│  │  │
│  │  └──────────────────────────────────────┘  │  │
│  │                                            │  │
│  │  REQUIRED DISCLOSURES                      │  │
│  │  ✓ NCAA activity report filed              │  │
│  │  ✓ University notification submitted       │  │
│  │  ✗ State disclosure form (Kentucky)        │  │  ← Missing item
│  │  ✓ Brand contract on file                  │  │
│  │  ○ Conference compliance check             │  │  ← Pending
│  │                                            │  │
│  │  STATE REQUIREMENTS: Kentucky              │  │
│  │  ┌──────────────────────────────────────┐  │  │
│  │  │  KY requires athlete disclosure to   │  │  │
│  │  │  institution within 7 days of deal.  │  │  │
│  │  │  Status: OVERDUE (14 days)           │  │  │
│  │  └──────────────────────────────────────┘  │  │
│  │                                            │  │
│  │  Last Reviewed:   Feb 14, 2026             │  │
│  │  Next Review Due: Mar 14, 2026             │  │
│  │  Reviewer:        AD Smith                 │  │
│  │                                            │  │
│  │  [Approve]  [Flag Issue]  [View Full Deal] │  │
│  │                                            │  │
│  └────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────┘
```

### Compliance Status Badges

| Status          | Background          | Border             | Icon  |
|-----------------|---------------------|---------------------|-------|
| Compliant       | `#16A34A` at 15%    | `#16A34A` 2px       | ✓     |
| Pending Review  | `#F59E0B` at 15%    | `#F59E0B` 2px       | ⚠     |
| Flagged         | `#DC2626` at 15%    | `#DC2626` 2px       | ⚑     |
| Expired         | zinc-700            | zinc-500 2px        | ✗     |

### Disclosure Checklist Anatomy

| Element              | Token / Style                          |
|----------------------|----------------------------------------|
| Completed item       | `#16A34A` check, Inter Regular 13      |
| Missing item         | `#DC2626` cross, Inter Medium 13       |
| Pending item         | zinc-500 circle, Inter Regular 13      |
| State requirement    | zinc-800 bg, 8px pad, amber left border|
| Overdue text         | `--color-brand-red`, Inter Bold 12     |

---

## Compliance Audit Trail

```
┌──────────────────────────────────────────────────┐
│  AUDIT TRAIL                       [Export CSV]  │
│  Nike Deal — Marcus Thompson                     │
│  ──────────────────────────────────────────────  │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │  ● Mar 4, 2026  14:22                        ││
│  │  Reviewer: AD Smith                          ││
│  │  Action: Flagged — missing KY disclosure      ││
│  │  Notes: "Contact athlete rep to submit        ││
│  │          state form within 48 hours."         ││
│  ├──────────────────────────────────────────────┤│
│  │  ● Feb 28, 2026  09:15                       ││
│  │  Reviewer: Compliance Bot (auto)             ││
│  │  Action: Contract expiration warning          ││
│  │  Notes: "Original contract expires Feb 28.    ││
│  │          Renewal required for continued use." ││
│  ├──────────────────────────────────────────────┤│
│  │  ● Feb 14, 2026  16:45                       ││
│  │  Reviewer: AD Smith                          ││
│  │  Action: Quarterly review — PASSED            ││
│  │  Notes: "All disclosures current.             ││
│  │          Next review: Mar 14."                ││
│  ├──────────────────────────────────────────────┤│
│  │  ● Feb 1, 2026  10:00                        ││
│  │  Reviewer: Agent Rivera                      ││
│  │  Action: Deal submitted for compliance review ││
│  │  Notes: "Initial deal submission. Contract    ││
│  │          and NCAA report attached."           ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  Showing 4 of 4 entries    [Load More]           │
│                                                  │
│  [Export for NCAA Reporting]                      │
└──────────────────────────────────────────────────┘
```

### Audit Trail Anatomy

| Element           | Token / Style                           |
|-------------------|-----------------------------------------|
| Timeline marker   | 10px circle, `--color-brand-red`        |
| Timeline line     | 2px solid, zinc-700                     |
| Date/time         | JetBrains Mono 12, zinc-400             |
| Reviewer name     | Inter Semi-Bold 13, white               |
| Action text       | Inter Medium 13, white                  |
| Notes             | Inter Regular 13, zinc-400, italic      |
| Auto-generated    | zinc-500 text, "[auto]" suffix          |
| Export button     | Secondary button, zinc-700 bg           |

---

## State Regulation Tracker

```
┌──────────────────────────────────────────────────┐
│  STATE NIL REGULATIONS              [Search]     │
│  ──────────────────────────────────────────────  │
│                                                  │
│  ┌────┬───────────┬──────────┬─────────┬───────┐│
│  │ ST │ State     │ Key Rule │Athletes │ Deals ││
│  ├────┼───────────┼──────────┼─────────┼───────┤│
│  │ KY │ Kentucky  │ 7-day    │ 24      │ 38   ││
│  │    │           │ disclosure│         │      ││
│  ├────┼───────────┼──────────┼─────────┼───────┤│
│  │ CA │ California│ No inst. │ 8       │ 12   ││
│  │    │           │ involve  │         │      ││
│  ├────┼───────────┼──────────┼─────────┼───────┤│
│  │ TX │ Texas     │ 30-day   │ 31      │ 47   ││
│  │    │           │ notice   │         │      ││
│  ├────┼───────────┼──────────┼─────────┼───────┤│
│  │ FL │ Florida   │ No school│ 18      │ 29   ││
│  │    │           │ marks    │         │      ││
│  └────┴───────────┴──────────┴─────────┴───────┘│
│                                                  │
│  ──────────────────────────────────────────────  │
│                                                  │
│  CROSS-STATE FLAG                                │
│  ┌──────────────────────────────────────────────┐│
│  │  ⚠ M. Thompson (KY) has a deal with brand   ││
│  │    headquartered in CA. California's          ││
│  │    institutional involvement restriction may  ││
│  │    apply to deal structure.                   ││
│  │    [Review Deal]  [Dismiss]                  ││
│  └──────────────────────────────────────────────┘│
│                                                  │
└──────────────────────────────────────────────────┘
```

### State Tracker Anatomy

| Element             | Token / Style                          |
|---------------------|----------------------------------------|
| State code          | JetBrains Mono 14, `--color-brand-red` |
| State name          | Inter Semi-Bold 14, white              |
| Key rule            | Inter Regular 13, zinc-400             |
| Athlete count       | JetBrains Mono 14, white               |
| Deal count          | JetBrains Mono 14, zinc-300            |
| Cross-state flag    | zinc-800 bg, amber left border, 12px pad|
| Flag icon           | `#F59E0B`, 16px                        |

---

## Role-Based Behavior

| Capability                    | AD               | Coach            | Agent              | Athlete           |
|-------------------------------|------------------|------------------|---------------------|-------------------|
| Compliance dashboard          | Full             | Team overview     | Client deals        | Personal deals    |
| Approve deals                 | Yes              | No               | No                  | No                |
| Flag issues                   | Yes              | No               | Yes (client only)   | No                |
| View audit trail              | Full             | Team deals only   | Client deals only   | Own deals only    |
| State regulation tracker      | Full             | Read-only         | Read-only           | No                |
| Export for NCAA               | Yes              | No               | No                  | No                |
| Receive compliance alerts     | All program      | Team-scoped       | Client-scoped       | Personal only     |
| Override compliance status    | Yes (with audit) | No               | No                  | No                |

### AD Compliance Workflow

1. Deal enters pipeline via agent or athlete
2. System auto-checks required disclosures
3. Compliance dashboard surfaces missing items
4. AD reviews and either approves or flags
5. Flagged deals return to agent/athlete for correction
6. Approved deals move to "Compliant" status
7. Quarterly audit cycles re-verify all active deals

---

## States

### All Compliant
```
┌──────────────────────────────────────────────────┐
│  NIL COMPLIANCE                                  │
│                                                  │
│              [✓ Icon, 48px, green]               │
│                                                  │
│              All deals compliant                  │
│              157 active deals passing all checks. │
│              Next scheduled audit: Apr 1, 2026.   │
│                                                  │
│              [View All Deals]                     │
└──────────────────────────────────────────────────┘
```

### Has Warnings
- Yellow accent on dashboard header
- Warning count prominently displayed
- Deadline countdown for pending items
- Suggested actions list

### Has Violations
- Red accent on dashboard header
- Violation cards pinned to top of feed
- Blocking indicator: deals with violations cannot advance in pipeline
- Escalation path shown (AD notification → conference reporting if unresolved)

### Audit In Progress
```
┌──────────────────────────────────────────────────┐
│  NIL COMPLIANCE              [● Audit Active]    │
│                                                  │
│  Q1 2026 COMPLIANCE AUDIT                        │
│  Progress: ████████████░░░░░░░░  62%            │
│                                                  │
│  Deals reviewed: 98 of 157                       │
│  Issues found: 4                                 │
│  Estimated completion: Mar 8, 2026               │
│                                                  │
│  [Continue Audit]   [Pause Audit]                │
└──────────────────────────────────────────────────┘
```

---

## Routes

| Route                               | Description                      |
|-------------------------------------|----------------------------------|
| `/dashboard/compliance`             | Compliance dashboard             |
| `/dashboard/compliance/deals`       | All deals compliance list        |
| `/dashboard/compliance/deal/[id]`   | Deal compliance detail           |
| `/dashboard/compliance/audit`       | Audit trail view                 |
| `/dashboard/compliance/regulations` | State regulation tracker         |

---

## Design Tokens

| Token Family           | Example Tokens                                        |
|------------------------|-------------------------------------------------------|
| `--compliance-*`       | `--compliance-gauge-size`, `--compliance-badge-height` |
| `--compliance-status-*`| `--compliance-status-ok`, `--compliance-status-warn`   |
| `--compliance-audit-*` | `--compliance-audit-marker`, `--compliance-audit-line` |
| `--compliance-alert-*` | `--compliance-alert-border`, `--compliance-alert-icon` |
| `--compliance-state-*` | `--compliance-state-flag-bg`                          |

---

## Accessibility

- Status badges include text labels ("Compliant", "Pending Review") alongside color indicators
- Gauge ring has screen reader text: "Compliance rate: 90.4 percent"
- Audit trail timeline is keyboard-navigable (arrow keys between entries)
- Alert feed uses `aria-live="polite"` for new compliance alerts
- Disclosure checklist items have explicit status announcements
- Export actions have visible loading states and success confirmations
