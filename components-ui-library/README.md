# OpenBB Components — UI Library — Figma File Guide

> **File:** [Components — UI Library](https://www.figma.com/design/RFg3HgmBqsbX3OuLaJTAbb/Components-%E2%80%94-UI-Library) The component library of the OpenBB design system, built with Atomic Design principles on top of the tokens defined in the [Styleguide](https://www.figma.com/design/Gbu811BkBJBtez3ajbr7lw/Styleguide) file.
>
> **Local file:** `Components — UI Library.fig` (this folder) · **Back to overview:** [../README.md](../README.md)

## Table of contents

- [READ ME page (in-file onboarding)](#read-me-page-in-file-onboarding)
- [Page structure](#page-structure)
- [Atomic Design levels](#atomic-design-levels)
- [Documentation pattern](#documentation-pattern)
- [Inside a component page](#inside-a-component-page)
- [Status markers](#status-markers)
- [Quick navigation guide](#quick-navigation-guide)

## READ ME page (in-file onboarding)

The file has its own `🤓 READ ME` page with four numbered onboarding cards, all tagged `design system`:

1. **Getting started** — introduces the design system's purpose: consistency and efficiency across product design.
2. **Atomic Design Principles** — the library follows Brad Frost's Atomic Design methodology: atoms → molecules → organisms → templates → pages, for a systematic, scalable structure.
3. **Components in Figma** — explains that components are organized following that same Atomic Design methodology inside this file.
4. **Collaboration and Contribution** — invites feedback and contributions to keep the system evolving.

This guide below maps that methodology onto the file's actual page structure.

## Page structure

Content is organized as divider pages (level headers, no content) followed by one page per component, in ascending complexity order:

```
🧩 LEVEL 1                      ← divider — Atoms
      —  Avatar
      —  Badge
      —  Buttons
      —  ...
---------------------           ← separator
🧬 LEVEL 2                      ← divider — Molecules
      —  Accordion
      —  Cards
      —  ...
------------------              ← separator
🎯 LEVEL 3                      ← divider — Organisms
      —  Header
      —  Table
      —  ...
```

## Atomic Design levels

| Figma group                   | Atomic Design role                      | Examples                                                                                                                                                           |
|-------------------------------|-----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `🎨 BASE`                     | Raw brand assets, not yet components    | Logos, Icons                                                                                                                                                       |
| `📚 Widget components — BASE` | Base primitives specific to widgets     | Widgets structure                                                                                                                                                  |
| `🧩 LEVEL 1`                  | **Atoms** — smallest building blocks    | Avatar, Badge, Buttons, Checkbox, Radio Button, Tag, Tooltip, Scrollbar, Window bar, Layer, Grouping, Connections status indicator                                 |
| `🧬 LEVEL 2`                  | **Molecules** — atoms combined          | Accordion, Cards, Dropdown, Search input, Date Picker 🖌️, OTP input 🖌️, Tab, Toggle, Slider, Pagination, Carousel Images, Placeholder, Actions group, Color Picker |
| `🎯 LEVEL 3`                  | **Organisms** — groups of molecules     | Header, Table, Modal, Toast Message, Input field, Status, Widgets                                                                                                  |
| `🏆 LEVEL 4`                  | **Templates** — full composite patterns | Sidebar, AI, Widget Studio                                                                                                                                         |

## Documentation pattern

Component categories are introduced with the same **Header** component used elsewhere in the design system — a gradient strip plus a heading and supporting description of what the component is for (defined once on the `🧩 Components information` page and reused as an instance everywhere).

## Inside a component page

Each component page groups its variants into named frames, and each variant frame can hold multiple theme-specific component sets. Example from `Buttons`:

```
—  Buttons
├─ Secondary
│   ├─ Header (documentation)
│   ├─ Light   (component set)
│   └─ Dark    (component set)
├─ Danger
│   ├─ Header (documentation)
│   └─ Danger (component set)
└─ Outlined
    ├─ Header (documentation)
    ├─ Light   (component set)
    └─ Dark    (component set)
```

- Each **button style** (Secondary, Danger, Outlined, …) gets its own frame.
- **Dark/Light is expressed as a variant set**, not a separate frame or page — `Light` and `Dark` are sibling component sets holding the same variant properties.
- Typical variant properties within a set: `Size` (sm / md / lg / xlg), `Structure` (Text / Text + Icon), `Align` (Left / Right / Center / Default), `Status` (Default / Hover / Disabled).

This pattern (style frame → Header → Light/Dark component sets → size/structure/align/status variants) repeats across most Level 1–3 components.

## Status markers

A few component pages carry an extra 🖌️ next to their name (e.g. `Date Picker 🖌️`, `OTP input 🖌️`). This isn't explained on the READ ME page — treat it as a flag that the component needs extra attention, and confirm the exact meaning with the design team before relying on it.

## Quick navigation guide

1. Identify the Atomic Design level of what you need (Base asset, Atom, Molecule, Organism, or Template) using the table above.
2. Go to that level's divider page, then open the specific component page right after it.
3. Read the Header block at the top of each variant frame for context.
4. Pick the `Light` or `Dark` component set for your theme, then filter by the `Size` / `Structure` / `Align` / `Status` variant properties to get the exact instance you need.
