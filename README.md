# JondriDev Design System

**Earth · Glass · Future** — the visual foundation for every JondriDev app.

JondriDev is an ecosystem of mobile-first apps built by a self-taught Indonesian
developer. Everything shares one account, one cloud, and this single design
system. It is bilingual (EN / ID) and ships both dark and light themes (dark is
the default in `prefers-color-scheme: dark` environments).

Two non-negotiables:

1. **Earth-from-Space palette** — deep ocean, shallow cyan, land green, desert
   sand, cloud white, atmosphere haze, aurora glow, city-light amber. Warm,
   planetary, slightly romantic.
2. **Liquid Glass** UI — near-transparent fills, heavy backdrop blur, directional
   edges (bright top-left, dim bottom-right), a thin inset specular at the top,
   a dark rim at the bottom, and a faint prismatic edge ring. Inspired by Apple's
   Liquid Glass.

## Structure

| File | Purpose |
|---|---|
| `index.html` | The single-page showcase — four tabs (Design · UI Kit · Tokens · Account), language + theme toggles, the full component layer. Open it directly in a browser; no build step. |
| `colors_and_type.css` | The reusable foundation: design tokens (colors, glass, spacing, radius, opacity, z-index, motion, layout) + semantic type classes + local `@font-face`. **Copy this into every app.** |
| `fonts/` | Sora (weights 100–800, local `.ttf`) + the SIL Open Font License. JetBrains Mono is still loaded from the Google Fonts CDN. |

## Colors — two deliberate layers

The Earth-from-Space identity exists in **two parallel token sets**:

1. **Brand / accent (`--c-*`)** — *vivid, stylized.* Powers gradients, the logo,
   buttons, badges, status dots, app accents. Saturated on purpose — this is the
   identity, not a literal photo.
2. **Photographic (`--earth-*`)** — *muted, literal.* Sampled from NASA Blue
   Marble / ISS night-side composites. Use for backgrounds, swatches, hero
   washes, imagery overlays.

**Rule:** never use `--earth-*` for buttons/badges (too low-contrast) and never
use the vivid `--c-*` for a full-bleed "satellite" background (too cartoon).
Backgrounds are multi-stop radial gradients, never flat color.

### App accents

| App | Role | Accent | Hex |
|---|---|---|---|
| **Keuangan** | Finance tracker | Aurora glow | `#66d9a0` |
| **Kamus** | Dictionary | Shallow cyan | `#1a8caa` |
| **Kosakata** | Vocabulary trainer | Desert sand | `#c4a265` |
| **Pembaca** | Book reader | City lights | `#f0c94e` |
| **Cakra** | AI assistant | Atmosphere | `#5b8fb9` |

## Typography

- **Sora** — everything display, heading, UI, body. **Weight 800 (ExtraBold) is
  the heaviest cut shipped — never specify 900** (it triggers fake-bold
  synthesis). 800 for display/h1/h2; 700 for h3 / buttons; 500 for inputs; 400
  for body.
- **JetBrains Mono** — stat values, labels, tokens, code, eyebrow micro-type.
- Body line-height is `1.75` — unusually generous, for relaxed mobile reading.

## Liquid Glass recipe

Every surface uses the `.gl` class, driven by `--gl-*` tokens:

1. **Top specular line** — bright inset highlight. This is what reads as "glass."
2. **Bottom dark rim** — gives the lens bottom weight.
3. **Prismatic edge ring** — a faint conic gradient on the 1px border (`.gl::before`).
4. **Directional border** — bright top-left, dim bottom-right.
5. **Near-zero fill** — the blur does the work, not opacity.

Navbar / bottom nav use a stronger blur (`blur(32px)`) than cards. **Never nest
`.gl` inside `.gl`** — compound glass looks muddy. True refraction
(`feDisplacementMap`) is opt-in for one hero surface per screen, never on
repeated cards (it tanks mobile-Safari scroll performance).

## Accessibility

- **Visible focus.** Every interactive element gets a 2px `:focus-visible` aurora
  outline; inputs additionally show a 28%-alpha aurora ring (≥3:1 contrast — the
  old 8% cyan ring failed WCAG).
- **`--text3` is decorative only** (eyebrow labels, chevrons) — it fails AA for
  body copy. Use `--text2`/`--text` for readable prose.
- **Emoji icons** carry `aria-label` when they stand alone, and `aria-hidden`
  when adjacent visible text already names them.
- **Toggles announce state** via `aria-pressed`; the language pair is a labelled
  `role="group"`.
- **Reduced motion** clamps all animation/transition to `0.01ms`.

## Voice & copy

Bilingual, confident, compact. Title Case for headings/badges, UPPER CASE +
wide tracking for eyebrow labels. Signature punctuation: middle dot `·` as a
connector (`Earth · Glass · Future`), `→` after CTAs, em-dash `—` for asides.
Emoji is a first-class icon system — each app has a fixed emoji
(💰 Keuangan · 📖 Kamus · 🧠 Kosakata · 📄 Pembaca · 🤖 Cakra); don't strip them.
Write every user-facing string in both EN and ID.

---

_Implemented from a Claude Design handoff bundle. Foundation tokens live in
`colors_and_type.css`; the showcase composes them in `index.html`._
