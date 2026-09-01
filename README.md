# The 2–4–6 Game

A single-page web app that runs Wason's 2–4–6 task and ends with a short lesson on confirmation bias. No build step, no dependencies, no backend — just `index.html`.

## How it works

1. Player sees `2, 4, 6` and writes their initial guess at the rule (no confidence rating yet).
2. Each round: enter three integers → see whether the set is consistent with the rule → restate the rule and confidence.
3. The game ends when confidence is ≥ 90% or after 10 rounds. The rule is revealed, the player self-assesses, and a lesson tailored to how they played is shown.

The hidden rule is `a < b < c` (strictly increasing). Negative integers are allowed; decimals are rejected.

## Run locally

Open `index.html` in a browser, or in VS Code use the Live Server extension.

## Deploy (VS Code → GitHub → Vercel)

```bash
git init
git add .
git commit -m "Initial 2-4-6 game"
```

Push to GitHub (VS Code: Source Control → Publish to GitHub, or `gh repo create`), then on vercel.com choose **Add New → Project**, import the repo, leave Framework Preset as **Other**, and click **Deploy**. Every push to `main` redeploys automatically.

## Customize

Constants at the top of the `<script>` block in `index.html`:

- `MAX_ROUNDS` — round cap (default 10)
- `END_CONF` — confidence threshold that ends the game (default 90)
- `isConsistent(a, b, c)` — the hidden rule
