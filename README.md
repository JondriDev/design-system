# XENO · JondriDev Design System

**A first-contact interface** — the visual foundation for every JondriDev app.

JondriDev is an ecosystem of mobile-first apps built by a self-taught Indonesian
developer. Everything shares one account, one cloud, and this single design
system. It is bilingual (EN / ID) and ships both dark and light themes (dark
"Void" is the default).

Two non-negotiables:

1. **Deep-Field palette** — a void backdrop with bioluminescent signals: signal
   teal, aurora green, plasma violet, ion blue, ember warm, xenon glow. Cold,
   precise, slightly otherworldly — technology that doesn't look like it's from
   here.
2. **Holographic Glass** — near-invisible fills, heavy backdrop blur, a single
   bright signal rim (top-left) fading to a dark void edge (bottom-right), and a
   faint scanline texture beneath, as if the surface is being read by something.

## Structure

| File | Purpose |
|---|---|
| `index.html` | The single-page showcase — four tabs (System · Kit · Tokens · Network), language + theme toggles, the full component layer, a living constellation backdrop. Open it directly in a browser; no build step. |
| `colors_and_type.css` | The reusable foundation: design tokens (palette, holo glass, spacing, radius, opacity, z-index, motion, layout) + semantic type classes + the `.holo` recipe + local `@font-face`. **Copy this into every app.** |
| `fonts/` | Sora (weights 100–800, local `.ttf`) + the SIL Open Font License. JetBrains Mono loads from the Google Fonts CDN. |

## Palette — Deep Field

| Token | Role | Hex |
|---|---|---|
| `--signal` | Primary · bioluminescent teal | `#34F5D6` |
| `--aurora` | Green | `#5CF0A8` |
| `--ion` | Electric blue | `#4D9BFF` |
| `--plasma` | Rare violet (accent) | `#B06BFF` |
| `--ember` | Warm signal / warning | `#FF9B6B` |
| `--xenon` | Pale luminescence / glow | `#D6FBF4` |
| `--void` | Deep-field backdrop | `#03060E` |

Backgrounds are multi-stop radial gradients over `--void`, never flat color.

### App accents

| App | Role | Accent | Hex |
|---|---|---|---|
| **Keuangan** | Finance tracker | Aurora | `#5CF0A8` |
| **Kamus** | Dictionary | Signal | `#34F5D6` |
| **Kosakata** | Vocabulary trainer | Ember | `#FF9B6B` |
| **Pembaca** | Book reader | Ion | `#4D9BFF` |
| **Mesin** | Terminal emulator | Pale signal | `#9BF7E6` |
| **Cakra** | AI agent | Plasma | `#B06BFF` |

## Typography

- **Sora** — everything display, heading, UI, body. Weight **800 is the heaviest
  local cut — never specify 900** (it triggers fake-bold synthesis). 800 for
  display/h1/h2; 700 for h3 / buttons; 500 for inputs; 400 for body.
- **JetBrains Mono** — telemetry, stat values, labels, tokens, glyph data, code,
  eyebrow micro-type. The "alien readout" voice.
- Body line-height is `1.75` — generous, for relaxed mobile reading in the dark.

## Holographic Glass recipe

Every surface uses the `.holo` class, driven by `--holo-*` tokens:

1. **Near-zero fill** — the backdrop blur does the work, not opacity.
2. **Signal rim** — bright bioluminescent edge on top-left.
3. **Void edge** — dark, dim border on bottom-right for weight.
4. **Scanline overlay** — a faint repeating-linear-gradient (`.holo::after`),
   blended `overlay`, so the glass reads as instrumented.

Navbar / bottom nav use a stronger blur than cards. **Never nest `.holo` inside
`.holo`** — compound glass looks muddy.

## The living network

The showcase paints a constellation field behind everything — a starfield plus a
drifting node mesh that links up as nodes near each other. The **Network** tab
renders the ecosystem as one literal node-graph: a CORE identity wired to every
app. The interconnection, made visible.

## Accessibility

- **Visible focus.** Interactive controls get a 2px `:focus-visible` signal
  outline. Switches are real `<button role="switch">` with `aria-checked`.
- **`--text3` is decorative only** (eyebrow labels, chevrons) — use
  `--text2` / `--text` for readable prose.
- **Reduced motion** clamps CSS animation/transition to `0.01ms` **and** omits
  the SVG SMIL pulses on the network graph (CSS alone can't stop SMIL).
- **Token snippets keep their units**, so copy-paste examples are valid CSS.

## Voice & copy

Bilingual, confident, compact. Title Case for headings, UPPER CASE + wide
tracking for eyebrow / telemetry labels. Signature punctuation: middle dot `·`
as a connector, `→` after CTAs, em-dash `—` for asides. Emoji and a constructed
geometric **xeno-script** glyph set serve as the icon language. Write every
user-facing string in both EN and ID.

---

_One account. One mesh. Many instruments._
