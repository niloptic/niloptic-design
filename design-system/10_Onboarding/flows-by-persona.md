# Per-Persona Onboarding Flows

Last updated: 2026-03-04

---

## Overview

Each persona follows a tailored onboarding flow rendered inside the shared Onboarding Wizard Template. Steps are filtered by the user's authenticated role -- never self-selected. All flows use basketball-first examples and sample data. This document defines the exact step sequence, wireframes, timing, and first-value moments for every role.

---

## Athletic Director Onboarding

### Prerequisites

- Accepted org invite with `athletic_director` role
- Organization already created (by operator or admin)
- Invite carries: `org_id`, `program_id` (optional), `role: athletic_director`

### Step 1: Welcome + Organization Context Confirmation

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 1 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────○─────○─────○─────○                       │
│  Welcome Setup  Tour  Invite  Action             │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Welcome to NIL Optic, Coach Barnhart        ││
│  │                                              ││
│  │  You've been invited to manage NIL           ││
│  │  intelligence for:                           ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  University of Kentucky               │  ││
│  │  │  Athletic Organization                │  ││
│  │  │  SEC Conference                       │  ││
│  │  │  Lexington, KY                        │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Your Role: Athletic Director                ││
│  │                                              ││
│  │  (o) This looks correct                      ││
│  │  ( ) Something needs to be updated           ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│                                    [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Source               | Editable |
|--------------------|----------------------|----------|
| User name          | Invite + auth        | No       |
| Organization name  | Invite metadata      | No       |
| Org category       | Invite metadata      | No       |
| Conference         | Org profile          | No       |
| Role               | Invite metadata      | No       |
| Confirmation       | User radio selection | Required |

### Step 2: Sport / Program Selection

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 2 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────●─────○─────○─────○                       │
│  Welcome Setup  Tour  Invite  Action             │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Select Your Programs                        ││
│  │  Choose the sports your department manages.  ││
│  │                                              ││
│  │  [x] Men's Basketball          <- first      ││
│  │      Team: Kentucky Wildcats                 ││
│  │      SportsRadar: Connected                  ││
│  │                                              ││
│  │  [ ] Women's Basketball                      ││
│  │  [ ] Football                                ││
│  │  [ ] Baseball                                ││
│  │  [ ] Softball                                ││
│  │  [ ] Volleyball                              ││
│  │  [ ] Track & Field                           ││
│  │  [ ] Swimming & Diving                       ││
│  │                                              ││
│  │  Each selection creates a program entity     ││
│  │  connected to SportsRadar team data.         ││
│  │                                              ││
│  │  Selected: 1 sport                           ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]                         [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Sport list         | Basketball always first, pre-checked         |
| SportsRadar link   | Auto-connected when team match found         |
| Minimum selection  | At least 1 sport required                    |
| Program creation   | Each checked sport creates a program entity  |

### Step 3: Budget Setup

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 3 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────○─────○                       │
│  Welcome Setup  Budget Invite  Action            │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Set Your NIL Budget                         ││
│  │  Allocate across your selected programs.     ││
│  │                                              ││
│  │  Total NIL Budget                            ││
│  │  $ [5,000,000__________]                     ││
│  │                                              ││
│  │  Sport Allocation:                           ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ Sport           Est. Value   Budget    │  ││
│  │  ├────────────────────────────────────────┤  ││
│  │  │ Men's BBall     $3,200,000  [$3,000K]  │  ││
│  │  │ Women's BBall   $1,100,000  [$1,200K]  │  ││
│  │  │ Football        $4,800,000  [$   800K] │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Allocated: $5,000,000 / $5,000,000          ││
│  │  Remaining: $0            [Balanced]         ││
│  │                                              ││
│  │  Est. Total Valuation: $9,100,000            ││
│  │  Budget vs. Estimate: -$4,100,000            ││
│  │                                              ││
│  │  You can adjust later in Org Settings.       ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]                         [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field                | Behavior                                    |
|----------------------|---------------------------------------------|
| Total budget         | Required, currency input                    |
| Sport allocation     | Basketball gets primary allocation slot      |
| Est. Value column    | Read-only, pulled from team predictions     |
| Allocation balance   | Must sum to total budget                    |
| Budget vs. Estimate  | Calculated, informational only              |

### Step 4: Invite Staff

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 4 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────●─────○                       │
│  Welcome Setup  Budget Invite  Action            │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Invite Your Staff                           ││
│  │  Build your team on NIL Optic.               ││
│  │                                              ││
│  │  Email           [________________________]  ││
│  │  Role            [Coach              ▼]      ││
│  │                  (Coach / Asst AD / GM)       ││
│  │  Program         [Men's Basketball   ▼]      ││
│  │                                              ││
│  │  [+ Add Another Invite]                      ││
│  │                                              ││
│  │  ────────────────────────────────────────── ││
│  │                                              ││
│  │  Pending Invites:                            ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ coach.cal@uky.edu   Coach   M.BBall  │  ││
│  │  │ asst.ad@uky.edu     Asst AD  All     │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  [Send All Invites]                          ││
│  │                                              ││
│  │  Or skip -- you can invite from Settings.    ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Skip]    [Next Step ->] │
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Email              | Standard email validation                    |
| Role dropdown      | AD-scoped roles: Coach, Asst AD, GM          |
| Program dropdown   | From selected sports in Step 2               |
| Bulk invite        | Add multiple before sending                  |
| This step          | Optional (can be skipped)                    |

### Step 5: First Dashboard Tour

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 5 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────●─────●                       │
│  Welcome Setup  Budget Invite  Action            │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Your Dashboard Is Ready                     ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [Preview: AD Dashboard]              │  ││
│  │  │                                        │  ││
│  │  │  KPI Cards | Roster | Compliance       │  ││
│  │  │  Valuation | Cap Table | Schedule      │  ││
│  │  │                                        │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  One more thing:                             ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [Shield Icon]                        │  ││
│  │  │                                        │  ││
│  │  │  Run Your First Compliance Check      │  ││
│  │  │  See how UK Men's Basketball stacks   │  ││
│  │  │  up against NIL guidelines.           │  ││
│  │  │                                        │  ││
│  │  │  [Run Compliance Check ->]            │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Or explore your dashboard                   ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]                [Go to Dashboard ->]   │
└──────────────────────────────────────────────────┘
```

### AD Onboarding Summary

| Property                | Value                                      |
|-------------------------|--------------------------------------------|
| Total steps             | 5                                          |
| Required steps          | 1 (Welcome), 2 (Sports), 3 (Budget), 5 (Tour) |
| Optional steps          | 4 (Invite Staff)                           |
| Time to complete        | ~15 minutes                                |
| First value moment      | Seeing program-wide NIL valuation          |
| Post-completion route   | `/athletic-director`                       |

---

## Agent Onboarding

### Prerequisites

- Accepted org invite with `agent` role OR created agency organization
- If invite: carries `org_id` (agency), `program_id` (office), `role: agent`
- If operator: agency org created during signup

### Step 1: Agency Profile Setup

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 1 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────○─────○─────○─────○                       │
│  Agency Avatar  Clients Pipeline  Value          │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Set Up Your Agency Profile                  ││
│  │                                              ││
│  │  Agency Name    [Klutch Sports Group___]     ││
│  │  Description    [Full-service athlete       ]││
│  │                 [representation agency       ]││
│  │                                              ││
│  │  Specialties                                 ││
│  │  [x] Basketball           <- first           ││
│  │  [ ] Football                                ││
│  │  [ ] Multi-Sport                             ││
│  │  [ ] Endorsements                            ││
│  │  [ ] Financial Planning                      ││
│  │                                              ││
│  │  Office Location                             ││
│  │  City   [Los Angeles__]  State [CA ▼]        ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│                                    [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Source                | Required |
|--------------------|-----------------------|----------|
| Agency name        | Org name (prefilled)  | Yes      |
| Description        | User input            | No       |
| Specialties        | Multi-select          | Yes (1+) |
| Office location    | User input            | Yes      |

### Step 2: Avatar Upload + Directory Listing

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 2 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────●─────○─────○─────○                       │
│  Agency Avatar  Clients Pipeline  Value          │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Your Agent Profile                          ││
│  │  This appears in the Agent Directory.        ││
│  │                                              ││
│  │  ┌──────────┐                                ││
│  │  │          │  [Upload Photo]                ││
│  │  │  Avatar  │  Professional headshot         ││
│  │  │  120px   │  JPG/PNG, up to 5MB            ││
│  │  │          │  Saved as 500x500              ││
│  │  └──────────┘                                ││
│  │                                              ││
│  │  First Name   [Rich_____________]            ││
│  │  Last Name    [Paul_____________]            ││
│  │  Public Email [rich@klutch.com__]            ││
│  │  Phone        [(310) 555-0199___]            ││
│  │  Bio          [________________________]     ││
│  │               [________________________]     ││
│  │                                              ││
│  │  Directory Preview:                          ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [Photo] Rich Paul                    │  ││
│  │  │  Klutch Sports Group                  │  ││
│  │  │  Los Angeles, CA                      │  ││
│  │  │  Basketball | Multi-Sport             │  ││
│  │  │  [Message]                            │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]                         [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Source                | Required |
|--------------------|-----------------------|----------|
| Avatar             | Upload                | No       |
| First/Last name    | Auth profile          | Yes      |
| Public email       | User input            | Yes      |
| Phone              | User input            | No       |
| Bio                | User input            | No       |
| Directory preview  | Live render           | Read-only|

### Step 3: Add Represented Players

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 3 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────○─────○                       │
│  Agency Avatar  Clients Pipeline  Value          │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Add Your Clients                            ││
│  │  Link athletes you represent.                ││
│  │                                              ││
│  │  Search [_________________________] [Search] ││
│  │                                              ││
│  │  Results:                                    ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ D. Wagner    Kentucky  PG   $420K [+] │  ││
│  │  │ R. Flagg     Duke      SF   $510K [+] │  ││
│  │  │ C. Cooper    Auburn    PG   $380K [+] │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Or invite athletes directly:                ││
│  │  Email [________________________] [Invite]   ││
│  │                                              ││
│  │  ────────────────────────────────────────── ││
│  │                                              ││
│  │  Your Clients (1):                           ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ D. Wagner  Kentucky  PG  $420K    [x] │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Minimum 1 client to proceed.                ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]                         [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Search             | Searches athlete directory                   |
| Results            | Shows name, school, position, Est. NIL       |
| Add button [+]     | Links athlete to agent                       |
| Invite option      | Send invite email to athlete not yet on platform |
| Minimum            | 1 client required to advance                 |
| Search priority    | Basketball athletes appear first in results  |

### Step 4: Pipeline Setup

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 4 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────●─────○                       │
│  Agency Avatar  Clients Pipeline  Value          │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Configure Your Pipeline                     ││
│  │  Track deals from prospect to signed.        ││
│  │                                              ││
│  │  Default Pipeline Stages:                    ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [1]  Prospect      [drag] [edit] [x] │  ││
│  │  │  [2]  Outreach      [drag] [edit] [x] │  ││
│  │  │  [3]  Negotiate     [drag] [edit] [x] │  ││
│  │  │  [4]  Signed        [drag] [edit] [x] │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  [+ Add Custom Stage]                        ││
│  │                                              ││
│  │  ────────────────────────────────────────── ││
│  │                                              ││
│  │  Add Your First Prospect                     ││
│  │  Search [_________________________] [Search] ││
│  │                                              ││
│  │  Suggested Basketball Prospects:             ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ A. Reeves    Kentucky  SG   $290K [+] │  ││
│  │  │ J. Knecht    Tennessee SF   $340K [+] │  ││
│  │  │ M. Ware      Alabama   PG   $260K [+] │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Skip]    [Next Step ->] │
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Pipeline stages    | Default 4 stages, drag-to-reorder            |
| Custom stages      | User can add, rename, delete                 |
| Minimum stages     | 2 required                                   |
| First prospect     | Optional search-and-add                      |
| Suggestions        | Basketball prospects surfaced first           |
| This step          | Pipeline config required, prospect optional  |

### Step 5: First Valuation Lookup

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 5 of 5   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────●─────●                       │
│  Agency Avatar  Clients Pipeline  Value          │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  See NIL Intelligence in Action              ││
│  │  Look up any athlete's AI-generated value.   ││
│  │                                              ││
│  │  Search [_________________________] [Search] ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │                                        │  ││
│  │  │  D. Wagner                             │  ││
│  │  │  Kentucky · PG · Sophomore             │  ││
│  │  │                                        │  ││
│  │  │  EST. NIL VALUATION                    │  ││
│  │  │  $420,000                   <- red     │  ││
│  │  │  ▲ +8.3% (30d)                        │  ││
│  │  │                                        │  ││
│  │  │  Social: 35%  |  Athletic: 40%         │  ││
│  │  │  Market: 15%  |  Comps: 10%            │  ││
│  │  │                                        │  ││
│  │  │  [Add to Pipeline ->]                  │  ││
│  │  │                                        │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Or explore your dashboard                   ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]                [Go to Dashboard ->]   │
└──────────────────────────────────────────────────┘
```

