# TITAN IX: HERALD -- Email Lifecycle Matrix

Last updated: 2026-03-04

---

## Overview

Every email NIL Optic sends, organized by trigger. This matrix defines the complete email lifecycle from transactional system messages through persona-specific onboarding drips, engagement loops, re-engagement sequences, administrative notices, and basketball-specific seasonal communications. Each email entry specifies the trigger event, recipient roles, subject line template, sender identity, timing, frequency caps, and success metrics.

**Basketball is the #1 priority sport.** All example content, sample data, and default personalization references basketball programs, athletes, and conferences.

### Sending Infrastructure

| Property | Value |
|---|---|
| ESP | SendGrid (primary) |
| From domain | `mail.niloptic.com` |
| Reply domain | `reply.niloptic.com` |
| DKIM/SPF/DMARC | Enforced on all sending domains |
| Tracking domain | `click.niloptic.com` |
| Suppression list | Global + per-category |
| Bounce handling | Hard bounce = immediate suppress; soft bounce = retry 3x over 48h |

### Global Email Design Standards

| Element | Specification |
|---|---|
| Max width | 600px |
| Background | `#09090B` (zinc-950) |
| Card surface | `#18181B` (zinc-900) |
| Primary text | `#FFFFFF` (white) -- Inter 16px |
| Secondary text | `#A1A1AA` (zinc-400) -- Inter 14px |
| Data/numbers | JetBrains Mono 14px, `#FFFFFF` |
| CTA button | `#DC2626` bg, white text, 8px radius, 48px height |
| CTA hover | `#B91C1C` bg |
| Logo | NIL Optic wordmark, white, top-left, 120px width |
| Footer | Unsubscribe link, preference center link, physical address, `#71717A` text |
| Preheader | Max 90 characters, unique per email |

---

## 1. Transactional Emails

Transactional emails are system-triggered, non-marketing messages. They are exempt from unsubscribe requirements under CAN-SPAM but must still include sender identification. Transactional emails bypass all frequency caps.

### 1.1 Welcome Email

| Property | Value |
|---|---|
| Trigger | Account creation (any entry point: public signup, invite acceptance, operator signup) |
| Recipient roles | All roles |
| Subject line | `Welcome to NIL Optic -- your NIL intelligence starts now` |
| Preheader | `See the value. Own the future.` |
| From | `NIL Optic <welcome@mail.niloptic.com>` |
| Reply-to | `support@niloptic.com` |
| Send timing | Immediate (within 60 seconds of account creation) |
| Frequency cap | Once per account lifetime |
| Content | Role-specific welcome message, link to dashboard, next step CTA |
| Success metric | Open rate > 80%, click-through to dashboard > 60% |
| Template ID | `txn-welcome-001` |

**Role-specific content blocks:**

| Role | Headline | CTA Text | CTA Link |
|---|---|---|---|
| Athletic Director | `Your NIL command center is ready` | `Open Your Dashboard` | `/athletic-director` |
| Agent | `Your client intelligence platform is live` | `View Your Pipeline` | `/agent` |
| Athlete | `Your NIL value is waiting` | `See Your Valuation` | `/athlete` |
| Coach | `Your team's NIL landscape, mapped` | `Review Your Roster` | `/coach` |
| Fan | `Explore the NIL market like a pro` | `Start Exploring` | `/fan` |
| Affiliate | `Connect with athletes who need your services` | `Set Up Your Profile` | `/affiliate` |
| Agency Admin | `Your agency operations hub is online` | `Open Agency Dashboard` | `/agency-admin` |
| Affiliate Admin | `Your affiliate network is ready to grow` | `Open Affiliate Dashboard` | `/affiliate-admin` |

### 1.2 Email Verification

| Property | Value |
|---|---|
| Trigger | Account creation (email not yet verified) |
| Recipient roles | All roles |
| Subject line | `Verify your email to activate NIL Optic` |
| Preheader | `One click to unlock your NIL intelligence.` |
| From | `NIL Optic <verify@mail.niloptic.com>` |
| Reply-to | `support@niloptic.com` |
| Send timing | Immediate (within 30 seconds of account creation) |
| Frequency cap | Max 3 sends per 24 hours (re-send on request) |
| Content | Verification link (expires 24h), fallback: copy-paste code |
| Success metric | Verification completion rate > 95% within 1 hour |
| Template ID | `txn-verify-001` |

### 1.3 Password Reset

| Property | Value |
|---|---|
| Trigger | User requests password reset via `/auth/forgot-password` |
| Recipient roles | All roles |
| Subject line | `Reset your NIL Optic password` |
| Preheader | `This link expires in 1 hour.` |
| From | `NIL Optic <security@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Immediate (within 30 seconds of request) |
| Frequency cap | Max 5 per hour per email address |
| Content | Reset link (expires 1h), security notice, "didn't request this?" copy |
| Success metric | Reset completion rate > 90% within 15 minutes |
| Template ID | `txn-pwreset-001` |

### 1.4 Invite Accepted Confirmation

| Property | Value |
|---|---|
| Trigger | Invited user accepts an organization/program invite |
| Recipient roles | Inviter (AD, Agency Admin, Affiliate Admin, Admin) |
| Subject line | `{InviteeName} accepted your invite to {OrgName}` |
| Preheader | `Your team is growing. View their profile now.` |
| From | `NIL Optic <notifications@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Immediate on invite acceptance |
| Frequency cap | 1 per invite event (transactional) |
| Content | Invitee name, role assigned, org/program context, link to team roster |
| Success metric | Open rate > 70% |
| Template ID | `txn-invite-accepted-001` |

