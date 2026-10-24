# DESIGN.md — Android Talk Design System

> **For AI tools:** read this whole file before making slides. It is the single source of truth. Follow it literally; when something isn't covered, pick the closest existing component and keep its rules.

A slide system for technical conference talks (Android, Kotlin, AI), Android-themed, created by **Dinoy Raj** from his last four conference talks (DevFest Dubai, DevFest Mumbai, FOSSASIA, droidcon Uganda — [slides on SlideShare](https://www.slideshare.net/dinoykraj)). Clean white canvases, Google green as the signature colour, a lime accent, key words lit up in blue and green, dark code panels.

## 1. Output contract

- **Canvas:** every slide is exactly **1920 × 1080 px** (16:9). All sizes in this file are at that resolution.
- **Preferred output: HTML.** One file, one `<section>` per slide, each slide built as:

```html
<link rel="stylesheet" href="tokens/tokens.css">
<link rel="stylesheet" href="css/slides.css">

<div class="dr-stage"><div class="dr-slide">        <!-- add is-green / is-mint for coloured slides -->
  <span class="dr-tag">Topic Label</span>
  <ul class="dr-bullets" style="position:absolute;top:260px;left:110px;width:840px">
    <li>Convert model <span class="hl-blue">weights</span> to <span class="hl-green">8-bit integers</span>.</li>
  </ul>
</div></div>
```

  - Use the CSS custom properties (`var(--green)`) and classes from `css/slides.css`. Never hard-code hex values that already exist as tokens.
  - Position content absolutely on the 1920×1080 canvas, as the files in `components/` do. Copy the closest component file and change its content rather than writing layout from scratch.
  - `examples/deck.html` shows a complete deck with keyboard navigation and scale-to-fit; reuse its script.
- **Other targets** (PowerPoint, Google Slides, Keynote, Figma, Reveal.js, Marp…): set the page to 1920×1080 (or 13.333 × 7.5 in / 33.867 × 19.05 cm and scale every px value by 0.5 pt per px), and apply the same tokens, type scale, positions and rules below.
- **Fonts:** Google Sans (load **Google Sans Flex** from Google Fonts) for everything; **Source Code Pro** for code. Fallbacks are in `tokens.css`.

## 2. The five rules that make it look right

1. **White first.** Most slides are plain white. About one slide in five is full green (`.dr-slide.is-green`): section interstitials, demos, the closing slide.
2. **Highlight, don't bold.** Light up 1–4 key phrases per line: **blue = the subject/concept**, **green = the platform, payoff or twist**. Highlights are weight 500 (700 in titles; same weight as the line in headlines).
3. **Pills for every label.** Topic tags, captions, badges and chips are fully rounded pills, usually lime (`--lime` with `--on-lime` text).
4. **One idea per slide, lots of air.** Bullets on the left ~45%, a visual on the right. Never fill the canvas.
5. **No decoration that isn't in this file.** No drop shadows, no gradients (except the blue numeral gradient), no coloured left-border cards, no emoji on bullets or headlines, no stock icons.

## 3. Writing style

- **Teach with questions.** Open sections with a provocation: "Is MediaPipe **LLM Inference** truly Write **Once**, Run Anywhere?", "Does shipping a **C++ engine** [come with app size overhead?]".
- **Title Case** for labels (tags, card titles, pill captions); sentence case for bullets.
- **Short and spoken:** bullets 1–3 lines, one idea each; card descriptions ≤ 6 words.
- **Warm, a little playful:** a ☺ may close a payoff pill ("Reusable Model ☺"); one emoji may lead a demo caption (🏃). Nowhere else.
- **Sign-off:** "Thankyou." — one word, lime period — then "Do you have any questions?".

## 4. Deck structure

1. `TitleSlide` → optional `SpeakerIntro`, `AgendaSlide`
2. Why / context — `FeatureCards`, `TintTiles`, `StatHighlight`
3. Section breaks — `SectionDivider` (long talks), `StatementSlide`, `GreenStatement`
4. Concept slides — `TopicTag` or `Headline` + `BulletList`, `CalloutNote`, `FlowDiagram`, `Timeline`, `VersusSplit`, `CodeBlock`, `CodePair`, `PromptResponse`, `DataTable`, `NumberedSteps`, `ScreenshotRow`; annotate with `ChipSet` badges
5. A "Code Walk" pill slide, then a numbered `DemoSlide` per demo
6. `KeyTakeaways`, `ResourcesSlide`
7. `ClosingSlide`

**Pick ONE header system per deck:** `TopicTag` pills (short, visual talks) or `Headline` (long, dense talks). Pick lime or green tags and keep it.

## 5. Colour tokens

| Token | Value | Use |
|---|---|---|
| `--surface` | `#ffffff` | Default slide background. Most content slides are plain white. |
| `--ink` | `#000000` | Headlines, titles and bullet copy on `surface`, `green-tint`, `blue-tint` and `lime` (21:1 on white). |
| `--ink-soft` | `#434343` | Column labels and diagram captions on `surface` (9.7:1). |
| `--ink-muted` | `#595959` | Card titles, card descriptions, footnotes and the event line on `surface` (7:1) and `gray-row`. |
| `--green` | `#34a853` | The signature colour. Full-bleed section, demo and closing slides; bullet dots; numbered step discs; green topic tags; highlight words for the payoff or outcome. As text on white it is 3:1, so only at 24px and up. |
| `--on-green` | `#ffffff` | Text on `green` slides: statements, the giant Demo numeral, Thankyou. 3:1 on green, so 24px and up only (every observed use is 48px+). |
| `--green-tint` | `#e9f4ec` | Soft green panels and tiles (Clean Architecture background, open-model logo tiles, emphasis tile in a trio), and the small status chip on green slides. |
| `--green-wash` | `#f7fbf8` | Faintest green fill for diagram nodes and inactive tiles on white. |
| `--lime` | `#e5fb79` | The accent. Topic tag pills, the caption pill on green slides, the vertical accent bar on question slides, the period after Thankyou/Demo. Text on lime is always `on-lime` or `ink`. |
| `--lime-deep` | `#cce84a` | Speaker pill on the title slide (bleeds off the left edge). |
| `--on-lime` | `#3b401f` | Text inside lime topic tags (10.6:1 on `lime`). |
| `--blue` | `#4285f4` | Highlight words naming the subject or concept, the event pill on title slides, gradient numerals 01/02, table header rows, the active diagram node. As text on white it is 3.6:1, so highlight words stay 24px and up. |
| `--blue-tint` | `#e9f0fe` | Soft blue panels: option cards, prompt/response stages, comparison panels, the second tile in a mint/blue pair. |
| `--blue-panel` | `#b9d0ef` | Background behind illustrations and device mockups (droidcon Uganda). |
| `--blue-row` | `#e5ebf7` | Alternating row in data tables (with `gray-row`). |
| `--gray-row` | `#f7f7f7` | Alternating row in data tables; light code-snippet cards on white. |
| `--hairline` | `#dfdfdf` | 1px lines of the background grid on question and statement slides; dividers. |
| `--card-border` | `#d6d6d6` | 2px outline of white feature cards. |
| `--accent-orange` | `#f86734` | Diagram-only: the middle phase in multi-stage flows (Composition, Layout, Drawing). Never for text or highlights. |
| `--accent-deep` | `#073042` | Diagram-only: the final phase node in multi-stage flows; white text on it (13:1). |
| `--code-bg` | `#1d262f` | Code block background and dark screenshot frames. |
| `--code-text` | `#ebf4ff` | Plain identifiers in code on `code-bg` (14:1). |
| `--code-keyword` | `#47ebb4` | Keywords (val, data, class, fun, import) on `code-bg`. |
| `--code-type` | `#88b4e7` | Types, packages, annotations and parameter names on `code-bg`. |
| `--code-punct` | `#f3cd12` | Brackets, dots, colons and commas on `code-bg`. |
| `--code-comment` | `#4a5f78` | Comments (italic) and line numbers on `code-bg`. 2.6:1 by design: recessive, never carry meaning in a comment. |

**Contrast:** `--blue` (3.6:1) and `--green` (3:1) as text on white, and white on `--green` (3:1), are only for text **24px and larger** — every highlight and green-slide line in this system is 36px+. `--lime` text on `--green` is 2.6:1: keep it to short bold labels. Small text is always `--ink`, `--ink-soft` or `--ink-muted`.

## 6. Typography

One family (`--font-sans`, Google Sans) plus `--font-mono` for code. Headlines and statements are **regular (400)**; bold is reserved for titles, the closing word, demo numerals, pill captions and tags. Left-align everything except green interstitials, card contents and pill captions (centred).

| Class | Family | Size | Line height | Weight | Use |
|---|---|---|---|---|---|
| `.t-demo-numeral` | sans | 560px | 0.8 | 700 | Giant white word on green demo slides; bleeds off the bottom edge. |
| `.t-closing` | sans | 180px | 1 | 700 | Closing and Demo-QR slides, white on green, period in lime. |
| `.t-title` | sans | 96px | 116px | 700 | Talk title on the title slide, 3 lines max, highlight words in blue and green. |
| `.t-statement` | sans | 88px | 114px | 400 | Question / statement slides over the grid; highlights at 500. |
| `.t-headline` | sans | 72px | 88px | 400 | Slide headline, top-left, when a deck uses headlines instead of topic tags. |
| `.t-green-statement` | sans | 68px | 84px | 400 | Centred white line above a lime pill on green section slides. |
| `.t-step-label` | sans | 48px | 56px | 400 | Label beside a numbered disc. |
| `.t-subtitle` | sans | 48px | 56px | 400 | Line under the closing word. |
| `.t-card-title` | sans | 40px | 48px | 400 | Feature card title in `ink-muted`. |
| `.t-body` | sans | 36px | 56px | 400 | Bullet copy. Highlights at 500 in blue/green. |
| `.t-pill-caption` | sans | 36px | 44px | 700 | Text in the large lime pill on green slides and in green statement pills. |
| `.t-speaker` | sans | 32px | 40px | 700 | Speaker name in the title slide pill. |
| `.t-card-body` | sans | 28px | 36px | 400 | Feature card description, centred, `ink-muted`. |
| `.t-tag` | sans | 24px | 32px | 600 | Topic tag pill text, Title Case. |
| `.t-speaker-role` | sans | 18px | 24px | 500 | Role line under the speaker name, in `green`. |
| `.t-chip` | sans | 16px | 20px | 500 | Small status chip, top-right. |
| `.t-code-l` | mono | 32px | 60px | 400 | Hero code block, up to ~10 lines. |
| `.t-code-s` | mono | 20px | 32px | 400 | Dense code beside bullets, up to ~25 lines. |

## 7. Spacing, radius, layout

| Token | Value | Use |
|---|---|---|
| `--space-xs` | 16px | Gap between a tag and its secondary segment; chip padding. |
| `--space-s` | 24px | Gap between cards in a row; caption gap under a card. |
| `--space-m` | 40px | Gap between bullets in a group; card inner padding. |
| `--space-l` | 72px | Inset of topic tags from the top and left edges. |
| `--space-xl` | 128px | Left content margin for headlines, titles and bullets. |
| `--grid-cell` | 528px | Pitch of the background grid on statement slides (lines every 528px, 274px row offset). |
| `--radius-node` | 8px | Diagram boxes and table corners. |
| `--radius-tile` | 12px | Tinted tiles (mint, blue) and logo tiles. |
| `--radius-code` | 24px | Code blocks and screenshot frames. |
| `--radius-card` | 32px | White outlined feature cards. |
| `--radius-pill` | 999px | Every tag, caption pill, chip and the speaker pill. |

- Left content margin **128px**; topic tags inset **72px** from top and left; headlines start **120px** from the top.
- Two-column slides: text in the left ~45%, visual in the right ~55%. Centred code and tables keep ~200–240px side margins.
- **Background grid** (statement and sparse slides only): 2px `--hairline` lines every 528px (offset 263px / 274px), with small white gaps where lines cross — use `<div class="dr-grid"></div>`.
- If a slide needs two visuals, use two equal panels with a green `dr-cap` caption pill under each.

## 8. Building blocks (classes in `css/slides.css`)

| Class | What it is |
|---|---|
| `dr-stage` > `dr-slide` (`is-green`, `is-mint`) | The 1920×1080 canvas |
| `dr-grid` | Hairline background grid |
| `hl-blue`, `hl-green` | Highlight words |
| `dr-tag` (`is-green`), `dr-tag-split` | Topic tag pinned top-left |
| `dr-headline` | 72px headline, top-left |
| `dr-bullets` | Green-dot bullet list, 36/56 |
| `dr-pill` (`is-m`) | Big lime caption pill (124px / 96px tall) |
| `dr-card` | White outlined feature card |
| `dr-tile` (`is-blue`, `is-solid`, `is-outline`) | Tinted tiles |
| `dr-code` (`is-s`) with `.ln .k .t .p .c` spans | Code block with line numbers + syntax colours |
| `dr-disc`, `dr-numeral`, `dr-code-pill` | Numbered steps |
| `dr-node` (`is-box`, `is-blue`, `is-outline`) | Diagram nodes |
| `dr-table` | Blue-header segmented table (M3 Expressive list style) |
| `dr-chip` (`is-green`) | Small chip pinned top-right |
| `dr-badge` (`is-green`, `is-lime`, `is-blue`, `is-muted`, `is-dark`) | Inline status/version badges |
| `dr-ichip` (`is-green`) | Lime chip inside running text |
| `dr-opill` | Outline fact pill |
| `dr-check` (`is-s`) | Lime check disc |
| `dr-cap` | Green caption pill under a panel |
| `dr-phone` | Phone frame for screenshots |

**Code syntax colours:** keywords `.k` `--code-keyword`, types/annotations/params `.t` `--code-type`, punctuation `.p` `--code-punct`, comments `.c` `--code-comment` italic, everything else `--code-text`. Each line is `<span class="ln">…</span>`; line numbers are automatic.

## 9. Components

Each component below is a complete slide in `components/<Name>.html`. Open the file, copy its markup, replace the content.

### Slides

#### AgendaSlide

`components/AgendaSlide.html` — Talk outline

The talk outline: 3–6 numbered rows, the current section highlighted, with an optional green fact tile.

**Consumer provides:** section titles (Title Case, ≤ 4 words), the index of the current section, and optionally one fact for the tile (demo count, duration).

- Rows 136px tall; numbers in 80px discs (`dr-disc` sized down). Done/current items use solid `green` discs; upcoming items use `green-wash` discs with `green` numbers and `ink-muted` labels.
- Current row: `green-tint` pill background plus a `lime` "Now" badge.
- Labels in `step-label` (48/56).
- Fact tile: `green` block, `radius-tile`, a large white number (120px/700) and a 36px label.
- Re-use the same slide between sections with the next row highlighted, as a progress marker.

#### ClosingSlide

`components/ClosingSlide.html` — Thankyou + QR

The last slide: "Thankyou." in giant white type on green with a lime period, and a QR code to connect.

**Consumer provides:** the QR image (your connect link) and, for the demo variant, the recording link QR.

- `green` ground; word in `closing` (180px/700) `on-green`, period in `lime`; subtitle in `subtitle` (48/56) `on-green`.
- QR on the right half, ~500px, styled with rounded dots in light gray/white; caption 22px "Scan to connect with me 😎".
- "Thankyou." is written as one word with the lime period — keep it as the signature sign-off.
- Demo variant: "Demo." with "Scan that QR to get recorded demo", QR on a white rounded card.

#### DemoSlide

`components/DemoSlide.html` — Demo section break

The demo break: a giant white "Demo N" bleeding off the bottom of a green slide, a lime caption pill riding on it, and a model chip top-right.

**Consumer provides:** the demo number, a one-line caption (with one emoji at the start and one `blue` highlight), and an optional chip (model or version).

- `green` ground; "Demo N" in `demo-numeral` (560px, 700) `on-green`, left-aligned at the edge, cropped by the bottom so roughly the top 55% shows.
- Caption: `dr-pill` — `lime`, 124px tall, `pill-caption` text in `ink`, centred, its bottom overlapping the numeral's cap line.
- Chip: `green-tint` pill, 16px, top-right.
- Number demos sequentially across the talk.

#### GreenStatement

`components/GreenStatement.html` — Section interstitial

A full-green interstitial: one white line plus a lime pill holding the answer or twist.

**Consumer provides:** a setup line and a short payoff (2–4 words).

- `green` ground; setup in `green-statement` (68/84) `on-green`, centred.
- Payoff in a `lime` pill (`pill-caption` at 48px/500, 96px tall) with `ink` text, often closed with ☺.
- Variant on white: setup in `ink` with a highlight + payoff in a lime pill ("Does shipping a **C++ engine** / [come with app size overhead?]"; "Does **AI** knows how to / [make a Launcher?]").
- Single-pill variant: just a lime pill centred on green ("@Composable", "Code Walk" — green text on lime).

#### SectionDivider

`components/SectionDivider.html` — Numbered chapter break

A chapter break: a giant blue-gradient numeral over the grid, the chapter title and one line of context.

**Consumer provides:** the chapter number, a 2–4 word title with one highlight, and a one-line subtitle.

- White ground + `dr-grid`; content aligned to the first grid column (x ≈ 250).
- Numeral: `dr-numeral` at 360px/700 (gradient `blue` → `blue-tint`), two digits.
- Small `lime` badge above ("Part Two", "Chapter 3").
- Title in `statement` (88/114) with one highlight; subtitle 32px `ink-muted`.
- Use it in long talks (30+ slides) instead of, or right before, a `StatementSlide`. Green variant: the numeral in white at 40% opacity on a `green` slide.

#### SpeakerIntro

`components/SpeakerIntro.html` — About me

The "who's talking" slide: portrait on a soft panel, name, one-line pitch, focus-area pills and two proof stats.

**Consumer provides:** a portrait cut-out (transparent PNG), the one-line pitch with a blue and a green highlight, 2–4 focus areas, and 1–2 stats.

- Portrait on a `blue-panel` block (`radius-card`), with a small `lime` greeting pill overlapping its bottom-right corner.
- Name in `title` (96/116, 700); pitch at 40/52 with highlights.
- Focus areas as `dr-opill` outline pills (2px `card-border`, `ink-soft` 28px/500).
- Stats: value 64px/700 in `green` or `blue`, label 24px `ink-muted`. Two stats max; use real, current numbers.
- Place right after `TitleSlide`, or skip it when the host introduces you.

#### StatementSlide

`components/StatementSlide.html` — Question over the grid

The thinking-pause slide: a question or provocation in large type over the hairline grid, with a `lime` accent bar.

**Consumer provides:** one sentence, usually a question, with one blue and one green highlight.

- White ground + `hairline` grid (lines every `grid-cell`, broken by small gaps at each crossing).
- 8px `lime` bar on a grid column, spanning one grid row.
- Text in `statement` (88/114, 400), highlights at 500.
- Used between sections: "Is Building **Custom Launcher** is **Tough** Thing to do?", "Constructing **UI** by describing **what**, not ~~how~~".
- Variant: a word inside a lime pill breaking the line ("Lets build a [launcher]"), with a tiny `blue` stat line under it.

#### TitleSlide

`components/TitleSlide.html` — Opening slide

The opening slide: event pill, a three-line title with highlight words, the speaker pill and one hero render.

**Consumer provides:** the event name(s) (one or two, split by a short `lime` bar), the title split into at most three lines, which words to highlight, and a hero image (a 3D render, usually the Android robot or a topic object) for the right ~40%.

- Event pill: `blue` fill, white 28px semibold text, `radius-pill`, top-left at `space-xl`. Use the event's own logos inside it when available.
- Title: `title` style (96/116, 700) in `ink`. Highlight the *subject* in `blue` and the *platform or payoff* in `green` (e.g. "Tiny On-Device LLMs" blue, "MediaPipe" green). Never more than two highlight runs.
- Speaker pill: `lime-deep`, flush to the left edge with its right end rounded; name in `speaker`, role in `speaker-role` `green`.
- Variant (Beyond the Grid, Compiler Magic): small kicker line in `blue`/`ink-muted` above the title, title at 72px, speaker as plain text — "Dinoy Raj" in `blue` 500 with role under it — at the bottom-left; event as a small dark pill or the event logo.
- Don't add a background grid or gradient here; white only.


### Labels

#### ChipSet

`components/ChipSet.html` — Badges and status chips

Small labels that annotate a slide: status, model/version, result, inline terms and quick facts.

**Consumer provides:** the label text (1–3 words) and its kind.

- `dr-badge` (40px, 20px/600, pill): `is-green` for stable/success and timings; `is-lime` for beta and highlights; `is-blue` for experimental; `is-muted` for deprecated; default `green-tint` for model names; `is-dark` (code colours) for versions and artifacts.
- `dr-ichip`: a lime (or green) pill inside a sentence for prompt variables and key terms.
- `dr-opill`: outline pill for neutral facts and focus areas.
- A pinned top-right chip is `.dr-chip` (see `DemoSlide`). Max three badges in one group; status always carries its word, never colour alone.

#### Headline

`components/Headline.html` — Slide headline

A large regular-weight headline top-left: the alternative slide header (droidcon Uganda deck) for long, content-dense talks.

**Consumer provides:** the headline text and one highlight phrase.

- `headline` style (72/88, 400) in `ink`, at `space-xl` left, 120px from the top.
- Highlight one phrase at the *same* weight (400) in `blue` (the concept) or `green` (the API/feature). For series slides use "Topic - **Facet**": the facet after the hyphen is the highlight ("Summarisation API - **Input restrictions**").
- Parenthetical qualifiers go in `ink-muted`.
- One line preferred; two lines max.

#### TopicTag

`components/TopicTag.html` — Slide label

The small pill pinned top-left that names the slide's topic: the default slide header in three of the four decks.

**Consumer provides:** a short Title Case label (1–5 words). Optional second segment for a sub-topic.

- Default: `lime` fill, `on-lime` text, `tag` style (24px/600), 64px tall, 32px side padding, `radius-pill`, inset `space-l` from top and left.
- Green variant: `green` fill with `lime` text. Pick lime *or* green per deck and keep it (Compiler Magic used green throughout).
- Split variant: lime segment + green segment inside a 3px `green` outline, for "Category | Sub-topic" (e.g. Querying | Launcher Service).
- A single emoji or ☺ may close the label when the slide is a punchline ("Recomposition 😵", "Reviews ☺").
- Don't combine a topic tag and a `Headline` on the same slide.


### Content

#### BulletList

`components/BulletList.html` — Bullets with highlights

Green-dot bullets in `body` with highlighted key terms; usually the left half, with a diagram, code or screenshot on the right.

**Consumer provides:** 1–4 bullets of 1–3 lines each; which phrases to highlight; the right-hand visual.

- `body` style (36/56) in `ink`; 14px `green` dot; groups separated by 80px.
- Highlights: concept nouns in `blue` 500, outcomes or qualifiers in `green`. Two to four highlights per bullet is the house rhythm.
- Keep bullets to the left ~45% when a visual sits right; full width (max 1500px) when alone.
- Don't use other bullet glyphs, numbers or nested bullets.

#### CalloutNote

`components/CalloutNote.html` — Tip and note boxes

A highlighted aside beneath bullets: `green-tint` for tips, `blue-tint` for notes and caveats.

**Consumer provides:** the kind (Tip, Note, Gotcha) and one or two sentences.

- Box: full content width, `radius-tile`, 44/56 padding; text 34/52 with highlights.
- Label: `dr-badge` — `lime` "Tip ☺" on green-tint; white "Note" with `blue` text on blue-tint.
- Inline API names as a green `dr-ichip` in the mono family.
- At most two callouts per slide; never a coloured left border.

#### CodeBlock

`components/CodeBlock.html` — Kotlin on dark

Code on a dark rounded panel with line numbers and a fixed five-colour syntax palette.

**Consumer provides:** the snippet (Kotlin, Gradle, XML, Python), already trimmed to what matters.

- `dr-code`: `code-bg`, `radius-code`, mono family. `code-l` (32/60) for ≤ 10 lines as the slide's hero; `is-s` / `code-s` (20/32) for longer code beside bullets.
- Colours: keywords `code-keyword`, types/annotations/params `code-type`, punctuation `code-punct`, identifiers `code-text`, comments and line numbers `code-comment` italic.
- Spotlight a line with a lime pill around it, or a small green label pill above the block ("Data set", "Open model & LoRA").
- Light variant for secondary snippets: `gray-row` card, no numbers, pastel syntax.
- Prefer one block per slide; two side by side with green caption pills under each when comparing (File structure / Python code).

#### CodePair

`components/CodePair.html` — Before / after code

Two code blocks side by side with caption pills underneath: before/after, Kotlin/Python, file tree/code.

**Consumer provides:** two snippets of similar length (≤ 12 lines each) and two short captions.

- Two equal `dr-code is-s` blocks (24/44 here), 56px gap, same height.
- Captions: `dr-cap` pills centred under each block. For before/after the "before" pill is an outline (white, 2px `card-border`, `ink-soft`) and the "after" pill is solid `green`, optionally closed with ☺.
- Keep the changed lines in the same position in both blocks so the eye can diff them.

#### DataTable

`components/DataTable.html` — Comparison table

Comparison tables with a blue header row and alternating gray/blue rows.

**Consumer provides:** a header row and up to ~8 rows; keep cells short.

- `dr-table`: a segmented list in the Material 3 Expressive style: every row is its own bar with small `radius-tile` corners and a 4px gap, and the table's four outer corners use the larger `radius-card`. No borders or rules anywhere.
- Header row `blue` with white 24px/500 text; body rows alternate `gray-row` and `blue-row`, text `ink-soft` 24/32.
- Small inline ✅ / 🟡 marks are fine in a "Result" column.
- For results tied to a device, put the device label as a small `blue`/`green` caption to the left of the table.

#### FeatureCards

`components/FeatureCards.html` — Outlined card row

A row of 3–5 white outlined cards, each an icon, a title and a one-line description.

**Consumer provides:** per card a 3D/glossy icon (Google-style 3D illustrations in the past decks), a title (1–3 words) and a description (≤ 6 words, two lines).

- `dr-card`: `surface`, 2px `card-border`, `radius-card`; title `card-title` and body `card-body`, both `ink-muted`, centred.
- Equal widths, 44px gaps, icon in the top half.
- Status variant: cards labelled with a state (Downloadable / Downloading / Available / Unavailable).
- Don't colour the cards; colour comes from the icons.

#### FlowDiagram

`components/FlowDiagram.html` — Nodes and connectors

Hand-built architecture and flow diagrams from pills and soft boxes joined by thin dashed lines.

**Consumer provides:** the nodes, their grouping into columns or rows, and the connections.

- Column headers / categories: `dr-node` lime pill with `green` text.
- Entry points / requests: `is-outline` pill (white, 2px `ink-soft` border).
- Steps: `is-box` — `green-wash` fill, `green-tint` border, `green` text, `radius-node`.
- The one highlighted system node: `is-blue` (`blue-tint` fill, `blue` text).
- Connectors: 2px dashed `card-border`, or solid with small arrowheads in the node's colour.
- Phase flows (Composition → Layout → Drawing) may use `blue`, `accent-orange`, `accent-deep` as solid node fills with white bold text, with outline boxes in the same colours for the "state reads" column.

#### KeyTakeaways

`components/KeyTakeaways.html` — Recap with checks

The recap before the closing slide: three statements, each behind a lime check disc.

**Consumer provides:** 3 (max 4) one-line takeaways, each with 1–2 highlights.

- 88px `dr-check` discs (`lime` with a `green` tick); statements at 48/64 with `blue`/`green` highlights; 64px between rows.
- One line each; if it wraps, cut words.
- Place immediately before `ClosingSlide`. Same content can open the talk as a promise ("By the end you'll…").

#### NumberedSteps

`components/NumberedSteps.html` — Discs and numerals

Numbered items as green discs with labels: a 2×2 grid, or a vertical list of four.

**Consumer provides:** 3–4 short labels (1–3 words), numbered 01–04.

- `dr-disc`: 170px `green` circle, two-digit number in white 32px/500; label in `step-label` (48/56) `ink`, 60px to the right.
- 2×2: columns read top-to-bottom (01, 02 left; 03, 04 right).
- Compact list (droidcon Uganda): 64px discs, labels at 28px, 52px rows.
- Ordered-pills variant: `dr-numeral` (gradient `blue` → `blue-tint`, 80px) next to a `dr-code-pill` (`green` fill, `lime` text) for code identifiers, staggered diagonally (01 left, 02 indented right).

#### PromptResponse

`components/PromptResponse.html` — Prompt and model output

A prompt and the model's answer side by side, for prompt-engineering and GenAI API talks.

**Consumer provides:** the prompt text with the variable parts marked, the response (JSON or text), the latency, and which output fields were correct.

- Both panels on `blue-tint`, `radius-card`, equal height.
- Prompt at 30/52; variables and the user's query as `dr-ichip` (lime with `on-lime`); the target format as a green `dr-ichip`; field names in `ink-muted`.
- Response in a `dr-code is-s` block inside the right panel; a green `dr-badge` "Generated in X s" straddles its top edge.
- Field checks: small `dr-check is-s` discs aligned to the lines they validate; a partial or wrong field gets a `lime` disc instead.
- Number iterations in the headline ("#1 Prompt", "#2 Prompt") so the audience can follow the refinement.

#### ResourcesSlide

`components/ResourcesSlide.html` — Links and QR

Where to go next: 3–5 links as soft pills with a type badge, plus one QR that collects them.

**Consumer provides:** per link a type (Docs, Code, Models, Slides, Video), a title and a short URL; one QR image.

- Rows: 128px `radius-pill` bands alternating `green-tint` / `blue-tint` (`gray-row` for the least important); a `dr-badge` for the type; title 32px/500 `ink`; URL 22px `blue`.
- QR in a white outlined card (`radius-card`, 2px `card-border`) on the right with a 26px `ink-muted` caption.
- Shorten URLs to the readable part; the QR carries the full links.

#### ScreenshotRow

`components/ScreenshotRow.html` — Phone screens with captions

A row of 2–4 phone screenshots, each on a tinted panel with a title and a one-line caption.

**Consumer provides:** the screenshots (portrait PNGs), a 1–3 word title and a short caption for each.

- Panels 820px tall, `radius-code`, cycling `green-tint`, `blue-tint`, `gray-row`, `blue-panel`.
- Title 30px/500 `ink`, caption 22/30 `ink-muted`, centred above the phone.
- Phone: `dr-phone` frame (10px `code-bg` bezel, 44px radius) holding the screenshot; it may bleed off the bottom of the panel.
- Two screens: make the panels wider and put a `dr-cap` green caption pill under each instead of the title.

#### StatHighlight

`components/StatHighlight.html` — Big numbers

Two to four big numbers that carry the argument, each with a label and a source line.

**Consumer provides:** values (≤ 4 characters each), a 1–3 word label, and a one-line qualifier or source.

- Value at 200px/700 alternating `green` and `blue`; label at 40/52 `ink`; qualifier 26px `ink-muted`.
- Equal columns divided by 2px `hairline` rules; content starts ~300px from the top under a `TopicTag`.
- Use only measured or well-established numbers; put the source in the qualifier line.
- Don't add icons or cards around the numbers; whitespace does the framing.

#### Timeline

`components/Timeline.html` — Horizontal steps

A left-to-right sequence of 3–6 steps on a dashed line, for pipelines, setup flows and histories.

**Consumer provides:** step labels (or years), a 1–3 word heading and a one-line detail for each; which step is the destination.

- Dashed `card-border` line across the slide; each step = lime `dr-node` pill on top, a 2px stem, a 40px `green` dot on the line, heading 30px/500 and detail 24/32 `ink-muted` below.
- The destination step: solid `green` pill with white text and a larger `lime` dot ringed in `green`.
- Equal columns; ≤ 6 steps. Longer flows go to `FlowDiagram`.

#### TintTiles

`components/TintTiles.html` — Mint, blue and solid tiles

Soft tinted tiles for grouping concepts, logos or options; the centre tile can carry the logo or emphasis.

**Consumer provides:** 2–6 short labels or logos, optional one-sentence descriptions.

- `dr-tile` on `green-tint`; `is-blue` on `blue-tint`; `is-outline` = white with a `green-tint` 2px border; `is-solid` = `green` with white content for the one emphasised item.
- Tile label in `green` (or `blue` on blue tiles) at 28–36px/500; description 22px `ink`.
- Corners `radius-tile`. Whole-slide variant: `is-mint` slide background with white panels on it (Clean Architecture slides).
- Logo grid: logos in full colour on `green-tint` tiles, 3×2.

#### VersusSplit

`components/VersusSplit.html` — A vs B

Two opposing ideas side by side: white half vs green half, with a lime "vs" disc on the seam.

**Consumer provides:** two short names (1–2 words), a one-line description each, and 1–3 trait badges each.

- Left half `surface` with the name in `green` 120px/700; right half a `green` panel inset 24px from the edges with `radius-card` corners, name in `on-green`.
- Descriptions 28px (`ink-muted` / `on-green`); traits as `dr-badge` (green-tint on white, lime on green).
- 160px `lime` disc with "vs" in `on-lime`, centred on the seam.
- Put the "good"/default side on the left (white), the problem/twist on the right (green).
- Header variant for denser comparisons: two `green-tint` pills as column headers with bullets under each (ProtoBuf vs FlatBuffers).


## 10. Imagery

- Hero and feature visuals: glossy 3D renders on white, no frame. Bring your own images; this repo ships none.
- Technology logos sit on `--green-tint` tiles in their own colours.
- IDE / web screenshots go in dark frames (`--code-bg`, `--radius-code`); phone screenshots in `dr-phone` on `--blue-tint` or `--blue-panel` panels.
- No icon font or line icons. Don't draw logos or mascots yourself; leave a labelled placeholder when an image is missing.

## 11. Checklist before you hand back slides

- [ ] Every slide is 1920×1080 and uses tokens/classes, not new hex values.
- [ ] One header system (tags or headlines) across the deck.
- [ ] Each content line has 1–4 blue/green highlights; no bold-for-emphasis.
- [ ] Highlights and coloured text are ≥ 24px; small text is ink/ink-soft/ink-muted.
- [ ] Green slides are ≤ ~20% of the deck; demos numbered in order.
- [ ] Code uses `dr-code` with the five syntax colours, ≤ 10 lines at `code-l` or ≤ 25 at `code-s`.
- [ ] No shadows, extra gradients, left-border cards, decorative emoji or invented logos.
- [ ] The deck ends with `KeyTakeaways` (optional) and the `ClosingSlide` "Thankyou."