### Agent Onboarding Summary

| Property                | Value                                      |
|-------------------------|--------------------------------------------|
| Total steps             | 5                                          |
| Required steps          | 1 (Agency), 2 (Avatar), 3 (Clients)       |
| Optional steps          | 4 (Pipeline prospect), 5 (Valuation action)|
| Time to complete        | ~10 minutes                                |
| First value moment      | Seeing client's AI-generated NIL valuation |
| Post-completion route   | `/agent`                                   |

---

## Athlete Onboarding

### Prerequisites

- Accepted program invite with `athlete` role
- Invite carries: `org_id`, `program_id`, `role: athlete`
- Player data may be pre-matched via SportsRadar

### Step 1: Profile Confirmation

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 1 of 4   │
│  ────────────────────────────────────────────── │
│  ●─────○─────○─────○                             │
│  Profile  Agent  Social  Valuation               │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Confirm Your Profile                        ││
│  │  We pulled your info from your program.      ││
│  │                                              ││
│  │  ┌──────────┐                                ││
│  │  │          │  Dillian Wagner                ││
│  │  │  Photo   │  University of Kentucky        ││
│  │  │  (from   │  Men's Basketball              ││
│  │  │  SR)     │  Point Guard · Sophomore       ││
│  │  └──────────┘                                ││
│  │                                              ││
│  │  First Name    [Dillian__________] <- prefill││
│  │  Last Name     [Wagner___________] <- prefill││
│  │  School        [Kentucky_________] <- locked ││
│  │  Sport         [Men's Basketball_] <- locked ││
│  │  Position      [Point Guard    ▼]            ││
│  │  Year          [Sophomore      ▼]            ││
│  │  Hometown      [________________________]    ││
│  │                                              ││
│  │  Pre-filled from SportsRadar.                ││
│  │  Edit anything that needs correction.        ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│                                    [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Source                | Editable |
|--------------------|-----------------------|----------|
| Name               | Invite + SportsRadar  | Yes      |
| School             | Invite metadata       | No       |
| Sport              | Invite metadata       | No       |
| Position           | SportsRadar           | Yes      |
| Year               | SportsRadar           | Yes      |
| Hometown           | User input            | Yes      |

### Step 2: Agent Association

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 2 of 4   │
│  ────────────────────────────────────────────── │
│  ●─────●─────○─────○                             │
│  Profile  Agent  Social  Valuation               │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Do You Have an Agent?                       ││
│  │                                              ││
│  │  (o) Yes, I have an agent                    ││
│  │  ( ) No, I don't have an agent yet           ││
│  │                                              ││
│  │  ────────────────────────────────────────── ││
│  │                                              ││
│  │  [If Yes:]                                   ││
│  │  Search Agent Directory                      ││
│  │  [_________________________] [Search]        ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ Rich Paul     Klutch Sports     [Link]│  ││
│  │  │ Mark Bartelstein  Priority Sports [Link]│  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  [If No:]                                    ││
│  │  No worries! You can browse the Agent        ││
│  │  Directory anytime to find representation.   ││
│  │                                              ││
│  │  [Browse Agent Directory]  <- links to       ││
│  │                               /agent-directory││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Skip]    [Next Step ->] │
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Agent question     | Binary radio (Yes / No)                      |
| Agent search       | Searches `/agent-directory` data             |
| Link action        | Associates agent with athlete profile        |
| No agent path      | Shows directory browse CTA                   |
| This step          | Optional (can be skipped)                    |

### Step 3: Social Media Linking

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 3 of 4   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────○                             │
│  Profile  Agent  Social  Valuation               │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Connect Your Social Media                   ││
│  │  Your social reach directly impacts your     ││
│  │  NIL valuation.                              ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [IG]  Instagram        [Connect]      │  ││
│  │  │  [X]   Twitter / X      [Connect]      │  ││
│  │  │  [TT]  TikTok           [Connect]      │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Connected:                                  ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [IG] @dub_wagner   142K followers [x] │  ││
│  │  │  [X]  @dwagner_uk    38K followers [x] │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  ────────────────────────────────────────── ││
│  │                                              ││
│  │  Social Reach Impact:                        ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  Combined Reach:  180,000              │  ││
│  │  │  Valuation Impact: +$24,000 est.       │  ││
│  │  │  ████████████░░░░░░░░  35% of value    │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  More followers = higher NIL value.          ││
│  │  You can add more accounts later.            ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Skip]    [Next Step ->] │
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Social platforms   | OAuth connect flow per platform              |
| Follower counts    | Pulled after successful connection            |
| Valuation impact   | Calculated and shown in real-time             |
| Impact bar         | Visual representation of social contribution |
| This step          | Optional (can be skipped)                    |