### 1.5 Invite Expired Notice

| Property | Value |
|---|---|
| Trigger | Invite token passes expiration date without acceptance |
| Recipient roles | Inviter (AD, Agency Admin, Affiliate Admin, Admin) |
| Subject line | `Invite to {InviteeEmail} for {OrgName} has expired` |
| Preheader | `Re-send or revoke the invitation.` |
| From | `NIL Optic <notifications@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Within 1 hour of expiration |
| Frequency cap | 1 per invite expiration event |
| Content | Invitee email, role, expiration date, CTA to re-invite or revoke |
| Success metric | Re-invite rate > 40% |
| Template ID | `txn-invite-expired-001` |

### 1.6 Invite Email (Outbound to Invitee)

| Property | Value |
|---|---|
| Trigger | Admin/AD/Agency Admin sends invite via platform |
| Recipient roles | Invitee (any role being invited) |
| Subject line | `{InviterName} invited you to {OrgName} on NIL Optic` |
| Preheader | `Join your team and start managing NIL intelligence.` |
| From | `NIL Optic <invites@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Immediate on invite creation |
| Frequency cap | Max 3 re-sends per invite per 7 days |
| Content | Inviter name, org name, program name, role, expiration date, accept CTA |
| Success metric | Accept rate > 65% within 72 hours |
| Template ID | `txn-invite-outbound-001` |
| Preview route | `/api/admin/invite-email/preview` |
| Test send route | `/api/admin/invite-email/test-send` |

---

## 2. Onboarding Drip Sequences

Persona-specific drip sequences designed to guide each user from account creation to full platform activation. Each sequence is triggered by onboarding completion (or partial completion) and follows a timed cadence. Drip emails stop immediately if the user completes the target action before the scheduled send.

**Global drip rules:**
- All drip emails respect the global frequency cap (max 1 marketing email per day, excluding transactional)
- If a drip email conflicts with a higher-priority engagement email, the drip is deferred by 24 hours
- Users who complete the drip's target action before send time are removed from that send
- All drip emails include an unsubscribe link and preference center link
- Basketball-first content: all examples reference basketball athletes, programs, and conferences

### 2.1 Athletic Director Drip Sequence

| Day | Email ID | Subject Line | Goal | CTA | Target Action | Success Metric |
|---|---|---|---|---|---|---|
| 1 | `drip-ad-d1` | `Your NIL command center: 3 things to do first` | Orient to dashboard | `Open Dashboard` | Visit `/athletic-director` | Dashboard visit within 24h > 70% |
| 3 | `drip-ad-d3` | `Set up compliance tracking for {ProgramName}` | Compliance configuration | `Configure Compliance` | Visit `/dashboard/compliance` | Compliance page visit > 50% |
| 7 | `drip-ad-d7` | `Your roster is ready for review -- {AthleteCount} athletes loaded` | Roster engagement | `Review Roster` | View roster page | Roster page visit > 55% |
| 14 | `drip-ad-d14` | `Your first NIL prediction is ready` | Prediction feature adoption | `View Prediction` | View `/predictions` | Prediction view > 40% |
| 30 | `drip-ad-d30` | `Q{Quarter} NIL review: prep your board presentation` | QBR adoption | `Download QBR Template` | Download or view QBR | QBR engagement > 30% |

**From:** `NIL Optic <onboarding@mail.niloptic.com>`
**Reply-to:** `support@niloptic.com`

### 2.2 Agent Drip Sequence

| Day | Email ID | Subject Line | Goal | CTA | Target Action | Success Metric |
|---|---|---|---|---|---|---|
| 1 | `drip-agent-d1` | `Your NIL intelligence platform is live -- here's where to start` | Orient to pipeline | `Open Your Pipeline` | Visit `/agent` | Dashboard visit within 24h > 75% |
| 2 | `drip-agent-d2` | `Add your first client to unlock deal intelligence` | Client onboarding | `Add a Client` | Add at least 1 client | Client added > 60% |
| 5 | `drip-agent-d5` | `Your deal pipeline: track every opportunity in one place` | Pipeline adoption | `View Deal Pipeline` | Visit `/dashboard/pipelines` | Pipeline visit > 50% |
| 10 | `drip-agent-d10` | `Brand matching is live -- see which brands fit your clients` | Brand matching feature | `Explore Brand Matches` | View brand matching | Brand match view > 35% |
| 21 | `drip-agent-d21` | `Portfolio review: how your clients are performing this month` | Portfolio engagement | `View Portfolio Report` | View portfolio report | Report view > 30% |

