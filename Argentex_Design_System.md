# Argentex Design System

*Version 1.0 — June 2026*

This is the single reference for how Argentex looks and reads across everything: the website, letters, decks, the company profile, and email signatures. It formalises the Bureau editorial style already in use so that any document or page can be built to match without guessing.

The intent: Argentex should read like a serious special report, not a startup landing page. Typography and ruled lines do the work. There is no decorative chrome, no rounded cards, no drop shadows, no icons sitting in coloured circles.

---

## I. Brand essence

Understated, editorial, and precise. The reader should feel they are looking at something considered and grown-up. Every page earns attention through clarity and restraint rather than through colour or movement.

Three words: editorial, exact, sober.

What to avoid: hype, exclamation marks, gradient backgrounds, glassy cards, stock photography of handshakes, anything that looks like a generic SaaS template.

---

## II. Colour

A narrow, warm palette. Oxblood is the only accent and it is used sparingly, mostly on small labels and rules.

| Role | Name | Hex | Use |
|---|---|---|---|
| Background | Paper | `#F8F6F1` | Default page and document background |
| Background alt | Paper Deep | `#F1EDE4` | Subtle panel shading, table stripes |
| Text | Ink | `#1C1B19` | Body text, headings |
| Accent | Oxblood | `#6E2329` | Eyebrows, section labels, rules, links |
| Accent light | Oxblood Light | `#9B4A4F` | Hover state, reversed-section accent |
| Secondary text | Stone | `#6B655C` | Captions, footnotes, metadata |
| Hairline | Rule | `#D8D2C6` | Dividers, table borders, underlines |

**Reversed sections** (used for visual rhythm, sparingly):
- Background: Ink `#1C1B19`
- Text: Paper `#F8F6F1`
- Accent: Oxblood Light `#9B4A4F`

Contrast note: Ink on Paper and Paper on Ink both clear WCAG AA for body text. Stone is for non-essential secondary text only.

---

## III. Typography

Two roles. A serif carries everything editorial. A sans handles small utility text only.

**Editorial serif: Georgia.** Headings and body. Georgia is on every machine, so no font loading, which keeps pages fast and on brand. This is deliberate, not a fallback.

**Utility sans: a clean system sans.** Eyebrows, section labels, captions, navigation, buttons, table headers. On documents this role is Calibri. On the web use the system stack below, which sits close to Calibri in warmth:

```
-apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif
```

### Type scale

| Token | Size | Line height | Face | Notes |
|---|---|---|---|---|
| Display | 3rem | 1.1 | Georgia | Hero headline only |
| H1 | 2.25rem | 1.15 | Georgia | Page title |
| H2 | 1.625rem | 1.2 | Georgia | Section heading |
| H3 | 1.25rem | 1.3 | Georgia | Sub-heading |
| Body | 1.125rem | 1.65 | Georgia | Default prose (18px) |
| Small | 0.9375rem | 1.5 | Sans | Captions, footer |
| Eyebrow | 0.75rem | 1.4 | Sans | Caps, tracked +0.12em, oxblood |

### Rules for type

- Body prose is justified with `hyphens: auto`. On narrow viewports (under 640px) fall back to left-aligned for readability.
- Measure for prose blocks: 62 to 68 characters. Do not let lines run full width.
- Headings are left-aligned, never centred except the hero.
- Eyebrows are short sans caps in oxblood, tracked out, sitting above a heading.
- Numbers in running text are conservative and defensible. No invented figures.

---

## IV. Layout

Single-column editorial. Wide outer margins, a narrow column of text. The page should breathe.

- Page frame max width: 1100px, centred.
- Prose column max width: 720px.
- Section vertical rhythm: 5rem to 7rem between major sections on desktop, 3rem on mobile.
- Baseline spacing unit: 8px. Use multiples (8, 16, 24, 32, 48, 64).
- Border radius: 0. Nothing is rounded.
- Shadows: none.

### The signature device

Major sections in a briefing or on the site are marked with a **roman numeral** (I, II, III) set in oxblood sans caps, followed by the section title in Georgia. This is the element Argentex is remembered by. Use it only where the sections form a genuine reading sequence, the way a report builds an argument, not as decoration on an unordered list.

A thin oxblood or hairline rule separates major sections.

---

## V. Components

**Masthead / wordmark.** The word ARGENTEX set in Georgia or sans caps, letter-spaced (+0.18em), in Ink. A 1px oxblood rule sits beneath it. This is the logo. No symbol is required; the wordmark is the mark.

**Eyebrow label.** Sans, caps, tracked, oxblood, sitting above a heading. Example: `WHAT WE DO`.

**Section header.** Roman numeral in oxblood, then the title in Georgia H2.

**Divider.** A full-width hairline rule in `#D8D2C6`, or a shorter oxblood rule for emphasis.

**Link.** Ink text with a 1px oxblood underline at rest. On hover the text shifts to oxblood. No colour-filled buttons unless a call to action genuinely needs the weight.

**Call to action.** Preferred: a bordered rectangle, 1px Ink border, Ink text, transparent fill, sans caps tracked, square corners. Fills to Ink with Paper text on hover. Use at most one per view.

**Reversed feature block.** Ink background, Paper text, used once or twice per page for rhythm. Keep the same type and spacing rules.

**Table.** Hairline borders on every cell. Sans caps header row. Generous cell padding (12px to 16px). Optional Paper Deep stripe on alternate rows.

**Footer.** Hairline rule on top, sans small text in Stone, wordmark repeated, registered name and address.

---

## VI. Voice

The way Argentex writes is part of the design.

- Plain, confident, specific. State things; do not sell them.
- No exclamation marks. No hype words.
- No em dashes and no en dashes. Use commas, full stops, or rewrite the sentence.
- Straight quotes and straight apostrophes, never curly.
- Sentence case for headings and buttons.
- Numbers are conservative. Any figure that appears must be defensible. Upside is a bonus, never a forecast.
- Never reach for AI phrasing such as "I'd suggest" or "let's dive in". Write the way a careful person writes.

---

## VII. Quick token reference (for build tools)

```
colour:
  paper        #F8F6F1
  paper-deep   #F1EDE4
  ink          #1C1B19
  oxblood      #6E2329
  oxblood-lt   #9B4A4F
  stone        #6B655C
  rule         #D8D2C6

type:
  serif  Georgia, "Times New Roman", serif
  sans   -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif

radius: 0
shadow: none
unit:   8px
prose-measure: 720px
page-max: 1100px
```
