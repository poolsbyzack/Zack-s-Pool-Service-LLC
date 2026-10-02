# Business plan notes

What's been decided so far in brainstorming. This is the hand-off from planning (chat) to building (code): once something is settled here, it's ready to build. Open questions live in `open-decisions.md`.

## The idea

- **Who it's for:** do-it-yourself pool owners, not Zack's service customers (they get everything with service).
- **The angle:** Pinch A Penny tests water free in the store. We win on convenience: test at home in a minute, and what you need shows up at your door.
- **Selling point:** built by a working pool tech.

## How it makes money

1. **Chemical delivery** (local, on route days). Chlorine and acid are hard to ship, which favors a local pro with a truck.
2. **Premium subscription** (convenience, not better answers).
3. **Test strips**, refilled automatically for Premium members. Strips can ship by mail, so this works outside the delivery area.
4. **Later:** brand rebates and co-op ad money, private-label strips, sponsorships, affiliate links outside the delivery area.
5. **Side door:** "want a pro to take over?" turns local DIY owners into service leads.

## Basic vs Premium (decided)

- **Basic (free):** every reading, every dose amount, safety warnings, big-jump retest warnings, last 5 tests shown (all are kept), delivery with a fee.
- **Premium:** whole season of tests, free delivery, automatic strip refills, photo strip reading (coming), reminders (coming).
- **Rule:** make Basic less convenient, never less accurate or less safe.

## Trial and billing (decided)

- 14-day free trial. Name, email, phone and address collected once at sign-up and reused, so there's nothing to re-enter later.
- Card saved through Stripe Checkout at sign-up; renews automatically after the trial.
- Must follow auto-renewal law: clear terms and an agree box before sign-up, a reminder before the trial ends, one-tap cancel. One free trial per person.

## Pricing (working numbers, not final)

- Premium $4.99/month for now. The profit planner shows free delivery makes that thin (each stop costs about $7 in time and gas), so consider Premium + Delivery at $14.99–19.99, or free delivery over a minimum order.
- Price chemicals against the store shelf, not your cost. Premium members pay about shelf price with free delivery; Basic pays shelf price plus the delivery fee.
- Markup guide: heavy price-checked items 25–40%, everyday treatments 35–50%, specialty items 50–80%.
- Details and sources: `tools/profit-planner.html`.

## Brands (direction)

- Start with a trusted name-brand strip (e.g. AquaChek) to build credibility and set the app's color blocks to match it.
- Move to private-label strips once there are about 100+ regular strip buyers (LaMotte minimum about 100 bottles; Bartovation has no minimum).
- Sponsors never change dosing advice, and sponsored items are labeled.

## Accuracy and safety (decided)

- Strips are ballpark; a drop kit could be a Premium add-on.
- Dosing safety: split big pH moves, cap daily alkalinity and calcium changes, cap chlorine at 10 ppm, no dose for readings that fail a check, retest confirmation for extreme readings or big jumps.