**From:** `NIL Optic <onboarding@mail.niloptic.com>`
**Reply-to:** `support@niloptic.com`

### 2.3 Athlete Drip Sequence

| Day | Email ID | Subject Line | Goal | CTA | Target Action | Success Metric |
|---|---|---|---|---|---|---|
| 0 | `drip-ath-d0` | `{FirstName}, your NIL value is live -- check it now` | Instant value reveal | `See Your Valuation` | View `/athlete` valuation | Valuation view within 1h > 80% |
| 1 | `drip-ath-d1` | `What drives your NIL value? Here's the breakdown` | Education on valuation | `Explore Your Breakdown` | View valuation detail | Detail view > 60% |
| 3 | `drip-ath-d3` | `Connect your socials to boost your NIL profile` | Social integration | `Connect Socials` | Link at least 1 social account | Social connect > 45% |
| 7 | `drip-ath-d7` | `New deal alert: a brand wants to work with you` | Deal awareness | `View Deal Alert` | View deal notification | Deal alert click > 50% |
| 14 | `drip-ath-d14` | `3 tips to grow your NIL value this season` | Growth education | `Read Growth Tips` | Click through to tips | Tips engagement > 35% |

**From:** `NIL Optic <onboarding@mail.niloptic.com>`
**Reply-to:** `support@niloptic.com`

### 2.4 Coach Drip Sequence

| Day | Email ID | Subject Line | Goal | CTA | Target Action | Success Metric |
|---|---|---|---|---|---|---|
| 1 | `drip-coach-d1` | `Your team's NIL landscape is mapped -- take a look` | Dashboard orientation | `View Team Dashboard` | Visit `/coach` | Dashboard visit > 65% |
| 3 | `drip-coach-d3` | `Review your team roster with NIL valuations attached` | Roster engagement | `Open Team Roster` | View roster page | Roster view > 55% |
| 7 | `drip-coach-d7` | `Recruiting pipeline: track NIL-eligible prospects` | Pipeline adoption | `View Recruiting Pipeline` | Visit pipeline | Pipeline visit > 40% |
| 14 | `drip-coach-d14` | `NIL budget review: where your program stands` | Budget awareness | `View Budget Overview` | View budget page | Budget view > 35% |

**From:** `NIL Optic <onboarding@mail.niloptic.com>`
**Reply-to:** `support@niloptic.com`

### 2.5 Fan Drip Sequence

| Day | Email ID | Subject Line | Goal | CTA | Target Action | Success Metric |
|---|---|---|---|---|---|---|
| 0 | `drip-fan-d0` | `Welcome to the NIL market -- explore like a pro` | Instant engagement | `Start Exploring` | Visit `/fan` | Dashboard visit within 1h > 70% |
| 1 | `drip-fan-d1` | `Top 10 most valuable basketball players this week` | Content hook | `See the Rankings` | View athlete rankings | Rankings click > 55% |
| 3 | `drip-fan-d3` | `Build your dream roster with Roster Builder` | Feature adoption | `Try Roster Builder` | Use Roster Builder | Roster Builder use > 40% |
| 7 | `drip-fan-d7` | `Unlock full valuations and predictions -- upgrade your plan` | Conversion | `See Upgrade Options` | View pricing page | Pricing page visit > 20% |

**From:** `NIL Optic <onboarding@mail.niloptic.com>`
**Reply-to:** `support@niloptic.com`

### 2.6 Affiliate Drip Sequence

| Day | Email ID | Subject Line | Goal | CTA | Target Action | Success Metric |
|---|---|---|---|---|---|---|
| 1 | `drip-aff-d1` | `Welcome to the NIL Optic affiliate network` | Orient to platform | `Open Your Dashboard` | Visit `/affiliate` | Dashboard visit > 65% |
| 3 | `drip-aff-d3` | `Set up your service catalog -- athletes are searching` | Catalog setup | `Add Services` | Add at least 1 service | Service added > 50% |
| 7 | `drip-aff-d7` | `Your first client match is ready` | Client matching | `View Your Match` | View match notification | Match view > 40% |

**From:** `NIL Optic <onboarding@mail.niloptic.com>`
**Reply-to:** `support@niloptic.com`

---

## 3. Engagement Emails

Recurring emails designed to drive ongoing platform usage and feature adoption. These are marketing emails and fully respect unsubscribe preferences and frequency caps.

### 3.1 Weekly Digest

