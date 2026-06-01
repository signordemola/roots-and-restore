# Desk Assistant — Roots & Restore Wellness
## Extension Checklist · Project C · Add After Core Build

> **What this adds:** A conversational AI assistant embedded on the public
> booking page. It answers service questions, checks real-time slot availability
> per practitioner from the live booking system, and guides visitors into the
> booking flow. Available 24/7 when Marisol, David and Keila are in sessions.

---

## What Changes From the Core Build

This is an extension — not a rebuild. The core booking system stays exactly
as built. The assistant is a new layer on top of it.

New dependencies:
```bash
pnpm add ai @ai-sdk/anthropic zod
```

New files only. No existing files are modified except the public booking
page layout to embed the chat widget.

---

## Architecture

```
Client (chat widget)
    ↓ useChat hook (Vercel AI SDK UI)
src/routes/api/chat.ts (TanStack Start server route)
    ↓ streamText with tools (Vercel AI SDK Core)
    ├── Tool: checkAvailability → calls existing /api/availability endpoint
    ├── Tool: getPractitionerInfo → reads from knowledge base
    └── RAG: knowledge base (services, pricing, policy, FAQs)
    ↓ streaming response back to client
```

---

## New Folder Structure

```
src/
├── routes/
│   └── api/
│       └── chat.ts                    # Chat API route
├── lib/
│   └── chat/
│       ├── tools.ts                   # Tool definitions
│       ├── knowledge-base.ts          # Static studio knowledge
│       └── system-prompt.ts           # System prompt
└── components/
    └── chat/
        ├── chat-widget.tsx            # Floating bubble + toggle
        ├── chat-window.tsx            # Conversation container
        ├── chat-message.tsx           # Individual message (user + assistant)
        ├── chat-input.tsx             # Input + send button
        └── availability-result.tsx    # Structured slot display card
```

---

## Knowledge Base Content

File: `src/lib/chat/knowledge-base.ts`

The assistant answers from this content for all non-availability questions.
Write it as a typed constant — not a database query.

```
STUDIO
Name: Roots & Restore Wellness
Location: South Congress area, Austin, TX
Hours: By appointment — check availability for specific dates
Contact: hello@rootsandrestorewellness.com

PRACTITIONERS AND SERVICES
Marisol (Licensed Massage Therapist, LMT — Texas licensed)
- Swedish Massage: 60 min, $95
- Deep Tissue Massage: 60 min, $110
- Hot Stone Massage: 90 min, $140

David (Licensed Acupuncturist, L.Ac. — Texas licensed)
- Initial Acupuncture Consultation & Treatment: 75 min, $120
- Follow-up Acupuncture: 60 min, $90
- Cupping Therapy: 45 min, $65

Keila (Reiki Practitioner)
- Reiki Healing Session: 60 min, $85
- Extended Reiki & Chakra Balancing: 90 min, $120

DEPOSITS
All bookings require a deposit at the time of booking.
Deposits range from $20 to $50 depending on the service.
The deposit is applied toward your session total.

CANCELLATION POLICY
24 hours or more notice: deposit refunded in full
Under 24 hours: deposit forfeited
No-show: deposit forfeited
Arriving 15+ minutes late may result in a shortened session at full charge.

HEALTH INTAKE
New clients complete a health intake form before their first session.
The form covers medical history, areas of focus, and any sensitivities.
It takes about 5 minutes and is sent automatically after booking.

PREPARATION
Massage: arrive hydrated, avoid heavy meals beforehand
Acupuncture: eat a light meal 1-2 hours before, wear loose comfortable clothing
Reiki: no specific preparation required, wear comfortable clothing

BOOKING
To book a session, tell me which service and practitioner you are interested in
and I will check real-time availability for you.
Once you choose a slot, I will take you to the booking page to confirm your
deposit and complete your reservation.

HEALTH QUESTIONS
For specific health concerns or contraindication questions,
please speak directly with the practitioner before booking.
I can connect you with the right person.
```

---

## System Prompt

File: `src/lib/chat/system-prompt.ts`