### Step 4: Valuation Preview Tour

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 4 of 4   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────●                             │
│  Profile  Agent  Social  Valuation               │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  This Is What You're Worth                   ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │                                        │  ││
│  │  │  [Photo]  Dillian Wagner               │  ││
│  │  │           Kentucky · PG · Sophomore    │  ││
│  │  │                                        │  ││
│  │  │  YOUR NIL VALUATION                    │  ││
│  │  │                                        │  ││
│  │  │  $420,000                  <- red, XL  │  ││
│  │  │  ▲ +8.3% (30d)            <- green     │  ││
│  │  │                                        │  ││
│  │  │  ────────────────────────────────────  │  ││
│  │  │                                        │  ││
│  │  │  VALUATION BREAKDOWN                   │  ││
│  │  │  Social Media     ████████░░░░  35%    │  ││
│  │  │  Athletic Perf    ██████████░░  40%    │  ││
│  │  │  Market Demand    ████░░░░░░░░  15%    │  ││
│  │  │  Comparable Deals ██░░░░░░░░░░  10%    │  ││
│  │  │                                        │  ││
│  │  │  ────────────────────────────────────  │  ││
│  │  │                                        │  ││
│  │  │  PREDICTION                            │  ││
│  │  │  Projected to increase 5-10% over      │  ││
│  │  │  the next 90 days based on current     │  ││
│  │  │  performance trajectory.               │  ││
│  │  │                                        │  ││
│  │  │  Predicted Range: $441K - $462K        │  ││
│  │  │                                        │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Go to My Dashboard ->]  │
└──────────────────────────────────────────────────┘
```

### Athlete Onboarding Summary

| Property                | Value                                          |
|-------------------------|------------------------------------------------|
| Total steps             | 4                                              |
| Required steps          | 1 (Profile), 4 (Valuation view)                |
| Optional steps          | 2 (Agent), 3 (Social)                          |
| Time to complete        | ~5 minutes                                     |
| First value moment      | Seeing personal NIL valuation for the first time |
| Post-completion route   | `/athlete`                                     |

---

## Coach Onboarding

### Prerequisites

- Accepted program invite with `coach` role
- Invite carries: `org_id`, `program_id`, `role: coach`
- Program must be linked to SportsRadar team data

### Step 1: Program / Team Confirmation

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 1 of 4   │
│  ────────────────────────────────────────────── │
│  ●─────○─────○─────○                             │
│  Team  Roster  Budget  Pipeline                  │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Confirm Your Team                           ││
│  │  We've pulled your assignment from your      ││
│  │  program invite.                             ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  University of Kentucky               │  ││
│  │  │  Men's Basketball                     │  ││
│  │  │  SEC Conference                       │  ││
│  │  │  Head Coach                           │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  School       [Kentucky_________] <- locked  ││
│  │  Sport        [Men's Basketball_] <- locked  ││
│  │  Conference   [SEC______________] <- locked  ││
│  │  Title        [Head Coach     ▼]             ││
│  │                                              ││
│  │  (o) This is correct                         ││
│  │  ( ) I need to contact my admin              ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│                                    [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Source                | Editable |
|--------------------|-----------------------|----------|
| School             | Invite metadata       | No       |
| Sport              | Invite metadata       | No       |
| Conference         | Org profile           | No       |
| Title              | User selection        | Yes      |
| Confirmation       | Radio selection       | Required |

### Step 2: Roster Review

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 2 of 4   │
│  ────────────────────────────────────────────── │
│  ●─────●─────○─────○                             │
│  Team  Roster  Budget  Pipeline                  │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Review Your Roster                          ││
│  │  Pulled from SportsRadar. Verify accuracy.   ││
│  │                                              ││
│  │  Kentucky Wildcats - Men's Basketball        ││
│  │  13 players on roster                        ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ #   Player          Pos  Yr   Est NIL  │  ││
│  │  ├────────────────────────────────────────┤  ││
│  │  │ 1   D. Wagner       PG   So   $420K   │  ││
│  │  │ 3   R. Harper       SF   Jr   $380K   │  ││
│  │  │ 5   T. Mitchell     C    Sr   $310K   │  ││
│  │  │ 11  A. Reeves       SG   Jr   $290K   │  ││
│  │  │ 13  J. Edwards      PF   Fr   $180K   │  ││
│  │  │ 15  K. Brooks       PG   So   $165K   │  ││
│  │  │ 21  M. Johnson      SF   Jr   $140K   │  ││
│  │  │ ...                                    │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Est. Team Valuation: $3,200,000             ││
│  │                                              ││
│  │  Missing a player? [Flag Missing Player]     ││
│  │                                              ││
│  │  (o) Roster looks correct                    ││
│  │  ( ) Players are missing or incorrect        ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]                         [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Roster table       | Read-only, from SportsRadar                  |
| Est. NIL column    | Per-player predicted valuation               |
| Team total         | Sum of all player valuations                 |
| Flag missing       | Opens form to report missing player          |
| Confirmation       | Radio selection required                     |

### Step 3: Budget Allocation Setup

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 3 of 4   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────○                             │
│  Team  Roster  Budget  Pipeline                  │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Set Per-Player NIL Allocation               ││
│  │  Budget set by your AD: $3,000,000           ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ #  Player       Est. Value  Allocated  │  ││
│  │  ├────────────────────────────────────────┤  ││
│  │  │ 1  D. Wagner    $420,000   [$400,000]  │  ││
│  │  │ 3  R. Harper    $380,000   [$350,000]  │  ││
│  │  │ 5  T. Mitchell  $310,000   [$300,000]  │  ││
│  │  │ 11 A. Reeves    $290,000   [$280,000]  │  ││
│  │  │ 13 J. Edwards   $180,000   [$170,000]  │  ││
│  │  │ ...                                    │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Team Budget:     $3,000,000                 ││
│  │  Total Allocated: $2,800,000                 ││
│  │  Remaining:       $200,000                   ││
│  │                                              ││
│  │  ██████████████████████████████░░░░  93%     ││
│  │                                              ││
│  │  Total must not exceed team budget.           ││
│  │  You can adjust later in Coach Settings.     ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Skip]    [Next Step ->] │
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Team budget        | Read-only (set by AD in org settings)        |
| Est. Value column  | Per-player, read-only from predictions       |
| Allocated column   | Editable currency input per player           |
| Budget validation  | Total allocated must not exceed team budget   |
| Progress bar       | Visual % of budget allocated                 |
| This step          | Optional (can be skipped)                    |

### Step 4: Pipeline Introduction

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 4 of 4   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●─────●                             │
│  Team  Roster  Budget  Pipeline                  │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Your Recruiting Pipeline                    ││
│  │  Track transfer targets and recruits.        ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  Pipeline Stages:                      │  ││
│  │  │                                        │  ││
│  │  │  [Prospect] -> [Outreach] ->           │  ││
│  │  │  [Negotiate] -> [Committed]            │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  ────────────────────────────────────────── ││
│  │                                              ││
│  │  Transfer Portal Awareness                   ││
│  │  Players entering the portal are             ││
│  │  automatically flagged in your pipeline.     ││
│  │                                              ││
│  │  Add Your First Recruiting Target            ││
│  │  Search [_________________________] [Search] ││
│  │                                              ││
│  │  Suggested (Basketball Transfer Portal):     ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ M. Ware     Alabama  PG  $260K   [+]  │  ││
│  │  │ T. Grant    Clemson  SF  $220K   [+]  │  ││
│  │  │ K. Fields   Florida  SG  $195K   [+]  │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Or explore your dashboard                   ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Go to My Dashboard ->]  │
└──────────────────────────────────────────────────┘
```