| Property | Value |
|---|---|
| Trigger | Automated weekly schedule (every Monday at 8:00 AM ET) |
| Recipient roles | All active users (logged in within last 30 days) |
| Subject line | `Your NIL Week in Review -- {WeekDateRange}` |
| Preheader | Role-specific: see content blocks below |
| From | `NIL Optic <digest@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Monday 8:00 AM ET (send-time optimized per user after 4 weeks of data) |
| Frequency cap | 1 per week (skipped if user received 5+ emails in trailing 7 days) |
| Template ID | `eng-weekly-digest-001` |
| Success metric | Open rate > 35%, click-through > 12% |

**Role-specific content blocks:**

| Role | Content Block 1 | Content Block 2 | Content Block 3 |
|---|---|---|---|
| Athletic Director | Program valuation summary | Compliance status snapshot | Top mover athletes |
| Agent | Client portfolio performance | Deal pipeline updates | New brand matching opportunities |
| Athlete | Personal valuation trend | Deal status updates | Social media impact score |
| Coach | Team valuation leaderboard | Recruiting pipeline summary | Upcoming calendar events |
| Fan | Top 10 athletes by valuation | Tournament impact highlights | New athletes to follow |
| Affiliate | Client activity summary | New match opportunities | Platform tips |

### 3.2 Monthly Report

| Property | Value |
|---|---|
| Trigger | Automated monthly schedule (1st of each month at 9:00 AM ET) |
| Recipient roles | AD, Agent, Agency Admin, Affiliate Admin |
| Subject line | `{MonthName} NIL Intelligence Report -- {OrgName}` |
| Preheader | `Your monthly NIL performance summary is ready.` |
| From | `NIL Optic <reports@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | 1st of month, 9:00 AM ET |
| Frequency cap | 1 per month |
| Template ID | `eng-monthly-report-001` |
| Success metric | Open rate > 45%, download/view full report > 25% |

**Content:** Month-over-month valuation trends, deal flow summary, compliance rate, top-performing athletes, prediction accuracy score, budget utilization (AD only).

### 3.3 Valuation Change Alert

| Property | Value |
|---|---|
| Trigger | Athlete valuation changes by more than 10% in 24 hours |
| Recipient roles | AD (program athletes), Agent (client athletes), Athlete (own valuation), Coach (team athletes) |
| Subject line | `{AthleteName} valuation {up/down} {X}% -- {Reason}` |
| Preheader | `See what's driving the change and what it means for deals.` |
| From | `NIL Optic <alerts@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Within 1 hour of threshold breach |
| Frequency cap | Max 3 valuation alerts per user per day; batch if > 3 athletes change |
| Template ID | `eng-valuation-alert-001` |
| Success metric | Open rate > 50%, click-through to athlete profile > 30% |

### 3.4 Deal Milestone Email

| Property | Value |
|---|---|
| Trigger | Deal reaches a key stage: `Negotiation`, `Signed`, `Completed`, `Expired` |
| Recipient roles | AD (program deals), Agent (client deals), Athlete (own deals) |
| Subject line | `Deal update: {AthleteName} x {BrandName} -- {StageName}` |
| Preheader | `Your deal pipeline has moved. Review the details.` |
| From | `NIL Optic <deals@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Within 30 minutes of stage change |
| Frequency cap | Max 5 deal emails per user per day |
| Template ID | `eng-deal-milestone-001` |
| Success metric | Open rate > 55%, click-through to deal > 40% |

### 3.5 Prediction Accuracy Update

| Property | Value |
|---|---|
| Trigger | Prediction model accuracy recalculated (weekly, after game results processed) |
| Recipient roles | AD, Agent, Coach |
| Subject line | `Prediction accuracy update: {AccuracyPercent}% for {ProgramName}` |
| Preheader | `See how NIL Optic's AI predictions are performing.` |
| From | `NIL Optic <intelligence@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Wednesday 10:00 AM ET (after weekend game data processing) |
| Frequency cap | 1 per week |
| Template ID | `eng-prediction-accuracy-001` |
| Success metric | Open rate > 30%, click-through to predictions > 15% |

---

## 4. Re-engagement Emails

Automated sequences triggered by declining user activity. Goal: bring inactive users back to the platform before they churn. Each stage escalates urgency and offer.

### 4.1 Seven-Day Inactive

| Property | Value |
|---|---|
| Trigger | User has not logged in for 7 consecutive days |
| Recipient roles | All roles except Admin |
| Subject line | `You're missing out -- {PersonalizedHook}` |
| Preheader | `Your NIL intelligence is waiting. Here's what changed.` |
| From | `NIL Optic <hello@mail.niloptic.com>` |
| Reply-to | `support@niloptic.com` |
| Send timing | Day 7 of inactivity, 10:00 AM user local time |
| Frequency cap | 1 per re-engagement cycle |
| Template ID | `re-engage-7d-001` |
| Success metric | Return rate > 25% within 48 hours |

**Personalized hooks by role:**

| Role | Subject Line Hook | Content Focus |
|---|---|---|
| Athletic Director | `3 compliance alerts need your attention` | Compliance status, valuation movers |
| Agent | `{ClientCount} client valuations changed this week` | Portfolio changes, new opportunities |
| Athlete | `Your valuation moved {Direction} -- see the update` | Valuation change, deal opportunities |
| Coach | `{X} roster changes since your last visit` | Roster updates, recruiting pipeline |
| Fan | `Top 5 NIL movers you haven't seen yet` | Trending athletes, tournament impact |
| Affiliate | `{X} new potential clients matched to your services` | Client matches, directory visibility |

### 4.2 Fourteen-Day Inactive