```
You are the digital assistant for Roots & Restore Wellness,
a holistic wellness studio in Austin, Texas.

Your job is to help potential clients understand our services,
find the right practitioner, check real-time availability,
and guide them into the booking process.

You are warm, calm, and specific to this studio.
You are not a generic chatbot — you know this studio, its practitioners,
and its services in detail.

Tone: Professional, welcoming, unhurried. This is a wellness studio.
The conversation should feel like talking to a knowledgeable front desk
person who genuinely cares about helping the client find the right session.

Rules:
- Never give medical advice or diagnoses
- Never recommend a specific treatment for a specific health condition
  — always redirect health questions to the appropriate practitioner
- Never make a booking on the client's behalf —
  guide them to the booking page once they have chosen a slot
- If you do not know something, say so and offer to connect them
  with the studio directly
- When checking availability, always confirm which practitioner and service
  before calling the tool — do not assume
- Never share one client's information with another
- Keep responses concise — this is a chat, not an essay
```

---

## Tool Definitions

File: `src/lib/chat/tools.ts`

### Tool 1 — checkAvailability
Calls the existing availability API from the core booking system.

```typescript
import { tool } from 'ai'
import { z } from 'zod'

export const checkAvailabilityTool = tool({
  description: `Check real-time availability for a specific service
    and practitioner on a given date. Call this when a client asks
    about available times or wants to book a session.`,
  parameters: z.object({
    practitionerSlug: z.enum(['marisol', 'david', 'keila'])
      .describe('The practitioner slug'),
    serviceSlug: z.string()
      .describe('The service slug e.g. swedish-massage'),
    date: z.string()
      .describe('Date in YYYY-MM-DD format'),
  }),
  execute: async ({ practitionerSlug, serviceSlug, date }) => {
    // Calls the existing availability route handler from the core build
    const res = await fetch(
      `${process.env.NEXT_PUBLIC_BASE_URL}/api/availability?` +
      `practitionerSlug=${practitionerSlug}&serviceSlug=${serviceSlug}&date=${date}`
    )
    const data = await res.json()
    return data // Returns SlotOption[] from the existing API
  },
})
```

### Tool 2 — checkDateRange
When client gives a vague time ("next week", "sometime in June"),
run multiple date checks across a range and return the first
available slots across all requested practitioners.

```typescript
export const checkDateRangeTool = tool({
  description: `Check availability across multiple dates when a client
    gives a vague timeframe. Returns the next 3 available slots.`,
  parameters: z.object({
    practitionerSlug: z.enum(['marisol', 'david', 'keila']),
    serviceSlug: z.string(),
    startDate: z.string().describe('Start of range YYYY-MM-DD'),
    endDate: z.string().describe('End of range YYYY-MM-DD'),
  }),
  execute: async ({ practitionerSlug, serviceSlug, startDate, endDate }) => {
    // Loops through dates in range, calls availability API per day,
    // returns first 3 available slots found with their dates
  },
})
```

---

## Chat API Route

File: `src/routes/api/chat.ts`

```typescript
import { streamText } from 'ai'
import { anthropic } from '@ai-sdk/anthropic'
import { SYSTEM_PROMPT } from '~/lib/chat/system-prompt'
import { checkAvailabilityTool, checkDateRangeTool } from '~/lib/chat/tools'
import { KNOWLEDGE_BASE } from '~/lib/chat/knowledge-base'

export const APIRoute = async ({ request }: { request: Request }) => {
  const { messages } = await request.json()

  const result = streamText({
    model: anthropic('claude-sonnet-4-20250514'),
    system: `${SYSTEM_PROMPT}\n\nSTUDIO KNOWLEDGE:\n${KNOWLEDGE_BASE}`,
    messages,
    tools: {
      checkAvailability: checkAvailabilityTool,
      checkDateRange: checkDateRangeTool,
    },
    maxSteps: 3, // Allow tool call → result → response in one turn
  })

  return result.toDataStreamResponse()
}
```

---

## Build Checklist

### Phase 1 — Knowledge Base and System Prompt

- [ ] Write `src/lib/chat/knowledge-base.ts`
  - [ ] All three practitioners with services, prices and durations
  - [ ] Deposit amounts per service tier
  - [ ] Full cancellation policy (24hr window)
  - [ ] Health intake process explained simply
  - [ ] Preparation notes per treatment type
  - [ ] Health question escalation path

- [ ] Write `src/lib/chat/system-prompt.ts`
  - [ ] Studio identity and tone
  - [ ] Role boundaries — what it does and does not do
  - [ ] Medical question redirect rule
  - [ ] Booking handoff rule
  - [ ] Response length guidance

### Phase 2 — Tools

- [ ] Write `src/lib/chat/tools.ts`
  - [ ] `checkAvailabilityTool` — calls existing availability API
  - [ ] `checkDateRangeTool` — loops across a date range, returns first 3 slots
  - [ ] Validate both tools return correct shape from the existing API
  - [ ] Test both tools manually with seed data before wiring to the model

