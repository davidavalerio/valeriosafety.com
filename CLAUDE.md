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

1. **Nav** — Sticky top bar with logo, links to `#services`, `#about`, `#contact`
2. **Hero** (no ID) — Flat deep purple, headline, byline, CTA button
3. `<main id="main">` — Wraps all content sections below
4. **Services** (`#services`) — Three cards: Site Assessments, Training & Investigation, Safety Documentation. Followed by Cook Compliance partnership note linking to `cookcompliance.co`.
5. **About** (`#about`) — Headshot, bio, credentials panel
6. **Contact** (`#contact`) — Form (Formspree), phone number: `713-478-9395`
7. **Footer** — Copyright with dynamic year

The phone number `713-478-9395` appears in two places that must stay in sync:
- Contact section: `<a href="tel:713-478-9395">`
- Schema.org JSON-LD in `<head>`: `"telephone": "+1-713-478-9395"`

## Design Tokens

CSS custom properties use the shared Discern Earth token system (matches `discern.earth/screen.css`).

**Color scales:**
- Purple: `--purple-500` (#481785) through `--purple-100` (#F8F3FF)
- Gold: `--gold-600` (#7D5C0D) through `--gold-100` (#FFFCF3)
- Neutrals: `--neutral-500` (#000) through `--neutral-100` (#FFF)

**Semantic aliases** (use these in new CSS):
- `--color-brand` / `--color-brand-hover` — purple-500 / purple-400
- `--color-accent` / `--color-accent-soft` — gold-400 / gold-200
- `--color-text` (#333), `--color-text-heading` (purple-500), `--color-text-secondary` (neutral-400), `--color-text-muted` (#5C5C5C)
- `--color-border` (neutral-300), `--color-border-accent` (gold-300)
- `--color-link` (purple-400)
- `--color-bg` (gold-100 — warm pale gold), `--color-bg-card` (white), `--color-bg-subtle` (purple-100)

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
