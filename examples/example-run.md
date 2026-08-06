# Example run

A full Mode A pass on a real-shaped request. This is what the skill produces when invoked.
Names and numbers are illustrative.

---

**Invocation:**

> Set up a 10x strategy session for my ecommerce team, 12 people, two hours. We sell
> outdoor gear direct to consumers and every plan we write is another five percent on
> conversion.

**No questions asked.** Mode A is decided by what arrived: business context plus a future
session. The attendee count and the slot are both supplied. Everything still missing gets
an assumption labeled in the packet where the value sits, which is faster for the reader
than a round of questions.

**1. Frame the contrast, silently.** Ten percent for this business is a better product
page and a smarter discount ladder. Tenfold is a different relationship with the customer
entirely, or a different set of customers. That contrast is working, not output. It shows
up only inside the packet's framing block, written in their own market terms.

**2. Design the groups.** Twelve people divides evenly, so four groups of three, each
carrying all three roles. No group gets a second Challenger, because doubling the
Challenger is how generation dies early.

**3. Tailor the starter questions.** The seven starters get rewritten in outdoor gear,
direct-to-consumer, and seasonal-demand terms. Generic questions produce generic ideas,
and a room that hears a generic question answers with what it already believes.

**4. Build the packet** from `assets/session-packet-template.md`. The slot was supplied,
so the five blocks are scaled to add up to the 120 minutes given, with present-back
priced per group and totaled. No canonical session length is asserted anywhere.

**5. Deliver only the packet.** The reply's first line is the session title line and its
last line is the capture plan's final line. Nothing before it, nothing after it.

**The Session Packet:**

```
10x Strategy Session: Direct-to-consumer outdoor gear team
Objective: Find the ideas that could grow this business tenfold, not the five percent
  on conversion the last several plans were built around.
Horizon: 24 months (default, none supplied)
Slot: 120 minutes
Owner: Owner needed
Groups: 12 people, 4 groups of 3
Roles per group: Idea Generator, Challenger, Note Taker

Framing, read aloud by the owner:
Ten percent thinking gets us a faster checkout and a better tent listing. Tenfold
thinking asks what it would take for ten times as many people to buy gear from us,
which almost certainly means reaching people who do not shop for gear online today.
Drop the assumption that we sell single items to individuals who already know what
they want. Ask why we should get there, not how.

Blocks:
1. Framing and rules (10 min) 10x not 10 percent, why-not-how, no feasibility
   objections during generation
2. Group ideation (40 min) Groups of 3 work the starter questions
3. Present back (8 min per group, 32 min total) The what and the why, any medium
4. Challenge and build (23 min) Challengers probe feasibility and scale, building
   on ideas rather than dismissing them
5. Capture and route (15 min) Note Takers consolidate; owner names next step

Starter questions, tailored to this business:
- Who buys gear from us today, and who spends weekends outdoors without ever
  buying anything from a brand like ours?
- What makes someone upgrade a piece of gear, and what makes them borrow, rent,
  or make do for another season instead?
- How are people getting outfitted through the nearest alternatives: big-box
  stores, secondhand markets, rentals, or hand-me-downs?
- What matters most to someone choosing where to buy gear they will trust in bad
  weather?
- What will buying outdoor gear look like in 24 months, given resale, rental, and
  the shift in who is going outside at all?
- Do we have, or can we find, data to support the idea?
- Can the idea scale past our current catalog and shipping footprint?

Capture plan:
Each Note Taker records every idea as What / Why / Discussion points, using the
capture template. The owner collects all four sheets before the room empties.
```

The packet is ready to send to the room. The owner slot reads Owner needed rather than a
guessed name, because the request named a team and not a person, and an owner is never
proposed.

After the session, the same skill runs Mode B on whatever the Note Takers wrote. That pass
consolidates one entry per idea, labels the ten percent ideas as incremental rather than
dressing them up or dropping them, and ends at a routing table where every idea carries a
next step, an owner, and a date. Ideas that need to become measurable goals route to
`business-goals`, and an idea chosen for a phased plan routes to
`how-to-plan-new-product-and-services`. Turning the captured ideas into a strategic plan
is not this skill's artifact.
