# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page static website for David Valerio's HSE consulting business. Pure HTML/CSS with no build system — changes go live when pushed to GitHub Pages.

Repository: `github.com/davidavalerio/valeriosafety.com`

## Architecture

**File inventory** (this is the entire repo):
- `content.md` — Source of truth for all website copy. Edit text here first.
- `index.html` — Complete site (HTML, CSS in `<style>` block, minimal vanilla JS for mobile menu)
- `og-image.png` — Open Graph social preview image
- `David-Valerio-Professional-Headshot.jpg` — About section headshot
- `CNAME` — GitHub Pages custom domain (`valeriosafety.com`)
- `CLAUDE.md` — This file

When David wants to change text, he edits content.md and asks Claude to sync those changes into index.html.

**Contact form** uses Formspree.io at `https://formspree.io/f/xnjnkknw`. Do not change this endpoint without direction.

**Hosting:** GitHub Pages, deploys automatically on push to main.

## Page Structure

Sections in DOM order, with their anchor IDs:

1. **Nav** — Fixed top bar with logo, links to `#services`, `#about`, `#contact`
2. **Hero** (no ID) — Purple gradient, headline, byline, CTA button
3. `<main id="main">` — Wraps all content sections below
4. **Services** (`#services`) — Three cards: Site Assessments, Training & Investigation, Safety Documentation. Followed by Cook Compliance partnership note linking to `cookcompliance.co`.
5. **About** (`#about`) — Headshot, bio, credentials panel
6. **Contact** (`#contact`) — Form (Formspree), phone number: `713-478-9395`
7. **Footer** — Copyright with dynamic year

The phone number `713-478-9395` appears in two places that must stay in sync:
- Contact section: `<a href="tel:713-478-9395">`
- Schema.org JSON-LD in `<head>`: `"telephone": "+1-713-478-9395"`

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

## Maintain on Edit

Patterns to preserve when making changes:

- **Accessibility:** Skip-to-content link, `sr-only` form labels, ARIA attributes on nav and logo, semantic `<main>` element
- **SEO:** Canonical URL, Open Graph meta tags, Twitter card, LocalBusiness schema.org JSON-LD in `<head>`
- **Phone number sync:** If the number changes, update both the contact section link and the schema.org `telephone` field

## Content Voice

The site explicitly rejects "safety theater." Copy is direct and honest — emphasizes outcomes (preventing fatalities) over compliance checkbox language. Don't soften this tone.

## Commands

No build system. Only git operations matter:

```bash
git add . && git commit -m "description" && git push   # Deploy changes
```
