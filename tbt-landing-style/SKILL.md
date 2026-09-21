---
name: tbt-landing-style
description: Design and build Thai-language marketing or landing pages in the TBT style — navy + red, soft playful shapes, hand-drawn annotations, illustrated SVG scenes instead of stock photos, and spoken-Thai copy. Use when asked for a landing page, หน้าแรก, marketing site, or a redesign in this style, and when extending an existing page that already uses it.
---

# TBT landing style

A warm, sales-minded look for Thai B2B landing pages. Light backgrounds, one navy
for structure, one red for action, chunky friendly shapes, and small hand-drawn
notes that make interactive parts feel inviting. Everything illustrated is drawn
as inline SVG — never stock photography.

## 1. Tokens

Colour — two brand colours, everything else is a cool neutral.

| Role | Value | Where |
|---|---|---|
| Ink / structure | `#16284A` | headings, body emphasis, icons, dark bands, logo |
| Action | `#E4002B` | primary buttons, prices, active nav underline, handwriting |
| Action (pressed/dark text) | `#C10024` | red text on tinted backgrounds |
| Body text | `#3D5075` | list items, paragraphs inside cards |
| Muted | `#5A6B85` → `#8496AE` → `#9BAAC0` | lead paragraphs, captions, fine print |
| Border | `#E3E7EE` (`#DDE3EC` inside cards) | every hairline |
| Surfaces | `#FFFFFF`, `#FAFBFD`, `#F2F5FA`, `#F7F9FC` | page, insets, tinted sections |
| Card tints | `#EEF3FB` blue · `#FDECEF` pink · `#EAF7F1` mint · `#F0EFFA` lavender | illustration bands, icon tiles |
| Success | `#12B76A` / `#ECFDF3` / `#027A48` | online dots, "done" pills |
| LINE | `#06C755` | LINE glyph only |

Rules: red is for *doing*, navy for *being*. If more than ~8% of a screen is red,
move something back to navy. Never introduce a third brand hue — vary with tints.

Typography — one family, weight does the work.

- Body + headings: **Anuphan** 400/500/600/700, fallback `'Noto Sans Thai', sans-serif`.
- Handwritten notes only: **Itim**, fallback `cursive`. Never for UI text.
- Headings: `font-weight: 700`, `letter-spacing: -0.018em` … `-0.028em`, `line-height: 1.2–1.45`.
- Fluid sizes: h1 `clamp(34px, 4.3vw, 58px)`, h2 `clamp(28px, 3.4vw, 48px)`,
  card title `clamp(21px, 2vw, 26px)`, body 16–19px.
- `text-wrap: balance` on headings, `text-wrap: pretty` on paragraphs.

Shape and depth — flat and friendly, never glassy.

- Radii: cards `18–20px`, illustration bands inherit the card, buttons/inputs `8–10px`,
  pills and avatars `999px`, icon tiles `17–20px`.
- Borders `1px` (`1.5px` on cards that are also links).
- Shadows are short and low: `0 12px 32px rgba(22,40,74,.10)` at most;
  hover `0 16px 34px rgba(22,40,74,.13)`. No blur above ~34px.
- Hover = lift 6–7px, sometimes a `0.35–0.8deg` tilt. Transition
  `.26s cubic-bezier(.2,.8,.2,1)`.

## 2. Page skeleton

Alternate light and tinted bands so sections separate without heavy rules.

1. **Nav** — white, hairline bottom, logo left, links centre, ghost + red button right.
2. **Hero** — tinted `#F7F9FC`, two columns on desktop, an illustrated skyline pinned
   to the bottom edge, one interactive thing on the right.
3. **Logo marquee** — one line of channel chips scrolling, white edge fades, pauses on hover.
4. **Core services** — white, 2×2 cards, each with a coloured illustration band.
5. **How it works** — navy band `#16284A`, 3 steps, white text, red step labels.
6. **Sub-services** — tinted band, 3×3 linked cards with illustrations.
7. **CTA** — bordered card on white, text left, illustration right.
8. **Footer** — 4 link columns, then a fine-print bar.

Each section: `display:flex; justify-content:center;` with
`padding-inline: clamp(18px, 4vw, 72px)` and an inner
`width:100%; max-width:1296px` wrapper. The section paints the background full-bleed,
the wrapper holds the content.

## 3. Component recipes

**Section header** — no eyebrow labels. Straight to `h2`, then a muted lead line
(max ~660px). If the header carries a button, `flex-wrap: wrap` with `gap: 28px 48px`.

