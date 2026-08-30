---
name: layout-grid-system
description: |
  Grounds web and mobile page design in a consistent layout and grid system — column and row
  structure, spacing scale, responsive breakpoints, and named layout presets (landing page,
  sidebar, board, modular). Produces a wireframe-level layout spec plus 2-3 layout explorations
  before any visual design. Use when user asks to "design a page layout", "explore layouts for
  this screen", "what grid should I use", "wireframe this page", "make this responsive", or
  "apply our grid system". Do NOT use for usability critique of an existing screen — use
  ux-heuristic-review instead. Do NOT use for colors, type or logo — use captech-brand-styling.
cowork:
  category: custom
  icon: Grid
---

## Overview

A grid is the invisible structure behind a good layout. This skill picks the right grid for a
screen, states it in concrete numbers (columns, gutters, margins, spacing), and shows a few
layout explorations so structure gets decided before pixels do.

## When to Use

- Starting a new web or mobile screen and you need a structure to design against
- Exploring two or three layout directions for the same content
- Deciding how many columns a page needs, or how it should reflow on smaller screens
- Auditing an existing layout for alignment, spacing, or hierarchy problems

## When NOT to Use

- Usability or heuristic critique of a built screen — use `ux-heuristic-review` instead
- **Tiebreaker when a request mixes both** (e.g. "review this checkout flow — the spacing feels
  off"): if the ask is *what is wrong*, it is a critique → `ux-heuristic-review`. If the ask is
  *what should it be instead*, it is structure → this skill. When genuinely both, do the layout
  work and say plainly that a usability review is the other half.
- Brand colors, typography, logo usage, or approved photography — use `captech-brand-styling`
- Building the deck or document that presents the layouts — use `pptx` or `docx`
- Writing production CSS or components — this skill defines structure, not code

## Core Instructions

### Step 1 — Establish the brief

First, check the conversation's attached files and the workspace `input/` folder for screenshots,
mockups, or an existing design. If one is there, read it and **extract the current grid before
proposing anything** — column count, apparent margins and gutters, and where alignment already
breaks. Say what the existing structure is, then offer alternatives against it.

**If an attached design cannot be read, do not stop.** Say clearly that it could not be read,
continue down the no-existing-design path with the defaults below, and note that resending it
would let you match the live layout. Only block and ask when the user's request depends on that
file ("match this design", "fix the grid on this screen") — then the file *is* the brief.

Then capture, or infer: the page type, the primary content blocks, the one action or message
that matters most, and the target device. If the page type is unclear, ask once with
`AskUserQuestion`; otherwise assume responsive web, mobile-first.

**If the brief is thin, do not quietly invent one.** Proceed with the defaults below and list
your assumptions under an "Assumptions" heading so the user can correct them in one pass.

### Step 2 — Choose the grid type

| Grid | Use it for |
|---|---|
| Single column | Simple, text-heavy content; most mobile screens |
| Multi-column | Content-rich pages and marketing sites |
| Modular (columns × rows) | Complex interfaces, dashboards, product catalogs |
| Baseline | Vertical rhythm — aligning text and elements down the page |

### Step 3 — Set the anatomy in numbers

State all four, every time:

- **Margin** — space around the content
- **Column** — vertical divisions the content sits in
- **Gutter** — space between columns
- **Module** — the individual cell where content lives (modular grids only)

**Vertical rhythm.** Columns and gutters are horizontal; rows need a rule too. Set a **row module
height of 96px** and use only multiples or halves of it (48, 96, 192, 384). This keeps vertical
measurements on the same scale as horizontal ones — never pick a row height off-scale.

Defaults unless the user has a system already:

| Breakpoint | Width | Columns | Gutter | Margin |
|---|---|---|---|---|
| Mobile | < 768px | 4 | 16px | 16px |
| Tablet | 769–1024px | 8 | 24px | 24px |
| Desktop | > 1024px | 12 | 24px | 32px or 64px |

**Choosing the desktop margin:** use **32px** for dense, functional screens (dashboards, apps,
data tools) where horizontal space is the scarce resource. Use **64px** for marketing and
editorial pages where outer breathing room carries the tone. Pick one of the two — not a value
in between.

### Step 4 — Apply the spacing scale

Use a 4px base unit and scale consistently: **4, 8, 16, 24, 32, 48, 64, 96**. Never invent an
in-between value. Tighter spacing groups related items; wider spacing separates sections.

### Step 5 — Pick layout presets for the explorations

Choose from this library, naming each one:

- **Default** — full-bleed single region
- **Landing page** — stacked full-width bands (hero, proof, features, CTA)
- **2 / 3 / 4 / 5 column grid** — equal vertical divisions
- **2 / 3 / 4 / 5 rows** — horizontal bands for sequential content
- **Left sidebar** — persistent nav or filters, content right
- **Right sidebar** — content left, supporting or contextual panel right
- **3 / 4 column board** — kanban or card-collection layouts

Offer **2–3 distinct explorations**, not variations of one idea, and say what each optimizes for.

**When the content fits no preset**, say so plainly rather than forcing it. Either combine two
presets (e.g. left sidebar + 3-column board) and name the combination, or define a custom
structure and state which principle drove it.

**Tools:** the markdown output below is always the deliverable. `render_ui` is an *optional
addition* when there are 3+ explorations and a side-by-side comparison table would help the user
choose — never a replacement for the written spec. When the explorations are going into a deck or
a handoff document, hand off to `pptx` or `docx` rather than building the file here.

### Step 6 — Check it against the layout principles

Before presenting, verify each: **visual hierarchy** (size, contrast and spacing point at what
matters most), **alignment** (everything snaps to the grid), **spacing** (consistent rhythm and
breathing room), **balance** (visual weight distributed, not pooled), **contrast** (used to
create emphasis and guide attention).

### Step 7 — Define the responsive behavior

Mobile-first: design the smallest screen, then expand. For each exploration, state what happens
at each breakpoint — which columns collapse, what stacks, what gets hidden or moved.

### Step 8 — Self-check before presenting

Verify every number traces back to the breakpoint table or the spacing scale — no one-off
values. Confirm each exploration is structurally distinct, names its tradeoff, and states its
mobile behavior. Fix anything that fails before showing the user.

## Output format

Copy this template exactly, every run. Keep it short and scannable.

```markdown
## Grid spec
| Breakpoint | Columns | Gutter | Margin |
|---|---|---|---|
| Mobile (<768px) | … | … | … |
| Tablet (769–1024px) | … | … | … |
| Desktop (>1024px) | … | … | … |

Grid type: [single / multi-column / modular / baseline]
Spacing scale: 4, 8, 16, 24, 32, 48, 64, 96
Row module: 96px (use 48 / 96 / 192 / 384)

## Assumptions
- [only when the brief was thin — otherwise omit this section]

## Exploration A — [preset name]
[block-diagram wireframe]
Optimizes for: [one line]   Tradeoff: [one line]

## Exploration B — [preset name]
[same shape — repeat this block once per exploration, lettered A, B, C]

## Responsive notes
- A: [what collapses / stacks / hides, mobile → desktop]
- B: […]  (one line per exploration you produced)

## Recommendation
[One pick, one sentence of why.]
```

Wireframe block style:

```
Left Sidebar  |  12-col desktop
+------+---------------------------+
| nav  |  header (8 col)           |
| 3col |---------------------------|
|      |  content grid (3 × 3 mod) |
+------+---------------------------+
Mobile: nav collapses to top bar, content stacks 1-col
```

## Guardrails

- **Structure before style.** Never introduce color, typefaces, imagery, or brand elements — hand
  those off to `captech-brand-styling`.
- **Every number comes from the system.** Column counts, gutters, margins, and spacing use the
  values above or the user's own system — never an arbitrary one-off value.
- **Always give more than one option** unless the user asked for a single layout.
- **Never invent the user's existing design tokens.** If they mention a design system you cannot
  see, ask for the values or clearly mark them as assumptions.
- **Name the tradeoff.** Every exploration states what it optimizes for and what it costs.
- **Accessibility floor:** minimum 44×44px touch targets on mobile, and a logical reading order
  that matches the visual order.
- **If an attached design cannot be read**, say so and ask for it again — never describe a layout
  you could not actually see.
- **If the content will not fit a preset**, say so rather than forcing it into the closest one.
- **State assumptions out loud** whenever the brief was incomplete; never present a guess as a
  given.
