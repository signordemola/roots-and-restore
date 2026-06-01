# Project C — Roots & Restore Wellness
## Demola Studio Portfolio · Full Studio Tier Demo

> **What this proves:** A US multi-practitioner holistic wellness studio with role-based
> access, health intake forms, SOAP notes, liability waivers, multi-practitioner
> availability, and an owner dashboard that tracks revenue and commission per practitioner.
> This is the system Acuity + Jane App + Google Sheets was trying to be — in one place,
> built for the studio that has outgrown all three.

---

## Industry Context — What You Need to Know

### Three US-Specific Requirements That Don't Exist in the UK Demos

**SOAP Notes (legal requirement in most US states)**
Massage therapists licensed in the US are required by most state boards to maintain
SOAP notes — Subjective, Objective, Assessment, Plan — for every client session.
Acupuncturists and holistic practitioners follow the same standard as clinical best
practice. These are practitioner-only clinical records: not shown to clients, not
shared between practitioners, but accessible to the studio owner for compliance.

**Health Intake Form (US liability and licensing standard)**
Before their first appointment, every US wellness client must complete a health intake
form covering medical history, conditions, medications, surgeries, contraindications,
areas of focus, areas to avoid, and reason for visit. This is required by state
licensing boards for massage therapists and is standard practice for acupuncture and
reiki. It drives clinical decisions and limits studio liability.

**Liability Waiver (US litigation culture)**
US wellness studios universally require a signed liability waiver before the first session.
The waiver acknowledges the nature of the treatment, confirms the client disclosed relevant
medical history, and limits the studio's liability. It is collected once and stored
permanently. This does not exist in the same formal way in UK wellness practice.

### The Independent Contractor Model

The dominant US wellness studio structure: the studio provides space, brand and booking
infrastructure. Independent contractors (the practitioners) deliver the service and
split revenue with the studio. Commission split: 35% to studio, 65% to practitioner.
This drives the owner dashboard's core use: tracking gross bookings, practitioner
payouts, and studio commission by month — not in a spreadsheet, in the system.

### Real US Wellness Tool Stack

| Tool | Purpose | Monthly Cost |
|---|---|---|
| Squarespace / Wix | Website | $16–$40 |
| Acuity Scheduling | Booking | $16–$61 |
| Jane App / SimplePractice | SOAP notes + intake forms | $39–$99 |
| Square / Stripe | Payment processing | 2.6–2.9% per transaction |
| Google Sheets | Commission tracking | Free |
| Gmail | Client communication | Free |
| **Total** | | **$71–$200+ / month** |

The gap: Acuity handles booking — no SOAP notes. Jane App has SOAP notes —
priced for clinical practices, too heavy for holistic studios. Square handles
payments — no intake forms. Commission tracking happens in a spreadsheet at month end.
No single tool connects all five. That is what this system builds.

### US Cancellation Policy — Industry Standard

| Notice given | Outcome |
|---|---|
| 24hrs+ | Full deposit refunded |
| Under 24hrs | Deposit forfeited |
| No-show | Deposit forfeited, full session fee may apply at owner's discretion |
| 15+ mins late | Session shortened, full fee applies |

---

## Fictional Studio

| | |
|---|---|
| **Studio name** | Roots & Restore Wellness |
| **Location** | South Congress area, Austin, TX |
| **Structure** | Owner-operated studio with 2 independent contractor practitioners |
| **Rooms** | 3 treatment rooms |
| **Current flow** | Acuity for booking, Jane App for SOAP notes (David only), Google Sheets for commission, Square for payments, Gmail for everything else |
| **Problem** | Three tools that don't talk to each other. Commission calculated manually at month end. David and Keila's clients visible to each other in Acuity. No-show handling inconsistent. Intake forms emailed as PDFs. |

### Practitioners and Services

**Marisol** — owner and licensed massage therapist (LMT, Texas)

| Service | Duration | Price | Deposit | Studio (35%) | Marisol (65%) |
|---|---|---|---|---|---|
| Swedish Massage | 60 min | $95 | $35 | $33.25 | $61.75 |
| Deep Tissue Massage | 60 min | $110 | $40 | $38.50 | $71.50 |
| Hot Stone Massage | 90 min | $140 | $50 | $49.00 | $91.00 |

**David** — licensed acupuncturist (L.Ac., Texas) — independent contractor

| Service | Duration | Price | Deposit | Studio (35%) | David (65%) |
|---|---|---|---|---|---|
| Initial Acupuncture Consultation | 75 min | $120 | $40 | $42.00 | $78.00 |
| Follow-up Acupuncture | 60 min | $90 | $30 | $31.50 | $58.50 |
| Cupping Therapy | 45 min | $65 | $25 | $22.75 | $42.25 |

**Keila** — reiki practitioner — independent contractor

| Service | Duration | Price | Deposit | Studio (35%) | Keila (65%) |
|---|---|---|---|---|---|
| Reiki Healing Session | 60 min | $85 | $30 | $29.75 | $55.25 |
| Extended Reiki & Chakra Balancing | 90 min | $120 | $40 | $42.00 | $78.00 |

*All monetary values stored in cents. Display formatted as USD ($95.00).*
*Commission split: 35% studio / 65% practitioner on every completed session.*
*Deposit counted as part of session revenue — not separate.*

### Health Intake Form (US Standard — Collected from Every New Client)

Triggered automatically by booking confirmation email. Client must complete before
their first session. Stored permanently on their client record. Accessible only to
the practitioner they booked with (and the studio owner for audit purposes).

Fields:
1. Full legal name, date of birth
2. Primary reason for visit (relaxation / stress relief / pain relief / specific
   condition / curiosity / recommendation)
3. Current medical conditions (free text)
4. Current medications and supplements (free text)
5. Recent surgeries or injuries in the last 12 months (free text)
6. Areas of focus during session
7. Areas to avoid during session
8. Pregnancy status (not pregnant / possibly pregnant / currently pregnant)
9. Pressure preference — massage clients: light / medium / firm / therapist's choice
10. Skin conditions or sensitivities relevant to treatment (free text)
11. Emergency contact: name, relationship, phone number
12. Have you received this type of treatment before? (yes / no)
13. How did you hear about us?
14. HIPAA acknowledgement — "I understand my health information is kept private and
    used only to provide care."
15. Liability waiver — full text displayed, client signs by typing full name
    and checking acknowledgement checkbox

### SOAP Note Structure (Per Session, Practitioner Only)

Recorded by the treating practitioner after every completed session.
Never shared with other practitioners. Never shown to clients.
Accessible to owner for compliance audit.

| Field | Description |
|---|---|
| **S — Subjective** | What the client reports: pain level (0–10 scale), areas of tension, how they feel today, changes since last session |
| **O — Objective** | Practitioner observations: posture, range of motion, tissue quality, palpation findings, what was observed |
| **A — Assessment** | Clinical findings: what the practitioner assessed, progress toward treatment goals |
| **P — Plan** | Next session plan: areas to focus, recommended frequency, any referrals or changes |
| Session duration | Actual minutes |
| Techniques used | Free text or tag list |
| Follow-up recommended | Yes / No + timeframe |

---

## Tech Stack

### Core Framework
- **TanStack Start v1** — full-stack React, server functions, file-based routing, Vite
- **TanStack Router** — type-safe routing, typed params, typed search params
- **React 19**
- **TypeScript** — strict mode

> TanStack Start is appropriate here for the same reasons as Project B: the
> application is a multi-role dashboard and client booking portal — no public SEO
> page needed. Server functions keep the auth and data access layer clean without
> separate route handlers. Multi-role access control integrates naturally with
> server-side session checks per function.