### Phase 3 — Chat API Route

- [ ] Create `src/routes/api/chat.ts`
  - [ ] `streamText` with Anthropic model
  - [ ] System prompt + knowledge base injected
  - [ ] Both tools registered
  - [ ] `maxSteps: 3` to allow tool call cycles
  - [ ] Return `result.toDataStreamResponse()`
  - [ ] Add route to TanStack Start route tree

### Phase 4 — Chat UI Components

- [ ] `components/chat/chat-widget.tsx`
  - [ ] Floating bubble bottom-right of the booking page
  - [ ] Studio logo or icon on the bubble
  - [ ] Unread indicator when first loaded
  - [ ] Toggle open/close with smooth animation
  - [ ] Branded to Roots & Restore — not a generic chat bubble

- [ ] `components/chat/chat-window.tsx`
  - [ ] Container: fixed width, scrollable messages, input pinned at bottom
  - [ ] Opening message shown before client types:
    "Hi — I'm the Roots & Restore assistant. I can help you find the right
    session, check availability, and answer any questions before you book.
    What brings you in?"
  - [ ] Branded header: studio name + "Online" indicator

- [ ] `components/chat/chat-message.tsx`
  - [ ] User message: right-aligned, studio accent colour
  - [ ] Assistant message: left-aligned, neutral background
  - [ ] Streaming text renders word by word — no spinner
  - [ ] Timestamp shown on hover

- [ ] `components/chat/chat-input.tsx`
  - [ ] Text area, expands on multiline
  - [ ] Send on Enter, new line on Shift+Enter
  - [ ] Disabled while assistant is responding
  - [ ] Placeholder: "Ask about services, availability..."

- [ ] `components/chat/availability-result.tsx`
  - [ ] Rendered when the assistant returns available slots
  - [ ] Shows: practitioner name, date, available times as clickable chips
  - [ ] Clicking a time chip shows: "Great — I'll take you to the booking
    page for [service] with [practitioner] at [time]" + booking link
  - [ ] This component is returned as a structured tool result rendered
    by the useChat hook — not plain text

### Phase 5 — Embed in Booking Page

- [ ] Import `<ChatWidget />` into the public booking page layout
- [ ] Widget does not appear on owner dashboard or client portal
- [ ] Widget does not appear on the payment page
  (client is mid-booking, do not distract)
- [ ] Mobile: widget collapses to bubble only, expands on tap

### Phase 6 — Test Conversations

Run these conversations manually against the live assistant with seed data:

- [ ] "What's the difference between Swedish and deep tissue massage?"
- [ ] "Do you have anything available this Thursday with Marisol?"
- [ ] "What should I do to prepare for acupuncture?"
- [ ] "I have lower back pain — what would you recommend?"
  → Must redirect to practitioner, not recommend a treatment
- [ ] "I want to book a reiki session next week sometime"
  → Must use checkDateRange tool, return real slots from seed
- [ ] "How much is a hot stone massage?"
- [ ] "What happens if I need to cancel?"
- [ ] "Is Keila available Saturday mornings?"
- [ ] "I'm pregnant, is massage safe?"
  → Must redirect to Marisol directly, never answer medically

### Phase 7 — Validation

- [ ] Every response is grounded in the knowledge base — no hallucination
- [ ] Availability responses use real seed data — not made-up times
- [ ] Health questions always redirect without answering medically
- [ ] Booking link always goes to the correct service and slot
- [ ] Widget does not appear on protected pages
- [ ] Mobile layout is clean and usable
- [ ] Streaming works — text appears word by word, no blank screen

---

## Environment Variables to Add

```bash
ANTHROPIC_API_KEY="sk-ant-..."
```

---

## Demo Conversation to Record

For the portfolio video, show this sequence:

1. Visitor lands on the booking page — chat bubble appears bottom-right
2. Opening message shown automatically
3. Visitor types: "What sessions do you offer for stress relief?"
4. Assistant explains the options — Marisol's massage, Keila's reiki
5. Visitor asks: "Do you have anything available next Tuesday with Keila?"
6. Assistant calls checkAvailability — real slots appear as clickable chips
7. Visitor clicks a time — assistant provides booking link
8. Cut to: booking flow opens with Keila's reiki pre-selected
9. Overlay: "Available 24/7. No phone tag. No inbox to check."

This sequence shows RAG (service knowledge) + tool calling (real availability)
+ booking handoff in under 90 seconds of screen time.
