---
name: deckify
title: Deckify
description: Turn any brand's website into a reusable Design System and a verified HTML slide deck — brand-faithful, mobile-safe, and built in the medium AI was born to write in
source: community
author: Xichang (Seacen) Zhao
githubUrl: https://github.com/seacen/deckify
docsUrl: https://github.com/seacen/deckify
category: design
tags:
  - slides
  - presentation
  - design-system
  - html-slides
  - brand
roles:
  - designer
  - developer
featured: false
popular: false
isOfficial: false
installCommand: |
  npx skills add seacen/deckify
date: 2026-06-15
---

## Use Cases

- Extract a complete Design System (colors, fonts, logo, voice) from any brand URL
- Generate a brand-faithful 9-slide HTML deck that opens in any browser
- Build a reusable brand spec once, then have AI generate every future deck from it
- Skin slides to match a specific company's visual language instead of generic AI styling
- Produce slides as living HTML — animatable, queryable, copy-paste-able — not `.pptx` binary

## How It Works

- **Learns by looking, not prompting**: visits the brand site like a designer — home, about, press kit — and reads the real colors, fonts, logo, and mood from evidence
- **Outputs a reusable asset**: a Design System markdown file, not a one-off deck. Update it once, every downstream deck moves with it
- **Checks its own work**: runs 11 deterministic hard checks (dimensions, logo visibility, mobile collapse, no emoji, 12px readability floor) then judges its own visual quality against 6 standards — and fixes what scores low
- **Knows what never changes**: 40+ engineering rules (fit contract, single-absorber rule, mobile inline-flex catch-all, logo-as-SVG-symbol pattern) are baked in; only the brand-specific visuals vary

## Example

```bash
# Install the skill (works across Claude Code, Codex, Cursor, and 70+ agents)
npx skills add seacen/deckify

# Then invoke it on any brand URL:
use deckify on https://www.tiffany.com
```

You get two compounding assets in 5–10 minutes:
a Design System `.md` (the reusable deliverable) and a verified `.html` demo deck (proof the spec works), both under `~/deckify/decks/<brand>/`.

## Notes

- Requires the standalone [`agent-browser`](https://github.com/vercel-labs/agent-browser) CLI for rendered-DOM recon, computed styles, and screenshots — `scripts/setup.py` checks for it and prints the install command for your platform
- All outputs land in `~/deckify/`, independent of where you run from
- Supports English and 中文 decks with maintained sister templates
- License: PolyForm Noncommercial 1.0.0 — free for personal, educational, research, and noncommercial use; commercial use requires a separate license