### Data & Validation
- **Prisma** — ORM, schema-first, migrations
- **PostgreSQL** — Railway or Neon (local: Docker)
- **Zod** — all input validation, form schemas, server function payloads

### Client State & Fetching
- **TanStack Query v5** — server state, cache invalidation, dashboard data
- **Zustand** — booking wizard state, multi-step intake form state

### UI
- **shadcn/ui** — base component library
- **Tailwind CSS v4**
- **Radix UI** — via shadcn (Dialog, Select, Tabs, etc.)
- **Lucide React** — icons
- **date-fns** — date/time calculations and US-format display (MM/DD/YYYY)

### Payments
- **Stripe** — deposit collection, refunds, webhook verification
- **@stripe/stripe-js + @stripe/react-stripe-js** — Stripe Elements

### Email
- **Resend** — transactional email delivery
- **React Email + @react-email/components** — typed email templates

### Auth (Multi-role — the core new feature vs Projects A and B)
- **iron-session** — encrypted cookie session
- **bcrypt** — password hashing
- Three roles: `owner`, `practitioner`, `client` (client access via session token — no password)
- Practitioners log in with email + password
- Owner logs in with email + password (different permissions)
- Each practitioner sees only their own data (enforced server-side, every query)

### Utilities
- **nanoid** — session tokens for client booking management links
- **date-fns** — US date formatting throughout (M/D/YYYY, 12hr time)

---

## Folder Structure

```
roots-and-restore/
│
├── app/
│   ├── routes/
│   │   │
│   │   ├── __root.tsx                             # Root layout
│   │   │
│   │   ├── index.tsx                              # Public booking page
│   │   │                                          # Service selection + practitioner picker
│   │   ├── book/
│   │   │   ├── $serviceSlug.$practitionerSlug.tsx # Date + time picker
│   │   │   ├── intake.tsx                         # New vs returning client check
│   │   │   ├── health-form.tsx                    # Health intake + liability waiver (new clients)
│   │   │   ├── policy.tsx                         # Cancellation policy acknowledgement
│   │   │   ├── payment.tsx                        # Stripe deposit payment
│   │   │   └── confirmed.tsx                      # Booking confirmed
│   │   │
│   │   ├── manage/
│   │   │   └── $sessionToken.tsx                  # Client self-service: view, reschedule, cancel
│   │   │       ├── reschedule.tsx
│   │   │       └── cancel.tsx
│   │   │
│   │   ├── practitioner/                          # Practitioner private portal
│   │   │   ├── login.tsx
│   │   │   ├── dashboard.tsx                      # Today's appointments + this week
│   │   │   ├── appointments/
│   │   │   │   ├── index.tsx                      # Their appointment list
│   │   │   │   └── $appointmentId.tsx             # Appointment detail + SOAP note entry
│   │   │   ├── clients/
│   │   │   │   ├── index.tsx                      # Their client list
│   │   │   │   └── $clientId.tsx                  # Client record: history + intake + notes
│   │   │   ├── soap/
│   │   │   │   └── $appointmentId.tsx             # Write / edit SOAP note for a session
│   │   │   └── availability/
│   │   │       └── index.tsx                      # Set working days + hours + block dates
│   │   │
│   │   ├── owner/                                 # Owner private dashboard
│   │   │   ├── login.tsx
│   │   │   ├── dashboard.tsx                      # Today across all practitioners + revenue
│   │   │   ├── appointments/
│   │   │   │   └── index.tsx                      # All appointments, filter by practitioner
│   │   │   ├── practitioners/
│   │   │   │   ├── index.tsx                      # Practitioner list + monthly stats
│   │   │   │   └── $practitionerId.tsx            # Practitioner detail + commission breakdown
│   │   │   ├── clients/
│   │   │   │   ├── index.tsx                      # All clients across studio
│   │   │   │   └── $clientId.tsx                  # Full client record (owner view)
│   │   │   └── settings/
│   │   │       ├── index.tsx
│   │   │       ├── services.tsx                   # Edit service prices and deposits
│   │   │       └── commission.tsx                 # Edit commission split percentage
│   │   │
│   │   └── api/
│   │       ├── availability/
│   │       │   └── route.ts                       # GET: slots by service + practitioner + date
│   │       ├── clients/
│   │       │   └── lookup.ts                      # POST: returning client email lookup
│   │       ├── booking/
│   │       │   └── checkout.ts                    # POST: create Stripe PaymentIntent
│   │       ├── intake/
│   │       │   └── submit.$sessionToken.ts        # POST: submit health intake + waiver
│   │       ├── manage/
│   │       │   ├── appointment.$sessionToken.ts   # GET: appointment detail by token
│   │       │   ├── reschedule.$sessionToken.ts    # POST: reschedule
│   │       │   └── cancel.$sessionToken.ts        # POST: cancel
│   │       ├── practitioner/
│   │       │   ├── auth.ts                        # POST: practitioner login / logout
│   │       │   ├── appointments.ts                # GET: their appointments
│   │       │   ├── appointments.$id.ts            # GET/PATCH: appointment detail
│   │       │   ├── appointments.$id.noshow.ts     # POST: mark no-show (their appts only)
│   │       │   ├── soap.$appointmentId.ts         # GET/POST/PUT: SOAP note for session
│   │       │   ├── clients.ts                     # GET: their clients only
│   │       │   ├── clients.$id.ts                 # GET: single client (their client only)
│   │       │   └── availability.ts                # GET/PUT: their availability settings
│   │       ├── owner/
│   │       │   ├── auth.ts                        # POST: owner login / logout
│   │       │   ├── dashboard.ts                   # GET: today across all + revenue snapshot
│   │       │   ├── appointments.ts                # GET: all appointments, filterable
│   │       │   ├── appointments.$id.noshow.ts     # POST: mark no-show (any appointment)
│   │       │   ├── practitioners.ts               # GET: all practitioners + stats
│   │       │   ├── practitioners.$id.ts           # GET: single practitioner commission detail
│   │       │   ├── clients.ts                     # GET: all clients across studio
│   │       │   ├── clients.$id.ts                 # GET: full client record
│   │       │   └── settings.ts                    # GET/PUT: services, commission split
│   │       ├── stripe/
│   │       │   └── webhook.ts                     # POST: Stripe webhook handler
│   │       └── cron/
│   │           └── reminders.ts                   # GET: 24hr + 2hr reminders
│
├── components/
│   ├── ui/                                        # shadcn/ui — do not edit manually
│   │   ├── button.tsx
│   │   ├── card.tsx
│   │   ├── dialog.tsx
│   │   ├── form.tsx
│   │   ├── input.tsx
│   │   ├── label.tsx
│   │   ├── select.tsx
│   │   ├── textarea.tsx
│   │   ├── badge.tsx
│   │   ├── tabs.tsx
│   │   ├── separator.tsx
│   │   └── toast.tsx
│   │
│   ├── booking/                                   # Client booking flow
│   │   ├── service-grid.tsx                       # Services grouped by practitioner
│   │   ├── service-card.tsx                       # Single service card
│   │   ├── practitioner-picker.tsx                # Choose practitioner or "no preference"
│   │   ├── date-picker.tsx                        # Calendar — blocked dates greyed
│   │   ├── time-slot-grid.tsx                     # Available slots for selected practitioner
│   │   ├── new-client-form.tsx                    # Email, name, phone
│   │   ├── returning-client-lookup.tsx            # Email lookup, pre-fill
│   │   ├── health-intake-form.tsx                 # Full intake + liability waiver
│   │   ├── waiver-text.tsx                        # Full waiver text display
│   │   ├── policy-panel.tsx                       # Cancellation policy + checkbox
│   │   ├── deposit-summary.tsx                    # What you pay today and why
│   │   ├── stripe-payment-form.tsx                # Stripe Elements
│   │   ├── booking-confirmed.tsx                  # Confirmed state
│   │   └── booking-progress.tsx                   # Step indicator
│   │
│   ├── manage/                                    # Client self-service
│   │   ├── appointment-summary.tsx
│   │   ├── cancellation-notice.tsx                # Policy displayed before confirming
│   │   ├── reschedule-picker.tsx
│   │   └── manage-locked-notice.tsx               # Inside 24hr window
│   │
│   ├── practitioner/                              # Practitioner portal components
│   │   ├── today-schedule.tsx                     # Today's appointments list
│   │   ├── appointment-row.tsx                    # Single row with actions
│   │   ├── no-show-button.tsx                     # Confirm no-show (active post start time)
│   │   ├── soap-form.tsx                          # SOAP note entry form (S/O/A/P fields)
│   │   ├── soap-view.tsx                          # Read-only SOAP note display
│   │   ├── client-card.tsx                        # Client summary with last visit
│   │   ├── client-detail.tsx                      # Full client record: intake + history + notes
│   │   ├── intake-view.tsx                        # Read-only health intake display
│   │   ├── availability-editor.tsx                # Weekly hours + blocked dates
│   │   └── earnings-summary.tsx                   # Their own monthly commission breakdown
│   │
│   ├── owner/                                     # Owner dashboard components
│   │   ├── multi-practitioner-today.tsx           # Today's view: all 3 practitioners
│   │   ├── practitioner-column.tsx                # One practitioner's day within the view
│   │   ├── revenue-overview.tsx                   # Studio gross + per-practitioner breakdown
│   │   ├── commission-table.tsx                   # Monthly commission: gross / studio / payout
│   │   ├── practitioner-stat-card.tsx             # Summary card: bookings, revenue, no-shows
│   │   ├── all-clients-table.tsx                  # Full studio client list
│   │   ├── flagged-badge.tsx                      # Warning indicator for flagged clients
│   │   └── no-show-log.tsx                        # Month's no-shows across all practitioners
│   │
│   └── shared/
│       ├── studio-logo.tsx
│       ├── page-shell.tsx                         # Client-facing branded wrapper
│       ├── practitioner-shell.tsx                 # Practitioner portal sidebar layout
│       ├── owner-shell.tsx                        # Owner dashboard sidebar layout
│       └── error-state.tsx
│
├── hooks/
│   ├── use-booking-wizard.ts                      # Zustand: booking flow steps
│   ├── use-intake-wizard.ts                       # Zustand: multi-step intake form
│   ├── use-availability.ts                        # TanStack Query: slots by service + practitioner + date
│   ├── use-appointment.ts                         # TanStack Query: single appointment by token
│   ├── use-practitioner-dashboard.ts              # TanStack Query: today + week for practitioner
│   ├── use-owner-dashboard.ts                     # TanStack Query: full studio today + revenue
│   ├── use-soap-note.ts                           # TanStack Query + mutation: SOAP note per session
│   ├── use-clients.ts                             # TanStack Query: client list (scoped by role)
│   └── use-no-show.ts                             # Mutation: mark no-show
│
├── lib/
│   ├── db.ts                                      # Prisma singleton (globalThis)
│   ├── stripe.ts                                  # Stripe server client
│   ├── stripe-client.ts                           # loadStripe() browser singleton
│   ├── resend.ts                                  # Resend client
│   ├── session.ts                                 # iron-session config, getSession, requireOwner,
│   │                                              # requirePractitioner, getPractitionerId
│   ├── availability.ts                            # Slot generation per practitioner
│   ├── policy.ts                                  # Cancellation outcome (24hr window)
│   ├── commission.ts                              # Commission split calculation helpers
│   ├── tokens.ts                                  # nanoid session token generation
│   └── utils.ts                                   # cn(), formatUSD(), formatDateUS(), formatTime12h()
│
├── schemas/
│   ├── booking.schema.ts                          # Zod: service/slot/client selection payloads
│   ├── intake.schema.ts                           # Zod: health intake form + waiver
│   ├── soap.schema.ts                             # Zod: SOAP note fields
│   ├── appointment.schema.ts                      # Zod: reschedule, cancel, no-show
│   ├── availability.schema.ts                     # Zod: availability query params
│   ├── auth.schema.ts                             # Zod: login (owner + practitioner)
│   └── settings.schema.ts                        # Zod: service price/deposit edits
│
├── types/
│   ├── appointment.ts                             # Appointment, AppointmentStatus, DepositStatus
│   ├── client.ts                                  # Client, ClientWithRelations
│   ├── practitioner.ts                            # Practitioner, PractitionerRole, PractitionerStats
│   ├── service.ts                                 # Service, ServiceWithPractitioner
│   ├── soap.ts                                    # SoapNote, SoapNoteFields
│   ├── intake.ts                                  # HealthIntakeForm, WaiverStatus
│   ├── dashboard.ts                               # OwnerDashboardData, PractitionerDashboardData
│   └── session.ts                                 # SessionUser, UserRole
│
├── emails/
│   ├── booking-confirmed.tsx                      # Booking confirmed + intake form prompt
│   ├── intake-reminder.tsx                        # Sent if intake not completed 48hrs before
│   ├── reminder-24h.tsx                           # 24hr reminder
│   ├── reminder-2h.tsx                            # 2hr reminder
│   ├── cancellation-refunded.tsx                  # Cancelled 24hrs+, deposit refunded
│   ├── cancellation-forfeited.tsx                 # Cancelled under 24hrs, deposit forfeited
│   └── reschedule-confirmed.tsx                   # Rescheduled, new details
│
└── prisma/
    ├── schema.prisma
    └── seed.ts                                    # Seed: practitioners, services, demo data
```

