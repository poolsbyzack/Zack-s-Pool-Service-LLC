# Pool Water Check

A phone-friendly web app for do-it-yourself pool owners (not Zack's service customers): enter test results, get a dosing plan, order chemicals delivered locally. Built by a working pool tech; selling point is convenience over driving to a pool store for a free water test.

## Start of every session

Briefly remind the user of the open items in `NEXT-STEPS.md` (a short list, not the whole file), and update that file as items get decided or new ones come up.

## Files

- `index.html`: the whole app (HTML, CSS and JS in one file, no build step). Key tables near the top of the script: `FIELDS` (readings and ranges), `TEST_KITS`, `PRODUCTS` (package sizes, dosing rates, prices), `DELIVERY`, `PREMIUM`, `JUMP_LIMITS`.
- `tools/profit-planner.html`: owner tool for costs, break-even and chemical pricing.
- `NEXT-STEPS.md`: open decisions and missing pieces.

## Conventions

- Keep it one self-contained file per page; no frameworks or build step.
- Everything between `<!-- ARTIFACT-START -->` and `<!-- ARTIFACT-END -->` is what gets published as a claude.ai artifact preview (strip `</head>`, `<body>`, the manifest and apple/theme meta lines).
- Safety first in dosing: split big pH moves, cap daily changes, never dose a reading that failed a check, require a retest confirmation for extreme readings or big jumps.
- Basic keeps every reading and dose amount; Premium sells convenience (full history, free delivery, strip refills, photo reading, reminders).
- Subscriptions must follow auto-renewal law: clear terms before sign-up, an agree box, a reminder before the trial ends, and one-tap cancel. Never make cancelling harder.
- Explain things to the user in plain language with analogies; they're a pool pro, not a programmer.
