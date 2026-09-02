# OpenBB Design System — Figma Files Overview

> Three Figma files make up the OpenBB design system. This page explains how they fit together and which one to open depending on what you need.

## Table of contents

- [The three files](#the-three-files)
- [Repository layout](#repository-layout)
- [How the layers connect](#how-the-layers-connect)
- [How the tokens actually work](#how-the-tokens-actually-work)
- [Why split into three files?](#why-split-into-three-files)
- [Which file do I need?](#which-file-do-i-need)

## The three files

| File | What it is | Where |
|---|---|---|
| 🎨 **Styleguide** | Design tokens: color, typography, grid, shadow | [`styleguide/`](styleguide/) · [README](styleguide/README.md) · [Figma](https://www.figma.com/design/Gbu811BkBJBtez3ajbr7lw/Styleguide) |
| 🧩 **Components — UI Library** | Reusable components, built with Atomic Design (Base → Atoms → Molecules → Organisms → Templates) | [`components-ui-library/`](components-ui-library/) · [README](components-ui-library/README.md) · [Figma](https://www.figma.com/design/RFg3HgmBqsbX3OuLaJTAbb/Components-%E2%80%94-UI-Library) |
| 🖼 **OpenBB Workspace (Mockups)** | Actual product screens and flows, organized by product area, each documented with status, dark/light versions, and notes | [`workspace/`](workspace/) · [README](workspace/README.md) · [Figma](https://www.figma.com/design/CGw3LHItVogmCC1CHP0bNi/OpenBB-Workspace) |

## Repository layout

Each Figma file lives in its own folder next to the guide that explains how that file is organized:

```
figma/
├── README.md                          ← this file: how the three files fit together
├── styleguide/
│   ├── README.md                      ← Styleguide file guide (tokens)
│   └── Styleguide.fig
├── components-ui-library/
│   ├── README.md                      ← Components — UI Library file guide (Atomic Design)
│   └── Components — UI Library.fig
└── workspace/
    ├── README.md                      ← OpenBB Workspace file guide (mockups)
    └── workspace.fig
```

The `.fig` files are local exports of the Figma documents linked above; the Figma links remain the live source of truth.

## How the layers connect

Each file builds on the one before it — nothing skips a layer:

```
🎨 Styleguide            🧩 Components — UI Library         🖼 OpenBB Workspace
   Colors, Type,     →      Atoms → Molecules →         →      Product screens,
   Grid, Shadow              Organisms → Templates               organized by feature
   (raw tokens)              (built FROM those tokens)            (built FROM those components)
```

- **Styleguide** defines the raw values — nothing in here references anything else.
- **Components — UI Library** consumes Styleguide tokens (colors, type styles) to build every Button, Card, Table, etc.
- **OpenBB Workspace** consumes Components — UI Library instances to assemble actual product screens (Dashboard, Admin Portal, Share flow...).

If a color needs to change, it changes once in Styleguide and should flow down. If a screen looks wrong, the fix is almost always in the Components file, not the mockup itself.

## How the tokens actually work

This isn't just a visual convention — Styleguide defines real Figma primitives, and Components — UI Library is wired directly to them:

| Token type                 | Mechanism                                                                                                                                                                                                                                             | Where      |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Colors                     | **Variables** — 2 linked collections: `Primitive` (91 raw values like `color/brand/50`, `color/dark/100`) → `Semantic: Colors` (91 role-based aliases like `components/buttons/secondary/bg`, `components/text/heading`), with **Light + Dark modes** | Styleguide |
| Spacing, font size, radius | **Variables** — 1 collection, `Semantic: Spacing-layout` (26 values: paddings, corner radii, heading/body font sizes)                                                                                                                                 | Styleguide |
| Typography                 | **Text Styles** — 55 fixed combinations of font + size + weight (`Title/XL/Bold`, `Body/S/Medium`...), all Manrope                                                                                                                                    | Styleguide |
| Shadows                    | **Effect Styles** — 6 styles, kept as separate Light/Dark pairs (`Shadow-Light-01/02/03`, `Shadow-Dark-01/02/03`) rather than one mode-switching value                                                                                                | Styleguide |

Components — UI Library has **zero variables of its own** — every fill, stroke, padding, and corner radius on every component is a *remote* reference back to one of these Styleguide variables. Checked directly on a Button: its background, border, padding, and corner radius are all bound to variables (e.g. `components/buttons/secondary/bg`), not typed-in values.

This is the real mechanism behind dark/light at the component level for **color**: it's not two separately-drawn components, it's the same component reading a semantic variable that resolves to a different value depending on which mode (Light/Dark) is active. Components additionally expose an explicit `Light`/`Dark` variant property on top of that, so you can pin a theme on a specific instance instead of relying on page-level mode switching. Typography and shadows don't use modes — they're just separate named styles applied per theme.

## Why split into three files?

The three layers change at very different speeds and are owned differently, so keeping them in one file would slow everyone down:

|                | Styleguide                     | Components — UI Library              | OpenBB Workspace                         |
|----------------|--------------------------------|--------------------------------------|------------------------------------------|
| Changes        | Rarely (brand-level decisions) | Occasionally (new component/variant) | Constantly (every feature, every sprint) |
| Owned by       | Design system / brand          | Design system team                   | Product design, per feature              |
| File size risk | Small, stable                  | Medium, grows slowly                 | Large, grows fast                        |

Splitting them means the fast-moving Workspace file doesn't drag down performance on the stable Styleguide file, and each team can work without stepping on the others' pages.

## Which file do I need?

| I need...                                                                                                                | Go to                                                                            |
|--------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| A specific color, font size, spacing, or shadow value                                                                    | 🎨 Styleguide                                                                    |
| A reusable component (Button, Card, Table, Modal...)                                                                     | 🧩 Components — UI Library                                                       |
| To see how a specific feature/flow should look (with dark/light + notes)                                                 | 🖼 OpenBB Workspace                                                               |
| To understand *why* something is categorized the way it is (Atomic Design levels, status badges, dark/light conventions) | Start with the README of the file above, they each explain their own conventions |