| Property | Value |
|---|---|
| Trigger | User has not logged in for 14 consecutive days (and did not return after 7-day email) |
| Recipient roles | All roles except Admin |
| Subject line | `We saved your spot -- {OrgName} needs you back` |
| Preheader | `Your team is active. Don't fall behind.` |
| From | `NIL Optic <hello@mail.niloptic.com>` |
| Reply-to | `support@niloptic.com` |
| Send timing | Day 14 of inactivity, 10:00 AM user local time |
| Frequency cap | 1 per re-engagement cycle |
| Template ID | `re-engage-14d-001` |
| Success metric | Return rate > 15% within 48 hours |

**Content:** Summary of activity they missed (deals moved, valuations changed, messages received), social proof ("Your organization had {X} platform actions this week"), single prominent CTA to return.

### 4.3 Thirty-Day Win-Back

| Property | Value |
|---|---|
| Trigger | User has not logged in for 30 consecutive days |
| Recipient roles | All roles except Admin and Fan |
| Subject line | `{FirstName}, your NIL data is going stale -- let's fix that` |
| Preheader | `A 5-minute check-in keeps your intelligence fresh.` |
| From | `NIL Optic <hello@mail.niloptic.com>` |
| Reply-to | `support@niloptic.com` |
| Send timing | Day 30 of inactivity, 10:00 AM user local time |
| Frequency cap | 1 per re-engagement cycle |
| Template ID | `re-engage-30d-001` |
| Success metric | Return rate > 8% within 7 days |

**Content:** "Here's what you missed" summary, offer to schedule a 1:1 platform walkthrough with CS team, single CTA. For paid users, mention remaining subscription value.

### 4.4 Sixty-Day Final Attempt

| Property | Value |
|---|---|
| Trigger | User has not logged in for 60 consecutive days |
| Recipient roles | All paid roles (AD, Agent, Agency Admin, Affiliate Admin) |
| Subject line | `Last check-in: is NIL Optic still right for {OrgName}?` |
| Preheader | `We'd love your feedback before we close the loop.` |
| From | `NIL Optic <hello@mail.niloptic.com>` |
| Reply-to | `support@niloptic.com` |
| Send timing | Day 60 of inactivity, 10:00 AM user local time |
| Frequency cap | 1 per re-engagement cycle (terminal -- no further emails after this) |
| Template ID | `re-engage-60d-001` |
| Success metric | Return rate > 3%; feedback survey completion > 10% |

**Content:** Direct ask: "Are you still using NIL Optic?" with three options: (1) Yes, take me back, (2) I need help, (3) I'm done. Option 3 links to cancellation feedback survey. No further automated emails after this unless user re-engages.

---

## 5. Administrative Emails

System-generated emails related to billing, account status, and platform administration.

### 5.1 Plan Upgrade Confirmation

| Property | Value |
|---|---|
| Trigger | User or org admin upgrades subscription plan |
| Recipient roles | Account owner (AD, Agency Admin, Affiliate Admin) |
| Subject line | `Plan upgraded to {PlanName} -- new features unlocked` |
| Preheader | `Your team now has access to {FeatureHighlight}.` |
| From | `NIL Optic <billing@mail.niloptic.com>` |
| Reply-to | `billing@niloptic.com` |
| Send timing | Immediate on successful plan change |
| Frequency cap | 1 per plan change event |
| Template ID | `admin-plan-upgrade-001` |
| Success metric | Open rate > 75% |

### 5.2 Plan Downgrade Confirmation

| Property | Value |
|---|---|
| Trigger | User or org admin downgrades subscription plan |
| Recipient roles | Account owner |
| Subject line | `Plan changed to {PlanName} -- effective {EffectiveDate}` |
| Preheader | `Your access will adjust at the end of your current billing period.` |
| From | `NIL Optic <billing@mail.niloptic.com>` |
| Reply-to | `billing@niloptic.com` |
| Send timing | Immediate on downgrade request |
| Frequency cap | 1 per plan change event |
| Template ID | `admin-plan-downgrade-001` |
| Success metric | Open rate > 70% |

### 5.3 Billing Receipt

| Property | Value |
|---|---|
| Trigger | Successful payment processed |
| Recipient roles | Account owner |
| Subject line | `Payment received: ${Amount} for {PlanName} -- {BillingPeriod}` |
| Preheader | `Your invoice is attached.` |
| From | `NIL Optic <billing@mail.niloptic.com>` |
| Reply-to | `billing@niloptic.com` |
| Send timing | Immediate on payment success |
| Frequency cap | 1 per payment event |
| Template ID | `admin-billing-receipt-001` |
| Success metric | Open rate > 65% |

### 5.4 Payment Failed

| Property | Value |
|---|---|
| Trigger | Payment attempt fails (card declined, insufficient funds, expired card) |
| Recipient roles | Account owner |
| Subject line | `Action needed: payment failed for {OrgName}` |
| Preheader | `Update your payment method to avoid service interruption.` |
| From | `NIL Optic <billing@mail.niloptic.com>` |
| Reply-to | `billing@niloptic.com` |
| Send timing | Immediate on failure; retry reminders at +3 days, +7 days, +12 days |
| Frequency cap | Max 4 emails per payment failure cycle (initial + 3 retries) |
| Template ID | `admin-payment-failed-001` |
| Success metric | Payment recovery rate > 60% within 7 days |

