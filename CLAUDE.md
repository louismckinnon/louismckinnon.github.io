# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static personal academic website for Louis McKinnon, deployed via GitHub Pages at `louismckinnon.github.io`. No build system, bundler, or dependencies — pure HTML, CSS, and JavaScript. Changes go live by pushing to `main`.

## Files

- `index.html` — Primary page: About bio, Presentations, Publications, Contact
- `recommendations.html` — Secondary page: personal recommendations (poetry, books, music, food). Uses an older structure inconsistent with `index.html` (different nav, `h1` for sections instead of `h2`, placeholder content including `example.com` links)
- `style.css` — Shared stylesheet for both pages
- `script.js` — Scroll-based nav active-state tracker (queries `nav ul li a`, which does not match the current `index.html` nav structure — effectively a no-op on the main page)
- `cv.pdf` — Curriculum vitae linked from the Contact section
- `headshot 2025 08 20.png` — Profile photo referenced in `index.html`

## Design system

Minimalist academic aesthetic:
- Font: Georgia serif, 16px base, 1.75 line-height
- Layout: single 680px-wide centered column (`.page`)
- Color palette: near-black body text `#1a1a1a`, muted grays for metadata/labels, white background
- Section headings (`h2`): 0.75rem, uppercase, letter-spaced, color `#999`
- Paper/entry lists: no bullets, left border `2px solid #eee`, slight indent
- `recommendations.html` does not currently follow this design system and would need updating to match

## Deployment

Push to `main` → GitHub Pages auto-deploys. No CI, no preview environments.
