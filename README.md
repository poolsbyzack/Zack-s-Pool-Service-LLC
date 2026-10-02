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
2. Dose calculator (how much of which product, based on pool size)
3. Accounts + reading history
4. Paid tier (Stripe)
5. Photo reading of test strips
6. Starter kits / strips by mail
