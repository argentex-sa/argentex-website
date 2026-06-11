# Argentex Website — Build Brief

*For Claude Code. Paste this whole file into a new Claude Code session in an empty repo and follow it top to bottom.*

---

## 1. What we are building

A single, fast, static company-profile website for **Argentex (Pty) Ltd**, South Africa's first specialist silver recovery operation for end-of-life solar panels.

This is not a marketing funnel. It is an editorial company profile that Argentex points partners, suppliers and potential investors to. It needs to look considered and credible on first load, read clearly, and deploy cleanly to Vercel from GitHub.

One page, anchored navigation. No backend, no database, no CMS, no forms that submit anywhere (contact is a `mailto:` link).

---

## 2. Hard constraints (read before building)

These are non-negotiable. Everything on this site is public, so:

- **Do not** add any financial figures, revenue numbers, margins, yields, recovery rates, or pricing.
- **Do not** name any supplier, recycler, refining partner, or counterparty. No partner logos.
- **Do not** state any commercial deal terms or revenue-share structures.
- **Do not** invent statistics. The only market figure permitted is the "estimated 11 gigawatts" line in the copy below, and it is phrased as an estimate.
- Keep all contact details as clearly marked `TODO` placeholders. Do not guess an email, phone number, or domain.

If a section feels thin without numbers, leave it thin. Restraint is the brand.

---

## 3. Stack and setup

- **Next.js** (App Router) + **TypeScript**, configured for static export (`output: 'export'`).
- **Tailwind CSS** with the custom theme in section 5.
- No external font loading. Use Georgia (system serif) and a system sans stack. This keeps the page fast and is on brand.
- No images required for v1. The design is typographic. If you add any imagery later, keep it restrained and monochrome.
- Deploy target: **Vercel**, from a **GitHub** repo. Both accounts already exist.

### Setup steps

1. Scaffold: `npx create-next-app@latest argentex-site --typescript --tailwind --app --eslint`
2. Apply the Tailwind theme tokens in section 5.
3. Build the single page from the structure and copy in sections 6 and 7.
4. Confirm it builds clean: `npm run build`.
5. Commit and push to the existing Argentex GitHub repo (`git remote add origin <repo-url>`).
6. Import the repo in the Vercel dashboard, or run `vercel` from the CLI. Next on Vercel is zero-config; no `vercel.json` needed.

---

## 4. Design direction

Follow the Argentex Design System (separate file) exactly. Summary for this build:

- Editorial, sober, precise. Reads like a special report, not a startup site.
- Warm paper background, deep ink text, a single oxblood accent used sparingly on small labels and rules.
- Georgia for all headings and body. System sans only for eyebrows, navigation, captions, and the one call to action.
- Border radius 0. No shadows. No cards. No icons in circles. No gradients.
- Hairline rules separate sections. Major sections are marked with a roman numeral in oxblood, because the page builds an argument in sequence.
- The wordmark ARGENTEX in letter-spaced caps is the logo. No symbol needed.
- Body prose justified with `hyphens: auto`, left-aligned under 640px. Prose column capped around 720px.

Take one disciplined risk: the roman-numeral editorial sectioning and the all-type masthead are the signature. Keep everything else quiet.

---

## 5. Tailwind theme tokens

Paste into `tailwind.config.ts` under `theme.extend`:

```ts
extend: {
  colors: {
    paper:      "#F8F6F1",
    "paper-deep":"#F1EDE4",
    ink:        "#1C1B19",
    oxblood:    "#6E2329",
    "oxblood-lt":"#9B4A4F",
    stone:      "#6B655C",
    rule:       "#D8D2C6",
  },
  fontFamily: {
    serif: ['Georgia', '"Times New Roman"', 'serif'],
    sans: ['-apple-system', '"Segoe UI"', 'Roboto', '"Helvetica Neue"', 'Arial', 'sans-serif'],
  },
  maxWidth: {
    prose: "720px",
    page: "1100px",
  },
  borderRadius: {
    none: "0",
  },
}
```

Set the page defaults in `globals.css`:

```css
body {
  background: #F8F6F1;
  color: #1C1B19;
  font-family: Georgia, "Times New Roman", serif;
  font-size: 18px;
  line-height: 1.65;
}
.eyebrow {
  font-family: -apple-system, "Segoe UI", Roboto, Arial, sans-serif;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  font-size: 0.75rem;
  color: #6E2329;
}
.prose-col { max-width: 720px; text-align: justify; hyphens: auto; }
@media (max-width: 640px) { .prose-col { text-align: left; } }
```

