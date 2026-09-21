# tbt-landing-style

A Claude skill that captures the design system behind the ตลาดบ้านที่ดิน (TBT) landing
page — navy `#16284A` + red `#E4002B`, soft playful shapes, hand-drawn annotations,
illustrated inline SVG instead of stock photography, and spoken-Thai sales copy.

Point Claude at it and you can skip most of the prompting: ask for a landing page and
it already knows the palette, the section rhythm, the card recipes, the copy tone, and
the four responsive traps that cost us a dozen rounds to find.

## Install

**Claude Code / Cowork** — copy the folder into your skills directory:

```bash
git clone https://github.com/surakitkun/tbt-landing-style.git
cp -r tbt-landing-style/tbt-landing-style ~/.claude/skills/
```

**Per project** — drop it in `.claude/skills/tbt-landing-style/` inside the repo.

Then just ask: *"ทำหน้า landing ให้หน่อย"* — the skill triggers on its own.

## What's inside

```
tbt-landing-style/
  SKILL.md        the whole design system
reference/
  example.dc.html the page this was extracted from
```

`SKILL.md` covers colour and type tokens, the eight-section page skeleton, component
recipes (nav with a real mobile menu, an interactive chat hero, service / step /
sub-service cards), the playful devices (self-drawing arrows, illustrated scenes,
ambient motion), copywriting rules, and a responsive section that names the specific
traps: inline `style` beating media queries, container-based wrapping fighting
viewport-based centring, shrink-to-fit export hosts, and `auto-fit` grid orphans.

## Adapting it to another brand

Swap the two brand colours in section 1 and keep everything else. The style survives
a hue change because the structure — flat shapes, short shadows, tinted bands, one
typeface, drawn illustrations — is doing the work, not the palette.

## Licence

MIT
