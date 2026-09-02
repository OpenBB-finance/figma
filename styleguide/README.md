# OpenBB Styleguide — Figma File Guide

> **File:** [Styleguide](https://www.figma.com/design/Gbu811BkBJBtez3ajbr7lw/Styleguide) The foundation layer of the OpenBB design system: color, typography, grid, and shadow tokens. This is the base that the [Components — UI Library](https://www.figma.com/design/RFg3HgmBqsbX3OuLaJTAbb/Components-%E2%80%94-UI-Library) file builds its components on top of.
>
> **Local file:** `Styleguide.fig` (this folder) · **Back to overview:** [../README.md](../README.md)

## Table of contents

- [Page structure](#page-structure)
- [Documentation pattern](#documentation-pattern)
- [Colors](#colors)
- [Typography](#typography)
- [Grid](#grid)
- [Shadow](#shadow)
- [Quick navigation guide](#quick-navigation-guide)

## Page structure

Unlike the Workspace mockups file, this file has no repeating page trio — it's a flat list of four token categories, framed by an intro/outro:

```
🖼 THUMBNAIL
🤓 READ ME                      ← currently empty, no onboarding content yet
----------------------
Colors
Typography
Grid
Shadow
```

## Documentation pattern

Every page opens with the same reusable **Header** component: a gradient strip plus a heading and supporting description explaining what that token category is and why it exists (e.g. the Colors header calls out that WCAG 2.1 contrast ratios are included so teams can design accessibly).

Individual tokens can carry **"Design note"** annotations — small instances attached next to a swatch or example with extra context, seen throughout the Colors page.

## Colors

Organized as three tonal groups, each broken into opacity-derived steps:

```
COLORS
├─ BASE     — full-strength brand/semantic colors
├─ TINT     — lighter derived steps (20%, 40%, 50%, 60% …)
└─ SHADES   — darker derived steps (20%, 40%, 50%, 60% …)
```

A second "Colors" section lists each color with a `Design note` instance next to it, documenting usage/contrast guidance per color.

## Typography

Three type categories, each with its own Header + a group of labeled text samples, plus a worked "Examples" section:

| Category   | Naming pattern             | Sizes                     | Weights               |
|------------|----------------------------|---------------------------|-----------------------|
| `Body`     | `Body/{size}/{weight}`     | XS, S, M, L, XL, Subtitle | Bold, Medium          |
| `Subtitle` | `subtitle/{size}/{weight}` | M, L, XL                  | Bold, Medium          |
| `Title`    | `Title/{size}/{weight}`    | XS, S, M, L, XL           | Regular, Medium, Bold |

The **Examples** frame shows these styles composed together in real layouts (title + description + CTA), so you can see how the type ramp is meant to be combined, not just each style in isolation.

## Grid

```
Grid
├─ Documentation 📚      — link out to external grid documentation
├─ Grid                  — 8pt grid overlays per breakpoint: Mobile, Tablet, Laptop, Desktop
└─ Variations            — additional Desktop grid examples
```

## Shadow

```
Shadows
├─ Light mode 🌞   — 3 elevation levels for light theme
└─ Dark mode 🌙    — 3 elevation levels for dark theme
```

Same dark/light split convention as the rest of the design system: both themes live on the same page, grouped side by side rather than on separate pages.

## Quick navigation guide

1. Pick the token category you need (Colors, Typography, Grid, or Shadow).
2. Read the Header block at the top of each section for context and any linked documentation.
3. For Colors, check both the BASE/TINT/SHADES frame and the secondary "Colors" section with per-swatch design notes.
4. For Typography, use the naming pattern `Category/Size/Weight` to find the exact style, and check the Examples frame for real usage.
5. For Grid and Shadow, remember both breakpoints (Grid) and themes (Shadow) live together on one page — scroll within the page rather than looking for separate pages.
