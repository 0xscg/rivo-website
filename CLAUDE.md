# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A single-file static marketing site for **NexusLink** — a fictional open banking & payments API platform. Everything lives in `index.html`: HTML structure, CSS styles, and JavaScript, all inline with no build tooling.

## Development

No build step required. To preview locally:

```bash
python3 -m http.server 8000
# or
npx serve .
```

Open `http://localhost:8000` in a browser.

## Architecture

`index.html` is structured in order:
1. `<head>` — Google Fonts imports (Outfit, DM Sans, JetBrains Mono) and all CSS in a `<style>` block
2. `<body>` — page sections: nav → hero → trust bar → products → how-it-works → features → metrics → developers → pricing → CTA → footer
3. `<script>` block at the bottom with all JavaScript

**CSS design tokens** are defined as CSS custom properties in `:root` at the top of the `<style>` block. The primary palette: `--deep-navy`, `--navy`, `--teal`, `--teal-light`, `--coral`, `--amber`. Font stacks: `--font-display` (Outfit), `--font-body` (DM Sans), `--font-mono` (JetBrains Mono).

**Responsive breakpoints**: 1024px (tablet) and 768px (mobile) via `@media` queries at the bottom of the `<style>` block.

**JavaScript behaviors** (inline `<script>`):
- Nav scroll shadow: toggles `.scrolled` on `#nav` via `window.scroll`
- Developer code tabs: `switchTab(tab)` shows/hides `.tab-content` panels
- Copy button: `copyCode(btn)` reads `.code-body` text and writes to clipboard
- Scroll-in animations: `IntersectionObserver` adds `.visible` to `.fade-in` elements
- Smooth scroll: intercepts `a[href^="#"]` clicks

**Section IDs** used for nav anchors: `#products`, `#developers`, `#pricing`.
