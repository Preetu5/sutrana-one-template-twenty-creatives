# Sutrana: one template, twenty creatives

An assignment package for a fictional personal-finance brand in India. It includes a 20-row data sheet, an annotated 1080 × 1080 master, reusable prompts, 20 generated SVG ads, a contact sheet, source assets, and a per-creative QA log.

> **Language review:** the Hindi and Marathi copy is draft and has not been verified by a native speaker. It is included here for assignment review; do not use it in a customer-facing campaign until a native speaker checks the headline, offer, CTA, product name, disclaimer, and rendered font. This package is a design exercise, not financial advice or a live offer.

## How the system works

Each JSON row is the source of truth for product, audience, offer, language, and headline. A fixed SVG renderer puts those values into one locked composition. Brand mark, layout, colours, CTA, and language-specific disclaimer stay controlled. Four generated illustrations provide product-family imagery. Image models do not write text into the artwork. The workflow contains no financial amounts, rates, percentages, dates, or return claims; therefore none can drift from a data row.

The annotated master labels locked, sheet-driven, and AI-generated fields. The 20 final creatives use the same composition and design tokens. The image assets are reused by product family so the ads stay coherent.

## Files

- `data/creative-data.csv` — spreadsheet-ready 20-row sheet.
- `data/creative-data.json` — exact input for the generator.
- `template/master-template.svg` — annotated master design, 1080 × 1080.
- `creatives/A01.svg`–`A20.svg` — one 1080 × 1080 SVG per row.
- `index.html` — 20-up contact sheet/gallery for side-by-side review.
- `brand/brand-guide.md` — brand identity and field ownership.
- `prompts.md` — copy and image prompts, constraints, and recreation steps.
- `qa-log.csv` — per-ad decision and follow-up.
- `assets/` — AI-generated PNG illustrations.
- `scripts/validate_creatives.mjs` — row, canvas, asset, and output-count checks.

## Recreate the creatives

Requires Node.js 18 or newer; no third-party packages or API key are needed.

1. Download or clone this repository.
2. Open a terminal in the `outputs/` (repository root) folder.
3. Run `node scripts/generate_creatives.mjs`. This regenerates the CSV, twenty ads, and annotated master from the JSON rows.
4. Run `node scripts/validate_creatives.mjs` to check the data mapping and generated files.
5. Open `index.html` in a browser to see all twenty side by side.
6. Review each ad visually and record any changes or rejections in `qa-log.csv`.
7. Open any `creatives/Axx.svg` to inspect its exact 1080 × 1080 layout.
8. For a new image style, use the prompt in `prompts.md`, save the generated image into `assets/`, and update the matching `art` field in the JSON sheet.

To edit a creative, change its source row in `data/creative-data.json` and rerun the generator. Update `qa-log.csv` after reviewing the new copy and appearance. Do not hand-edit generated SVGs: they are reproducible outputs.

## QA and what broke

The QA log records the checks and remaining review for each of the twenty files. The validator confirms row-to-SVG field matching, the 1080 × 1080 canvas, referenced image files, CSV/JSON parity, and file counts. It does not claim to replace visual review in a browser or native-speaker review. A07's early draft headline, “Invest for a richer future,” was rejected because it could imply an outcome; the final line is “Make a little space for long-term goals.” A master-template language tag also overlapped its field during review and was moved before regeneration.

Longer Devanagari headlines needed a smaller type size and word wrapping. Confirm their line breaks, glyphs, image crops, and disclaimer legibility at the target rendering size. A browser-level visual pass was not completed in this workspace, so the contact sheet is prepared for that final review. Native speakers must check all text in the six Hindi and Marathi ads before submission.

## Public repository

Public submission repository: [Preetu5/sutrana-one-template-twenty-creatives](https://github.com/Preetu5/sutrana-one-template-twenty-creatives). The Hindi and Marathi copy remains draft and unverified; see the language-review note before using it in any customer-facing campaign.

## AI and tools used

- OpenAI ImageGen — four supporting illustrations; no text was requested in the images.
- ChatGPT — fictional brand system, prompt design, English and draft regional-language copy, and QA framing.
- Node.js — deterministic local SVG rendering and the HTML contact sheet.

No real financial company was copied. Sutrana is an invented name, and the artwork is original. Before sharing publicly, check name availability if you plan to use the brand outside this assignment.
