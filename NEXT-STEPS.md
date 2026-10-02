# Open decisions and missing pieces

Things the app is waiting on. Check items off (or delete them) as they're decided, and add new ones as they come up.

## Decisions only you can make

- [ ] **Test strip brand to stock.** Sets the app's color blocks, the future photo reader and the strip price.
- [ ] **Products and package sizes you'll stock** (e.g. 1 gal liquid chlorine, 1 gal muriatic acid, 1 lb shock, 4 lb baking soda, 40 lb salt).
- [ ] **Your prices** for each product, the **delivery fee**, and the **phone or email** orders go to. Use `tools/profit-planner.html` and its pricing guide.
- [ ] **Delivery area**: zip codes or a radius. Outside it, strips could ship by mail.
- [ ] **Premium price and trial length** (now $4.99/month, 14 days). The profit planner shows free delivery makes Premium thin at $4.99; consider a higher Premium + Delivery tier or a minimum order for free delivery.
- [ ] **App and business name** (the app is called "Pool Water Check" for now).

## Brands and suppliers

- [ ] **Ask your distributor** (e.g. SCP/POOLCORP, Heritage) about loyalty rebates and which strip and chemical brands they carry at your price.
- [ ] **Ask manufacturers about dealer programs**: co-op advertising money, volume rebates, and whether an app-based seller qualifies.
- [ ] **Get 2–3 strip quotes**, including private label (your name on the bottle): LaMotte (5,000+ strip minimum, about 100 bottles) and Bartovation (no minimum).
- [ ] **Score the strip brands** on: tests included (does it read salt and stabilizer?), accuracy, color chart clarity (matters for photo reading), shelf life, your cost, store price, rebates, private label option.

## Numbers to check against your experience

- [ ] Dosing rates, especially acid (pH response varies pool to pool). In `PRODUCTS` in `index.html`.
- [ ] Ideal ranges (e.g. how you like to run pH and stabilizer). In `FIELDS`.
- [ ] Big-jump limits (pH 0.6, alkalinity 40, calcium 150, stabilizer 30, salt 800 ppm). In `JUMP_LIMITS`.

## Calls to make

- [ ] **Insurance agent:** coverage for selling and delivering chemicals to non-service customers, and for dosing advice in an app.
- [ ] **Sales tax / retail license** for selling chemicals to the public.
- [ ] **Lawyer review of the subscription terms** (auto-renewal disclosures, trial reminder, cancellation) before charging anyone.

## To build once the above is ready

- [ ] **Stripe account** → connect Stripe Checkout so the trial saves a card (Apple Pay / Google Pay too) and renews on its own. Needs a small server.
- [ ] **Accounts on a server**, so a customer's info, tests and plan follow them to a new phone and orders reach you directly instead of by copy and paste.
- [ ] **Where the app lives**: a domain and hosting (GitHub Pages is free for a start).
- [ ] **Photo strip reading** (after the strip brand is picked): free color matching for everyone, AI reading for Premium.
- [ ] **Reminders** (test day, second half of a dose, trial ending): needs the server for texts or notifications.
- [ ] **Guided strip test** with a timer and lighting tips.
- [ ] **Merge to a main branch / open a pull request**: all work is on `claude/claude-code-mobile-0e5x69`.
