# AGENTS.md — valeriosafety.com

## What This Is

Single-page business website for David Valerio's HSE consulting practice in the Williston Basin. Positions against "safety theater" and compliance-checkbox approaches — the voice is direct and honest.

## Tech Stack

- Pure HTML + inline CSS + minimal vanilla JS (mobile menu toggle only)
- Google Fonts: Josefin Sans (300 body, 700 headings)
- Remix Icon CDN
- Formspree.io for contact form
- GitHub Pages deployment

## Project Structure

```
valeriosafety.com/
├── index.html                 # Complete site (~20KB, CSS in <style> block)
├── content.md                 # SOURCE OF TRUTH for all website copy
├── CNAME                      # GitHub Pages custom domain
├── og-image.png               # Social preview image
├── David-Valerio-Professional-Headshot.jpg
└── CLAUDE.md                  # Detailed brand and design context
```

## Content Workflow

`content.md` is the single source of truth for all website text. When copy changes, update `content.md` first, then sync those changes into `index.html`. This decouples content authoring from HTML markup.

## Page Sections

1. **Nav** — Fixed top bar: logo, links to #services, #about, #contact
2. **Hero** — Full-viewport purple gradient, headline, CTA button
3. **Services** — Three cards: Site Assessments, Training & Investigation, Safety Documentation + Cook Compliance partnership
4. **About** — Headshot, bio, credentials
5. **Contact** — Formspree form (name, email, message) + phone number
6. **Footer** — Copyright with dynamic year

## Design Tokens

- Primary purple: `#5F2D9E`
- Primary deep: `#481785` (hero gradient, footer)
- Accent gold: `#A47B11` (buttons, hover)
- Gold decorative: `#E5A502` (card borders, bullets)
- Body text: `#3A3A3A`
- Light background: `#F8F3FF` (services section)
- Responsive breakpoints: 900px (tablet), 768px (mobile)

## Critical Details

- **Phone number appears in TWO places** that must stay in sync: the contact section `<a href="tel:...">` and the Schema.org JSON-LD in `<head>` as `"telephone"`.
- Accessibility: skip-to-content link, sr-only labels, ARIA nav, semantic `<main>`.
- SEO: canonical URL, Open Graph tags, Twitter card, LocalBusiness schema.org.
- No build system. Deploy by pushing to main: `git add . && git commit && git push`.

## What Codex Should Know

- Everything is in one HTML file. CSS is in the `<style>` block, JS is minimal. This is intentional.
- The Formspree endpoint (`https://formspree.io/f/xnjnkknw`) is hardcoded in the form action. Don't change it.
- The voice of the site matters. It's direct, honest, and explicitly anti-"safety theater." Maintain this tone in any copy changes.
- Always update `content.md` when changing website text, and keep `index.html` in sync.