### Coach Onboarding Summary

| Property                | Value                                      |
|-------------------------|--------------------------------------------|
| Total steps             | 4                                          |
| Required steps          | 1 (Team), 2 (Roster)                       |
| Optional steps          | 3 (Budget), 4 (Pipeline)                   |
| Time to complete        | ~8 minutes                                 |
| First value moment      | Seeing team roster with NIL valuations     |
| Post-completion route   | `/coach`                                   |

---

## Fan Onboarding (Lightweight)

### Prerequisites

- Public signup (no invite required)
- No org/program context
- Fan role assigned automatically on account creation

### Step 1: Interest Selection

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 1 of 3   │
│  ────────────────────────────────────────────── │
│  ●─────○─────○                                   │
│  Interests  Preview  Upgrade                     │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  What Are You Into?                          ││
│  │  Pick your favorites to personalize NIL      ││
│  │  Optic.                                      ││
│  │                                              ││
│  │  Favorite Sports:                            ││
│  │  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐       ││
│  │  │ BBall│ │ FBall│ │ Base │ │ Soft │       ││
│  │  │ [x]  │ │ [ ]  │ │ [ ]  │ │ [ ]  │       ││
│  │  └──────┘ └──────┘ └──────┘ └──────┘       ││
│  │  ┌──────┐ ┌──────┐ ┌──────┐                 ││
│  │  │ VBall│ │ Track│ │ Swim │                 ││
│  │  │ [ ]  │ │ [ ]  │ │ [ ]  │                 ││
│  │  └──────┘ └──────┘ └──────┘                 ││
│  │                                              ││
│  │  Favorite Teams / Conferences:               ││
│  │  Search [_________________________] [Search] ││
│  │                                              ││
│  │  Selected:                                   ││
│  │  [Kentucky Wildcats] [SEC] [Duke Blue Devils]││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│                                    [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Sports grid        | Basketball first, pre-checked                |
| Team search        | Search all teams in directory                |
| Conference chips   | Selectable conference tags                   |
| Minimum            | 1 sport + 1 team/conference                  |

### Step 2: Feature Preview

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 2 of 3   │
│  ────────────────────────────────────────────── │
│  ●─────●─────○                                   │
│  Interests  Preview  Upgrade                     │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Your Free Toolkit                           ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [Icon: Users]                        │  ││
│  │  │  Roster Builder                       │  ││
│  │  │  Browse every D1 basketball player.   │  ││
│  │  │  See top-3 NIL valuations per team.   │  ││
│  │  │                                        │  ││
│  │  │  [Try It ->]                          │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [Icon: Star]                         │  ││
│  │  │  Favorites                            │  ││
│  │  │  Track players and teams you follow.  │  ││
│  │  │  Quick-add from any directory page.   │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [Icon: Trophy]                       │  ││
│  │  │  Tournaments                          │  ││
│  │  │  March Madness intelligence with NIL  │  ││
│  │  │  values, Money Fight matchups, and    │  ││
│  │  │  conference value comparisons.        │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]                         [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Feature            | Fan Access Level                             |
|--------------------|----------------------------------------------|
| Roster Builder     | Full player list, top-3 NIL values visible   |
| Favorites          | Watchlist without private profile deep-links |
| Tournaments        | Capped valuation lists (top-3 preview depth) |
| Messaging/Huddles  | Not available                                |
| Predictions        | Not available                                |
| Pipeline           | Not available                                |

### Step 3: Upgrade Path Awareness

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 3 of 3   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●                                   │
│  Interests  Preview  Upgrade                     │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Unlock Full NIL Intelligence                ││
│  │                                              ││
│  │  What paid users see:                        ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [Preview: Valuation Card]            │  ││
│  │  │  D. Wagner - $420,000                 │  ││
│  │  │  Full breakdown, predictions,         │  ││
│  │  │  comparable deals, trend charts       │  ││
│  │  │                            [Locked]   │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  [Preview: Pipeline Board]            │  ││
│  │  │  Prospect -> Outreach -> Signed       │  ││
│  │  │  Deal management + CRM tools          │  ││
│  │  │                            [Locked]   │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  ────────────────────────────────────────── ││
│  │                                              ││
│  │  Upgrade for Full Access                     ││
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐    ││
│  │  │ Starter  │ │ Pro      │ │ Enterpr. │    ││
│  │  │ $49/mo   │ │ $199/mo  │ │ Custom   │    ││
│  │  │ [Select] │ │ [Select] │ │ [Contact]│    ││
│  │  └──────────┘ └──────────┘ └──────────┘    ││
│  │                                              ││
│  │  Or continue with your free account          ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]           [Start Exploring ->]        │
└──────────────────────────────────────────────────┘
```

### Fan Onboarding Summary

| Property                | Value                                      |
|-------------------------|--------------------------------------------|
| Total steps             | 3                                          |
| Required steps          | 1 (Interests)                              |
| Optional steps          | 2 (Preview), 3 (Upgrade awareness)         |
| Time to complete        | ~3 minutes                                 |
| First value moment      | Using Roster Builder with real NIL data    |
| Post-completion route   | `/fan`                                     |

---

## Affiliate Onboarding

### Prerequisites

- Accepted org invite with `affiliate` role
- Invite carries: `org_id` (affiliate org), `program_id` (office), `role: affiliate`
- Organization category: `affiliate`

### Step 1: Office Setup

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 1 of 3   │
│  ────────────────────────────────────────────── │
│  ●─────○─────○                                   │
│  Office  Services  Directory                     │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Set Up Your Office                          ││
│  │  Confirm your affiliate details.             ││
│  │                                              ││
│  │  Company Name   [The Kravitz Group | UBS___] ││
│  │  Office Name    [Dallas Office_____________] ││
│  │                                              ││
│  │  Service Categories:                         ││
│  │  [x] Wealth Management        <- primary    ││
│  │  [ ] Tax Advisory                            ││
│  │  [ ] Legal Services                          ││
│  │                                              ││
│  │  Office Location                             ││
│  │  City   [Dallas_________]  State [TX ▼]      ││
│  │                                              ││
│  │  Contact Email  [info@kravitz-ubs.com____]   ││
│  │  Phone          [(214) 555-0300__________]   ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│                                    [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Source                | Required |
|--------------------|-----------------------|----------|
| Company name       | Org profile (prefill) | Yes      |
| Office name        | User input            | Yes      |
| Service categories | Multi-select          | Yes (1+) |
| Location           | User input            | Yes      |
| Contact info       | User input            | Yes      |

### Step 2: Service Catalog

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 2 of 3   │
│  ────────────────────────────────────────────── │
│  ●─────●─────○                                   │
│  Office  Services  Directory                     │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Define Your Services                        ││
│  │  What services do you offer NIL athletes?    ││
│  │                                              ││
│  │  Wealth Management Services:                 ││
│  │  [x] Portfolio Management                    ││
│  │  [x] Financial Planning                      ││
│  │  [x] NIL Income Strategy                     ││
│  │  [ ] Estate Planning                         ││
│  │  [ ] Insurance Advisory                      ││
│  │                                              ││
│  │  Availability:                               ││
│  │  [x] Accepting new clients                   ││
│  │  [ ] Waitlist only                           ││
│  │  [ ] By referral only                        ││
│  │                                              ││
│  │  ────────────────────────────────────────── ││
│  │                                              ││
│  │  Service Description (optional):             ││
│  │  [Specialized wealth management for         ]││
│  │  [college athletes navigating NIL income    ]││
│  │  [with tax-efficient investment strategies  ]││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]                         [Next Step ->]│
└──────────────────────────────────────────────────┘
```

