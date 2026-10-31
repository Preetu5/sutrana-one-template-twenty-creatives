# Reusable prompts

The local generator applies these instructions to each JSON row and uses fixed SVG layout code. No external API key is needed to reproduce the supplied files.

## Headline prompt

> You are the copy assistant for Sutrana, a fictional Indian personal-finance brand. Write one short headline for the exact audience and product in the supplied row. Be warm, clear, calm, and non-judgmental. Do not invent or change facts, rates, eligibility, dates, amounts, savings, returns, approval, or product benefits. Never imply guaranteed or predictable investment returns. Do not create urgency or fear. Keep the headline to one simple thought. Write it in the row's language. Return only the headline. Row: `{{row}}`

The included headlines were drafted with ChatGPT and reviewed against these rules. English copy was checked directly. Hindi and Marathi lines remain **unverified draft translations** and need a native-speaker review.

## Image prompt

> Create a square premium editorial cut-paper illustration for Sutrana, a fictional Indian personal-finance brand. Show `{{product_family_scene}}`. Use only deep ink navy #142B38, warm ivory #F5F0E6, coral #F26B5B, and muted sage #A8B8A2. Warm, calm, contemporary, trustworthy. No words, letters, numbers, logo, currency, coins, charts, returns claims, or watermark. Leave a clear silhouette and uncluttered composition. Save as PNG. Use as a supporting image; never ask the image model to render ad copy.

## Data-integrity rule

Only the row supplies the product, audience, offer, and language. The headline prompt may not invent numeric claims. The workflow adds no financial amounts, rates, percentages, dates, or forecasts. The fixed legal line is localized separately and is never generated on the fly.

## Recreate

1. Edit `data/creative-data.json` (exactly twenty records).
2. If regenerating image art, use the image prompt for each product family and save PNGs to `assets/` using the same filenames referenced by the rows.
3. Run `node scripts/generate_creatives.mjs` from the `outputs/` folder.
4. Review `template/master-template.svg` and `index.html`; open the gallery in a browser.
5. Inspect every regional-language line with a native speaker before external use.
