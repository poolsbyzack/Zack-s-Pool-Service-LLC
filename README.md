# Pool Water Check

A phone-friendly web app for do-it-yourself pool owners (people who take care of their own pool, not service customers). They enter their test strip or test kit results and see, reading by reading, whether their water is balanced.

Open `index.html` in a browser. There's no build step. On a phone, use **Share → Add to Home Screen** to get an app icon.

## What it does today

- Big number boxes with a slider to get close and − / + buttons to fine-tune (color-block strips use tap-to-pick blocks instead)
- Sanitizer type (chlorine or saltwater) and pool size
- Each reading shows a status (Very low → Ideal → Very high), a range bar and a plain-language explanation
- A summary at the top lists what needs attention first
- Readings are saved on the device (localStorage)
- **Test kit choice for salt:** meter (ppm), drop kit (drops × ppm per drop) or color strip. Switching kits carries the reading over.

- **What to add:** a numbered treatment plan in the order chemicals should go in (alkalinity → pH → calcium → stabilizer → salt → chlorine), with amounts for the pool's size
- **Delivery request:** the plan rounded up to full packages, with prices once they're set, and a copyable request the customer texts or emails

- **Save this test:** keeps the last 5 tests on the phone, listed under Recent tests (each can be deleted). Copying a delivery request saves the test automatically
- **Big-jump check:** each reading is compared with the last saved test that included it (within 30 days). A change bigger than water usually makes on its own (pH 0.6, alkalinity 40, calcium 150, stabilizer 30, salt 800 ppm) shows a retest note and locks the delivery button until the customer confirms the retest. Chlorine is left out because it really does swing fast

## Basic and Premium

Basic keeps every reading, every dose amount and the big-jump check. Premium sells convenience:

- Every test for the season (Basic shows the last 5; all tests are kept, so upgrading reveals them)
- Free delivery
- Test strip refills: the app counts a strip per saved test and adds a bottle to the next delivery at 10 left (anyone can add a bottle by hand)
- Coming: photo strip reading, test-day reminders

**Trial and billing.** Starting the 14-day trial collects name, email, mobile number and delivery address, then shows the terms (free until the date shown, then $4.99/month, charged automatically until cancelled) with an "I agree" box. Card entry will happen on Stripe Checkout; until that's connected the preview starts the trial without a card. When the trial ends it rolls into the paid plan. One free trial per account. A reminder shows 3 days before the trial ends, and Cancel Premium is one tap plus a confirmation. Settings are in `PREMIUM` in `index.html`.

**Owner preview.** The "Preview as Premium" checkbox at the bottom unlocks Premium on that phone without a trial, for testing.

## Safety rules in the plan

- pH moves bigger than 0.2 are split: add half, retest after 4 hours, then the rest only if still needed
- Alkalinity is raised at most 40 ppm a day and calcium at most 100 ppm a day
- Chlorine is never pushed above 10 ppm, and goes in at least 30 minutes after acid or pH up
- A reading that fails a check gets no dose. A reading that's very low or very high locks the delivery button until the customer confirms they retested
- High alkalinity, calcium, stabilizer and salt get advice (aeration or partial drain), not a product
- Amounts are estimates from standard dosing rates; every step says to retest

## Setting products and prices

`PRODUCTS` in `index.html` lists each product, its package size and its dosing rate. Set `price` per package and `DELIVERY.fee` / `DELIVERY.contact` to show prices and your contact on the order.

## Adding a test kit brand

Kits live in the `TEST_KITS` table in `index.html`. Each kit has a `method`:

| Method | Person enters | Converted by |
|---|---|---|
| `direct` | ppm | nothing |
| `drops` | number of drops | `drops × perDrop` |
| `pads` | taps a color block | the block's ppm value |
| `scale` | number on a titrator strip | the brand's `chart`, interpolated |

Add a brand by copying an entry and filling in its values. A commented-out titrator example is included. The same kit entries will tell the photo reader what to look for later.

## Target ranges used

| Reading | Ideal | Kit's readable range |
|---|---|---|
| Free chlorine | 2–4 ppm | 0–20 |
| Combined chlorine (total − free) | under 0.2 ppm | — |
| pH | 7.4–7.6 | 6.0–9.0 |
| Total alkalinity | 80–120 ppm | 0–300 |
| Calcium hardness | 200–400 ppm | 0–1200 |
| Stabilizer (CYA) | 30–50 ppm (salt: 60–80) | 0–300 |
| Salt (saltwater pools) | 3000–3400 ppm | 0–6000 |

All ranges live in the `FIELDS` table at the top of the script in `index.html`, so they're easy to adjust.

## Owner tools

- `tools/profit-planner.html`: costs, profit per member, members needed to break even, and a fair chemical pricing guide. Numbers are saved on the device.
- `NEXT-STEPS.md`: open decisions and missing pieces.

## Roadmap

1. ✅ Reading entry + status
2. ✅ Dose calculator + delivery request (manual: customer sends it, you confirm)
3. Accounts + reading history
4. ✅ Basic / Premium with free trial (preview) → connect Stripe Checkout + accounts
5. Photo reading of test strips
6. Starter kits / strips by mail