| Field              | Behavior                                     |
|--------------------|----------------------------------------------|
| Service checkboxes | Filtered by selected categories              |
| Availability       | Radio selection, single choice               |
| Description        | Optional free text                           |
| Minimum            | 1 service checked                            |

### Step 3: Directory Presence

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 3 of 3   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●                                   │
│  Office  Services  Directory                     │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Preview Your Directory Listing              ││
│  │                                              ││
│  │  This is how you'll appear in the            ││
│  │  Affiliate Directory:                        ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │                                        │  ││
│  │  │  The Kravitz Group | UBS              │  ││
│  │  │  Financial Services Inc                │  ││
│  │  │                                        │  ││
│  │  │  Wealth Management                     │  ││
│  │  │  Dallas, TX                            │  ││
│  │  │                                        │  ││
│  │  │  Services:                             │  ││
│  │  │  Portfolio Mgmt | Financial Planning   │  ││
│  │  │  NIL Income Strategy                   │  ││
│  │  │                                        │  ││
│  │  │  Accepting New Clients                 │  ││
│  │  │                                        │  ││
│  │  │  [Message]                             │  ││
│  │  │                                        │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Category Placement:                         ││
│  │  /affiliate-directory/wealth-management      ││
│  │                                              ││
│  │  Your listing goes live when you complete    ││
│  │  setup.                                      ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Go to Dashboard ->]     │
└──────────────────────────────────────────────────┘
```

### Affiliate Onboarding Summary

| Property                | Value                                      |
|-------------------------|--------------------------------------------|
| Total steps             | 3                                          |
| Required steps          | 1 (Office), 2 (Services), 3 (Preview)      |
| Optional steps          | None                                       |
| Time to complete        | ~5 minutes                                 |
| First value moment      | Appearing in affiliate directory           |
| Post-completion route   | `/affiliate`                               |

---

## Agency Admin Onboarding

### Prerequisites

- Created agency organization via operator signup OR accepted invite with `agency_admin` role
- Organization category: `agency`

### Step 1: Agency Organization Setup

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 1 of 3   │
│  ────────────────────────────────────────────── │
│  ●─────○─────○                                   │
│  Agency  Team  Directory                         │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Set Up Your Agency                          ││
│  │                                              ││
│  │  Agency Name    [________________________]   ││
│  │  Description    [________________________]   ││
│  │                 [________________________]   ││
│  │                                              ││
│  │  Primary Sports Focus:                       ││
│  │  [x] Basketball           <- first           ││
│  │  [ ] Football                                ││
│  │  [ ] Multi-Sport                             ││
│  │                                              ││
│  │  Headquarters                                ││
│  │  City [____________]  State [__ ▼]           ││
│  │                                              ││
│  │  Office Setup:                               ││
│  │  Office Name  [Main Office___________]       ││
│  │  This creates your first office/program.     ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│                                    [Next Step ->]│
└──────────────────────────────────────────────────┘
```