---

## Database Schema

```prisma
// prisma/schema.prisma

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

// ─── Practitioners ────────────────────────────────────────────────────────────

model Practitioner {
  id              String         @id @default(cuid())
  slug            String         @unique          // "marisol" "david" "keila"
  name            String
  role            String                          // "Licensed Massage Therapist (LMT)"
  bio             String?
  email           String         @unique
  passwordHash    String
  isOwner         Boolean        @default(false)
  commissionSplit Float          @default(0.65)   // 0.65 = 65% to practitioner
  isActive        Boolean        @default(true)
  services        Service[]
  availability    WeeklyAvailability[]
  blockedDates    BlockedDate[]
  appointments    Appointment[]
  createdAt       DateTime       @default(now())
  updatedAt       DateTime       @updatedAt
}

// ─── Services ─────────────────────────────────────────────────────────────────

model Service {
  id              String        @id @default(cuid())
  slug            String        @unique           // "swedish-massage"
  name            String                          // "Swedish Massage"
  description     String?
  duration        Int                             // minutes: 60
  price           Int                             // cents: 9500 = $95.00
  deposit         Int                             // cents: 3500 = $35.00
  displayOrder    Int           @default(0)
  isActive        Boolean       @default(true)
  practitioner    Practitioner  @relation(fields: [practitionerId], references: [id])
  practitionerId  String
  appointments    Appointment[]
  createdAt       DateTime      @default(now())
  updatedAt       DateTime      @updatedAt
}

// ─── Clients ──────────────────────────────────────────────────────────────────

model Client {
  id              String        @id @default(cuid())
  email           String        @unique
  name            String
  phone           String?
  noShowCount     Int           @default(0)
  isFlagged       Boolean       @default(false)
  intakeForm      IntakeForm?
  appointments    Appointment[]
  createdAt       DateTime      @default(now())
  updatedAt       DateTime      @updatedAt
}

// ─── Health Intake Form ───────────────────────────────────────────────────────

model IntakeForm {
  id                    String    @id @default(cuid())
  client                Client    @relation(fields: [clientId], references: [id])
  clientId              String    @unique                // one per client, lifetime
  dateOfBirth           String?
  reasonForVisit        String?
  medicalConditions     String?
  medications           String?
  recentSurgeries       String?
  areasOfFocus          String?
  areasToAvoid          String?
  pregnancyStatus       String?                          // "not_pregnant" | "possibly" | "pregnant"
  pressurePreference    String?                          // "light" | "medium" | "firm" | "therapist"
  skinConditions        String?
  emergencyContactName  String?
  emergencyContactRel   String?
  emergencyContactPhone String?
  previousTreatment     Boolean   @default(false)
  referralSource        String?
  hipaaAcknowledgedAt   DateTime?
  waiverSignedAt        DateTime?
  waiverSignature       String?                          // typed full name as e-signature
  submittedAt           DateTime  @default(now())
  updatedAt             DateTime  @updatedAt
}

// ─── Appointments ─────────────────────────────────────────────────────────────

model Appointment {
  id                    String              @id @default(cuid())
  client                Client              @relation(fields: [clientId], references: [id])
  clientId              String
  practitioner          Practitioner        @relation(fields: [practitionerId], references: [id])
  practitionerId        String
  service               Service             @relation(fields: [serviceId], references: [id])
  serviceId             String

  startsAt              DateTime
  endsAt                DateTime
  status                AppointmentStatus   @default(CONFIRMED)

  // Pricing (all in cents)
  servicePrice          Int
  depositAmount         Int
  depositStatus         DepositStatus       @default(HELD)
  studioCommission      Int                 // cents: servicePrice * (1 - commissionSplit)
  practitionerPayout    Int                 // cents: servicePrice * commissionSplit

  // Stripe
  stripePaymentIntentId String?             @unique

  // Client access token
  sessionToken          String              @unique   // nanoid, manage link

  // Intake tracking
  intakeRequired        Boolean             @default(true)  // false for returning clients
  intakeCompletedAt     DateTime?

  // SOAP note
  soapNote              SoapNote?

  // Reminders
  reminder24hSentAt     DateTime?
  reminder2hSentAt      DateTime?
  intakeReminderSentAt  DateTime?

  // Lifecycle
  noShowMarkedAt        DateTime?
  cancelledAt           DateTime?
  cancellationReason    String?
  completedAt           DateTime?

  createdAt             DateTime            @default(now())
  updatedAt             DateTime            @updatedAt
}

enum AppointmentStatus {
  CONFIRMED
  COMPLETED
  CANCELLED
  NO_SHOW
}

enum DepositStatus {
  HELD        // paid, appointment active
  REFUNDED    // cancelled 24hrs+, Stripe refund issued
  FORFEITED   // cancelled under 24hrs or no-show
}

// ─── SOAP Notes ───────────────────────────────────────────────────────────────

model SoapNote {
  id              String      @id @default(cuid())
  appointment     Appointment @relation(fields: [appointmentId], references: [id])
  appointmentId   String      @unique
  // Only the treating practitioner's ID is stored here — enforced in queries
  practitionerId  String

  // SOAP fields
  subjective      String?     // client's report: pain level, areas of tension
  objective       String?     // practitioner observations: posture, ROM, palpation
  assessment      String?     // clinical findings and progress
  plan            String?     // next session focus, frequency, referrals

  // Additional fields
  sessionDuration Int?        // actual minutes (may differ from booked)
  techniquesUsed  String?     // comma-separated or free text
  followUpRec     Boolean     @default(false)
  followUpNotes   String?

  createdAt       DateTime    @default(now())
  updatedAt       DateTime    @updatedAt
}

// ─── Availability ─────────────────────────────────────────────────────────────

model WeeklyAvailability {
  id              String       @id @default(cuid())
  practitioner    Practitioner @relation(fields: [practitionerId], references: [id])
  practitionerId  String
  dayOfWeek       Int          // 0=Sun, 1=Mon ... 6=Sat
  startTime       String       // "09:00" (24hr)
  endTime         String       // "17:00"
  isActive        Boolean      @default(true)

  @@unique([practitionerId, dayOfWeek])
}

model BlockedDate {
  id              String       @id @default(cuid())
  practitioner    Practitioner @relation(fields: [practitionerId], references: [id])
  practitionerId  String
  date            DateTime     @db.Date
  reason          String?
  createdAt       DateTime     @default(now())
}

// ─── Cron Log ─────────────────────────────────────────────────────────────────

model CronLog {
  id              String    @id @default(cuid())
  type            String    // "reminder_24h" | "reminder_2h" | "intake_reminder"
  appointmentId   String
  sentAt          DateTime  @default(now())
  success         Boolean
  error           String?
}
```