**Service card** — a link-looking card, top to bottom:
illustration band on a tint (full-bleed inside the card, `width:100%; height:auto`),
benefit headline in spoken Thai, the official product name in 14px `#9BAAC0`,
three check bullets (22px filled circle in the card's tint colour, white tick),
a dashed `1.5px` divider, then a text CTA `สนใจอันนี้ →` in the card's colour.
Keep the bullet count equal across cards in a row — split a long bullet rather than
invent a new one.

**Sub-service card** — whole card is an `<a>`: illustration band on top, title below.
Signal clickability with hover (lift + title turns red), never with an arrow button —
users disliked the floating circular ↗.

**Step card** (on navy): `background: rgba(255,255,255,.06)`,
`border: 1px solid rgba(255,255,255,.15)`, illustration on `rgba(255,255,255,.05)`,
a red pill label (`ขั้นที่ 1`), white title, `#9FB0C8` body. Red circular arrows
between cards on wide screens, hidden when they stack.

**Interactive hero** — the strongest device in this style. A chat panel the visitor can
actually type in: header (avatar, name, green online pill), scrolling message list,
quick-reply chips for the first turn, composer with a red send button. On send, append
the user's bubble, show a three-dot typing indicator for ~850ms, then reply with result
cards. Every first-run hint (chips, handwriting, pulsing send button) disappears once
the visitor has sent one message.

## 4. Playful devices

**Hand-drawn annotations** — an Itim line plus a curved SVG arrow that draws itself:

```css
.draw{stroke-dasharray:190;stroke-dashoffset:190;animation:draw 1.1s ease-out .35s forwards}
@keyframes draw{to{stroke-dashoffset:0}}
.wiggle{animation:wiggle 2.9s ease-in-out infinite}
@keyframes wiggle{0%,100%{transform:translateY(0) rotate(0)}50%{transform:translateY(-6px) rotate(-1.6deg)}}
```

Arrow paths are a single curve plus a two-segment head, `stroke-width: 2.4`,
`stroke-linecap: round`, in the action red. Use at most **two per page** and point
them at something the visitor should touch. Give them room — never let one land on a
busy background.

**Illustrated scenes** instead of icons wherever there is space: a `viewBox` about
`320×120` (cards) or `640×178` (wide bands), flat shapes in the brand colours at
`opacity .08–.9`, white for highlights, rounded corners everywhere, a soft ground line.
Draw the actual mechanism — a house flying to three platform boxes, a radar with a
notification bell — not a generic glyph.

**Ambient motion**, all slow and optional: drifting clouds, a bobbing balloon,
a pulsing status dot, a marquee that pauses on hover, a `ping` ring on the primary
button until first use.

## 5. Copy

- Write the way a salesperson talks. `ลงประกาศให้เอง แล้วดูสถิติย้อนหลังได้`,
  not `ระบบโพสต์ทรัพย์อัตโนมัติพร้อมติดตามสถิติ`.
- Card headline = the benefit. Put the official product name underneath in small grey.
- Headlines under ~40 Thai characters. Add `white-space: nowrap` to pills so they
  never break to two lines.
- **Never invent a fact.** No made-up statistics, testimonials, prices or customer
  counts. Missing values are visible placeholders: `[ราคา]`, `[LINE ID]`, `[เบอร์ติดต่อ]`.
- Strip partner-specific wording when the page is meant to sell to everyone —
  internal system names and partner brands make it unsellable elsewhere.
- Mark obvious mockups: a `CONCEPT UI / SAMPLE DATA` note in the footer bar.

## 6. Responsive — and the four traps

Breakpoints: **1080px** nav collapses to a burger · **960px** hero stacks and
everything centres · **640px** grids drop to one column · **560/420px** shed
secondary nav buttons.

Grids use fixed column counts with explicit breakpoints, not `auto-fit`:

```css
.g2{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:26px}
.g3{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:22px}
.g4{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:36px}
@media(max-width:1140px){.g4,.g3{grid-template-columns:repeat(2,minmax(0,1fr))}}
@media(max-width:1020px){.g2{grid-template-columns:1fr}}
@media(max-width:640px){.g4,.g3{grid-template-columns:1fr}}
```

**Trap 1 — inline `style` beats every media query.** A `style="display:flex"` or
`style="align-self:flex-start"` can never be overridden by a stylesheet rule without
`!important`. Anything a breakpoint needs to change — `display`, `flex`, `align-self`,
`align-items`, `text-align` — must live in a class from the start. This is the single
most common cause of "the responsive layout is broken".

**Trap 2 — wrapping is container-based, centring is viewport-based.** `flex-wrap`
fires on the container's width, a media query on the window's. If they disagree you
get a stacked layout that is still left-aligned. Size the flex bases so they wrap at
exactly the breakpoint: `440px + 476px + 44px gap = 960px`.

**Trap 3 — exported or embedded HTML may sit in a shrink-to-fit host.** Then
`width:100%` resolves against a box narrower than the window. Pin the chain:

```css
html,body{margin:0!important;padding:0!important;width:100%!important;overflow-x:hidden}
x-dc,x-dc>*,#root,#app{width:100%!important;max-width:100%!important;box-sizing:border-box}
```

and give the page root `width:100vw; max-width:100vw`.

**Trap 4 — `auto-fit` orphans.** `repeat(auto-fit, minmax(…))` will happily leave one
card alone on the last row at mid widths. Fixed counts per breakpoint never do.

Mobile menu is real state, not CSS-only: a burger toggles a panel below the bar with
52px link rows and full-width buttons; tapping a link closes it.

## 7. Before shipping

- Render at 1440 / 960 / 700 / 390 and look at every band.
- Nav: one row at every width; burger appears exactly when the centre links vanish.
- No annotation, pill or heading wraps awkwardly or overlaps artwork.
- Bullet counts match across cards in the same row.
- Every interactive element is a real `<button>`, `<a href>` or `<input>` with a
  `<label>`; icon-only buttons carry `aria-label`.
- Body text ≥ 4.5:1 against its background; muted greys on tints are the usual failure.
- No invented facts left; placeholders still in brackets.