---

## 6. Page structure (single page, anchored nav)

```
+--------------------------------------------------+
|  ARGENTEX                  what · why · process · |
|  ____ (oxblood rule)       company · contact      |
+--------------------------------------------------+
|                                                  |
|  [HERO]  Silver recovery for South Africa's      |
|          end-of-life solar panels.               |
|          one-line sub. one CTA -> contact         |
|                                                  |
|  ---- hairline ----                              |
|  I.  The opportunity                             |
|  II. What we do                                  |
|  III. How we work with recyclers                 |
|  IV. Responsibility                              |
|  [reversed ink block: short positioning line]    |
|  V.  Company / team                              |
|  ---- hairline ----                              |
|  [CONTACT]  address, mailto, TODO details        |
|  [FOOTER]  ARGENTEX wordmark, reg name, address  |
+--------------------------------------------------+
```

Header is sticky, paper background, thin rule beneath. Nav links are sans, small, lowercase or sentence case, scroll to anchors. On mobile, collapse the nav to a short list or hide it and rely on scroll.

---

## 7. Copy (use verbatim, this is the approved public wording)

**Hero**
- Eyebrow: `ARGENTEX (PTY) LTD`
- Headline: Silver recovery for South Africa's end-of-life solar panels.
- Sub: We recover precious metals from solar panel back-sheets and silver-bearing e-waste, refine the silver to investment-grade purity, and return it to the South African economy as bullion.
- CTA: Get in touch (anchors to contact)

**I. The opportunity**
South Africa installed an estimated 11 gigawatts of solar capacity through the energy-supply crisis of recent years. Those panels carry a finite life. As they reach the end of it, the glass, the aluminium frames and the junction boxes are already recovered by the country's licensed recyclers. The back-sheet, which holds the silver, is not. Today it is stockpiled, sent to landfill, or exported for processing abroad. The material, and its value, leaves the country. Argentex exists to close that gap at home.

**II. What we do**
We take back-sheet material and silver-bearing e-waste from licensed recyclers and recover the silver through a controlled refining process. The recovered metal is refined to .9999 purity and sold into the bullion market. We carry the processing, the equipment and the operational risk, so our supply partners turn a stockpiled waste stream into recurring value without carrying any of the cost.

**III. How we work with recyclers**
Argentex is built to work alongside the existing recycling industry, not against it. Licensed recyclers already do the heavy work of collection and primary separation. We add the step the local market is missing: commercial silver recovery. Material flows to us, value flows back, and a waste stream that used to carry a disposal cost becomes a source of revenue.

**IV. Responsibility**
Recovering silver domestically keeps both the material and its value inside South Africa, and it keeps end-of-life panel waste out of landfill and out of export containers. We operate to the environmental and licensing standards the work demands, with traceability from the input material through to the refined metal.

**Reversed positioning line** (ink block)
The first commercial silver recovery operation built for South Africa, by people who know its solar and refining industries.

**V. Company**
Argentex brings together commercial, operational and technical experience drawn from the South African solar and refining industries.
- Angus Henderson, Co-Founder. Strategy and commercial.
- Beyers Visagie, Managing Director. Operations, supplier development and plant management.
- Andrew Martin, Co-Founder. Technical and refining.

**Contact**
Argentex (Pty) Ltd
39A First Avenue East, Parktown North, Johannesburg, 2193
Email: TODO confirm address
Telephone: TODO confirm number

**Footer**
ARGENTEX (wordmark) · Argentex (Pty) Ltd · 39A First Avenue East, Parktown North, Johannesburg 2193 · © 2026

---

## 8. Acceptance criteria

- `npm run build` produces a clean static export with no errors.
- Renders correctly on mobile (360px) through desktop (1440px).
- Matches the design system: paper background, Georgia type, oxblood accent only on labels and rules, zero radius, no shadows.
- Keyboard focus is visible; colour contrast clears AA; `prefers-reduced-motion` respected if any animation is added.
- No financial figures, no partner names, no deal terms anywhere in the output.
- All contact details remain marked `TODO`.
- Deploys to Vercel from the GitHub repo without extra configuration.

---

## 9. Nice-to-have (only after the above is solid)

- A subtle scroll-triggered fade-in on each section as it enters view, respecting reduced motion. Keep it slight.
- A `/favicon`: the letter A in Georgia on paper, or the oxblood square. Nothing elaborate.
