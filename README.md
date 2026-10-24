# Android Talk Design System

An **Android-themed**, AI-ready slide design system for tech talks — built so **any AI tool can make on-brand slides from it**. White canvases, Android green and lime accents, blue/green highlight words, dark Kotlin code panels, 27 slide components.

Created from the slides of my last 4 conference talks — see them on **[SlideShare](https://www.slideshare.net/dinoykraj)**:

| Talk | Event |
|---|---|
| Build Your Pocket Brain: Tiny On-Device LLMs via MediaPipe on Android | DevFest Dubai · Mobile Developers Week |
| Beyond the Grid: Crafting a Custom Android Launcher from Scratch | DevFest Mumbai |
| Compiler Magic & Stability: Optimising Compose Recomposition | FOSSASIA Summit 2026 |
| Supercharging Android Apps with On-Device AI: Gemini Nano | droidcon Uganda 2025 |

- 🖼 **Gallery:** open `index.html` (or the GitHub Pages site of your fork)
- ▶️ **Example deck:** `examples/deck.html` — arrow keys to navigate, `F` for fullscreen
- 📐 **The spec:** [`DESIGN.md`](DESIGN.md) — everything an AI (or a human) needs

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
index.html           Gallery of every component (works on GitHub Pages)
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

## License

- Code (CSS, HTML, JSON): [MIT](LICENSE)
- Documentation (`DESIGN.md`, `README.md`): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — please credit "Android Talk Design System by Dinoy Raj".

Contributions welcome: open an issue or PR with new components that follow `DESIGN.md`.
