# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A [reveal.js](https://revealjs.com/) slide deck for RE01 Lecture 10/12: Real Estate Investment Trusts (Indirect Real Estate). Authored by Thies Lindenthal / Colin Lizieri, Cambridge.

## Running the presentation

The reveal.js framework lives in `../reveal.js/` (a sibling directory), symlinked into this repo as `css`, `dist`, `plugin`, and `package.json`.

**Option 1 – Open directly:** Open `index.html` in a browser. No build step needed.

**Option 2 – Dev server with live reload:**
```bash
cd ../reveal.js
npm install   # first time only
npm start     # runs gulp serve, then open http://localhost:8000 and navigate to this talk
```

## Repository structure

- `index.html` — the entire presentation; all content lives here
- `tweaks.css` — custom CSS overrides for the presentation (`.subtitle`, `.figure`, `.smalltable`, `.centred`, `.source`, transparency helpers, two-column `.box1`/`.box2` layout, etc.)
- `imgs/` — all images and SVGs used in slides; some charts exist in multiple versions (e.g. `nareit-market-cap-1/2/3.svg` for animated build-up across slides)
- `css/`, `dist/`, `plugin/`, `package.json` — symlinks to `../reveal.js/`

**Do not edit `../reveal.js/` or any files reached through the symlinks.** Only `index.html`, `tweaks.css`, and files in `imgs/` are in scope for editing.

## Slide authoring conventions

Slides are `<section>` elements inside `<div class="slides">`. Two patterns are used:

**Markdown slides** (most common):
```html
<section data-markdown>
  <textarea data-template>
    ## Title <span class="subtitle"><br>Subtitle text</span>
    * Bullet point
  </textarea>
</section>
```

**Raw HTML slides** (used when fine-grained layout is needed, e.g. the bubble chart on market sizes):
```html
<section>
  <h2>Title<span class='subtitle'><br>Subtitle</span></h2>
  <!-- HTML content -->
  <aside class="notes">Speaker notes here</aside>
</section>
```

Speaker notes in Markdown slides go after `Notes:` on their own line inside the textarea; in raw HTML slides they go in `<aside class="notes">`.

**Math** is rendered via MathJax (loaded from CDN). Inline: `$...$` or `\(...\)`. Display: `$$...$$`.

**Key CSS classes defined in `tweaks.css`:**
- `.subtitle` — smaller, non-uppercase heading suffix
- `.figure` / `.figure .title` / `.figure .source` — centred figure with caption and source line
- `.smalltable` — compact table styling (wraps a markdown table in a `<div class="smalltable">`)
- `.centred` — centre-align text
- `.transparent50/70/80` — white semi-transparent background (useful over background images)
- `.box1` / `.box2` / `.boxwrapper` — float-based two-column layout
- `mark` — green highlight (`#c0ffc8`)

**Background images** on a section: `data-background-image="imgs/foo.jpg"`.
