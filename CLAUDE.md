# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page static website for David Valerio's HSE consulting business. Pure HTML/CSS with no build system—changes go live when pushed to GitHub Pages.

## Architecture

**Two-file content system:**
- `content.md` — Source of truth for all website copy. Edit text here first.
- `index.html` — Complete site (HTML, CSS in `<style>` block, minimal vanilla JS for mobile menu)

When David wants to change text, he edits content.md and asks Claude to sync those changes into index.html.

**Contact form** uses Formspree.io (endpoint in HTML). No backend.

**Hosting:** GitHub Pages, deploys automatically on push to main.

## Commands

No build system. Only git operations matter:

```bash
git add . && git commit -m "description" && git push   # Deploy changes
```

## Design Tokens

CSS custom properties define the palette (Discern Earth brand):
- `--primary`: #5F2D9E (purple-400)
- `--primary-deep`: #481785 (purple-500 — hero gradient endpoint, footer)
- `--accent`: #A47B11 (gold-500 — button backgrounds, passes contrast for white text)
- `--accent-hover`: #7D5C0D (darker gold for hover states)
- `--accent-decorative`: #E5A502 (gold-400 — card borders, bullets, icons)
- `--secondary`: #3A3A3A (dark gray — body text)
- `--light-bg`: #F8F3FF (purple-100)
- `--dark`: #1A1A1A (near-black)

Typography: Josefin Sans (300 body, 700 headings) via Google Fonts.
Icons: Remix Icon CDN.

Breakpoints: 900px (tablet), 768px (mobile)

## Content Voice

The site explicitly rejects "safety theater." Copy is direct and honest—emphasizes outcomes (preventing fatalities) over compliance checkbox language. Don't soften this tone.