---

## Role-Based Access — Enforced Server-Side

This is the defining feature of Project C. Every server function checks the
authenticated user's role and practitioner ID before returning any data.

| Data | Owner | Practitioner |
|---|---|---|
| Their own calendar | ✓ | ✓ |
| Other practitioners' calendars | Date/time only — no client names | ✗ |
| Their own client records | ✓ | ✓ |
| Other practitioners' clients | ✓ (owner audit) | ✗ |
| Their own SOAP notes | ✓ | ✓ |
| Other practitioners' SOAP notes | ✓ (owner audit only) | ✗ |
| Health intake forms | All clients | Their clients only |
| Studio revenue total | ✓ | ✗ |
| Their own earnings | ✓ | ✓ |
| Commission breakdown (all) | ✓ | ✗ |
| No-show marking | Any appointment | Their appointments only |
| Service price edits | ✓ | ✗ |

**Implementation rule:** Every practitioner-facing server function calls
`requirePractitioner(req)` and then filters all Prisma queries with
`WHERE practitionerId = session.practitionerId`. There are no client-side
permission checks — the server never returns data the role should not see.

---

## Environment Variables

```bash
# .env.local

# Database
DATABASE_URL="postgresql://..."

# Stripe
STRIPE_SECRET_KEY="sk_test_..."
STRIPE_WEBHOOK_SECRET="whsec_..."
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY="pk_test_..."

# Resend
RESEND_API_KEY="re_..."
EMAIL_FROM="Roots & Restore Wellness <hello@rootsandrestorewellness.com>"

# Auth
SESSION_SECRET="..."         # 32+ char random string

# Cron
CRON_SECRET="..."

# App
NEXT_PUBLIC_BASE_URL="http://localhost:3000"
```

---

## Build Checklist

### Phase 0 — Project Setup

- [ ] Initialise TanStack Start project
  ```bash
  npx create-tsrouter-app@latest roots-and-restore \
    --framework=react \
    --bundler=vite \
    --add-ons=shadcn
  ```
- [ ] Install core dependencies
  ```bash
  pnpm add prisma @prisma/client zod @tanstack/react-query zustand
  pnpm add stripe @stripe/stripe-js @stripe/react-stripe-js
  pnpm add resend @react-email/components react-email
  pnpm add iron-session bcrypt nanoid date-fns lucide-react
  pnpm add -D @types/bcrypt @types/node
  ```
- [ ] Add shadcn components
  ```bash
  npx shadcn@latest add button card input label select textarea form
  npx shadcn@latest add dialog badge separator toast tabs
  ```
- [ ] Initialise Prisma
  ```bash
  pnpm prisma init
  ```
- [ ] Create all folders per structure above
- [ ] Set up `.env.local`
- [ ] Set up Prettier + ESLint + Husky + lint-staged

---

### Phase 1 — Database

- [ ] Write `prisma/schema.prisma` (full schema above)
- [ ] Run first migration
  ```bash
  pnpm prisma migrate dev --name init
  ```