**Escalation timeline:**

| Day | Action | Email Tone |
|---|---|---|
| 0 | Initial failure notice | Informational -- "update your payment method" |
| 3 | First retry reminder | Gentle urgency -- "your service may be interrupted" |
| 7 | Second retry reminder | Firm -- "service will be suspended in 5 days" |
| 12 | Final notice before suspension | Final -- "update now or access will be paused" |
| 14 | Account suspended (see 5.5) | Suspension notice triggered |

### 5.5 Account Suspension

| Property | Value |
|---|---|
| Trigger | Payment not resolved after 14-day grace period, or manual admin suspension |
| Recipient roles | Account owner + all org members |
| Subject line | `Your NIL Optic access has been paused` |
| Preheader | `Resolve your payment to restore full access.` |
| From | `NIL Optic <billing@mail.niloptic.com>` |
| Reply-to | `billing@niloptic.com` |
| Send timing | Immediate on suspension |
| Frequency cap | 1 per suspension event |
| Template ID | `admin-suspension-001` |
| Success metric | Reactivation rate > 40% within 7 days |

### 5.6 Data Export Ready

| Property | Value |
|---|---|
| Trigger | User-requested data export (GDPR/CCPA or manual) has finished processing |
| Recipient roles | Requesting user |
| Subject line | `Your data export is ready for download` |
| Preheader | `Download link expires in 72 hours.` |
| From | `NIL Optic <data@mail.niloptic.com>` |
| Reply-to | `support@niloptic.com` |
| Send timing | Immediate on export completion |
| Frequency cap | 1 per export request |
| Template ID | `admin-data-export-001` |
| Success metric | Download rate > 80% within 24 hours |

---

## 6. Basketball-Specific Emails

Seasonal and event-driven emails tied to the NCAA basketball calendar. These are the highest-engagement emails in the system due to the time-sensitive, high-stakes nature of basketball NIL activity.

### 6.1 March Madness Bracket Preview

| Property | Value |
|---|---|
| Trigger | NCAA Tournament bracket announced (Selection Sunday) |
| Recipient roles | All roles |
| Subject line | `March Madness NIL Impact: your bracket, valued` |
| Preheader | `See which athletes' valuations are about to surge.` |
| From | `NIL Optic <intelligence@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Within 2 hours of bracket announcement |
| Frequency cap | 1 per tournament (annual) |
| Template ID | `bball-bracket-preview-001` |
| Success metric | Open rate > 60%, click-through > 35% |

**Content by role:**

| Role | Primary Content |
|---|---|
| Athletic Director | Program athletes in the tournament, projected NIL impact by round |
| Agent | Client athletes in the bracket, deal opportunity windows |
| Athlete | Personal tournament valuation projection |
| Coach | Team impact analysis, recruiting implications |
| Fan | Full bracket with NIL valuations overlaid, top value athletes per region |

### 6.2 Tournament Valuation Surge Alert

| Property | Value |
|---|---|
| Trigger | After each tournament round, athletes whose valuations surge > 15% |
| Recipient roles | AD (program athletes), Agent (client athletes), Athlete (personal), Coach (team), Fan (favorites) |
| Subject line | `Tournament surge: {AthleteName} valuation up {X}% after {RoundName}` |
| Preheader | `{TeamName} advances and NIL values spike.` |
| From | `NIL Optic <intelligence@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | Within 4 hours of round completion |
| Frequency cap | Max 2 tournament surge emails per user per round; batch multiple athletes |
| Template ID | `bball-surge-alert-001` |
| Success metric | Open rate > 55%, click-through > 30% |

### 6.3 Transfer Portal Window Opening

| Property | Value |
|---|---|
| Trigger | NCAA transfer portal window opens (spring: Apr 15 - Apr 30; winter: Dec 4 - Dec 28) |
| Recipient roles | AD, Agent, Coach |
| Subject line | `Transfer portal is OPEN -- {WindowName} window begins now` |
| Preheader | `Track entries, valuations, and commitment projections in real time.` |
| From | `NIL Optic <intelligence@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | 8:00 AM ET on portal opening day |
| Frequency cap | 1 per portal window |
| Template ID | `bball-portal-open-001` |
| Success metric | Open rate > 50%, click-through to portal dashboard > 35% |

### 6.4 Transfer Portal Window Closing

| Property | Value |
|---|---|
| Trigger | 48 hours before NCAA transfer portal window closes |
| Recipient roles | AD, Agent, Coach |
| Subject line | `Transfer portal closes in 48 hours -- {X} athletes still uncommitted` |
| Preheader | `Last chance to act on portal prospects.` |
| From | `NIL Optic <intelligence@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | 8:00 AM ET, 48 hours before portal close |
| Frequency cap | 1 per portal window |
| Template ID | `bball-portal-close-001` |
| Success metric | Open rate > 45%, click-through to portal > 30% |

