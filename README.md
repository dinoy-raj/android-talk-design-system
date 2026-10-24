<p align="center"><img src="docs/banner.png" alt="Android Talk Design System — 27 slide components, DESIGN.md, AI-ready" width="100%"></p>

# Android Talk Design System

An **Android-themed**, AI-ready slide design system for tech talks — built so **any AI tool can make on-brand slides from it**. White canvases, Android green and lime accents, blue/green highlight words, dark Kotlin code panels, 27 slide components.

Created from the slides of my last 4 conference talks — see them on **[SlideShare](https://www.slideshare.net/dinoykraj)**:

| Talk | Event |
|---|---|
| Build Your Pocket Brain: Tiny On-Device LLMs via MediaPipe on Android | DevFest Dubai · Mobile Developers Week |
| Beyond the Grid: Crafting a Custom Android Launcher from Scratch | DevFest Mumbai |
| Compiler Magic & Stability: Optimising Compose Recomposition | FOSSASIA Summit 2026 |
| Supercharging Android Apps with On-Device AI: Gemini Nano | droidcon Uganda 2025 |

- 🌐 **Live site:** [dinoy-raj.github.io/android-talk-design-system](https://dinoy-raj.github.io/android-talk-design-system/): showcase, component gallery, foundations and the example deck
- ▶️ **Example deck:** `examples/deck.html` — arrow keys to navigate, `F` for fullscreen
- 📐 **The spec:** [`DESIGN.md`](DESIGN.md) — everything an AI (or a human) needs

## Components

Every component is a standalone 1920×1080 slide in [`components/`](components). Click a preview to open its source.

### Slides

Full-slide layouts for the moments of a talk.

<table>
<tr>
<td width="33%" valign="top"><a href="components/AgendaSlide.html"><img src="docs/preview/AgendaSlide.png" alt="AgendaSlide slide preview"></a><br><b>AgendaSlide</b><br><sub>Talk outline</sub></td>
<td width="33%" valign="top"><a href="components/ClosingSlide.html"><img src="docs/preview/ClosingSlide.png" alt="ClosingSlide slide preview"></a><br><b>ClosingSlide</b><br><sub>Thankyou + QR</sub></td>
<td width="33%" valign="top"><a href="components/DemoSlide.html"><img src="docs/preview/DemoSlide.png" alt="DemoSlide slide preview"></a><br><b>DemoSlide</b><br><sub>Demo section break</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><a href="components/GreenStatement.html"><img src="docs/preview/GreenStatement.png" alt="GreenStatement slide preview"></a><br><b>GreenStatement</b><br><sub>Section interstitial</sub></td>
<td width="33%" valign="top"><a href="components/SectionDivider.html"><img src="docs/preview/SectionDivider.png" alt="SectionDivider slide preview"></a><br><b>SectionDivider</b><br><sub>Numbered chapter break</sub></td>
<td width="33%" valign="top"><a href="components/SpeakerIntro.html"><img src="docs/preview/SpeakerIntro.png" alt="SpeakerIntro slide preview"></a><br><b>SpeakerIntro</b><br><sub>About me</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><a href="components/StatementSlide.html"><img src="docs/preview/StatementSlide.png" alt="StatementSlide slide preview"></a><br><b>StatementSlide</b><br><sub>Question over the grid</sub></td>
<td width="33%" valign="top"><a href="components/TitleSlide.html"><img src="docs/preview/TitleSlide.png" alt="TitleSlide slide preview"></a><br><b>TitleSlide</b><br><sub>Opening slide</sub></td>
</tr>
</table>

### Labels

Headers and small labels.

<table>
<tr>
<td width="33%" valign="top"><a href="components/ChipSet.html"><img src="docs/preview/ChipSet.png" alt="ChipSet slide preview"></a><br><b>ChipSet</b><br><sub>Badges and status chips</sub></td>
<td width="33%" valign="top"><a href="components/Headline.html"><img src="docs/preview/Headline.png" alt="Headline slide preview"></a><br><b>Headline</b><br><sub>Slide headline</sub></td>
<td width="33%" valign="top"><a href="components/TopicTag.html"><img src="docs/preview/TopicTag.png" alt="TopicTag slide preview"></a><br><b>TopicTag</b><br><sub>Slide label</sub></td>
</tr>
</table>

### Content

Layouts for explaining things.

<table>
<tr>
<td width="33%" valign="top"><a href="components/BulletList.html"><img src="docs/preview/BulletList.png" alt="BulletList slide preview"></a><br><b>BulletList</b><br><sub>Bullets with highlights</sub></td>
<td width="33%" valign="top"><a href="components/CalloutNote.html"><img src="docs/preview/CalloutNote.png" alt="CalloutNote slide preview"></a><br><b>CalloutNote</b><br><sub>Tip and note boxes</sub></td>
<td width="33%" valign="top"><a href="components/CodeBlock.html"><img src="docs/preview/CodeBlock.png" alt="CodeBlock slide preview"></a><br><b>CodeBlock</b><br><sub>Kotlin on dark</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><a href="components/CodePair.html"><img src="docs/preview/CodePair.png" alt="CodePair slide preview"></a><br><b>CodePair</b><br><sub>Before / after code</sub></td>
<td width="33%" valign="top"><a href="components/DataTable.html"><img src="docs/preview/DataTable.png" alt="DataTable slide preview"></a><br><b>DataTable</b><br><sub>Comparison table</sub></td>
<td width="33%" valign="top"><a href="components/FeatureCards.html"><img src="docs/preview/FeatureCards.png" alt="FeatureCards slide preview"></a><br><b>FeatureCards</b><br><sub>Outlined card row</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><a href="components/FlowDiagram.html"><img src="docs/preview/FlowDiagram.png" alt="FlowDiagram slide preview"></a><br><b>FlowDiagram</b><br><sub>Nodes and connectors</sub></td>
<td width="33%" valign="top"><a href="components/KeyTakeaways.html"><img src="docs/preview/KeyTakeaways.png" alt="KeyTakeaways slide preview"></a><br><b>KeyTakeaways</b><br><sub>Recap with checks</sub></td>
<td width="33%" valign="top"><a href="components/NumberedSteps.html"><img src="docs/preview/NumberedSteps.png" alt="NumberedSteps slide preview"></a><br><b>NumberedSteps</b><br><sub>Discs and numerals</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><a href="components/PromptResponse.html"><img src="docs/preview/PromptResponse.png" alt="PromptResponse slide preview"></a><br><b>PromptResponse</b><br><sub>Prompt and model output</sub></td>
<td width="33%" valign="top"><a href="components/ResourcesSlide.html"><img src="docs/preview/ResourcesSlide.png" alt="ResourcesSlide slide preview"></a><br><b>ResourcesSlide</b><br><sub>Links and QR</sub></td>
<td width="33%" valign="top"><a href="components/ScreenshotRow.html"><img src="docs/preview/ScreenshotRow.png" alt="ScreenshotRow slide preview"></a><br><b>ScreenshotRow</b><br><sub>Phone screens with captions</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><a href="components/StatHighlight.html"><img src="docs/preview/StatHighlight.png" alt="StatHighlight slide preview"></a><br><b>StatHighlight</b><br><sub>Big numbers</sub></td>
<td width="33%" valign="top"><a href="components/Timeline.html"><img src="docs/preview/Timeline.png" alt="Timeline slide preview"></a><br><b>Timeline</b><br><sub>Horizontal steps</sub></td>
<td width="33%" valign="top"><a href="components/TintTiles.html"><img src="docs/preview/TintTiles.png" alt="TintTiles slide preview"></a><br><b>TintTiles</b><br><sub>Mint, blue and solid tiles</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><a href="components/VersusSplit.html"><img src="docs/preview/VersusSplit.png" alt="VersusSplit slide preview"></a><br><b>VersusSplit</b><br><sub>A vs B</sub></td>
</tr>
</table>

## Use it with an AI tool

Give the tool `DESIGN.md` (attach it, paste it, or point it at this repo), then ask for your talk:

> Using the attached DESIGN.md, create a 20-slide HTML deck for my talk "Building Offline-First Apps with Kotlin Multiplatform". Use the TopicTag header style, include one StatementSlide per section, two demos, KeyTakeaways and the ClosingSlide. Output one HTML file that links `tokens/tokens.css` and `css/slides.css`.

| Tool | How |
|---|---|
| Claude, ChatGPT, Gemini (chat) | Attach `DESIGN.md` (plus a component file or two from `components/` for best fidelity) and describe your talk. |
| Claude Code, Codex, Cursor, Copilot, other coding agents | Clone or fork the repo and ask in it. `AGENTS.md` / `CLAUDE.md` point the agent at `DESIGN.md` and tell it where to write decks. |
| v0, Lovable, Bolt and other site builders | Paste `DESIGN.md` and ask for an HTML slide deck. |
| PowerPoint / Google Slides / Keynote / Figma | Ask the AI to apply `DESIGN.md` to a 1920×1080 (16:9) file; the spec includes the mapping. Or set it up by hand from the tokens. |
| Tools that read `llms.txt` | `llms.txt` lists the files to read. |

## What's inside

```
DESIGN.md            The spec: rules, tokens, type scale, layouts, all 27 components, checklist
AGENTS.md, CLAUDE.md Instructions for coding agents
llms.txt             Index for LLM tools
tokens/tokens.json   Design tokens (colour, type, spacing, radius)
tokens/tokens.css    The same tokens as CSS custom properties + .t-* type classes
css/slides.css       Slide primitives (dr-slide, dr-tag, dr-bullets, dr-code, dr-badge …)
components/*.html    27 standalone 1920×1080 slide components
examples/deck.html   A 10-slide example deck with navigation
index.html           Showcase website (deployed to GitHub Pages)
.github/workflows/   Builds the site on every PR, deploys it when main changes
docs/                README banner and component preview images
```

## Make it yours

1. **Fork** this repo.
2. Change colours, fonts or sizes in `tokens/tokens.json` **and** `tokens/tokens.css` (keep them in sync), and update the tables in `DESIGN.md` to match.
3. Replace the placeholder name, role and links in `TitleSlide`, `SpeakerIntro`, `ResourcesSlide` and `ClosingSlide`.
4. Turn on **GitHub Pages** (Settings → Pages → deploy from the `main` branch, root) to get a public gallery link.

## Fonts, images and trademarks

- Fonts load from Google Fonts: **Google Sans Flex** and **Source Code Pro**, both under the SIL Open Font License. Nothing is bundled.
- This repo ships **no images**. Bring your own photos, screenshots and renders. Product and event logos belong to their owners. If you use the Android robot, credit it: *"The Android robot is reproduced or modified from work created and shared by Google and used according to terms described in the Creative Commons 3.0 Attribution License."*
- The palette is inspired by Google's brand colours. This project is not affiliated with or endorsed by Google.

## Contributing

`main` is protected: every change goes through a pull request.

1. Create a branch from `main` with a descriptive name, e.g. `feature/agenda-progress-bar` or `fix/table-row-contrast`.
2. Keep `tokens/tokens.json`, `tokens/tokens.css` and the tables in `DESIGN.md` in sync, and refresh the matching image in `docs/preview/` when a component changes.
3. Open a PR into `main`. The **Showcase site** workflow builds the site and checks that every linked file exists.
4. When the PR is merged, the same workflow deploys the site to GitHub Pages automatically.

## License

- Code (CSS, HTML, JSON): [MIT](LICENSE)
- Documentation (`DESIGN.md`, `README.md`): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — please credit "Android Talk Design System by Dinoy Raj".

Contributions welcome: open an issue or PR with new components that follow `DESIGN.md`.
