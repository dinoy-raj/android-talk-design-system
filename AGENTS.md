# Instructions for AI agents

This repository is a slide design system. When asked to create or edit slides:

1. Read `DESIGN.md` completely before writing anything. It is the source of truth.
2. Build slides as HTML at 1920×1080: link `tokens/tokens.css` and `css/slides.css`, one `<section class="deck-slide">` per slide, each containing `<div class="dr-stage"><div class="dr-slide">…</div></div>`.
3. Start every slide from the closest file in `components/` and replace its content. Do not invent new colours, fonts, shadows or gradients.
4. Reuse the navigation and scale-to-fit script from `examples/deck.html`.
5. Write new decks to `decks/<talk-slug>/index.html` (create the folder), with paths `../../tokens/tokens.css` and `../../css/slides.css`.
6. Run the checklist at the end of `DESIGN.md` before finishing.

When changing the system itself, keep `tokens/tokens.json`, `tokens/tokens.css` and the tables in `DESIGN.md` in sync.
