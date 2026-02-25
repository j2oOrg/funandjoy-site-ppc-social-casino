# Moonlightkids Style Migration Plan

## Goal
Restyle this site (`index.html`, `games.html`, `play.html` and shared header/nav treatment) to match `moonlightkids.co`, while:
- keeping our current menu item labels and destinations
- using the same font system
- using the same background treatment

## Hard Requirements
1. Keep existing menu items and links:
   - Home (`index.html`)
   - Games (`games.html`)
   - About (`about.html`)
   - Contact (`contact.html`)
   - Terms (`terms.html`)
   - Privacy (`policy.html`)
2. Apply Moonlight Kids menu styling only (not menu content changes).
3. Use the Moonlight Kids background style:
   - tiled texture image
   - dark overlay
   - fixed background behavior
4. Keep all current games on the main landing page (`index.html`) exactly as a full catalog section.
   - Do not reduce to a single featured game.
   - Each game card must include:
     - local image
     - short description
     - `Play now` button linking to `play.html?game=<id>`
5. Preserve compliance language and social-casino wording exactly.
   - Do not remove or weaken wording like:
     - `social casino`
     - `practice-only`
     - `18+ only`
     - `No real money, prizes, purchases, or cash-out`
   - Style updates must not rewrite compliance text, disclaimers, terms, or policy phrasing.

## Source Style Tokens (from moonlightkids.co)
- Primary font families to adopt:
  - `lulo-clean-w01-one-bold`
  - `avenir-lt-w01_35-light1475496`
  - `amatic sc`
- Key palette variables from source:
  - `--color_37: 42,42,42` (dark surfaces)
  - `--color_41: 120,111,105` (muted brown accent)
  - `--color_42: 210,205,201` (light text/accent)
  - `--color_44: 40,37,35` (deep dark)
- Header/nav styling pattern from source:
  - dark sticky header
  - large handwritten nav font (`amatic sc`) around `38px`
  - lighter hover/selected state
  - right-aligned menu cluster
- Background source from page background:
  - texture URL:
    - `assets/moonlightkids-bg-tile.png`
  - behavior:
    - repeat tiled (`180x101`)
    - fixed background positioning
    - dark overlay (`rgb(43,42,42)`)
    - image opacity target near `0.36`

## Implementation Plan
1. Create a shared style token block for all pages.
   - Add Moonlight-style CSS variables for color, typography, spacing.
   - Keep existing class names to minimize layout regressions.
   - Keep compliance copy blocks text-identical (style only, no wording edits).

2. Integrate font loading.
   - Add `@font-face` or hosted equivalents for:
     - `amatic sc` (menu/nav and playful accents)
     - `lulo-clean-w01-one-bold` (headline/brand accents)
     - `avenir-lt-w01_35-light1475496` (body text)
   - Add fallbacks and `font-display: swap`.

3. Apply Moonlight-style global background.
   - Replace current radial gradient background with tiled texture + overlay.
   - Keep readability by layering:
     - texture base
     - dark overlay
     - content cards above at higher contrast
   - Ensure behavior is consistent on desktop/mobile.

4. Restyle header and navigation (menu items unchanged).
   - Keep existing nav labels/links exactly as-is.
   - Restyle nav to Moonlight look:
     - sticky dark bar
     - `amatic sc` large nav labels
     - hover/active colors from source palette
     - spacing and alignment similar to reference

5. Harmonize cards, buttons, and text hierarchy.
   - Buttons: muted brown fills, light text, rounded corners.
   - Card surfaces: dark/neutral backgrounds with stronger contrast.
   - Heading/body fonts mapped to source equivalents.

6. Preserve current game functionality.
   - Do not change game data wiring (`games.md`-driven content already implemented).
   - Ensure all `Play now` links still route to `play.html?game=<id>`.
   - Ensure all current games remain rendered on the landing page card grid.
   - Keep all compliance/disclaimer sections present in the same pages.

7. QA and polish pass.
   - Visual checks: index/games/play on desktop and mobile widths.
   - Accessibility checks:
     - color contrast
     - focus-visible states
     - readable font sizing
   - Performance checks:
     - font loading behavior
     - no broken image/font links

## Acceptance Criteria
- Menu item set and destinations are unchanged.
- Site uses Moonlight-style fonts and visual tone.
- Site background matches Moonlight’s tiled dark style.
- Header/nav appearance matches Moonlight’s style direction.
- Existing game cards and play flow continue working.
- Landing page still shows the complete game list (not a single featured room).
- Social-casino and compliance wording remains intact across pages.

