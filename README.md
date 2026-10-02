# Pool Water Check

A phone-friendly web app for do-it-yourself pool owners (people who take care of their own pool, not service customers). They enter their test strip or test kit results and see, reading by reading, whether their water is balanced.

Open `index.html` in a browser. There's no build step. On a phone, use **Share → Add to Home Screen** to get an app icon.

## What it does today

- Big number boxes with − / + buttons and tap-to-fill chips that match common test strip color steps
- Sanitizer type (chlorine or saltwater) and pool size
- Each reading shows a status (Very low → Ideal → Very high), a range bar and a plain-language explanation
- A summary at the top lists what needs attention first
- Readings are saved on the device (localStorage)
- **Test kit choice for salt:** meter (ppm), drop kit (drops × ppm per drop) or color strip. Switching kits carries the reading over.

- **What to add:** a numbered treatment plan in the order chemicals should go in (alkalinity → pH → calcium → stabilizer → salt → chlorine), with amounts for the pool's size
- **Delivery request:** the plan rounded up to full packages, with prices once they're set, and a copyable request the customer texts or emails

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

## Roadmap

1. ✅ Reading entry + status
2. ✅ Dose calculator + delivery request (manual: customer sends it, you confirm)
3. Accounts + reading history
4. Paid tier (Stripe)
5. Photo reading of test strips
6. Starter kits / strips by mail
