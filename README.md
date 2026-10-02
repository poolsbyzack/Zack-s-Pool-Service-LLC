# Pool Water Check

A phone-friendly web app where pool owners enter their test strip or test kit results and see, reading by reading, whether their water is balanced.

Open `index.html` in a browser. There's no build step. On a phone, use **Share → Add to Home Screen** to get an app icon.

## What it does today

- Big number boxes with − / + buttons and tap-to-fill chips that match common test strip color steps
- Sanitizer type (chlorine or saltwater) and pool size
- Each reading shows a status (Very low → Ideal → Very high), a range bar and a plain-language explanation
- A summary at the top lists what needs attention first
- Readings are saved on the device (localStorage)

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
4. Paid tier (Stripe) + free codes for service customers
5. Photo reading of test strips
6. Starter kits / strips by mail