### 6.5 Signing Day Reminder

| Property | Value |
|---|---|
| Trigger | 7 days before NCAA early signing period (Nov) or late signing period (Apr) |
| Recipient roles | AD, Agent, Coach |
| Subject line | `Signing day in 7 days -- {X} prospects with NIL valuations ready` |
| Preheader | `Review prospect valuations and deal projections before commitments.` |
| From | `NIL Optic <intelligence@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | 8:00 AM ET, 7 days before signing period opens |
| Frequency cap | 1 per signing period |
| Template ID | `bball-signing-day-001` |
| Success metric | Open rate > 40%, click-through to recruiting pipeline > 25% |

### 6.6 Conference Tournament Kickoff

| Property | Value |
|---|---|
| Trigger | Conference tournament week begins (early March, varies by conference) |
| Recipient roles | AD (own conference), Agent (clients in tournament), Coach (own conference), Fan (followed conferences) |
| Subject line | `{ConferenceName} Tournament starts today -- NIL valuations to watch` |
| Preheader | `These athletes could see the biggest NIL swings this week.` |
| From | `NIL Optic <intelligence@mail.niloptic.com>` |
| Reply-to | `noreply@niloptic.com` |
| Send timing | 7:00 AM ET on first day of conference tournament |
| Frequency cap | 1 per conference tournament |
| Template ID | `bball-conf-tourney-001` |
| Success metric | Open rate > 45%, click-through > 25% |

---

## 7. Complete Email Inventory (Master Reference)

| # | Email ID | Category | Trigger | Recipient Roles | Frequency Cap |
|---|---|---|---|---|---|
| 1 | `txn-welcome-001` | Transactional | Account creation | All | 1/lifetime |
| 2 | `txn-verify-001` | Transactional | Account creation | All | 3/24h |
| 3 | `txn-pwreset-001` | Transactional | Password reset request | All | 5/hour |
| 4 | `txn-invite-accepted-001` | Transactional | Invite accepted | Inviter | 1/event |
| 5 | `txn-invite-expired-001` | Transactional | Invite expired | Inviter | 1/event |
| 6 | `txn-invite-outbound-001` | Transactional | Invite sent | Invitee | 3/7d per invite |
| 7 | `drip-ad-d1` | Onboarding | Day 1 post-signup | AD | 1/sequence |
| 8 | `drip-ad-d3` | Onboarding | Day 3 post-signup | AD | 1/sequence |
| 9 | `drip-ad-d7` | Onboarding | Day 7 post-signup | AD | 1/sequence |
| 10 | `drip-ad-d14` | Onboarding | Day 14 post-signup | AD | 1/sequence |
| 11 | `drip-ad-d30` | Onboarding | Day 30 post-signup | AD | 1/sequence |
| 12 | `drip-agent-d1` | Onboarding | Day 1 post-signup | Agent | 1/sequence |
| 13 | `drip-agent-d2` | Onboarding | Day 2 post-signup | Agent | 1/sequence |
| 14 | `drip-agent-d5` | Onboarding | Day 5 post-signup | Agent | 1/sequence |
| 15 | `drip-agent-d10` | Onboarding | Day 10 post-signup | Agent | 1/sequence |
| 16 | `drip-agent-d21` | Onboarding | Day 21 post-signup | Agent | 1/sequence |
| 17 | `drip-ath-d0` | Onboarding | Day 0 (immediate) | Athlete | 1/sequence |
| 18 | `drip-ath-d1` | Onboarding | Day 1 post-signup | Athlete | 1/sequence |
| 19 | `drip-ath-d3` | Onboarding | Day 3 post-signup | Athlete | 1/sequence |
| 20 | `drip-ath-d7` | Onboarding | Day 7 post-signup | Athlete | 1/sequence |
| 21 | `drip-ath-d14` | Onboarding | Day 14 post-signup | Athlete | 1/sequence |
| 22 | `drip-coach-d1` | Onboarding | Day 1 post-signup | Coach | 1/sequence |
| 23 | `drip-coach-d3` | Onboarding | Day 3 post-signup | Coach | 1/sequence |
| 24 | `drip-coach-d7` | Onboarding | Day 7 post-signup | Coach | 1/sequence |
| 25 | `drip-coach-d14` | Onboarding | Day 14 post-signup | Coach | 1/sequence |
| 26 | `drip-fan-d0` | Onboarding | Day 0 (immediate) | Fan | 1/sequence |
| 27 | `drip-fan-d1` | Onboarding | Day 1 post-signup | Fan | 1/sequence |
| 28 | `drip-fan-d3` | Onboarding | Day 3 post-signup | Fan | 1/sequence |
| 29 | `drip-fan-d7` | Onboarding | Day 7 post-signup | Fan | 1/sequence |
| 30 | `drip-aff-d1` | Onboarding | Day 1 post-signup | Affiliate | 1/sequence |
| 31 | `drip-aff-d3` | Onboarding | Day 3 post-signup | Affiliate | 1/sequence |
| 32 | `drip-aff-d7` | Onboarding | Day 7 post-signup | Affiliate | 1/sequence |
| 33 | `eng-weekly-digest-001` | Engagement | Weekly schedule | All active | 1/week |
| 34 | `eng-monthly-report-001` | Engagement | Monthly schedule | AD, Agent, Agency Admin, Aff Admin | 1/month |
| 35 | `eng-valuation-alert-001` | Engagement | >10% valuation change | AD, Agent, Athlete, Coach | 3/day |
| 36 | `eng-deal-milestone-001` | Engagement | Deal stage change | AD, Agent, Athlete | 5/day |
| 37 | `eng-prediction-accuracy-001` | Engagement | Weekly recalculation | AD, Agent, Coach | 1/week |
| 38 | `re-engage-7d-001` | Re-engagement | 7-day inactive | All except Admin | 1/cycle |
| 39 | `re-engage-14d-001` | Re-engagement | 14-day inactive | All except Admin | 1/cycle |
| 40 | `re-engage-30d-001` | Re-engagement | 30-day inactive | All except Admin, Fan | 1/cycle |
| 41 | `re-engage-60d-001` | Re-engagement | 60-day inactive | Paid roles only | 1/cycle (terminal) |
| 42 | `admin-plan-upgrade-001` | Administrative | Plan upgrade | Account owner | 1/event |
| 43 | `admin-plan-downgrade-001` | Administrative | Plan downgrade | Account owner | 1/event |
| 44 | `admin-billing-receipt-001` | Administrative | Payment success | Account owner | 1/event |
| 45 | `admin-payment-failed-001` | Administrative | Payment failure | Account owner | 4/cycle |
| 46 | `admin-suspension-001` | Administrative | Account suspended | Account owner + org members | 1/event |
| 47 | `admin-data-export-001` | Administrative | Export complete | Requesting user | 1/event |
| 48 | `bball-bracket-preview-001` | Basketball | Selection Sunday | All | 1/year |
| 49 | `bball-surge-alert-001` | Basketball | Tournament round end | AD, Agent, Athlete, Coach, Fan | 2/round |
| 50 | `bball-portal-open-001` | Basketball | Portal window opens | AD, Agent, Coach | 1/window |
| 51 | `bball-portal-close-001` | Basketball | Portal window -48h | AD, Agent, Coach | 1/window |
| 52 | `bball-signing-day-001` | Basketball | Signing period -7d | AD, Agent, Coach | 1/period |
| 53 | `bball-conf-tourney-001` | Basketball | Conference tournament day 1 | AD, Agent, Coach, Fan | 1/conference |

**Total unique email templates: 53**

---

## 8. Email Template Governance

### Template Management

| Process | Owner | Tool |
|---|---|---|
| Template creation | Marketing + Design | SendGrid Dynamic Templates |
| Template review | Brand + Legal | PR review in template repo |
| Template testing | QA + Marketing | `/api/admin/invite-email/test-send` (invites); SendGrid sandbox (all others) |
| Template deployment | Engineering | CI/CD pipeline, template version pinning |
| A/B testing | Marketing | SendGrid A/B testing with 10% holdout |

### Template Versioning

- All templates use SendGrid Dynamic Templates with version IDs
- Active version is pinned in application config
- Rollback: revert to previous version ID in config
- No template is deleted -- only deactivated

### Subject Line A/B Testing Protocol

| Parameter | Standard |
|---|---|
| Minimum sample size | 1,000 recipients per variant |
| Test duration | 4 hours before winner selection |
| Winner criteria | Open rate (primary), click-through (secondary) |
| Max concurrent tests | 2 per email type |
| Statistical significance | 95% confidence interval |

---

## 9. Compliance and Legal

### CAN-SPAM Requirements

| Requirement | Implementation |
|---|---|
| Physical mailing address | Included in every email footer |
| Unsubscribe mechanism | One-click unsubscribe in header + footer link |
| Unsubscribe processing | Within 24 hours (target: immediate) |
| Sender identification | Clear "From" name and address |
| Subject line accuracy | No deceptive subject lines |
| Transactional exemption | Welcome, verification, password reset, billing exempt from unsubscribe |

### GDPR Considerations

| Requirement | Implementation |
|---|---|
| Consent basis | Legitimate interest (transactional); explicit opt-in (marketing) |
| Data portability | Data export email includes all stored email preferences |
| Right to erasure | Account deletion removes all email preferences and suppression entries |
| Processing records | All sends logged with timestamp, template ID, and consent basis |

### Suppression Management

| List | Scope | Trigger |
|---|---|---|
| Global suppression | All emails | Hard bounce, spam complaint, manual unsubscribe from all |
| Category suppression | Per-category | User preference center toggle |
| Drip suppression | Specific drip | User completes target action or unsubscribes from onboarding |
| Complaint suppression | All emails | Spam complaint (immediate, permanent) |

---

*NIL Optic -- See the Value. Own the Future.*
