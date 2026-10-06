# Junli’s Arcade

A small static site that will grow into a collection of browser games over the semester (CS 5610 Web Development, Fall 2026, Northeastern University).

**Live site:** <https://junli-gong.github.io/arcade/>

Project 1 is built with plain HTML and CSS only: no JavaScript, no CSS frameworks, and no build step.

## Pages

| Path | Contents |
|---|---|
| `/` | Landing page with an introduction and a link to the mini crossword |
| `/game/` | A playable 5×5 web-development mini crossword |
| `/about/` | Experience, education, skills, and selected publications |
| `/contact/` | Email and professional links |

## The crossword

- The board is a CSS Grid of 25 squares: 19 letter squares and 6 blocked squares.
- Each letter square is a `label` wrapping a single-character `input`. Its accessible name gives the row, column, and clue numbers.
- Clue numbers are drawn with a `::before` pseudo-element.
- **Reveal solution** is a native `details` / `summary` element, so it works with a mouse, touch, or the keyboard.
- In browsers that support `:has()`, opening it overlays the answers on the board. A text version of the answers is always available inside the panel.
- **Clear letters** is a native form reset.

## Design notes

- All colors, spacing, and type sizes are custom properties defined once at the top of `styles/global.css`.
- The palette is warm neutrals with a single forest-green accent. All text meets WCAG AA contrast.
- The site uses system fonts only, plus original SVG illustrations and icons.
- The header is sticky at every width. Below 640px the navigation links move into a fixed bottom tab bar, and the page reserves space for it.
- Every page has a skip link, a visible `:focus-visible` style, and an `aria-current="page"` marker on the active nav link.

## Project structure

```text
├── index.html / index.css       Landing page
├── styles/global.css            Design tokens, base styles, header, nav, footer
├── game/                        Crossword page and its styles
├── about/                       About page and its styles
├── contact/                     Contact page and its styles
└── assets/                      SVG icon and illustrations
```

Shared CSS lives in `styles/`. Page-specific CSS sits next to its page. All internal links are relative, so the site works under the `/arcade/` path on GitHub Pages.

## Run locally

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000/>. Use a local server rather than opening the files directly, because the folder links (such as `about/`) rely on the server to serve `index.html`.

## Credits

- The crossword words and clues were AI-generated (Claude) and lightly edited.
- The SVG illustrations were created with help from OpenAI Codex.