- [ ] Write `prisma/seed.ts`
  - [ ] Seed 3 practitioners: Marisol (owner), David, Keila — with hashed passwords
  - [ ] Seed all 8 services across the 3 practitioners
  - [ ] Seed weekly availability for each (different working days per practitioner):
    - Marisol: Mon–Fri, 9am–6pm
    - David: Tue, Thu, Sat, 10am–5pm
    - Keila: Mon, Wed, Fri, Sat, 11am–6pm
  - [ ] Seed 1 blocked date per practitioner (demonstrating the feature)
  - [ ] Seed 6 demo clients
  - [ ] Seed appointments across all 3 practitioners in various states
  - [ ] Seed completed intake forms for returning clients
  - [ ] Seed SOAP notes for completed appointments
- [ ] Run seed: `pnpm prisma db seed`
- [ ] Create `lib/db.ts` — Prisma singleton

---

### Phase 2 — Core Library Functions

- [ ] `lib/session.ts`
  - [ ] iron-session config, cookie name, TTL
  - [ ] `getSession(req)` — returns `{ userId, role, practitionerId? }`
  - [ ] `requireOwner(req)` — throws 401 if role !== 'owner'
  - [ ] `requirePractitioner(req)` — throws 401 if role not in ['owner', 'practitioner']
  - [ ] `getPractitionerId(req)` — returns practitioner ID from session (used to scope queries)

- [ ] `lib/availability.ts`
  - [ ] `getAvailableSlots(practitionerId, serviceId, date)` → `SlotOption[]`
    - Fetch `WeeklyAvailability` for that practitioner + day of week
    - Fetch `BlockedDate` for that practitioner + date
    - Fetch all `CONFIRMED` appointments for that practitioner + date
    - Generate slots every `service.duration + 15min buffer`
    - Skip overlaps, past times for today's date
    - Return open slots only
  - [ ] `getPractitionerWorkingDates(practitionerId, month)` → `Date[]`
    - Returns which dates in a given month have any availability
    - Used to grey out unavailable days in the calendar

- [ ] `lib/policy.ts`
  - [ ] `getCancellationOutcome(appointment)` → `'refund' | 'forfeit'`
    - 24hrs+: refund
    - Under 24hrs or no-show: forfeit
  - [ ] `isRescheduleAllowed(appointment)` → `boolean` (24hrs+ away)
  - [ ] `canMarkNoShow(appointment)` → `boolean` (after start time, same day)

- [ ] `lib/commission.ts`
  - [ ] `calculateCommission(servicePrice, commissionSplit)` →
    `{ studioCommission, practitionerPayout }`
  - [ ] `getPractitionerMonthlyStats(practitionerId, month, year)` →
    `{ grossRevenue, studioCommission, practitionerPayout, appointmentCount, noShowCount }`
  - [ ] `getStudioMonthlyRevenue(month, year)` →
    `{ totalGross, totalStudioCommission, byPractitioner[] }`

- [ ] `lib/tokens.ts`
  - [ ] `generateSessionToken()` — nanoid(21)
  - [ ] `getAppointmentBySessionToken(token)` — Prisma join with client + practitioner + service

- [ ] `lib/utils.ts`
  - [ ] `formatUSD(cents: number)` → `"$95.00"`
  - [ ] `formatDateUS(date: Date)` → `"Tuesday, January 14, 2025"` (US long format)
  - [ ] `formatShortDateUS(date: Date)` → `"1/14/2025"`
  - [ ] `formatTime12h(date: Date)` → `"10:30 AM"`
  - [ ] `cn(...classes)` — shadcn class merge

---

### Phase 3 — Zod Schemas

- [ ] `schemas/booking.schema.ts`
  - [ ] `SelectServiceSchema` — serviceSlug, practitionerSlug (or "no-preference")
  - [ ] `SelectSlotSchema` — date (ISO string), time ("10:30")
  - [ ] `NewClientSchema` — name, email, phone
  - [ ] `ReturningClientSchema` — email
  - [ ] `CreateBookingSchema` — full pre-checkout payload

- [ ] `schemas/intake.schema.ts`
  - [ ] `HealthIntakeSchema` — all 15 intake fields (see health intake form above)
  - [ ] `WaiverSchema` — waiverSignature: string (min 2), hipaaAcknowledged: literal(true),
    waiverAgreed: literal(true)
  - [ ] `IntakeSubmissionSchema` — combined: HealthIntakeSchema + WaiverSchema

- [ ] `schemas/soap.schema.ts`
  - [ ] `SoapNoteSchema` — subjective, objective, assessment, plan (all optional strings),
    sessionDuration (optional int), techniquesUsed (optional string),
    followUpRec (boolean), followUpNotes (optional string)

- [ ] `schemas/appointment.schema.ts`
  - [ ] `RescheduleSchema` — sessionToken, date, time
  - [ ] `CancelSchema` — sessionToken
  - [ ] `NoShowSchema` — appointmentId

- [ ] `schemas/auth.schema.ts`
  - [ ] `LoginSchema` — email, password

- [ ] `schemas/settings.schema.ts`
  - [ ] `UpdateServiceSchema` — serviceId, price (cents), deposit (cents)
  - [ ] `UpdateCommissionSchema` — practitionerId, commissionSplit (0.0–1.0)

---

### Phase 4 — Server Functions (API Layer)

- [ ] `api/availability/route.ts` — `getSlots(practitionerSlug, serviceSlug, date)`
  - [ ] Handle "no-preference" practitionerSlug: query all active practitioners
    who offer that service and merge available slots (labelled by practitioner)
  - [ ] Call `getAvailableSlots()` per practitioner
  - [ ] Return `SlotOption[]` with practitioner name on each slot

- [ ] `api/clients/lookup.ts` — `lookupClient(email)`
  - [ ] Find client by email, return `{ found, name, phone }`
  - [ ] Never return health intake data to the booking flow

- [ ] `api/booking/checkout.ts` — `createCheckout(bookingData)`
  - [ ] Validate `CreateBookingSchema`
  - [ ] Re-check slot availability (race condition guard)
  - [ ] Look up practitioner and service to calculate commission split
  - [ ] Create Stripe PaymentIntent with metadata:
    - `clientEmail`, `clientName`, `clientPhone`
    - `practitionerId`, `serviceId`
    - `startsAt`, `endsAt`
    - `depositAmount`, `servicePrice`
    - `studioCommission`, `practitionerPayout`
    - `intakeRequired` (true if new client, false if returning with existing intake)
  - [ ] Return `{ clientSecret }`

- [ ] `api/stripe/webhook.ts`
  - [ ] Verify Stripe signature
  - [ ] `payment_intent.succeeded`:
    - [ ] Find or create `Client` by email
    - [ ] Create `Appointment` from metadata — `CONFIRMED`, `depositStatus: HELD`
    - [ ] Set `intakeRequired` from metadata
    - [ ] Generate `sessionToken`
    - [ ] Send `booking-confirmed` email with:
      - Appointment summary (US date/time format)
      - Practitioner name and service
      - Intake form link if `intakeRequired = true`
      - Manage link
    - [ ] If `intakeRequired = true`: schedule intake reminder for 48hrs before session
  - [ ] `payment_intent.payment_failed`: log, no appointment

- [ ] `api/intake/submit.$sessionToken.ts` — `submitIntake(token, data)`
  - [ ] Validate `IntakeSubmissionSchema`
  - [ ] Look up appointment by `sessionToken`
  - [ ] Find client on appointment
  - [ ] Check if client already has an `IntakeForm` — update if so, create if not
  - [ ] Set `waiverSignedAt`, `hipaaAcknowledgedAt`, `waiverSignature`
  - [ ] Set `appointment.intakeCompletedAt`
  - [ ] Return `{ submitted: true }`

