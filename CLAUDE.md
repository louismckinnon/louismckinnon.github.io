# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static personal academic website for Louis McKinnon, deployed via GitHub Pages at `louismckinnon.github.io`. No build system, bundler, or dependencies — pure HTML, CSS, and JavaScript. Changes go live by pushing to `main`.

## Files

- `index.html` — Primary page: About bio, Presentations, Publications, Contact
- `recommendations.html` — Secondary page: personal recommendations (poetry, books, music, food). Uses an older structure inconsistent with `index.html` (different nav, `h1` for sections instead of `h2`, placeholder content including `example.com` links that need to be filled in)
- `style.css` — Shared stylesheet (currently only `index.html` follows the design system below)
- `script.js` — Scroll-based nav active-state tracker; highlights the current section's nav link with `.active`
- `cv.pdf` — Curriculum vitae linked from the Contact section
- `headshot 2025 08 20.png` — Profile photo referenced in `index.html`

## Design system

Concept: **"The Margin"** — the visual grammar of empirical health economics papers (precise column, footnote-style metadata, labels embedded in rules). Every choice is tied to this specific researcher's field; nothing here is a generic academic default.

### Color palette

| Token | Hex | Role |
|---|---|---|
| Background | `#F8F9FA` | Cool white — clinical, not warm/creamy |
| Primary text | `#111827` | Deep navy-black, richer than pure `#000` |
| Accent | `#1E5A96` | JAMA/NEJM institutional blue — used for metadata labels, nav hover/active, link hover underlines |
| Secondary / meta | `#94A3B8` | Muted slate — position text, nav default, section labels, research-interests paragraph |
| Rule | `#E2E8F0` | Hairline dividers, paper-list left borders, headshot border, `.sep` dots in nav |

No warm tones anywhere. The cool palette reads as precise and clinical.

### Typography

Three typefaces, each with a single role. Do not swap them between roles.

| Face | Weight | Role | Google Fonts spec |
|---|---|---|---|
| **Fraunces** | 700 | Name only (`h1`) — display, used large, used once | `Fraunces:opsz,wght@9..144,700` |
| **Source Serif 4** | 400 / 600 | All body text, section labels, position line | `Source+Serif+4:ital,opsz,wght@0,8..60,400;0,8..60,600;1,8..60,400` |
| **Space Mono** | 400 | Research metadata panel only — nowhere else | `Space+Mono` |

Base: 16px, line-height 1.75. Section labels (`h2`): 0.7rem, uppercase, letter-spacing 0.12em, color `#94A3B8`.

### Layout

Single centered column, `max-width: 720px`, `padding: 3.5rem 1.5rem 5rem`. No sidebars.

**Header structure** (top to bottom):
1. `h1` in Fraunces — name with pronunciation in italic Source Serif 4 at 0.44em
2. `.position` — institution line in `#94A3B8`
3. `.research-meta` — the signature element (see below)
4. `nav` — anchor links, sits below the metadata panel

**Section headings** use a rule extending to the right via flexbox + `::after` pseudo-element:
```css
h2::after { content: ''; flex: 1; height: 1px; background: #E2E8F0; }
```
This produces `Presentations ────────────────` — the label is embedded in the rule, not above it.

**Paper/entry lists** (`.paper-list`): no bullets, `padding-left: 1rem`, `border-left: 2px solid #E2E8F0`.

### Signature element: research metadata panel

```html
<div class="research-meta">
    <div class="meta-row">
        <span class="meta-label">Keywords</span>
        <span class="meta-value">…</span>
    </div>
    <div class="meta-row">
        <span class="meta-label">Methods</span>
        <span class="meta-value">…</span>
    </div>
</div>
```

Rendered in Space Mono at 0.7rem. `.meta-label` in `#1E5A96`, `.meta-value` in `#94A3B8`. Left-bordered with `2px solid #E2E8F0`. The entire block mimics the indexing metadata at the bottom of a JAMA/NEJM abstract. **This is the only place Space Mono appears.** Adding it elsewhere breaks the contrast that makes this element distinctive.

### What to preserve when extending

- Keep the palette strictly cool — no warm neutrals, no cream, no terracotta
- New sections get an `h2` with the inline-rule treatment, not a standalone heading
- New typefaces should not be introduced; use the three above
- If adding a new page, bring it in line with `index.html`'s structure (note: `recommendations.html` currently does not follow this system)

## Local preview

```
python -m http.server 8080
```

Then open `http://localhost:8080`.

## Deployment

Push to `main` → GitHub Pages auto-deploys. No CI, no preview environments.
