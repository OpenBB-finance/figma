# OpenBB Workspace — Figma File Guide

> **File:** [OpenBB Workspace](https://www.figma.com/design/CGw3LHItVogmCC1CHP0bNi/OpenBB-Workspace) UI/UX mockups for every product area of OpenBB Workspace — login, onboarding, navigation, dashboards, widgets, AI, admin, sharing, settings, and more.
>
> **Local file:** `workspace.fig` (this folder) · **Back to overview:** [../README.md](../README.md)

## Table of contents

- [Page structure](#page-structure)
- [Status legend](#status-legend)
- [Documentation components](#documentation-components)
- [Inside a Mockups page](#inside-a-mockups-page)
- [Dark / Light versions](#dark--light-versions)
- [Notes & annotations](#notes--annotations)
- [Quick navigation guide](#quick-navigation-guide)

## Page structure

Every product area is built from the same repeating trio of top-level pages, always in this order:

```
🎯 DASHBOARD (WIDGETS)          ← 1. Area title — visual divider, no content
—  Mockups 🟢                   ← 2. Screens live here
----------------------          ← 3. Separator — empty, purely visual
```

| #   | Page                       | Purpose                                                          |
|-----|----------------------------|------------------------------------------------------------------|
| 1   | `<emoji> AREA NAME`        | Divider that labels the start of a new product area. No content. |
| 2   | `— Mockups <status emoji>` | Where the actual screens/frames for that area live.              |
| 3   | `----------------------`   | Empty divider marking the end of the area.                       |

Larger areas split step 2 into **several Mockups pages**, one per sub-flow, instead of a single page:

```
📕 LIBRARY: APPS
—  Mockups: General 🟢
—  Mockups: Marketplace 🟢
—  Mockups: Submission Flow 🟢
----------------------
```

Seen on: `LIBRARY: APPS`, `AI COPILOT`, `ADMIN PORTAL`.

## Status legend

The emoji at the end of a `— Mockups` page name reports the overall status of that area:

| Dot | Meaning          |
|-----|------------------|
| 🟢  | Approved / Final |
| 🟡  | Work in Progress |
| 🔴  | Cancelled / Test |

The same three states are also used per-screen, via the `Status` badge component described below.

## Documentation components

The `🧩 Mockups information` page (near the start of the file) has no mockups of its own — it's the **component library used to document every other page**:

| Component                     | What it's for                                                                                                                                                 |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Header`                      | Applied above a documented screen/section: Status badge, title + description + release, Owner + Jira ticket links, and separate Content/Design status badges. |
| `Status` (badge)              | The 🟢/🟡/🔴 states from the legend above, as a reusable component.                                                                                           |
| `Status` (Content vs. Design) | Tracks copy and visual design completion independently — a screen's text can be `Complete` while its design is still `Work in progress`, or vice versa.       |
| `Screen notes`                | Free-text block for general context about a screen.                                                                                                           |
| `Action`                      | Free-text block describing the user interaction being shown.                                                                                                  |
| `User story`                  | Free-text block for the user story behind the flow.                                                                                                           |

## Inside a Mockups page

Content is nested two levels deep:

```
—  Mockups 🟢
├─ Section: "Share a Dashboard — FLOW"
│   ├─ Frame: Share Dashboard (dropdown menu)
│   ├─ Frame: Share Dashboard (modal, first share)
│   ├─ Frame: Share Dashboard (modal, already shared)
│   └─ Note: "To share a dashboard from the side bar: click the 3 dots → Select 'Share'"
├─ Section: "Delete shared dashboard"
│   └─ ...
└─ Section: "invite and remove users"
    └─ ...
```

- **Sections** group frames belonging to the same flow (e.g. a specific user journey or interaction).
- **Frames** inside a section are the individual screens for that flow.

## Dark / Light versions

There's no separate "dark" or "light" page — both themes live side by side, inside the same frame or section, distinguished by naming:

- `Side Bar — Dark` / `Side Bar — Light`
- `Navigation dark` / `Navigation light`
- Widget instances with the variant spelled out, e.g. `Terminal PRO - Widgets - Company News - Default/Light/Professional`

## Notes & annotations

Two patterns are used to document behavior directly on the canvas:

- **Loose text nodes** next to a frame, e.g. `"while the other flow is not implemented - add tooltip with information"`.
- **`Note` frames** — a dedicated frame with step-by-step instructions, e.g. `"Note: To share a dashboard from the side bar: Click on the 3 dots → Select 'Share'"`.

## Quick navigation guide

1. Find the area title page for the feature you need (e.g. `🎯 DASHBOARD (WIDGETS)`).
2. Move to the `— Mockups` page(s) right after it — that's where the screens are.
3. Open the **Section** matching the flow you're after.
4. Check frame names for `Dark`/`Light` to find the theme variant you want.
5. Read nearby `TEXT` notes or `Note` frames for behavior context.
6. Check the `Status` badge on each screen/section against the [legend](#status-legend) to know if it's approved, WIP, or cancelled.