- [ ] `api/manage/appointment.$sessionToken.ts` — `getAppointmentManage(token)`
  - [ ] Look up appointment by `sessionToken` with client + practitioner + service
  - [ ] Return: service, practitioner name, date, time, status, deposit status
  - [ ] Do NOT return SOAP notes, intake form, or other client data

- [ ] `api/manage/reschedule.$sessionToken.ts` — `rescheduleAppointment(token, date, time)`
  - [ ] Validate `RescheduleSchema`
  - [ ] Verify `isRescheduleAllowed()` — return 403 if within 24hrs
  - [ ] Check new slot availability
  - [ ] Update `startsAt`, `endsAt`, reset reminder flags
  - [ ] Send `reschedule-confirmed` email
  - [ ] Return updated appointment summary

- [ ] `api/manage/cancel.$sessionToken.ts` — `cancelAppointment(token)`
  - [ ] Validate `CancelSchema`
  - [ ] Call `getCancellationOutcome()` — refund or forfeit
  - [ ] Execute Stripe action:
    - [ ] `refund`: `stripe.refunds.create({ payment_intent: ... })`
    - [ ] `forfeit`: update `depositStatus: FORFEITED`, no Stripe action
  - [ ] Update `status: CANCELLED`, `cancelledAt`, `depositStatus`
  - [ ] Send correct cancellation email (refunded or forfeited)
  - [ ] Return outcome

- [ ] `api/practitioner/auth.ts` — `practitionerLogin(email, password)` / `logout()`
  - [ ] Validate `LoginSchema`
  - [ ] Find practitioner by email
  - [ ] Compare password with `bcrypt.compare()`
  - [ ] Set session: `{ userId: practitioner.id, role: 'practitioner', practitionerId: practitioner.id }`
  - [ ] If `practitioner.isOwner`: set `role: 'owner'` instead

- [ ] `api/practitioner/appointments.ts` — `getPractitionerAppointments(filters?)`
  - [ ] `requirePractitioner(req)`
  - [ ] Prisma query scoped to `practitionerId = session.practitionerId`
  - [ ] Filterable: status, date range
  - [ ] Return appointments with client name only (not full intake)

- [ ] `api/practitioner/appointments.$id.noshow.ts` — `markNoShow(appointmentId)`
  - [ ] `requirePractitioner(req)`
  - [ ] Verify appointment belongs to `session.practitionerId`
  - [ ] Verify `canMarkNoShow()` — after start time, same day
  - [ ] Update `status: NO_SHOW`, `depositStatus: FORFEITED`, `noShowMarkedAt`
  - [ ] Increment `client.noShowCount`
  - [ ] If `client.noShowCount >= 2`: set `client.isFlagged = true`
  - [ ] Return updated appointment

- [ ] `api/practitioner/soap.$appointmentId.ts`
  - [ ] `GET`: `requirePractitioner(req)`, verify appointment belongs to them, return SOAP note
  - [ ] `POST`: create SOAP note — verify no existing note (idempotency)
  - [ ] `PUT`: update existing SOAP note
  - [ ] All three: confirm `soapNote.practitionerId === session.practitionerId`

- [ ] `api/practitioner/clients.ts` — `getPractitionerClients(search?)`
  - [ ] `requirePractitioner(req)`
  - [ ] Prisma: find all clients who have at least one appointment with this practitioner
  - [ ] Return: name, email, last visit, last service, appointment count
  - [ ] Client health intake: returned only when fetching single client