### Step 2: Invite Agents

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 2 of 3   │
│  ────────────────────────────────────────────── │
│  ●─────●─────○                                   │
│  Agency  Team  Directory                         │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Invite Your Agents                          ││
│  │  Build your team on NIL Optic.               ││
│  │                                              ││
│  │  Email           [________________________]  ││
│  │  Office          [Main Office        ▼]      ││
│  │                                              ││
│  │  [+ Add Another Invite]                      ││
│  │                                              ││
│  │  Pending:                                    ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │ agent1@agency.com   Main Office       │  ││
│  │  │ agent2@agency.com   Main Office       │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  [Send Invites]                              ││
│  │                                              ││
│  │  Or skip -- invite from Settings later.      ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Skip]    [Next Step ->] │
└──────────────────────────────────────────────────┘
```

### Step 3: Agency Directory Preview

```
┌──────────────────────────────────────────────────┐
│  [NIL Optic Logo]                  Step 3 of 3   │
│  ────────────────────────────────────────────── │
│  ●─────●─────●                                   │
│  Agency  Team  Directory                         │
│                                                  │
│  ┌──────────────────────────────────────────────┐│
│  │                                              ││
│  │  Your Agency Dashboard Is Ready              ││
│  │                                              ││
│  │  ┌────────────────────────────────────────┐  ││
│  │  │  Total Agents: 0 (2 invited)          │  ││
│  │  │  Total Athletes: 0                    │  ││
│  │  │  Total Est. NIL Value: --             │  ││
│  │  └────────────────────────────────────────┘  ││
│  │                                              ││
│  │  Next steps to get value from NIL Optic:     ││
│  │  1. Wait for agents to accept invites        ││
│  │  2. Agents add their represented clients     ││
│  │  3. Track portfolio NIL value in real time   ││
│  │                                              ││
│  └──────────────────────────────────────────────┘│
│                                                  │
│  [<- Back]              [Go to Dashboard ->]     │
└──────────────────────────────────────────────────┘
```

### Agency Admin Onboarding Summary

| Property                | Value                                      |
|-------------------------|--------------------------------------------|
| Total steps             | 3                                          |
| Required steps          | 1 (Agency Setup)                           |
| Optional steps          | 2 (Invite Agents), 3 (Preview)             |
| Time to complete        | ~5 minutes                                 |
| First value moment      | Agency listed with agent pipeline ready    |
| Post-completion route   | `/agency-admin`                            |

---

## Onboarding Flow Comparison Matrix

| Property          | AD      | Agent   | Athlete | Coach   | Fan     | Affiliate | Agency Admin |
|-------------------|---------|---------|---------|---------|---------|-----------|--------------|
| Total steps       | 5       | 5       | 4       | 4       | 3       | 3         | 3            |
| Required steps    | 4       | 3       | 2       | 2       | 1       | 3         | 1            |
| Optional steps    | 1       | 2       | 2       | 2       | 2       | 0         | 2            |
| Time estimate     | 15 min  | 10 min  | 5 min   | 8 min   | 3 min   | 5 min     | 5 min        |
| Needs invite      | Yes     | Mixed   | Yes     | Yes     | No      | Yes       | Mixed        |
| Needs org context | Yes     | Yes     | Yes     | Yes     | No      | Yes       | Yes          |
| Budget setup      | Yes     | No      | No      | Yes     | No      | No        | No           |
| Social linking    | No      | No      | Yes     | No      | No      | No        | No           |
| Staff invites     | Yes     | No      | No      | No      | No      | No        | Yes          |
| Pipeline setup    | No      | Yes     | No      | Yes     | No      | No        | No           |
| Directory listing | No      | Yes     | No      | No      | No      | Yes       | No           |
| Valuation preview | No      | Yes     | Yes     | No      | No      | No        | No           |

---

## Basketball-First Content Reference

All onboarding flows use basketball-first examples. This table documents the specific basketball content used across flows:

| Flow Context           | Basketball Reference                                |
|------------------------|-----------------------------------------------------|
| Sport selection        | "Men's Basketball" first in list, pre-checked       |
| Team examples          | Kentucky Wildcats, Duke Blue Devils, Auburn Tigers  |
| Player examples        | D. Wagner (PG), R. Harper (SF), T. Mitchell (C)    |
| Conference examples    | SEC, ACC, Big Ten, Big 12                           |
| Valuation examples     | $420K, $380K, $310K (realistic basketball NIL)      |
| Pipeline prospects     | Basketball transfer portal athletes                  |
| Tournament references  | March Madness intelligence, Money Fight matchups    |
| Position references    | PG, SG, SF, PF, C                                  |
| Stat references        | PTS, AST, REB (per40 metrics)                       |
| Budget examples        | Basketball gets primary allocation in budget setup  |
