# Offer Currency Converter

Internal tool for the Talent Acquisition team to convert candidate offers between USD and supported local currencies, using rates approved by our Compensation team.

**Live tool:** `https://YOUR-USERNAME.github.io/REPO-NAME/`

## How to use it

Open the link, type a number in either field, pick currencies in the dropdowns. The swap button flips direction. The line below the amounts shows the implied per-unit rate so you can sanity-check.

Rates default to USD on the left and EUR on the right. Initial amount is 100,000 (a typical offer figure) — overwrite it.

## Updating rates each quarter

Do this once per quarter when Comp publishes new rates. Takes about 2 minutes.

1. Go to the repo on github.com
2. Click `index.html`
3. Click the pencil icon (top right of the file view) to edit
4. Find the `const RATES = {` block — it's about 20 lines, well-commented
5. Update each rate to the new value. **Format: 1 unit of that currency = X USD.** For example, if 1 EUR = $1.08, write `EUR: 1.08,`
6. Find this line near the top of the HTML: `<span class="rate-period">Rates effective Q2 2026</span>` and update the quarter label
7. Scroll down, write a short commit message like "Q3 2026 rate update", click **Commit changes**
8. The live page updates within ~1 minute. Hard-refresh your browser (Ctrl+Shift+R or Cmd+Shift+R) to see the new version.

That's the whole update process. No code knowledge needed — you're just changing numbers and a label.

## Currencies included

USD, EUR, GBP, CAD, AUD, SGD, CHF, AED, CNY, ILS, INR, BRL, MXN, DKK, BGN, IDR, KRW, RON, ZAR, CRC, CLP.

To add a new currency: in the `RATES` block, add a new line in the same format (e.g., `JPY: 0.0067,`). It'll automatically appear in both dropdowns. To remove one, delete the line.

## Notes for the team

- Rates are the **company-approved quarterly rates**, not live market rates. Use this tool for offer conversions, not for general FX reference.
- If you're seeing rates from a quarter that's already over, ping whoever owns this tool to update them.
- Numbers over 1,000 display without decimals (rounded). Smaller values show 2–4 decimals. The implied rate line uses more precision for the small-value currencies (IDR, KRW, CRC, CLP).

## Tech notes

Single-file static HTML. No dependencies, no build step, no backend. Hosted on GitHub Pages.