- [ ] `api/practitioner/clients.$id.ts` — `getPractitionerClient(clientId)`
  - [ ] `requirePractitioner(req)`
  - [ ] Verify this client has appointments with `session.practitionerId`
  - [ ] Return: client details + intake form + appointment history + SOAP notes
    (all scoped to this practitioner's appointments only)

- [ ] `api/practitioner/availability.ts`
  - [ ] `GET`: return this practitioner's `WeeklyAvailability` + `BlockedDate`
  - [ ] `PUT`: update `WeeklyAvailability` records for this practitioner
  - [ ] Both scoped to `session.practitionerId`

- [ ] `api/owner/dashboard.ts` — `getOwnerDashboard()`
  - [ ] `requireOwner(req)`
  - [ ] Today's appointments across ALL practitioners — grouped by practitioner
  - [ ] This week's appointment count
  - [ ] Revenue snapshot: studio gross this month, per practitioner breakdown
  - [ ] No-show count this month across all practitioners

- [ ] `api/owner/practitioners.ts` — `listPractitioners()`
  - [ ] `requireOwner(req)`
  - [ ] Return all practitioners with their monthly stats:
    `getPractitionerMonthlyStats()` per practitioner for current month

- [ ] `api/owner/practitioners.$id.ts` — `getPractitionerCommission(id, month, year)`
  - [ ] `requireOwner(req)`
  - [ ] Detailed commission breakdown: every completed appointment that month,
    gross / studio commission / practitioner payout per appointment
  - [ ] Totals at the bottom: month summary

- [ ] `api/owner/clients.ts` — `getAllClients(search?)`
  - [ ] `requireOwner(req)`
  - [ ] Returns ALL clients across the studio
  - [ ] Includes: name, email, practitioners seen, last visit, no-show flag

- [ ] `api/owner/clients.$id.ts` — `getClientFull(clientId)`
  - [ ] `requireOwner(req)`
  - [ ] Full client record: intake form, appointment history across all practitioners,
    SOAP notes from all practitioners (owner audit access)

- [ ] `api/owner/settings.ts`
  - [ ] `PUT /service`: validate `UpdateServiceSchema`, update price + deposit
  - [ ] `PUT /commission`: validate `UpdateCommissionSchema`, update `commissionSplit`
  - [ ] Both require `requireOwner(req)`

- [ ] `api/cron/reminders.ts`
  - [ ] Verify `CRON_SECRET` header
  - [ ] **Reminder 1 — Intake reminder:** find appointments where `intakeRequired = true`
    and `intakeCompletedAt IS NULL` and `startsAt` within 48hrs
    and `intakeReminderSentAt IS NULL`
    → Send `intake-reminder` email, set `intakeReminderSentAt`
  - [ ] **Reminder 2 — 24hr reminder:** find `CONFIRMED` appointments where `startsAt`
    within 24hrs and `reminder24hSentAt IS NULL`
    → Send `reminder-24h`, set `reminder24hSentAt`
  - [ ] **Reminder 3 — 2hr reminder:** find `CONFIRMED` appointments where `startsAt`
    within 2hrs and `reminder2hSentAt IS NULL`
    → Send `reminder-2h`, set `reminder2hSentAt`
  - [ ] Log all to `CronLog`

---

### Phase 5 — Email Templates (React Email)

All emails use US date/time format (1/14/2025, 10:30 AM). Branded as Roots & Restore Wellness.

- [ ] `emails/booking-confirmed.tsx`
  - [ ] Props: `clientName`, `service`, `practitionerName`, `date`, `time`, `depositPaid`,
    `manageUrl`, `intakeUrl` (null if returning client), `studioAddress`
  - [ ] Content: appointment summary, deposit paid, what to bring/wear/expect
  - [ ] If `intakeUrl` present: "Before your visit, please complete your health intake form"
    with prominent CTA. It must be done before arrival.
  - [ ] Manage link in footer

- [ ] `emails/intake-reminder.tsx`
  - [ ] Props: `clientName`, `practitionerName`, `date`, `time`, `intakeUrl`
  - [ ] Content: "Your appointment is coming up — please complete your intake form
    before arriving. It only takes a few minutes and helps [practitionerName]
    prepare your session."
  - [ ] Single CTA: "Complete Health Intake Form"

- [ ] `emails/reminder-24h.tsx`
  - [ ] Props: `clientName`, `service`, `practitionerName`, `date`, `time`,
    `studioAddress`, `manageUrl`, `intakeComplete` (boolean)
  - [ ] If `intakeComplete = false`: include intake reminder callout (urgent tone)
  - [ ] Content: tomorrow's appointment, address, what to bring

- [ ] `emails/reminder-2h.tsx`
  - [ ] Props: `clientName`, `service`, `practitionerName`, `time`, `studioAddress`
  - [ ] Content: "Your appointment is today at [time]." Address. Arrive 5 mins early.
    "Please note our 24-hour cancellation policy applies."

- [ ] `emails/cancellation-refunded.tsx`
  - [ ] Props: `clientName`, `service`, `date`, `depositAmount`, `practitionerName`
  - [ ] Content: cancelled, full deposit refunded, timeline 3–5 business days, rebook CTA

- [ ] `emails/cancellation-forfeited.tsx`
  - [ ] Props: `clientName`, `service`, `date`, `depositAmount`, `practitionerName`
  - [ ] Content: cancelled under 24hrs, deposit forfeited per agreed policy, rebook CTA

- [ ] `emails/reschedule-confirmed.tsx`
  - [ ] Props: `clientName`, `service`, `practitionerName`, `newDate`, `newTime`, `manageUrl`
  - [ ] Content: rescheduled confirmation, new details, deposit transfers automatically

---

### Phase 6 — Client Booking Flow

Multi-step wizard. State in Zustand. URL advances per step.

#### Public Booking Page `routes/index.tsx`
- [ ] Server component — fetch all active services grouped by practitioner
- [ ] `<ServiceGrid />`:
  - [ ] Tabs or sections per practitioner (Marisol / David / Keila)
  - [ ] Each `<ServiceCard />`: service name, duration, price, deposit, practitioner
- [ ] On service select: navigate to `/book/[serviceSlug]/[practitionerSlug]`
  OR let client pick practitioner on next step if "no preference" shown

#### Date + Time `routes/book/$serviceSlug.$practitionerSlug.tsx`
- [ ] Validate service + practitioner slugs server-side — 404 if invalid
- [ ] `<DatePicker />` — uses `getPractitionerWorkingDates()` to grey unavailable days
- [ ] On date select: query `api/availability` for that practitioner + service + date
- [ ] `<TimeSlotGrid />` — slots with practitioner name (relevant for "no preference" path)
- [ ] On slot select: save to Zustand, navigate to `/book/intake`

#### Client Intake `routes/book/intake.tsx`
- [ ] Email lookup first — returning or new?
  - [ ] Returning client with existing intake: skip health form, proceed to policy
  - [ ] Returning client without intake (edge case): show health form
  - [ ] New client: show `<NewClientForm />` (name, email, phone), proceed to health form
- [ ] Save client data to Zustand, navigate to health form if needed or policy

#### Health Intake + Waiver `routes/book/health-form.tsx`
- [ ] Only shown for new clients (or returning without intake on file)
- [ ] Render `<HealthIntakeForm />` — all 15 fields, US-standard order
- [ ] Render `<WaiverText />` — full liability waiver text, must scroll to bottom
- [ ] E-sign: client types full name, ticks HIPAA acknowledgement and waiver agreement
- [ ] Note: intake is NOT submitted yet — stored in Zustand until after payment
  (if payment fails, no intake record is created)
- [ ] On complete: navigate to policy page

#### Policy `routes/book/policy.tsx`
- [ ] Full cancellation policy shown
- [ ] Booking summary sidebar: service, practitioner, date, time, deposit to pay
- [ ] Checkbox: "I have read and agree to the cancellation policy"
- [ ] Navigate to payment

#### Payment `routes/book/payment.tsx`
- [ ] POST to `createCheckout()` on mount — get `clientSecret`
- [ ] `<DepositSummary />`: service, deposit amount, what it secures
- [ ] `<StripePaymentForm />` — Stripe Elements
- [ ] Test card shown: 4242 4242 4242 4242
- [ ] On payment success: Stripe webhook fires → appointment created → intake submitted
  via a separate call immediately after payment confirmation
  - [ ] POST intake data from Zustand to `api/intake/submit.[sessionToken]` once token
    is returned from the confirmation page poll

#### Booking Confirmed `routes/book/confirmed.tsx`
- [ ] Poll for appointment creation (polling `api/manage/appointment.[sessionToken]`)
- [ ] Show: service, practitioner, date, time, deposit paid
- [ ] If intake required: "Check your email — you'll find a link to complete your
  health intake form before your visit"
- [ ] Manage link shown

---

### Phase 7 — Client Self-Service

Same pattern as Project A — tokenised manage link. No login.

#### Appointment View `routes/manage/$sessionToken.tsx`
- [ ] Fetch appointment by token (server component)
- [ ] Show: service, practitioner, date, time, deposit status, current status
- [ ] Intake status: "Complete before your visit" if not done
- [ ] If `CONFIRMED`: Reschedule button (if allowed) + Cancel button
- [ ] If inside 24hrs: reschedule locked, manage link shows lock notice

#### Reschedule `routes/manage/$sessionToken/reschedule.tsx`
- [ ] Same date/time picker — reuse components
- [ ] POST to `rescheduleAppointment()`
- [ ] Confirmation email sent server-side

#### Cancel `routes/manage/$sessionToken/cancel.tsx`
- [ ] Policy shown with outcome based on current timing
- [ ] "Your deposit will be [refunded / forfeited] because [reason]"
- [ ] Confirm button → POST to `cancelAppointment()`
- [ ] Confirmation email sent

---

### Phase 8 — Practitioner Portal

Login at `routes/practitioner/login.tsx`. All routes protected by
`requirePractitioner()` in server function or `beforeLoad` in route tree.

#### Practitioner Dashboard `routes/practitioner/dashboard.tsx`
- [ ] TanStack Query: `getPractitionerAppointments({ date: today })`
- [ ] `<TodaySchedule />` — today's appointments in time order
  - [ ] Each row: client name (first name only on mobile), service, time, intake status badge
  - [ ] Actions: Mark Complete / Mark No-show (active after start time)
  - [ ] Click row → appointment detail
- [ ] Compact this-week view below
- [ ] Earnings this month: gross bookings → their payout (35/65 split shown simply)

#### Appointment Detail `routes/practitioner/appointments/$appointmentId.tsx`
- [ ] Appointment summary: client, service, date, time, status
- [ ] Intake status: "Completed" or "Pending" with prompt if pending
- [ ] SOAP note section:
  - [ ] If no note: `<SoapForm />` — write new note (all 4 SOAP fields)
  - [ ] If note exists: `<SoapView />` — read-only, with "Edit" toggle
  - [ ] Submit / update note → POST or PUT to `api/practitioner/soap.[appointmentId]`

#### Client List `routes/practitioner/clients/index.tsx`
- [ ] TanStack Query: `getPractitionerClients()`
- [ ] Table: name, last service, last visit date, appointment count
- [ ] Searchable by name or email
- [ ] Flagged clients show `<FlaggedBadge />`

#### Client Detail `routes/practitioner/clients/$clientId.tsx`
- [ ] Full client record scoped to this practitioner's data:
  - [ ] Health intake form (read-only view of all fields)
  - [ ] Appointment history (their sessions only — other practitioners hidden)
  - [ ] SOAP notes per session (their notes only)
- [ ] No edit access to intake data — practitioners read only

#### Availability `routes/practitioner/availability/index.tsx`
- [ ] `<AvailabilityEditor />` — 7 day toggles, start/end time per active day
- [ ] `<BlockedDatesManager />` — add/remove specific blocked dates
- [ ] Save → PUT to `api/practitioner/availability`

---

### Phase 9 — Owner Dashboard

Login at `routes/owner/login.tsx` (same login form as practitioner — role determined
by `practitioner.isOwner`). All routes protected by `requireOwner()`.

#### Owner Dashboard `routes/owner/dashboard.tsx`
- [ ] Server component: `getOwnerDashboard()`
- [ ] `<MultiPractitionerToday />`:
  - [ ] Three columns (or tabs on mobile): Marisol / David / Keila
  - [ ] Each `<PractitionerColumn />`: today's appointments for that practitioner
    - [ ] Client name, service, time, deposit status
    - [ ] No-show button (active after start time)
- [ ] `<RevenueOverview />` — current month:
  - [ ] Studio gross: total across all practitioners
  - [ ] Studio commission: total earned by the studio
  - [ ] Per practitioner: gross, studio commission, their payout
- [ ] No-show count this month across all practitioners

#### Practitioner List `routes/owner/practitioners/index.tsx`
- [ ] TanStack Query: `listPractitioners()`
- [ ] 3 `<PractitionerStatCard />` components:
  - [ ] Name, role, this month: bookings count, gross revenue, their payout, no-shows

#### Practitioner Commission Detail `routes/owner/practitioners/$practitionerId.tsx`
- [ ] Month picker (default: current month)
- [ ] `<CommissionTable />`:
  - [ ] Every completed appointment: date, client name, service, gross, studio %, payout
  - [ ] Totals row at bottom
- [ ] "Total to pay [David]: $X this month" — the number Marisol needs to transfer

#### All Clients `routes/owner/clients/index.tsx`
- [ ] All clients across the studio
- [ ] Table: name, email, practitioners seen (badges), last visit, no-show flag
- [ ] Searchable by name or email

#### Client Detail (Owner) `routes/owner/clients/$clientId.tsx`
- [ ] Full record: intake form, complete appointment history across ALL practitioners,
  ALL SOAP notes from all practitioners (audit access)
- [ ] Read-only — owner audits, does not edit practitioner notes

#### Settings `routes/owner/settings/services.tsx`
- [ ] Service list grouped by practitioner
- [ ] Inline price and deposit editing per service
- [ ] Save per row

#### Commission Settings `routes/owner/settings/commission.tsx`
- [ ] Per-practitioner commission split editor
- [ ] Shows: practitioner name, current split (65% / 35%), editable split slider or input
- [ ] Save → `api/owner/settings` PUT /commission

---

### Phase 10 — Cron Configuration

```json
// vercel.json
{
  "crons": [{ "path": "/api/cron/reminders", "schedule": "*/15 * * * *" }]
}
```

- [ ] `CRON_SECRET` verified in the reminders route
- [ ] All 3 reminder types implemented: intake reminder, 24hr, 2hr
- [ ] `CronLog` entries created for every send attempt

---

### Phase 11 — Polish and Demo Readiness

- [ ] All Stripe interactions use test mode keys
- [ ] Test card shown on payment page: 4242 4242 4242 4242
- [ ] Seed includes appointments at all stages for a realistic demo
- [ ] Mobile-responsive: booking flow and manage page (client's primary device)
- [ ] Confirm all 7 email templates render: `pnpm email dev`
- [ ] Full end-to-end test:
  - [ ] New client books with David → receives confirmation + intake prompt
  - [ ] Client submits health intake form
  - [ ] 24hr and 2hr reminders fire (manual trigger for demo)
  - [ ] David logs in → sees today's appointment → writes SOAP note post-session
  - [ ] Owner logs in → sees all 3 practitioners' days → sees David's booking in revenue
  - [ ] Owner views commission table for David (month total)
  - [ ] Client cancels within 24hrs → deposit forfeited, forfeiture email received
  - [ ] No-show flow: David marks a client as no-show after start time
  - [ ] Client with 2 no-shows appears as flagged in owner client list
  - [ ] Returning client books Keila → intake skipped, goes straight to policy + payment
- [ ] Write `README.md` — setup, env vars, seed instructions, demo walkthroughs,
  test credentials for owner login and each practitioner login

---

### Phase 12 — Portfolio Writeup (Case Study)

- [ ] Write case study for Demola Studio portfolio page
  - [ ] Before: the four-tool stack — Acuity + Jane App + Square + Google Sheets —
    what each one misses and where the handoff breaks
  - [ ] The core problem: one Acuity account means practitioners can see each other's
    clients. Commission is calculated in a spreadsheet at month end.
    No-show policy is enforced differently by each person.
  - [ ] What stays: their existing Square hardware for in-person card payments
  - [ ] What was built: role-based access, health intake, SOAP notes, commission
    tracking — all in one system, not four
  - [ ] What it solves: David and Keila's clients are private.
    Marisol sees one number at month end, not a spreadsheet.
    The no-show policy is enforced the same way by everyone.
- [ ] Record video walkthrough — 3 parts:
  - [ ] Part 1 (3 min): client books a new appointment → health intake form →
    payment → confirmation email
  - [ ] Part 2 (2 min): David logs in → sees his day → writes SOAP note →
    marks session complete
  - [ ] Part 3 (3 min): Marisol logs in as owner → multi-practitioner today view →
    commission table for David → all clients (flagged client visible) →
    commission settings

---

## Key Implementation Notes

**Role-based access is enforced server-side only**
There are no client-side permission checks. The UI shows the right things because
the server only returns what the session role is allowed to see. A practitioner
cannot access another practitioner's data by guessing a URL — the server function
checks `WHERE practitionerId = session.practitionerId` on every query.

**Commission calculated at booking creation, not at query time**
`studioCommission` and `practitionerPayout` are stored on each `Appointment` at the
moment of creation (inside the Stripe webhook). This means: if the commission split
changes later, historical appointments retain their original split. The commission
table is a simple SUM of stored values — no recalculation needed.

**Health intake is client-scoped, not appointment-scoped**
One `IntakeForm` per client (OneToOne on `Client`). It is created on first booking
and updated if the client updates it. It is not recreated per appointment. If a
returning client's medical history changes, the intake form is the place to update it.
Future improvement (out of demo scope): version the intake form so changes are tracked.

**SOAP notes are appointment-scoped and practitioner-locked**
One `SoapNote` per appointment. The `practitionerId` field on `SoapNote` must always
match the `Appointment.practitionerId`. The server verifies this match on every SOAP
note read or write. The owner can read all SOAP notes for compliance — but the
practitioner server functions reject cross-practitioner access.

**No-preference booking**
When a client selects "no preference" for practitioner, the availability query runs
against all practitioners who offer that service and merges slots. Each slot is
labelled with the practitioner's name. The client sees availability across the
whole studio, not just one person. The practitioner is assigned at slot selection and
carried through the booking wizard in Zustand.

**US date and time formatting throughout**
All emails, dashboard displays and client-facing pages use US format:
- Dates: "Tuesday, January 14, 2025" (long) or "1/14/2025" (short)
- Times: "10:30 AM" (12-hour with AM/PM)
- Currency: "$95.00" (USD)
`date-fns` handles all formatting via `formatDateUS()` and `formatTime12h()` in `lib/utils.ts`.

**HIPAA considerations (noted for client conversations)**
The demo stores health intake data in a PostgreSQL database with standard Prisma
security. For a production build, this would require: encrypted fields for sensitive
health data, audit logs for all data access, Business Associate Agreements (BAAs)
with any third-party services (Resend, database host), and a formal HIPAA compliance
review. The demo demonstrates awareness of these requirements — mention this in the
case study and when talking to US health/wellness clients. It signals you know the
landscape, not just the technology.
